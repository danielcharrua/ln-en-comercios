# Lightning Network en comercios
Guía para la implementación de Lightning Network en comercios usando BTCPay Server para gestionar ambos tipos de comercio (online y offline).

## Introducción
Esta guía busca hacer la implementación basándose en el control y libertad total o casi total. Dependerás de ti mismo, con tu propio nodo, credenciales, hardware wallet, etc. Es un setup más complejo pero tendrás el control total sobre tus fondos.

Si quieres comenzar de forma "fácil y rápida" puedes usar un servicio como [Breez](https://breez.technology/#business) en donde tendrás todo listo para la venta offline (comercio sin venta online). Debes tener en cuenta que al usar Breez te conectarás probablemente a su propio nodo por lo tanto no será la opcion más privada ni segura.

> Recordatorio: esta guía no pretende sumergirse profundamente en conceptos técnicos ni definiciones pero sí servir de punto de partida para la implementación. Si necesitas profundizar en algún concepto puedes buscar en la web o hacerme una consulta en [twitter](https://twitter.com/danielpcostas).

## Recibir pagos en Lightning Network
Para que un comercio pueda recibir pagos es fundamental que la wallet que quiere enviar el pago (el cliente) encuentre un camino hacia el nodo (el comercio) que emite la factura. Ese camino (canal o ruta) también tiene que tener balance y capacidad suficiente para poder enviar el pago.

La wallet del cliente escaneará la factura y buscará un camino para poder entregar el pago. Si encuentra un camino que cumpla con las necesidades se mostrará que se puede efectuar el pago y posiblemente unas pequeñas comisiones de "enrutado". Esas comisiones son otros nodos "enrutadores" por el que pasa el pago y que permiten la conexión entre la wallet del cliente y el nodo destino del comercio.

![pago con enrutado](./img/indirect-channel.svg)

En la imagen se muestran canales con líneas y flechas indicando el flujo. En este ejemplo se ha encontrado un camino (o ruta) hacia el nodo del comercio.

Si la wallet no encuentra un camino tienes la posibilidad de abrir un canal de pago directo con el comercio. Tienes que pensar si es un comercio con el que seguirás efectuando compras ya que abrir y cerrar un canal incurre en comisiones on-chain (Bitcoin).

![pago con canal directo](./img/direct-channel.svg)

## Liquidez entrante
Cuando trabajamos con comercios y queremos recibir pagos es fundamental establecer canales con liquidez entrante con nodos bien conectados. Una posible idea sería abrirlos con nodos que se encuentren en el top 10. Puedes revisar esa información en [https://1ml.com](https://1ml.com). Recuerda que no eres tú quien debe abrirlos sino estos nodos hacia tí ya que si los abres tú, el balance estará de tu lado imposibilitando que puedas recibir pagos (solo podrás enviarlos).

Existen servicios en los que puedes comprar esa liquidez entrante, por ejemplo: [Thor Lightning Channel Capacity de Bitrefill](https://www.bitrefill.com/buy/lightning-channel/) o [LND Pool](https://lightning.engineering/pool/).

![liquidez entrante](./img/inbound-liquidity.svg)

>Por favor investiga las condiciones antes de hacerlo ya que algunos servicios cerrarán el canal si no hay pagos en un determinado tiempo.

Es importante que recuerdes que esos nodos no solo deben darte liquidez entrante sino que también deben estar bien conectados ya que la idea es que los clientes puedan pagarte a través de otros nodos haciendo un enrutado del pago sin tener que abrir un canal directo con tu comercio.

## Diagrama lógico
![diagrama lógico](./img/logic-diagram.svg)
En el siguiente diagrama se puede apreciar un caso de ejemplo donde un comercio por la parte izquierda tiene montada la infraestructura necesaria para aceptar pagos en Lightning y por la derecha vemos a los potenciales clientes.

Como hemos visto antes algunos pagan con canales directos mientras que otros lo hacen mediante otros nodos enrutadores.

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
    * Encendido de servicios automáticos ante fallas (crashes)
    * Reconexión automática de red ante fallas del ISP/router
    * Tener logfiles para evaluar problemas
  * Backup de canales (Static Channel Backup) encriptados y frases semillas de la wallet on-chain
  * Decide si vas a vender en Sats o Fiat. De esto dependerá la expiración de las invoices de LN
    * Sats: 24h sería correcto y cómodo.
    * Fiat físico: 1 min cantidad fija (quizá lo más seguro) o 10 min cantidad no fija (lo calculará la wallet del pagador al enviar su pago)
    * Fiat online: 15 min cantidad fija

## Conceptos básicos a considerar
El comercio que quiera implementar pagos en Lightning Network debe plantearse varias cosas. Por el momento voy a ir planteando algunas preguntas que se me ocurren.
Por ejemplo:
* ¿Tiene un mínimo de conocimiento en Bitcoin?
* ¿Conoce cómo funciona una wallet de Bitcoin o Lightning? ¿Sabe diferenciar si es custodial o no custodial?
* ¿Entiende los riesgos que conlleva?
* ¿Tiene un mínimo de conocimiento en cómo manejar su privacidad y la seguridad de sus fondos / nodo?

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
Puedes probar todo este setup usando la red de Bitcoin en Testnet, para ello tienes los siguientes faucets para obtener un poco de tBTC y realizar pruebas.
* https://coinfaucet.eu/en/btc-testnet
* https://testnet-faucet.mempool.co
* https://bitcoinfaucet.uo1.net
* https://testnet.help/en/btcfaucet/testnet

## Lecturas de interés
* [LNBits para pequeños comerciantes](https://darthcoin.substack.com/p/lnbits-para-comerciantes)

## Lecturas técnicas
* [Mastering the Lightning Network](https://github.com/lnbook/lnbook)
* [Lightning Invoice Expiration: UX Considerations](https://d.elor.me/2022/01/lightning-invoice-expiration-ux-considerations/)
