# Steps de mise en place de système d'authentification

## Première étape : Mise en place des routes

```php
//Routes d'authentification

Route::get('/register', [RegisterController::class, 'index'])->name('register');//Affiche la page d'inscription
Route::post('/register', [RegisterController::class, 'store']); // permet d'effectuer l'enregistrement une fois le formulaire soumis

Route::get('/login', [SessionsController::class, 'index'])->name('login');//Affiche la page de connexion
Route::post('/login', [SessionsController::class, 'login']);// permet d'effectuer la connexion une fois le formulaire soumis
```

## Première étape : Mise en place des vues

-   Il faut mettre en place les deux vues dans un dossier Auth
    _login.blade.php et register.blade.php_

  ### A quoi ressemble les deux formulaires?

#### Pour le register

```php
// views/Auth/register.blade.php

<form method="POST" action="{{route('login')}}">
           @csrf
          <!-- les champs de votre formulaire ici-->
           <div class="mb-3">
                <label for="password" class="form-label">Mot de passe</label>
                <input type="password" class="form-control @error('password') is-invalid @enderror" id="password"
                    required value="{{old('password')}}" name="password">
                @error('password')
                    <div class="invalid-feedback">
                        {{$message}}
                    </div>
                @enderror
            </div>
            <div class="mb-3">
                <label for="password_confirmation" class="form-label">Confirmez le mot de passe</label>
                <input type="password" class="form-control @error('password_confirmation') is-invalid @enderror"
                    id="password_confirmation" required value="{{old('password_confirmation')}}"
                    name="password_confirmation">
                @error('password_confirmation')
                    <div class="invalid-feedback">
                        {{$message}}
                    </div>
                @enderror
            </div>
            <button type="submit" class="btn btn-primary w-100">Créer le compte</button>
</form>
```
**Note: il faut noter que le champ password_confirmation est obligatoire**

#### Pour le login

```php
// views/Auth/login.blade.php
<form method="POST" action="{{route('login')}}">
           @csrf
          <!-- les champs de votre formulaire ici-->
           <div class="mb-3">
               <label for="password" class="form-label">Mot de passe</label>
               <input type="password" class="form-control @error('password') is-invalid @enderror" id="password"
                   required value="{{old('password')}}" name="password">
               @error('password')
                   <div class="invalid-feedback">
                       {{$message}}
                   </div>
               @enderror
           </div>
           <button type="submit" class="btn btn-primary w-100">Se connecter</button>
       </form>
```

### Deuxième étape: Mettre en place un validator request 

Ici on va juste mettre l'accent sur la validation du passsword

```php
// App/Http/Requests/RegisterResquest.php 

//on peut mettre plusieurs regles si on le souhaite

 public function rules(): array
    {
        return [
                //vos autres rules de validation ici...
            'password' => [ 'required','confirmed',Password::default(), //utiliser le password default 
            // ou si vous le voulez,utiliser des regles précises comme ci-dessous

                // Password::min(8)
                //     ->mixedCase()
                //     ->symbols()
            ],
        ];
    }
```

### Troisième étape: Mettons maitenat en place la méthode qui permet d'enregistrer l'utilisateur

```php
// app\Http\Controllers\Auth\RegisterController.php

<?php

namespace App\Http\Controllers\Auth;

use App\Models\User;
use Illuminate\Http\Request;
use App\Http\Controllers\Controller;
use Illuminate\Support\Facades\Auth;
use App\Http\Requests\RegisterRequest;

class RegisterController extends Controller
{
    public function index(){
       //
    }

    public function store(RegisterRequest $request)
    {
        //on récupère les données validées
        $validated = $request->validated();
            //créer le nouvel utilisateur
        User::create([
            "name" => $validated["name"],
            "email" => $validated["email"],
            "password" => bcrypt($validated["password"]),
        ]);
        //connecter l'utilisateur 
        $user= User::where('email',$validated['email'])->firstOrFail();
        Auth::login($user);
        //le rediriger 
        return redirect()->route('...');
    }
}

```
