# SYMFONY STRIPE INTEGRATION

This repository is a small tutorial which explains how to integrate stripe using Symfony 5 project
and how to accept payments with Stripe

##### CREATE DATABASE IF EXIST 

```
php app/console doctrine:database:create --if-not-exists
php app/console doctrine:schema:update --force
php app/console doctrine:fixtures:load
```

##### INSTALL STRIPE composant 

STRIPE DASHBOARD DEBUG :  https://dashboard.stripe.com/test/logs

```
composer require stripe/stripe-php
```

STRIPE DOC : https://stripe.com/docs/payments/accept-a-payment?integration=elements
Expose root : 

```PHP
    /**
     * @Route(
     *  "/create-checkout-session", 
     *  name="stripe-create-checkout-session", 
     *  options={"expose"=true},
     *  methods={"GET","POST"} 
     *  )
     */
    public function create(
        StripeService $stripeService
        ): Response
    {
        #your code here
    }
```
Next you have to generate js Route

```
bin/console fos:js-routing:dump --format=json --target=public/bundles/js/fos_js_routes.json
```

MAPPING : 

CHECKOUT PROCESS into  [StripeController](./src/Controller/StripeController.php) and [StripeService](./src/Services/StripeService.php)

CHECKOUT JS PROCESS into [checkout.html.twig](./templates/default/checkout.html.twig)
