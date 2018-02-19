# Indication pour le proj du jour en production
	Si la page affichée ne contient pas d'icones ou d'images de fond, merci de faire F5 ! :)
	Merci

# PROCESS UTILISATION DEVISE

## CREER UNE NOUVELLE APP RAILS
#### CONSOLE
```
rails new nomApp
```

### GemFile Heroku compatible + gem 'devise'
#### ATOM (dans le Gemfile)
	1) Récupérer un gemfile heroku compatible
	2) Ajouter la gem devise
```
gem 'devise'
```

### Installation de l'environnement
#### CONSOLE
```
bundle install --without production
```

### Initialisation du repo Github + création app heroku
#### CONSOLE (Init repo github)
```
git init
git add .
git commit -am "Initial commit -> App Heroku compatible"
git push origin master
```
#### CONSOLE (cration app Heroku)
```
heroku create
heroku rename nomApp --> optionnel
```

## Création d'un controller Home (de pages statiques)
#### CONSOLE
```
rails g controller Home index
```

#### ATOM
		Modifier le fichier Routes.rb (config/routes.rb)
```
root : 'Home#index'
```
			(le get généré par la création du controller peut être supprimé)

## Intégration de Devise
#### CONSOLE
```
rails g devise:install
```
	Suivre les indications
	1) Mailer : si voulu
	2) La root : OK
	3) Intégration du gestionnaire d'affichage des msg flash
		app/views/layouts/application.html.erb
			Copier les 2 lignes dans le body, avant le yield
```ruby
<p class="notice"><%= notice %></p>
<p class="alert"><%= alert %></p>
```

## Générer un model pour les Users
#### CONSOLE
```
rails g devise User
```
Ce qui se passe automatiquement:
	--> Création de tous les fichiers nécessaires
	--> Initialisation des Routes

#### CONSOLE
```
rails db:migrate
```

## Possibilité de modification des views pour les sessions / gestion users
```
rails g devise:views
```


# Projet du jour
#### ATOM
### Faire persister les icones en production
	config/environments/production.rb
	Ajouter ces 2 lignes:
```
config.serve_static_assets = true
config.assets.compile = true
```

### Faire persister la background image en production
	Dans le CSS (body)
```
background: asset-data-url('background.jpg')
```
