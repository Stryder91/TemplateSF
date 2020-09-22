# Symfony

Install symfony, symfony-cli & composer. 
Symfony -
CLI -  wget https://get.symfony.com/cli/installer -O - | bash
composer - sudo apt install composer

Install selon une version : 
composer create-project symfony/website-skeleton:"^4.4" app_name

Lancer serveur : php -S 127.0.0.1:8000 -t public

Présentation de dossiers: 
- bin qui contient des executables comme la console.
- config/ écrit en yaml pour les routes et services.
- public/ qui sera la racine ou pointe Apache.
- src/ qui contient le code.
- composer.json pointe vers src/ dans autoload.
- tests pour les unitaires et fonctionnels.
- vendor propre à composer.
- .env pour gérer la connexion à la BDD (initialisé par l'environnement DEV et une APP_SECRET et DATABASE_URL)

