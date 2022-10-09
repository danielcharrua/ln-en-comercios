# Lightning Network en comercios
Guía para la implementación de Lightning Network en comercios usando BTCPay Server para gestionar ambos tipos de comercio (online y offline).

## Introducción
Esta guía busca hacer la implementación basandose en el control y libertad total o casi total. Dependerás de ti mismo, con tu propio nodo, credenciales, hardware wallet, etc. Es un setup más complejo pero tendras el control total sobre tus fondos.

Más adelante se agregará una nueva guía o apartado para la implementacion "fácil y rápido" pero tendrás menos privacidad, seguridad y control sobre tus fondos.

Esta guía no pretende sumergirse profundamente en conceptos técnicos ni definiciones pero si servir de punto de partida para la implementación. Si necesitas profundizar en algún concepto puedes buscar en la web.

## Recibir pagos en Lightning Network en comercios
En un comercio que quiera recibir pagos es fundamental la "inbound liquidity" o liquidez entrante. Esto significa que debes tener capacidad para poder recibir pagos que quieran hacer tus clientes. Esto se logra teniendo canales con capacidad de pago apuntando hacía tí.

Cuando un cliente quiera enviarte un pago, sea en tu comercio online u offline, tu nodo generará una factura Lightning y él cliente la escaneará probablemente con su wallet en su teléfono móvil. A continuación su wallet intentará buscar un camino hacia tu nodo y poder enviar ese pago.

Aquí existen dos posibilidades, la primera sería que al escanear la factura la wallet de tu cliente encuentre un camino hacia tu nodo y pueda enviarte el pago, y la segunda sería que el cliente abra un canal de pago con tu nodo. Es fundamental que exista un camino o se cree uno, de lo contrario no se podrá enviar el pago.

## Idea
La idea general de implementación será:
* Instalar BTCPay Server en Linux, usando hardware propio o un VPS en la nube
* Montar los nodos de Bitcoin y Lightning Network en el hardware
* Configurar BTCPay Server para nuestra tienda online/offline
* Configurar nuestra hardware wallet
* Realizar pruebas en Testnet
* A tener en cuenta cuando participes en Lightning Network:
  * Costo de las transacciones on-chain de apertura y cierre de canales
  * Debes tener el nodo online 24/7
  * Para mayor seguridad usa Watchtowers (para vigilar "Protocol breach force close" channels)
  * En el hardware y software que utilices
    * Encendido automático ante fallas eléctricas
    * Encendido de servicios automaticos ante fallas (crashes)
    * Reconexión automática de red ante fallas del ISP/router
    * Tener logfiles para evaluar problemas
  * Backup de canales (Static Channel Backup) encriptados y frases semillas de la wallet on-chain
  * Decide si vas a vender en Sats o Fiat. De esto dependerá la expiración de las invoices de LN
    * Sats: 24 h sería correcto y cómodo.
    * Fiat físico: 1 min cantidad fija (quizá lo más seguro) o 10 min cantidad no fija (lo calculará la wallet del pagador al enviar su pago)
    * Fiat online: 15 min cantidad fija

## Conceptos básicos a considerar
El comercio que quiera implementar pagos en Lightning Network debe plantearse varias cosas. Por el momento voy a ir planteando algunas preguntas que se me ocurren.
Por ejemplo:
* ¿Tiene un mínimo de conocimiento en Bitcoin?
* ¿Conoce cómo funciona una wallet de Bitcoin o Lightning? ¿Sabe diferenciar si es custodial o no custodial?
* ¿Entiende los riesgos que conlleva?
* ¿Tiene un mínimo de conocimiento en como manejar su privacidad y la seguridad de sus fondos / nodo?

## Hardware
Puedes usar otro hardware similar que encuentres en el mercado. Incluso comprar de segunda mano.
* Ordenador con 8GB RAM / 1TB disco SSD
* Cold Card Wallet (o cualquier hardware wallet, puede ser Ledger Nano por ejemplo)
* Teléfono móvil o tablet para usar como POS (punto de venta) en tiendas físicas

## Software
* Linux Ubuntu Server 22.04
* BTCPay Server
* Si vas a vender online
  * Una página web con WordPress (podría ser también con Prestashop, Magento, Shopify, etc.)
  * WooCommerce
  * Plugin de BTCPay Server para WordPress

## Legislación
Sección pendiente de desarrollo.

## Bitcoin Testnet tBTC faucet
* https://coinfaucet.eu/en/btc-testnet
* https://testnet-faucet.mempool.co
* https://bitcoinfaucet.uo1.net
* https://testnet.help/en/btcfaucet/testnet

## Lecturas de interés
* [LNBits para pequeños comerciantes](https://darthcoin.substack.com/p/lnbits-para-comerciantes)

## Lecturas técnicas
* [Mastering the Lightning Network](https://github.com/lnbook/lnbook)
* [Lightning Invoice Expiration: UX Considerations](https://d.elor.me/2022/01/lightning-invoice-expiration-ux-considerations/)
