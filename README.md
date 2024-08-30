# MyFirstSymfony

## Installation

```bash
symfony new MyFirstSymfony
cd MyFirstSymfony
```

### Installation de maker

```bash
composer require --dev symfony/maker-bundle
```

Pour voir ce que l'on peut faire dans la console

```bash
symfony console
php bin/console
```

Pour voir les actions de maker

```bash
php bin/console make:
```

 ### Création d'un  controleur

```bash
php bin/console make:controller First
```

Le nom doit être en Pascal case

un fichier est créé dans `src/controller/FirstController.php`

Pour voir une route depuis la console : 

```bash
php bin/console debug:router
```

Pour voir le détail d'une route 

```bash
php bin/console debug:router nom_de_la_route
```

### Utilisation de `yaml` comme `routing`

Ceci n'est pas conseillé, mais est parfois utilisé

Voir la documentation :

https://symfony.com/doc/current/routing.html#generating-urls-in-commands

On commente l'activation par défaut des `attribute` dans `config/routes.yaml`
```yaml
#controllers:
 #   resource:
  #      path: ../src/Controller/
  #      namespace: App\Controller
 #   type: attribute

```

Ensuite on crée le lien vers la méthode de notre contrôlleur

```yaml
my_json:
    path: /json
    controller: App/Controller\FirstController::my_json
```

En vérifiant bien que notre contrôleur  soit modifié : 

```php
#src/Controller/FirstController.php

namespace App\Controller;


 # use Symfony\Component\Routing\Attribute\Route;

class FirstController extends AbstractController
{
     // #[Route('/first', name: 'app_first')]
    public function myJson(): JsonResponse
    {
        return $this->json([
            'message' => 'Welcome to your new controller!',
            'path' => 'src/Controller/FirstController.php',
        ]);
    }
}

```