## Manual de uso: Widget Register + Plans
Es una combinación de ambos widgets. Por lo tanto se aplican configuraciones similares.

``` html
<script>
// Register Configuration
var tripod_register = {
  plans_selected: ["pyji"], /* CODIGO DE PRUEBA: "lTOW" - planes de 3Pod Admin panel */
  userFromCampaign: "TEST-TAG", // TAG - CRM
  is_online: true,
  type: "default", // default, trial, basic (set one of these).
  // send_to: "",
  affiliate: null,
  stripeTokens: {
    live: "pk_live_ZodCkKBak1MPlwBJsxsMuubx",
    test: "pk_test_X7AvKFxbFhE5jaMPKPqiAbql003mxvgpKe",
  },
  module: "all",
  membership: "funnels",
  currency: ["$", "USD"],
  host_offline: "https://app.3pod.io/", // http://localhost/app.3pod.io/
  has_chooser_plan_module: true, // will be activated in second step.
  lang: {
    title: "Crea tu cuenta",
    plan_text: "Plan",
    subtitle: "Y obten 14 dias de prueba para<br> comenzar tu negocio digital",
    goBack: "Volver",
    intervals: {
      // mantener el mismo orden.
      month: ["mes", "meses", "mensual"],
      year: ["año", "años", "anual"]
    },
    forms: {
      /* Register Module Start  */
      basic: {
        name: "Nombre",
        lastname: "Apellido",
        email: "Correo electrónico",
        password: "Contraseña",
        button: "Continuar",
        adviseRequired: "Campos requeridos (<span class='has-text-danger'>*</span>)",        
        sign_in: {
          active: true, // TRUE para mostrar "Iniciar sesión!"
          already_has: `Ya tienes una cuenta`,
          in: "Inicia sesión aquí",
        },
        errors: {
          password_error: "Introduce una contraseña mayor a 6 dígitos",          
        }
      },
      /* Register Module End  */
      /* Payment Module Start  */
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
        button: "Pagar",
        headband: "Ahorra",
        securePayment: "Pago Seguro SSL",
      }, 
      /* Payment Module End  */
      /* Sign In Module Start  */
      signIn: {
        title: "Inicia Sesión",
        subtitle: "y obtén beneficios 3Pod",
        button: "Iniciar Sesión",
        errors: {
          not_exist: "Datos de usuario incorrectos. Por favor intente de enuevo"
        }
      },
      paymentAnyPlan: {
        title: "Resumen de compra",
        months: "meses",
        total: "Total",
        discounts: "Descuentos",
        subtotal: "Subtotal",
        price: "Precio",
        changePlan: "cambiar plan",
        pay: "Pagar"
      },
      /* Sign In Module End  */
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

// Plans Configuration
var tripod_plans = {
  component: "plans",
  selected: "funnels",
  showCurrentMemberships: false,
  showProducts: false,
  host: "https://app.3pod.io/",
  title: "Elije uno de nuestros planes",
  subtitle: "Tenemos un plan justo a la medida de tu negocio",
  currency: ["$", "USD"], // $ 15 USD for example
  subscriptions: null,
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
    "funnels",
    "campaigns",
    "designs",
  ],
  //showPlans: false,
  //showOnly: "campaigns",
};

/*
* @param plan {object} Plan selected
* @param interval {string} payment interval (year, month, etc..)
*/
tripod_plans.onSelect = function(plan, interval, button){
    return {
      plan: plan,
      interval: interval,
      button: button,
    }
}

</script>
<style>
.Title-Plan-recommended span{
    color:#fff;
}
.Title-Plan-Default span{
    color:var(--color-dark-grey); 
}
.CurrencyFormatter--container .CurrencyFormatter{
    display: inline-flex;
    align-items: baseline;
}
.CurrencyFormatter--cents{
    font-size: calc(8px + 0.3em);
}
</style>
<div style="display:flex;justify-content:center;">
	<div class="register-gadget-3pod" style="max-width:1440px;min-width:320px;"></div>
</div>
<link rel="stylesheet" type="text/css" replace-source-app href="https://cdn.jsdelivr.net/gh/Yerikmiller/3pod-us.github.io@latest/widgets/Plans/Register.css">
<script replace-source-app src='https://cdn.jsdelivr.net/gh/Yerikmiller/3pod-us.github.io@latest/widgets/Plans/Register.js'></script>
```