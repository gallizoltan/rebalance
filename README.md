## Go to [rebalance c-lightning plugin](https://github.com/lightningd/plugins/tree/master/rebalance) for the latest version of rebalance. The version here is still functional but is no longer under active development.

## Lightning Channel rebalancing tool for c-lightning
This tool helps to rebalance [Lightning Network](https://en.wikipedia.org/wiki/Lightning_Network) channel liquidity between two of your channels. Tested with c-lightning 0.7.0.

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

| WARNING: this software is highly experimental! Use it at your own responsibility! |
| --- |

### Dependencies ###
1) Python3
2) [c-lightning](https://github.com/ElementsProject/lightning)
3) [pylightning](https://github.com/ElementsProject/lightning/tree/master/contrib/pylightning): `pip3 install pylightning`

### Usage ###
1) Choose one of your channels, where your balance is higher than desired. The peer belongs to this channel will be the outgoing peer. 
2) Choose one of your channels, where your balance is less than desired. The peer belongs to this channel will be the incoming peer. 
3) Choose an amount you want to transfer in msatoshi (millisatoshi or 0.00000000001 BTC)
4) Run: `./rebalance.py outgoing_node_id incoming_node_id msatoshi`
5) If the script offers a route with an acceptable routing fee, hit Enter.

### Warnings and Tips ###
- Be patient! This software is highly experimental.
- If the rebalance failed, try again with a smaller amount.
- However, some node does not forwards too small amounts, i.e. less than a thousand msatoshi.
- After some failed attempts, check the `rebalance.log` for further information.
- If the rebalance does not succeed after several attempts, please leave it! 10-20 attempts are okay, but more than 30 failed attempts may cause a channel closure!
- When running the script, please **check the fee for the offered route before hit Enter!** This fee goes to the routing nodes. Transactions are irreversible! After a successful rebalance, there is no way to regain this fee!

### Further information
See my article:
https://medium.com/coinmonks/redistribute-lightning-channels-balances-9ba3265584ee
