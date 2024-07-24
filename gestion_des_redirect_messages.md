
Comment utiliser un redirect message

```php
    //utiliser un return redirect with le message
     return redirect('/route-de-redirection')->with('key-du-message', 'le message');
```

# Avoir accès au message dans le front-end

```php
   //utiliser la methode session qui contient un tableau de tous les messages envoyés par (with) après un redirect
   @if (session('success'))
  <div class="alert alert-success">
      {{session('success')}}
  </div>
    @endif
```
*Pour faire simple pour acceder a un message envoyé par redirect il suffit d'utiliser la méthode session('') et lui passer en paramettre la clé du message*
