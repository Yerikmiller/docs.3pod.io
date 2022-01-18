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
  plans_selected: ["pyji"], /* CODIGO DE PRUEBA: "lTOW" - planes de 3Pod Admin panel */
  userFromCampaign: "Campaña de Prueba", // TAG - CRM
  is_online: false,
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
  host_offline: "http://localhost/app.3pod.io/",
  lang: {
    title: "Crea tu cuenta",
    plan_text: "Plan",
    subtitle: "Y obten 14 dias de prueba para<br> comenzar tu negocio digital",
    goBack: "Volver",
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
        button: "Comienza ahora mismo",
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
</script>
<div style="display:flex;justify-content:center;">
	<div class="register-gadget-3pod" style="max-width:640px;min-width:320px;"></div>
</div>
<link rel="stylesheet" type="text/css" replace-source-app href="https://cdn.jsdelivr.net/gh/Yerikmiller/3pod-us.github.io@latest/widgets/Plans/Register.css">
<script replace-source-app src='https://cdn.jsdelivr.net/gh/Yerikmiller/3pod-us.github.io@latest/widgets/Plans/Register.js'></script>
```