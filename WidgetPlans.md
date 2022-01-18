## Manual de uso: Widget Plans

<b>selected:</b> indicar el tipo de membresía "funnels", "campaigns" o "designs".

<b>showCurrentMemberships:</b> indica si queremos mostrar las membresías activas o no.
		false -> no muestra ninguna.
		true -> muestra las membresías activas.

<b>showProducts:</b> indica si queremos mostrar productos de pago único o 
	de pago por servicio(true) y en caso de no querer mostrarlos(false).

<b>title y subtitle</b> ambos son contenido y aceptan una cadena de texto por ejemplo "este es el subtitulo"

<b>currency:</b> también es contenido y acepta dos cadenas de texto por ejemplo ["15", "USD"]

<b>subscriptions:</b> si el usuario tiene suscripciones, se pasaría el valor a éste campo.

<b>links:</b> nos permite agregar rutas a cada uno de los campos, cuando queramos que cada una de las membresías envíen a un link específico.

<b>order:</b> acepta 3 cadenas de texto separadas por comas que definirán el orden en que queremos mostrar
	las membresías, además solo aparecerán las cadenas de texto que pasemos a order, es decir que
	["campaigns, "funnels"] solo mostraría los recuadros de las membresías para campañas y embudos.

<b>showOnly:</b> acepta una sola cadena de texto en caso que queramos mostrar únicamente una membresía,
	las opciones serían -> "funnels", "campaigns" o "designs".

<b>showPlans:</b> acepta un valor verdadero -> true o falso -> false, esto define si vamos a mostrar o no los planes o tipos de membresías.


# Widget Plans
``` html
<script>
var tripod_plans = {
  component: "plans",
  selected: "funnels",
  showCurrentMemberships: false, // MOSTRAR MEMBRESIAS SOLO CUANDO SE ESTA LOGUEADO.
  showProducts: true,
  title: "Elije uno de nuestros planes",
  subtitle: "Tenemos un plan justo a la medida de tu negocio",
  currency: ["$", "USD"], // $ 15 USD for example
  subscriptions: [],
  stripe_subs: {},
  links: {
    /*plansSelector: {
      "campaigns": "",
      "funnels": "",
      "designs": "",
    },*/
    currentMemberships: {
      viewPlans: "",
      invoiceData: "",
    }
  },
  lang: {
    setPlan: "Seleccionar plan",
    currentPlan: "Tu plan actual!",
    eachMonth: "mes",
    eachYear: "año",
    year: "Anual",
    month: "Mensual",
    day: "Diario",
    defaultItem: "Mejor Valor",
    help: {
      contactus: "Contáctanos",
      needhelp: "¿Necesitas mas información sobre nuestros planes?",
    },
    currentMemberships: {
      title: "Membresías Activas",
      invoiceInfo: "Información de facturación",
      recurrent: "Pago por servicio",
      renewal: "Renueva el",
      endAt: "Finaliza el",
      buttonView: "Ver planes & Membresías",
      canceled: "Cancelada",
      cancel: "Cancelar",
      withOutMemberships: "No Tienes membresías activas",
    },
    fields: {
      "campaigns": "Optimizador de Campañas",
      "funnels": "Websites y Funnels",
      "designs": "Diseño Grafico",
    },
  },
  order: [
    "campaigns",
    "funnels",
    "designs",
  ],
  //showPlans: false,
  //showOnly: "campaigns", // funnels, campaigns, designs
};
</script>

<link rel="stylesheet" type="text/css" replace-source-app href="https://cdn.jsdelivr.net/gh/Yerikmiller/3pod-us.github.io@4.0.0/widgets/Plans/Plans.css">
<link rel="stylesheet" type="text/css" replace-source-app href="https://cdn.jsdelivr.net/gh/Yerikmiller/3pod-us.github.io@master/widgets/Plans/styles.css">
<script replace-source-app src='https://cdn.jsdelivr.net/gh/Yerikmiller/3pod-us.github.io@latest/widgets/Plans/Plans.js'></script>
```