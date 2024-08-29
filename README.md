<h2 align=center>Nillion Verifier Node Guide</h2>

- You can use either VPS or Ubuntu on Windows
- Ubuntu troubleshooting related video is [here](https://x.com/ZunXBT/status/1827779868630876651)
- Make sure that you have a nillion address, if u have not, you can install [Keplr](https://chromewebstore.google.com/detail/keplr/dmkamcknogkgcdfhhbddcghachkejeap) and create a nillion address
- Open your Keplr wallet, search for `nillion`, click on manage chain and the add nillion testnet to your Keplr wallet
- Copy this nillion address from Keplr
- Now request nillion faucet from [here](https://faucet.testnet.nillion.com/)
- Use this command to install docker on your system
```bash
sudo apt update && sudo apt install curl && curl -fsSL https://get.docker.com -o get-docker.sh && sudo sh get-docker.sh
```
- Use this command to pull nillion accuser image
```bash
sudo docker pull nillion/retailtoken-accuser:latest
```
- Use the below command to create a directory and to initialise the accuser
```bash
mkdir -p nillion/accuser && sudo docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:latest initialise
```
- After executing the above command, you will see `accound_id` and `public_key` in your terminal, copy the value
- Now visit [this site](https://verifier.nillion.com/verifier), submit your `accound_id` and `public_key` in the appropriate field
- Visit [faucet site](https://faucet.testnet.nillion.com/) to request faucet in your `account_id` you copied earlier
- Now run this command to get your accuser wallet private key
```bash
cat ~/nillion/accuser/credentials.json
```
- Copy the private key and save it, if you lose, you will not regain access to your accuser wallet
---
<h2 align=center>NOW TAKE A BREAK FOR 60 MINS</h2>

---
- After 60 mins, run these 2 final commands
- Install `jq` now
```bash
sudo apt update && sudo apt install jq
```
```bash
sudo docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:latest accuse --rpc-endpoint "https://testnet-nillion-rpc.lavenderfive.com/" --block-start "$(curl -s https://testnet-nillion-rpc.lavenderfive.com/abci_info | jq -r '.result.response.last_block_height')"
```
- Done ✅ , Follow me [ZunXBT](https://x.com/ZunXBT)
