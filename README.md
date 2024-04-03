# Demo Fixtures et Faker

### Sources 
- DataFixtures : [doc](https://symfony.com/bundles/DoctrineFixturesBundle/current/index.html)
- Faker (Packagist) : [Packagist](https://packagist.org/packages/fakerphp/faker)
- Faker (Github) : [FakerPHP/Github](https://github.com/FakerPHP/Faker?tab=readme-ov-file#faker)
- Faker Documentation : [doc](https://fakerphp.github.io/)

## Actions dans l'ordre pour générer les données

1. Installer les dépendances (de développement) : **orm-fixtures** et **fakerphp**
    ```shell
    composer require orm-fixtures --dev
    ```
    ```shell
    composer require fakerphp/faker --dev
    ```
2. Créer une classe de Fixture par entité à générer
    ```shell
    symfony console make:fixtures
    # Préciser le nom de la fixture, ex : VilleFixtures
    ```
3. Dans le fichier généré par la commande, instanciez les entitées souhaité
    Ex :
    ```php
    # Récupération de l'instance de Faker, permettant de générer des datas
    $faker = Faker\Factory::create();
    # Itération en fonction de vos besoins
    for ($i = 0; $i < 3; $i++) {
        $user = new User();
        $user->setName($faker->name);

        $manager->persist($user);
    }
    # Enregistrement en bdd
    $manager->flush();
    ```
4. Pour lancer la génération de données, exécutez la commande suivante :
    ```shell
    symfony console doctrine:fixtures:load
    # Attention la bdd sera purgée avant d\'être remplie
    ```