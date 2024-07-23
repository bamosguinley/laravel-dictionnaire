### Artisan (CLI) Commands

#### Les plus utilisés

1. *Serveur de développement*
   bash
   
   # php artisan serve
    *Pour démarrer un serveur de développement local.*
   

3. *Migration*
   bash
   
   # php artisan migrate
   *Pour exécuter toutes les migrations non exécutées.*

  # php artisan migrate:rollback
   *Pour annuler la dernière migration exécutée.*

   # php artisan migrate:refresh
    *Pour annuler toutes les migrations et les réexécuter.*

   php artisan migrate:reset
   # Pour annuler toutes les migrations.

   php artisan migrate:status
   # Pour voir l'état actuel des migrations.
   

5. *Modèles*
   bash
   php artisan make:model ModelName
   # Pour créer un nouveau modèle.

   php artisan make:model ModelName -m
   # Pour créer un nouveau modèle avec une migration.

   php artisan make:model ModelName -c
   # Pour créer un nouveau modèle avec un contrôleur.

   php artisan make:model ModelName -r
   # Pour créer un nouveau modèle avec une ressource.
  
  composer dump -autoload
   # Pour les controllers créer soit même

4. *Contrôleurs*
   bash
   php artisan make:controller ControllerName
   # Pour créer un nouveau contrôleur.

   php artisan make:controller ControllerName --resource
   # Pour créer un nouveau contrôleur avec des méthodes de ressource RESTful.

   php artisan make:controller ControllerName --model=ModelName
   # Pour créer un nouveau contrôleur et l'associer à un modèle.
   

5. *Migration*
   bash
   php artisan make:migration create_table_name_table
   # Pour créer une nouvelle migration pour créer une table.
   

6. *Factory*
   bash
   php artisan make:factory FactoryName
   # Pour créer une nouvelle factory.
   

7. *Seeder*
   bash
   php artisan make:seeder SeederName
   # Pour créer un nouveau seeder.

   php artisan db:seed
   # Pour exécuter les seeders et peupler la base de données avec des données fictives.
   

8. *Commande personnalisée*
   bash
   php artisan make:command CommandName
   # Pour créer une nouvelle commande Artisan personnalisée.
   

9. *Middleware*
   bash
   php artisan make:middleware MiddlewareName
   # Pour créer un nouveau middleware.
   

10. *Notifications*
    bash
    php artisan make:notification NotificationName
    # Pour créer une nouvelle notification.
    

11. *Events*
    bash
    php artisan make:event EventName
    # Pour créer un nouvel événement.
    

12. *Jobs*
    bash
    php artisan make:job JobName
    # Pour créer une nouvelle tâche (job).
    

13. *Listeners*
    bash
    php artisan make:listener ListenerName
    # Pour créer un nouveau listener pour un événement.
    

14. *Requests*
    bash
    php artisan make:request RequestName
    # Pour créer une nouvelle requête de validation.
    

#### Moins utilisés

15. *Policy*
    bash
    php artisan make:policy PolicyName
    # Pour créer une nouvelle policy d'autorisation.
    

16. *Mail*
    bash
    php artisan make:mail MailName
    # Pour créer une nouvelle classe de mail.
    

17. *Notifications Channel*
    bash
    php artisan make:notification-channel ChannelName
    # Pour créer un nouveau canal de notification.
    

18. *Observer*
    bash
    php artisan make:observer ObserverName --model=ModelName
    # Pour créer un nouvel observer pour surveiller les changements sur un modèle.
    

19. *Provider*
    bash
    php artisan make:provider ProviderName
    # Pour créer un nouveau service provider.
    

20. *Rule*
    bash
    php artisan make:rule RuleName
    # Pour créer une nouvelle règle de validation personnalisée.
    

21. *Test*
    bash
    php artisan make:test TestName
    # Pour créer un nouveau test.
    
22.*Link storage resources (image) to public app
   bash
   php artisan storage:link
   # Pour lier le dossier storage aux ressouces du dossier public 
### Eloquent ORM

#### Les plus utilisés

1. *Créer un enregistrement*
   php
   $model = new Model;
   $model->field = 'value';
   $model->save();
   # Pour créer et enregistrer un nouvel enregistrement.
   

