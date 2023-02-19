# Authentication

To connect to the Pinata Submarine API, you will need to generate a Submarine API key. Visit the [Submarine Keys](https://app.pinata.cloud/v2) page to generate new keys.

When you click "New Key", a new key will be generated and the key can be copied from the table directly.&#x20;

Any key can have its access revoked by clicking the Revoke button. Once a key has been revoked, it can no longer be utilized for any purpose.

## Connecting to the Submarine API

The base URL for Pinata requests is: `https://managed.mypinata.cloud/api/v1`

Authentication happens via a customer header:&#x20;

`x-api-key: YOUR SUBMARINE KEY`
