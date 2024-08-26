---
id: notices
title: Notices

---
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

A notice is a verifiable data declaration that attests to off-chain event and is accompanied by proof. 

Notices provide a mechanism to communicate essential off-chain events in the execution layer to the base layer in a verifiable manner.

For example, in a gaming dApp where players engage in battles, the dApp's backend could generate a notice declaring the victorious player after a match. This notice, containing pertinent off-chain data about the match outcome, is then submitted to the rollup server as evidence of the off-chain event.

## Create a notice

To create a notice, the `Advance` handler sends an output to the rollup server via the `/notice` endpoint:

<Tabs>
  <TabItem value="JavaScript" label="JavaScript" default>
<pre><code>

```javascript
async function handle_advance(data) {
  console.log("Received advance request data " + JSON.stringify(data));

  const inputPayload = data["payload"];

  try {
    await fetch(rollup_server + "/notice", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({ payload: inputPayload }),
    });
  } catch (error) {
    //Do something when there is an error
  }

  return "accept";
}
```

</code></pre>
</TabItem>

<TabItem value="Python" label="Python" default>
<pre><code>

```python

def handle_advance(data):
   logger.info(f"Received advance request data {data}")

   status = "accept"
   try:
       inputPayload = data["payload"]
       ## Send the input payload as a notice
       response = requests.post(
           rollup_server + "/notice", json={"payload": inputPayload}
       )
       logger.info(
           f"Received notice status {response.status_code} body {response.content}"
       )
   except Exception as e:
       #  Emits report with error message here
   return status

```

</code></pre>
</TabItem>

</Tabs>


## Query notices

Frontend clients can query notices using a GraphQL API exposed by the Cartesi Node. To all query notices, you can use the following GraphQL query:

```graphql
query notices {
  notices {
    edges {
      node {
        index
        input {
          index
          timestamp
          msgSender
          blockNumber
        }
        payload
      }
    }
  }
}
```

Refer to the complete [GraphQL reference for querying notices](../graphql/queries/notices.md) using different filters.


## Validate a notice

Crucially, the base layer conducts on-chain validation of these notices through the [`validateNotice()`](../json-rpc/application.md/#validatenotice) function of the `CartesiDApp` contract.

This validation process ensures the integrity and authenticity of the submitted notices, enabling the blockchain to verify and authenticate the declared off-chain events.




