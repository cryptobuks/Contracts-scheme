# Contracts-scheme
Scheme of smart-contracts organization
![Image alt](https://github.com/sonm-io/Contracts-scheme/raw/master/images/ContrScheme.jpg)


Structure of contracts:

1. Migrations(Standard)
2. Sonm Token
https://github.com/sonm-io/token
3. DAO(Standard)
4. Hub wallet factory
5. Hub wallet
6. RegApp (Simple React/Webpack App to work with hub registrations)
7. PayOut App (already implemanted for DD@H project)
https://github.com/sonm-io/drugdiscovery-token


Abstract:

It is schematic of smart-contracts system which will be implemented in SONM network. More info about network and contracts interaction you could find in whitepaper - [http://sonm.io/Sonm1.pdf](http://sonm.io/Sonm1.pdf)



Simple Data flow:

HUB

Before hub started to payout tokens to miners and recive payments from buyers – he must create a hub wallet – simple contract with defined amount of frozen funds. If hub will be cheating – DAO could initiate process of blacklisting this hub and expropriate frozen funds from it.

Frozen funds it also will be frozen at DAO account for defined time – it&#39;s special protection against malicious descisions of DAO – tokens could lower it price for time from expropriation to undfreeze, therefore there is no motivation to &#39;raskulachivat&#39;(expropriate) every hub.

HUB FACTORY

This hub wallets could be created only throught Hub wallet factory (which is actually simplified replication factory), which create new hub wallet contract and register it in &#39;whitelist&#39; contract.

WHITELIST

Whitelist contract – it is simple registry contract which contain info about hubs and it&#39;s status. All hub wallet created throught hub wallet factory is registrates in this contract. It suppose to be simple registry + special mapping for &#39;trusted&#39; hubs. For the first time &#39;trusted&#39; hub&#39;s will be only hub&#39;s which will be checked by SONM developers manually / be official SONM hubs. In the future it suppose to be also a rating list – everyone could check hub and rate it, betting some amount of sonm tokens (to prevent rating fraud).

REGAPP

Simple React.js application which is simple web application (web-page) with purpose to simplified hub registration process.

PAYOUT APP

Simple application to proceed miners token payout mechanism. For now it is implemented to work with BOINC statistic mechanism.
