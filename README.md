Symfony Custom GCP SecretManager EnvVarProcessor
=================================

What is this EnvVarProcessor for the GCP Secret Manager?
---------------------------
This bundle will help you to retrieve secrets from GCP Secret Manager on runtime.
Define this service within your Symfony services.yaml by adding the following:
``` yaml
EnvVarProcessor\GCPSecretManagerEnvVarProcessor:
    tags: ['container.env_var_processor']
    arguments:
        $gcpProjectId: 'YOUR GCP PROJECTID'
        $gcpCredentialsFile: 'YOUR SERVICE ACCOUNT PRIVATE KEY'
```

Now you can define which secrets you want to request on runtime:
``` yaml
App\Controller\DefaultController:
    class: 'App\Controller\DefaultController'
    arguments:
        $secret: '%env(string:gcpsecretmanager:YOURSECRET)%'
```

Installation
------------
* Require the bundle with composer:

``` bash
composer require rauchfuss-io/gcpsecretmanager-envvarprocessor
```