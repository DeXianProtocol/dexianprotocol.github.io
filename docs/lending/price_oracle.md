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

Throughout the DeXian Lending Protocol, we rely on reliable, up-to-date, and secure price feeds. However, due to the infancy of Radix Babylon, large-scale and widely available price oracles are yet to emerge. We've identified [two](https://twitter.com/jimmyhumania/status/1725867423566299605) oracles with Scrypto-compatible interfaces, but their update frequency is suboptimal, ranging from [half an hour](https://dashboard.radixdlt.com/component/component_rdx1czqqs4t8f62jeyp47ctyqwmtk3vnf9sffnqd9lu7tgtgtvshj6x9lp/recent-transactions) to [a few hours](https://dashboard.radixdlt.com/component/component_rdx1czqqs4t8f62jeyp47ctyqwmtk3vnf9sffnqd9lu7tgtgtvshj6x9lp/recent-transactions), introducing additional risks for protocol participants.

## Price Feed(endpoint)
We propose the design of a neutral role provider that utilizes cryptography to sign price information, enabling anyone to verify the data. As illustrated in the figure:
![price oracle](/assets/images/lending_protocol_price_oracle.png)

#### Price Provider
* Current price sources: [coingecko](https://www.coingecko.com/en/coins/radix), [bitfinex](https://trading.bitfinex.com/t/XRD:USD), [gate.io](https://www.gate.io/zh/trade/XRD_USDT), [kucoin](https://www.kucoin.com/trade/XRD-USDT)
* The aforementioned prices are cryptographically signed, with the public key readily available for anyone to verify the information by accessing the endpoint.
* The [price provider](https://price.dexian.io/stokenet/xrd-usdt) acts as an impartial entity solely dedicated to delivering secure, timely, and reliable price data.

![xrd-usdc](/assets/images/xrd-usdt-endpoint.png)

#### Public Verifiable
* Price information comprises price, timestamp, epoch, and token address details to safeguard against tampering or replay attacks.
* Price information is presented in plaintext, ensuring human readability while maintaining cryptographic double verifiability.

[https://cyphr.me/ed25519_tool/ed.html](https://cyphr.me/ed25519_tool/ed.html)

![ed25519 verify](/assets/images/ed25519_verify.png)

#### DeXian Lending Protocol participants
* Borrowing, renewing, and liquidating participants must reference price information from the price provider when interacting with the protocol.
* The Scrypto component of the DeXian Lending Protocol employs cryptographic techniques to validate the authenticity of its data prior to advancing to the subsequent interaction step.
* Developers and projects that need to integrate the protocol send their requests via X or Telegram.







