### Artisan (CLI) Commands

#### Les plus utilisés

1. **Serveur de développement**
   ```bash
   php artisan serve
   ```
   *Pour démarrer un serveur de développement local.*

2. **Migration**
   ```bash
   php artisan migrate
   ```
   *Pour exécuter toutes les migrations non exécutées.*

   ```bash
   php artisan migrate:rollback
   ```
   *Pour annuler la dernière migration exécutée.*

   ```bash
   php artisan migrate:refresh
   ```
   *Pour annuler toutes les migrations et les réexécuter.*

   ```bash
   php artisan migrate:reset
   ```
   *Pour annuler toutes les migrations.*

   ```bash
   php artisan migrate:status
   ```
   *Pour voir l'état actuel des migrations.*

3. **Modèles**
   ```bash
   php artisan make:model ModelName
   ```
   *Pour créer un nouveau modèle.*

   ```bash
   php artisan make:model ModelName -m
   ```
   *Pour créer un nouveau modèle avec une migration.*

   ```bash
   php artisan make:model ModelName -c
   ```
   *Pour créer un nouveau modèle avec un contrôleur.*

   ```bash
   php artisan make:model ModelName -r
   ```
   *Pour créer un nouveau modèle avec une ressource.*

   ```bash
   composer dump-autoload
   ```
   *Pour les controllers créés soi-même.*

4. **Contrôleurs**
   ```bash
   php artisan make:controller ControllerName
   ```
   *Pour créer un nouveau contrôleur.*

   ```bash
   php artisan make:controller ControllerName --resource
   ```
   *Pour créer un nouveau contrôleur avec des méthodes de ressource RESTful.*

   ```bash
   php artisan make:controller ControllerName --model=ModelName
   ```
   *Pour créer un nouveau contrôleur et l'associer à un modèle.*

5. **Factory**
   ```bash
   php artisan make:factory FactoryName
   ```
   *Pour créer une nouvelle factory.*

6. **Seeder**
   ```bash
   php artisan make:seeder SeederName
   ```
   *Pour créer un nouveau seeder.*

   ```bash
   php artisan db:seed
   ```
   *Pour exécuter les seeders et peupler la base de données avec des données fictives.*

7. **Commande personnalisée**
   ```bash
   php artisan make:command CommandName
   ```
   *Pour créer une nouvelle commande Artisan personnalisée.*

8. **Middleware**
   ```bash
   php artisan make:middleware MiddlewareName
   ```
   *Pour créer un nouveau middleware.*

9. **Notifications**
   ```bash
   php artisan make:notification NotificationName
   ```
   *Pour créer une nouvelle notification.*

10. **Events**
    ```bash
    php artisan make:event EventName
    ```
    *Pour créer un nouvel événement.*

11. **Jobs**
    ```bash
    php artisan make:job JobName
    ```
    *Pour créer une nouvelle tâche (job).*

12. **Listeners**
    ```bash
    php artisan make:listener ListenerName
    ```
    *Pour créer un nouveau listener pour un événement.*

13. **Requests**
    ```bash
    php artisan make:request RequestName
    ```
    *Pour créer une nouvelle requête de validation.*

#### Moins utilisés

14. **Policy**
    ```bash
    php artisan make:policy PolicyName
    ```
    *Pour créer une nouvelle policy d'autorisation.*

15. **Mail**
    ```bash
    php artisan make:mail MailName
    ```
    *Pour créer une nouvelle classe de mail.*

16. **Notifications Channel**
    ```bash
    php artisan make:notification-channel ChannelName
    ```
    *Pour créer un nouveau canal de notification.*

17. **Observer**
    ```bash
    php artisan make:observer ObserverName --model=ModelName
    ```
    *Pour créer un nouvel observer pour surveiller les changements sur un modèle.*

18. **Provider**
    ```bash
    php artisan make:provider ProviderName
    ```
    *Pour créer un nouveau service provider.*

19. **Rule**
    ```bash
    php artisan make:rule RuleName
    ```
    *Pour créer une nouvelle règle de validation personnalisée.*

20. **Test**
    ```bash
    php artisan make:test TestName
    ```
    *Pour créer un nouveau test.*

21. **Link storage resources (image) to public app**
    ```bash
    php artisan storage:link
    ```
    *Pour lier le dossier storage aux ressources du dossier public.*

### Eloquent ORM

#### Les plus utilisés

