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
 * Transacciones de apertura y cierre de canales

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
