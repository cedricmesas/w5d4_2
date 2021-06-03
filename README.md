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

- **rails db:create db:migrate** : création et migration de la DB.


How to test in rails console ?

1. d = Doctor.create
2. p = Patient.create
3. a = Appointment.create(doctor: d, patient: p)
4. a.doctor (return array)
5. a.patient (return array)
6. d.patients (return array)
7. p.doctors (return array)