1. **Créer un enregistrement**
   ```php
   $model = new Model;
   $model->field = 'value';
   $model->save();
   ```
   *Pour créer et enregistrer un nouvel enregistrement.*

2. **Trouver un enregistrement par ID**
   ```php
   $model = Model::find($id);
   ```
   *Pour trouver un enregistrement par son ID.*

3. **Tous les enregistrements**
   ```php
   $models = Model::all();
   ```
   *Pour récupérer tous les enregistrements d'un modèle.*

4. **Requêtes avec condition**
   ```php
   $models = Model::where('field', 'value')->get();
   ```
   *Pour récupérer des enregistrements avec une condition.*

5. **Mettre à jour un enregistrement**
   ```php
   $model = Model::find($id);
   $model->field = 'new value';
   $model->save();
   ```
   *Pour mettre à jour un enregistrement existant.*

6. **Supprimer un enregistrement**
   ```php
   $model = Model::find($id);
   $model->delete();
   ```
   *Pour supprimer un enregistrement existant.*

7. **Relations**
   ```php
   $model->relation()->save($relatedModel);
   ```
   *Pour sauvegarder un modèle lié dans une relation.*

8. **Pagination**
   ```php
   $models = Model::paginate(10);
   ```
   *Pour récupérer des enregistrements paginés.*

#### Moins utilisés

9. **Créer avec les données en masse**
   ```php
   Model::create([
       'field' => 'value',
   ]);
   ```
   *Pour créer un nouvel enregistrement avec des attributs spécifiés.*

10. **Mass update**
    ```php
    Model::where('field', 'value')->update(['field' => 'new value']);
    ```
    *Pour mettre à jour plusieurs enregistrements correspondant à une condition.*

11. **Incrémenter / Décrémenter**
    ```php
    $model->increment('field');
    $model->decrement('field');
    ```
    *Pour incrémenter ou décrémenter une valeur dans un enregistrement.*

12. **Relations polymorphiques**
    ```php
    $model->morphTo();
    $model->morphMany(RelatedModel::class, 'relation');
    ```
    *Pour gérer des relations polymorphiques.*

13. **Lazy Eager Loading**
    ```php
    $models = Model::with('relation')->get();
    ```
    *Pour charger une relation de manière paresseuse.*

14. **Event Observers**
    ```php
    Model::observe(ObserverClass::class);
    ```
    *Pour attacher un observer aux événements d'un modèle.*

15. **Soft Deletes**
    ```php
    use Illuminate\Database\Eloquent\SoftDeletes;
    ```
    *Pour activer la suppression douce sur un modèle.*

16. **Query Scopes**
    ```php
    public function scopeActive($query)
    {
        return $query->where('active', 1);
    }
    ```
    *Pour définir une portée de requête réutilisable.*

17. **Accessor et Mutator**
    ```php
    public function getFieldAttribute($value)
    {
        return ucfirst($value);
    }

    public function setFieldAttribute($value)
    {
        $this->attributes['field'] = strtolower($value);
    }
    ```
    *Pour personnaliser la récupération ou la définition d'un attribut de modèle.*

### Divers

#### Les plus utilisés

1. **Clearing Cache**
   ```bash
   php artisan cache:clear
   ```
   *Pour vider le cache de l'application.*

   ```bash
   php artisan config:clear
   ```
   *Pour vider le cache de configuration.*

   ```bash
   php artisan route:clear
   ```
   *Pour vider le cache des routes.*

   ```bash
   php artisan view:clear
   ```
   *Pour vider le cache des vues compilées.*

2. **Composer Commands**
   ```bash
   composer install
   ```
   *Pour installer les dépendances du projet.*

   ```bash
   composer update
   ```
   *Pour mettre à jour les dépendances du projet.*

   ```bash
   composer dump-autoload
   ```
   *Pour régénérer le fichier autoload de Composer.*

#### Moins utilisés

3. **Tinker**
   ```bash
   php artisan tinker
   ```
   *Pour ouvrir une console interactive pour interagir avec votre application.*

4. **Scheduler**
   ```bash
   php artisan schedule:run
   ```
   *Pour exécuter les tâches planifiées définies dans votre application.*

5. **Queue Worker**
   ```bash
   php artisan queue:work
   ```
   *Pour démarrer un worker de file d'attente.*

   ```bash
   php artisan queue:listen
   ```
   *Pour écouter et traiter les jobs de la file d'attente
