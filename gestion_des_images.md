# Gestion des images laravel

## Première étape :

-   Définir le storage link dans le fichier _filsystems.php du dossier config_

```php
  'links' => [
        public_path('storage') => storage_path('app/public'), //le dossier public situé dans le dossier storage/app/public sera lié  à un dossier storage qui sera créé  dans le dossier public de l'application
        //le dossier app/storage recevra les fichier ou dossier lors du upload des images.
    ],

    //Le public vient en réalité du filsystems.php au niveau de :
      'public' => [
            'driver' => 'local',
            'root' => storage_path('app/public'),
            'url' => env('APP_URL').'/storage',
            'visibility' => 'public',
            'throw' => false,
        ],

```

## Deuxième étape :

-   Dans le controller

```php
   $path= $request
             -> file('image') //preciser que le champ 'image' est un fichier
            ->store('images','public'); //stocker l'image dans un dossier 'images' dans le dossier public ('storage/app/public')
            $validated['image'] = $path; // mettre à jour le champ 'image'

```

## Troisième étape :

-   Activer le lien (création du symbolique link dans le dossier public du projet)

```bash
    php artisan storage:link;
```

## Final :

-   Gestion du path d'affichage des images

```php
   {{asset('storage/' . $article->image)}}

   /* utilisation de la méthode asset pour créer un path valide qui contient la concatenation du chemin vers le dossier 
storage du dossier public de l'application ('public/storage') avec le chemin du fichier venant de la base de donnée.*/
```

_Exemple: 'storage/images/mon-image.png'_ avec pour chemin complet '/public/storage/images/mon-image.png'



## Pour la suppression des images il suffit d'utiliser: 
```php
  Storage::disk("public")->delete($article->image);
```
*Dans ce cas on a supprimer l'image d'une article stocker dans le dossier public
