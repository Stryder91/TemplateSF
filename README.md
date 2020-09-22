# Symfony

Install symfony, symfony-cli & composer. 
Symfony -
CLI -  wget https://get.symfony.com/cli/installer -O - | bash
composer - sudo apt install composer

Install selon une version : 
composer create-project symfony/website-skeleton:"^4.4" app_name

Lancer serveur : 
php -S 127.0.0.1:8000 -t public
(ou)
symfony server:start

Présentation de dossiers: 
- bin qui contient des executables comme la console (par exemple php bin/console server:log etc..)
- config/ écrit en yaml pour les routes et services.
- public/ qui sera la racine ou pointe Apache.
- src/ qui contient le code.
- composer.json pointe vers src/ dans autoload.
- tests pour les unitaires et fonctionnels.
- vendor propre à composer.
- .env pour gérer la connexion à la BDD (initialisé par l'environnement DEV et une APP_SECRET et DATABASE_URL)


## Implémentation 

### Routes
Dans config/routes.yaml: on spécifie un nom, un path ainsi que son controlleur associé. Exemple 
```
home:
  path: /
  controller: App\Controller\HomeController::index
```

### Controller 
Créer ensuite le fichier HomeController.php dans src/
On spéficie le namespace et la classe ainsi que Response pour retourner quelque chose sur la page.
```
<?php
namespace App\Controller;

use Symfony\Component\HttpFoundation\Response;

class HomeController
{
  public function index(): Response
  {
    return new Response('Hello world');
  }
```
### Services
Dans services.yaml On peut charger des services sur les Controller: comme une instance de twig (pour l'utiliser tout simplement)
```
App\Controller\HomeController:
    arguments:
        $twig: '@twig'
```
Mais au lieu de cela, on peut simplement spécifier 
```
public function __construct(Environment $twig) {}
```
pour charger twig


### Routage depuis twig
Une route peut-être défini en annotation (meilleur choix), YAML (second choix) ou encore en XML ou Php

On prend le nom qui est dans route.yaml (si on écrit en yaml)
href="{{ path('property.index') }}"

En annotation, au dessus de la public function:
/**
  * @Route("/biens", name="property.index")
  *
  */


### Rendre des pages
Rendre une page twig TBC
```
return $this->render('pages/home.html.twig');
```

