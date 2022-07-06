# kani-mp

aplicacion back-end para el manejo de mercado pago en Kani app

---------------------

links importantes:

panel
- https://www.mercadopago.com.ar/developers/panel

Aplicacion
- https://www.mercadopago.com.ar/developers/panel/credentials?id=1267152345385744

Tarjetas de prueba
- https://www.mercadopago.com.ar/developers/es/docs/subscriptions/additional-content/test-cards




Pasos para integracion Mercado Pago:

- crear una app en https://www.mercadopago.com.ar/developers/panel


- generar usuario de prueba (cambiar el access token)

curl -X POST \
-H "Content-Type: application/json" \
-H 'Authorization: Bearer TEST-8579855292081055-060618-64b5a94a36e22b09e25ddaab6086db60-1104410545' \
"https://api.mercadopago.com/users/test_user" \
-d '{"site_id":"MLA"}'


- guardar usuarios de prueba

Vendedor
{
	"id":1137937620,
	"nickname":"TESTFKVMAWWF",
	"password":"qatest8781",
	"site_status":"active",
	"email":"test_user_91832043@testuser.com"
}

Comprador
{
	"id":1137946222,
	"nickname":"TT849027",
	"password":"qatest8256",
	"site_status":"active",
	"email":"test_user_88956061@testuser.com"
}

- pagos recurrentes

https://api.mercadopago.com/preapproval

const body = {
	reason: "Suscripcion Mensual a Kani",
	auto_recurring: {
		frecuency: 1,
		frecuency_type: "months",
		transaction_amount: 2000,
		currency_id: "ARS"
	},
	back_url: "https://kani-test.netlify.app/subs_success",
	payer_email: "test_user_88956061@testuser.com"
};
