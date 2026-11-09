# Rapport d'audit — à compléter

Auteur : rayane badi 
Date : 9 / 11 / 2026
Référence de départ (commit) : commit documentaire

| ID constat | Règle CT | Fichier et fonction | Reproduction / observation | Impact | Priorité P0/P1/P2 | Action (corriger / surveiller / différer) |
|---|---|---|---|---|---|---|
| A-01 | CT-06 |src/fees.js: calculateXhippingFee |(0,'FR') -> reçu 4E, attendu RangerError/(1,'XX') -> NaN alorque attendu RangeError |facturation sur entrée interdite, sortie non numerique  | p1  | corriger avec 3 test initialement: weight :0 , inifnity et Zone:'XX||' | 
| A-02 | CT-03 | src/shipment.js: advanceShipment() | Créer un colis, l’annuler avec cancelShipment(), puis demander prepared avec advanceShipment() : la transition est acceptée. | Un colis annulé peut reprendre son parcours alors que canceled est terminal. | P0 | Corriger : interdire toute transition depuis canceled en levant une Error. |
| A-03 | CT-04 | src/shipment.js: cancelShipment() | Faire avancer un colis jusqu’à in_transit, puis appeler cancelShipment() : l’annulation est acceptée. | Un colis déjà en transport peut être annulé contrairement au contrat. | P1 | Corriger : autoriser l’annulation uniquement depuis created ou prepared. |
| A-06 | CT-08 | src/php/TrackingPresenter.php — publicCard() | La carte publique contient recipientEmail en plus de reference et statusLabel. | Divulgation du courriel du destinataire dans la carte publique PHP. | P0 | Corriger en priorité : tester les clés exactes, puis retirer recipientEmail tout en conservant les libellés existants. || A-05 | CT-07 | src/tracking.js — getPublicTracking() | La vue publique contient recipientEmail en plus de reference, status et history. | Divulgation du courriel du destinataire dans une représentation publique. | P0 | Corriger en priorité : tester les clés exactes et l'indépendance de l'historique, puis retirer recipientEmail de la vue publique. |

## Dette différée et justification

## Contrôles avant modification

## Contrôles après modification

## Limites et risques résiduels
