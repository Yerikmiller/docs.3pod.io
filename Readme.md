# Manual de uso: Widget Register

<b>plans_selected:</b> indicar el id del panel de planes en 3pod.

<b>userFromCampaign:</b> cadena de texto, será el TAG o etiqueta "Campaña Diciembre".

<b>is_online:</b> indica si está en local(false) o en producción(true).

<b>type:</b> define el tipo de widget, los valores "basic" o "trial" NO muestran información del plan ni para pagos por el contrario el valor "default" muestra toda la información.

<b>membership:</b> tipo de membresía del plan seleccionado, embudos de venta, diseños o campañas.

<b>currency:</b> tipo de signo y divisa que se va a usar en todo el widget.

<b>lang:</b> {aquí irá el contenido del widget}.

## Widget Register
``` html
<script>
var tripod_register = {
  plans_selected: ["pyji"], // from 3Pod Admin panel
  userFromCampaign: "Campaña Diciembre", // TAG - CRM
  is_online: true,
  type: "basic", // default, trial, basic (set one of these). // ESTABLECER basic PARA REGISTRO NORMAL
  // send_to: "",
  stripeTokens: {
    live: "pk_live_ZodCkKBak1MPlwBJsxsMuubx",
    test: "pk_test_X7AvKFxbFhE5jaMPKPqiAbql003mxvgpKe",
  },
  module: "all",
  membership: "funnels",
  currency: ["$", "USD"],
  lang: {
    title: "Crea tu cuenta",
    subtitle: "Y obten 14 dias de prueba para<br> comenzar tu negocio digital",
    plan_text: "Plan",
    forms: {
      basic: {
        name: "Nombre",
        lastname: "Apellido",
        email: "Correo electrónico",
        password: "Contraseña",
        button: "Continuar",
        sign_in: {
          active: false,
          already_has: `Ya tienes una cuenta`,
          in: "Inicia sesión aquí",
        },
        errors: {
          password_error: "Introduce una contraseña mayor a 6 dígitos",          
        }
      },
      planSelection: {
        title: "¡Emprende a otro nivel!",
        subtitle: "Pon tu información de pago para empezar.",
        text_off: "Ahorra",
        intervals2: {
          year: "año",
          month: "mes"
        },
        year: "anual",
        month: "mensual",
        phone: "Celular",
        city: "Ciudad",
        address: "Dirección",
        zip: "Código Postal",
        coupon: "Cupón",
        card: "Número de tarjeta",
        card_name_owner: "Titular de la tarjeta",
        button: "Comienza ahora mismo",
        headband: "Ahorra"
      }, 
      guarantee: [
        `<span class="fw600 has-text-dark">Tienes 7 días de garantía de devolución de tu dinero</span>.`,

        `Para cancelar o tener resolver dudas adicionales, puede ponerte en contacto con nuestro equipo de <span class="fw600 has-text-dark">Soporte</span>. También acepto los <a target="_blank" href="https://mi3pod.com/terminosycondiciones" class="fw600 has-text-dark is-underlined">Términos de servicio</a>, la <a target="_blank" href="https://mi3pod.com/terminosycondiciones" class="fw600 has-text-dark is-underlined">Política de privacidad</a> y el <a target="_blank" href="https://mi3pod.com/terminosycondiciones" class="fw600 has-text-dark is-underlined">Acuerdo de afiliación</a>.`
      ]     
    },
    errors: {
      email_registered: "El e-mail que has ingresado ya está en uso.",
      uncompleted: "Por favor, verifique los campos del formulario.",
    }
  },
  captchaToken: null,
}

function captchaSubmit(token){
  tripod_register.captchaToken = token;
  tripod_register.submit(token);
}
</script>
<div style="display:flex;justify-content:center;">
	<div class="register-gadget-3pod" style="max-width:640px;"></div>
</div>
<link rel="stylesheet" type="text/css" replace-source-app href="https://cdn.jsdelivr.net/gh/Yerikmiller/yerikmiller.github.io@latest/projects/3Pod/Plans/Widgets/Register.css">
<script replace-source-app src='https://cdn.jsdelivr.net/gh/Yerikmiller/yerikmiller.github.io@latest/projects/3Pod/Plans/Widgets/Register.js'></script>
<script src="https://js.hcaptcha.com/1/api.js" async defer></script>
```


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
  selected: "campaigns",
  showCurrentMemberships: true,
  showProducts: true,
  title: "Elije uno de nuestros planes",
  subtitle: "Tenemos un plan justo a la medida de tu negocio",
  currency: ["$", "USD"], // $ 15 USD for example
  subscriptions: Subscriptions,
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

<link rel="stylesheet" type="text/css" replace-source-app href="https://cdn.jsdelivr.net/gh/Yerikmiller/yerikmiller.github.io@latest/projects/3Pod/Plans/Widgets/Plans.css">
<link rel="stylesheet" type="text/css" replace-source-app href="https://cdn.jsdelivr.net/gh/Yerikmiller/yerikmiller.github.io@latest/projects/3Pod/Plans/style.css">
<script replace-source-app src='https://cdn.jsdelivr.net/gh/Yerikmiller/yerikmiller.github.io@latest/projects/3Pod/Plans/Widgets/Plans.js'></script>
```