2. *Trouver un enregistrement par ID*
   php
   $model = Model::find($id);
   # Pour trouver un enregistrement par son ID.
   

3. *Tous les enregistrements*
   php
   $models = Model::all();
   # Pour récupérer tous les enregistrements d'un modèle.
   

4. *Requêtes avec condition*
   php
   $models = Model::where('field', 'value')->get();
   # Pour récupérer des enregistrements avec une condition.
   

5. *Mettre à jour un enregistrement*
   php
   $model = Model::find($id);
   $model->field = 'new value';
   $model->save();
   # Pour mettre à jour un enregistrement existant.
   

6. *Supprimer un enregistrement*
   php
   $model = Model::find($id);
   $model->delete();
   # Pour supprimer un enregistrement existant.
   

7. *Relations*
   php
   $model->relation()->save($relatedModel);
   # Pour sauvegarder un modèle lié dans une relation.
   

8. *Pagination*
   php
   $models = Model::paginate(10);
   # Pour récupérer des enregistrements paginés.
   

#### Moins utilisés

9. *Créer avec les données en masse*
   php
   Model::create([
       'field' => 'value',
   ]);
   # Pour créer un nouvel enregistrement avec des attributs spécifiés.
   

10. *Mass update*
    php
    Model::where('field', 'value')->update(['field' => 'new value']);
    # Pour mettre à jour plusieurs enregistrements correspondant à une condition.
    

11. *Incrémenter / Décrémenter*
    php
    $model->increment('field');
    $model->decrement('field');
    # Pour incrémenter ou décrémenter une valeur dans un enregistrement.
    

12. *Relations polymorphiques*
    php
    $model->morphTo();
    $model->morphMany(RelatedModel::class, 'relation');
    # Pour gérer des relations polymorphiques.
    

13. *Lazy Eager Loading*
    php
    $models = Model::with('relation')->get();
    # Pour charger une relation de manière paresseuse.
    

14. *Event Observers*
    php
    Model::observe(ObserverClass::class);
    # Pour attacher un observer aux événements d'un modèle.
    

15. *Soft Deletes*
    php
    use Illuminate\Database\Eloquent\SoftDeletes;
    # Pour activer la suppression douce sur un modèle.
    

16. *Query Scopes*
    php
    public function scopeActive($query)
    {
        return $query->where('active', 1);
    }
    # Pour définir une portée de requête réutilisable.
    

17. *Accessor et Mutator*
    php
    public function getFieldAttribute($value)
    {
        return ucfirst($value);
    }

    public function setFieldAttribute($value)
    {
        $this->attributes['field'] = strtolower($value);
    }
    # Pour personnaliser la récupération ou la définition d'un attribut de modèle.
    

### Divers

#### Les plus utilisés

1. *Clearing Cache*
   bash
   php artisan cache:clear
   # Pour vider le cache de l'application.

   php artisan config:clear
   # Pour vider le cache de configuration.

   php artisan route:clear
   # Pour vider le cache des routes.

   php artisan view:clear
   # Pour vider le cache des vues compilées.
   

2. *Composer Commands*
   bash
   composer install
   # Pour installer les dépendances du projet.

   composer update
   # Pour mettre à jour les dépendances du projet.

   composer dump-autoload
   # Pour régénérer le fichier autoload de Composer.
   

#### Moins utilisés

3. *Tinker*
   bash
   php artisan tinker
   # Pour ouvrir une console interactive pour interagir avec votre application.
   

4. *Scheduler*
   bash
   php artisan schedule:run
   # Pour exécuter les tâches planifiées définies dans votre application.
   

5. *Queue Worker*
   bash
   php artisan queue:work
   # Pour démarrer un worker de file d'attente.

   php artisan queue:listen
   # Pour écouter et traiter les jobs de la file d'attente en temps réel.
   

6. *Route List*
   bash
   php artisan route:list
   # Pour afficher la liste de toutes les routes définies dans l'application.
   
7. *Database Backup*
   bash
   php artisan db:backup
   # Pour effectuer une sauvegarde de la base de données.
   

8. *Maintenance Mode*
   bash
   php artisan down
   # Pour mettre l'application en mode maintenance.

   php artisan up
   # Pour remettre l'application en mode actif.
   

