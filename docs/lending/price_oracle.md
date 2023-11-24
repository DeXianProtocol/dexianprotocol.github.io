---
layout: page
menubar: docs_menu
title: The Price Oracle of DeXian Lending Protocol
subtitle: reliable, up to date, and secure.
# hero_image: /path/to/image.jpg
show_sidebar: false
toc: true
---
## Price Oracle

Throughout the DeXian Lending Protocol, we require reliable, up to date, and secure price feeds. However Radix Babylon has not been online long enough for there to be a large-scale and widely available price oracle. We already know of [two](https://twitter.com/jimmyhumania/status/1725867423566299605) that offer interfaces that can be integrated natively in Scrypto, but they are not updated in a timely manner, some of them [half an hour](https://dashboard.radixdlt.com/component/component_rdx1czqqs4t8f62jeyp47ctyqwmtk3vnf9sffnqd9lu7tgtgtvshj6x9lp/recent-transactions) ~ [a few hours](https://dashboard.radixdlt.com/component/component_rdx1czqqs4t8f62jeyp47ctyqwmtk3vnf9sffnqd9lu7tgtgtvshj6x9lp/recent-transactions), which poses an additional risk for participants in the protocol.

## Price Feed(endpoint)
We contextualize the design of a neutral role provider that uses cryptography to sign price information and whose data can be verified by anyone. As shown in Figure:
![price oracle](/assets/images/lending_protocol_price_oracle.png)

#### Price Feed Provider
* Current price sources: [coingecko](https://www.coingecko.com/en/coins/radix), [bitfinex](https://trading.bitfinex.com/t/XRD:USD),[gate.io](https://www.gate.io/zh/trade/XRD_USDT), [kucoin](https://www.kucoin.com/trade/XRD-USDT)
* The above prices are signed using cryptography and the public key is made public so that anyone can verify the information, by accessing the endpoint.
* The price provider is a neutral actor that only aims to provide secure, timely and reliable price information.

#### Public Verifiable
* Price information contains price, timestamp, epoch, and token address information to prevent tampering or replay.
* Price information is presented in plaintext, human-readable and cryptographically doubly verifiable.

[https://cyphr.me/ed25519_tool/ed.html](https://cyphr.me/ed25519_tool/ed.html)

![ed25519 verify](/assets/images/ed25519_verify.png)

#### DeXian Lending Protocol participants
* Borrowing, renewing, and liquidating participants need to reference price information from the price provider when interacting with the protocol.
* The Scrypto component of the DeXian Lending Protocol uses cryptographic methods to verify the validity of its data before proceeding to the next step of the interaction.
* Developers and projects that need to integrate the protocol send their requests via X,Telegram.






