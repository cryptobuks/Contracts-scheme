# Contracts-scheme
Scheme of smart-contracts organization
![Image alt](https://github.com/sonm-io/Contracts-scheme/raw/master/images/ContrScheme.jpg)


### Structure of contracts:

1. Migrations(Standard)
2. [Sonm Token](https://github.com/sonm-io/token)
3. DAO(Standard)
4. [Hub wallet factory](https://github.com/sonm-io/Forge/blob/master/contracts/Hubs/HubFactory.sol)
5. [Hub wallet](https://github.com/sonm-io/Smart-dummy/tree/master/contracts/Hubs)
6. [Whitelist prototype](https://github.com/sonm-io/Forge/tree/master/contracts/Whitelist)
7. RegApp (Simple React/Webpack App to work with hub registrations)
8. PayOut App (already implemented for DD@H project)
https://github.com/sonm-io/drugdiscovery-token


### Abstract:

Outline of the smart-contracts system which will be implemented in SONM network is presented. More info about network and contracts interaction can be found in the [whitepaper](http://sonm.io/Sonm1.pdf)


### Simple Data flow

#### HUB

Before hub started to payout tokens to miners and recive payments from buyers, he must create a hub wallet — simple contract with fixed amount of frozen funds. If hub is caught on cheating, DAO can initiate process of blacklisting this hub and expropriate its frozen funds.

Those expropriated funds will also be frozen at the DAO account for some specified time. This is to protect against malicious descisions of the DAO: tokens can drop in price during freeze, therefore there is no motivation to 'raskulachivat' (expropriate) every hub.

#### HUB FACTORY

*Hub wallet* can be created only by *Hub wallet factory* (which is actually simplified replication factory), which create new hub wallet contract and register it in 'whitelist' contract.

#### WHITELIST

*Whitelist contract* is a registry contract containing info about hubs and their statuses. All hub wallet created by hub wallet factory are registered in this contract. It supposed to be simple registry with a special mapping for 'trusted' hubs. Initially, 'trusted' hubs will be checked by SONM developers manually / be official SONM hubs. Later, it supposed to be also a rating list — everyone could check hub and rate it (betting some amount of SONM tokens to prevent rating fraud).

#### REGAPP

React.js application which is simple web application (web-page) with the purpose of user friendly hub registration process.

#### PAYOUT APP

Application to proceed miners token payout mechanism. For now it is implemented to work with BOINC statistic mechanism.
