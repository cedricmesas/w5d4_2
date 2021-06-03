# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version : _2.7.1_

Configuration :

- **rails new -d postgresql w5d4** : création de l'appli.

- **rails g model Patient** : création d'un model User.

- **rails g model Doctor** : création d'un model User.

- **rails g model Appointment** : création d'un model User.

- **t.belongs_to :doctor, index: true // t.belongs_to :patient, index: true** Rajout des id **Doctor** et **Patient** dans la table intermédiaire appointments.

- Dans app>model>Appointment : **belongs_to :doctor // belongs_to :patient** => créer les 2 liaisons : Un rendez-vous appartient à un docteur ; Un rendez-vous appartient à un patient ;

- Dans app>model>Doctor : **has_many :appointments // has_many :patients, through: :appointments** => créer les 2 liaisons : Un docteur peut avoir plusieurs rendez-vous ; Un docteur peut avoir plusieurs patients, à travers les rendez-vous ;

- Dans app>model>Patient : **has_many :appointments // has_many :doctors, through: :appointments** => créer les 2 liaisons : Un patient peut avoir plusieurs rendez-vous ; Un patient peut avoir plusieurs docteurs, à travers les rendez-vous. ;

- **rails generate migration AddIndexToArticles** : rajout de l'identifiant de la table users dans la table article.

- **add_reference :articles, :user, foreign_key: true** : rajout dans articles un identifiant de user.

- **rails db:create db:migrate** : création et migration de la DB.

- **belongs_to :user** : liaison entre les 2 models (Article -> User)

- **has_many :articles** : liaison entre les 2 models (User -> Article)

Use : 
- lauch rails console : **rails c**

- create an article in your console :
    * **$ my_article = Article.new(title: "THP", subject: "publicité", content: "Lorem Ipsum dolore iresm")**

- create an user instance with db save : 
    * **$ my_user = User.create(first_name: "Barack", last_name: "Obama", city: "Washington", age: 45)**

- link "my_article" object with "my_user" object :
    * **my_article.user = my_user**

- save object "my_article" in DB :
    * **my_article.save**

- retrieve the last article in the database :
    * **article1 = Article.last**

- retrieve the user object linked to the article.1 :
    * **article1.user**

- retrieve an array with all articles written by "my_user" :
    * **my_user.articles**

How to test an Article belong to User and an User has many Articles ?
1. a = Article.new
2. a.user
3. u = User.first
4. a.user = u
5. a.save
6. Article.last.user.articles
