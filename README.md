# Lightning Network en comercios
Guía para la implementación de la Lightning Network en comercios online y offline usando testnet.

## Introducción
Esta guía busca hacer la implementación basandose en el control y libertad total o casi total. Dependerás de ti mismo, con tu propio nodo, credenciales, hardware wallet, etc. Es un setup más complejo pero tendras el control total sobre tus fondos.

Más adelante la idea será agregar una nueva guía o apartado para la implementacion "fácil y rápido" pero tendrás menos seguridad y control sobre tus fondos.

Esta guía no pretende entrar muy profundamente en conceptos técnicos ni definiciones pero si servir de punto de partida para la implementación. Si necesitas profundizar en algún concepto puedes buscar en la web.

## Idea
La idea general de implementación será:
* Instalar BTCPay Server en Linux, usando hardware propio o un VPS en la nube
* Montar los nodos de Bitcoin y Lightning Network en el hardware
* Configurar BTCPay Server para nuestra tienda online/offline
* Configurar nuestra hardware wallet
* Realizar pruebas en Testnet
* A tener en cuenta en LN:
  * Transacciones on-chain de apertura y cierre de canales
  * Nodo corriendo 24/7 o uso de Watchtowers (para vigilar "Protocol breach force close" channels)
  * 100% uptime para recibir pagos
  * Backup de canales y semillas
  * Decide si vas a vender en Sats o Fiat. De esto dependerá la expiracion de las invoices de LN.
    * Sats: 24 h sería correcto y cómodo.
    * Fiat físico: 1 min cantidad fija (quizá lo más seguro) o 10 min cantidad no fija (lo calculará la wallet del pagador al enviar su pago)
    * Fiat online: 15 min cantidad fija

## Conceptos básicos
El comercio que quiera implementar pagos en Lightning debe plantearse varias cosas. Por el momento voy a ir planteando algunas preguntas que se me ocurren.
Por ejemplo:
* ¿Tiene un mínimo de conocimiento en Bitcoin?
* ¿Conoce cómo funciona una wallet de Bitcoin o Lightning? ¿Sabe diferenciar si es custodial y no custodial?
* ¿Entiende los riesgos que conlleva?
* ¿Tiene un minimo de conocimiento en como manejar la privacidad y la seguridad?

## Hardware
Puedes usar otro hardware similar que encuentres en el mercado. Incluso comprar de segunda mano.
* Ordenador con 8GB RAM / 120GB disco
* Ledger Nano hardware wallet
* Teléfono móvil o tablet para usar como POS en tiendas físicas

## Software
* Linux Ubuntu Server 22.04
* BTCPay Server
* Una página web con WordPress (podría ser también con Prestashop, Magento, Shopify, etc.)

## Legislación
Sección pendiente de desarrollo.

## Bitcoin Testnet tBTC faucet
* https://coinfaucet.eu/en/btc-testnet
* https://testnet-faucet.mempool.co
* https://bitcoinfaucet.uo1.net
* https://testnet.help/en/btcfaucet/testnet

## Lectura de interés
* [LNBits para pequeños comerciantes](https://darthcoin.substack.com/p/lnbits-para-comerciantes)

## Lecturas técnicas
* [Mastering the Lightning Network](https://github.com/lnbook/lnbook)
* [Lightning Invoice Expiration: UX Considerations](https://d.elor.me/2022/01/lightning-invoice-expiration-ux-considerations/)
