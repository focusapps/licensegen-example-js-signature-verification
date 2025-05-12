# Example Signature Verification
This is an example of [verifying response signatures](https://licensegen.focusapps.app/docs/api#signatures)
using your LicenseGen account's unique Ed25519 public key. You can find your public keys
within [your account's settings page](https://licensegen-admin.focusapps.app/settings).

Verifying response signatures will help prevent man-in-the-middle and replay
attacks, where the attacker redirects traffic from your licensing server
(e.g. LicenseGen) to their own locally controlled server. Other examples are
when you have cached an API response locally and want to verify its integrity
(i.e. it has not been tampered with).

## Running the example

First up, configure a few environment variables:

```bash
# Your LicenseGen account's Ed25519 verify key
export LICENSEGEN_VERIFY_KEY="YOUR_LICENSEGEN_ED25519_VERIFY_KEY"

# LicenseGen product token (don't share this!)
export LICENSEGEN_PRODUCT_TOKEN="YOUR_LICENSEGEN_PRODUCT_TOKEN"

# Your LicenseGen account ID
export LICENSEGEN_ACCOUNT_ID="YOUR_LICENSEGEN_ACCOUNT_ID"
```

You can either run each line above within your terminal session before
starting the app, or you can add the above contents to your `~/.bashrc`
file and then run `source ~/.bashrc` after saving the file.

Next, install dependencies with [`yarn`](https://yarnpkg.comg):

```
yarn
```

Then run the script with the route you want to fetch:

```
yarn start '/licenses/4e7ff22a-4cce-4cbf-a5d4-5e0839b2b7a1'
yarn start '/users/2ed45aa2-b1e9-4ba7-83bb-a037ccf5a85e'
yarn start '/machines?page[number]=1&page[size]=5'
```

The above commands will only succeed if the signature verification is
successful, so be sure to copy your public key correctly. You can find
your public key within [your account's settings page](https://licensegen-admin.focusapps.app/settings).

## Questions?

Reach out at [licensegen@focusapps.app](mailto:licensegen@focusapps.app) if you have any
questions or concerns!
