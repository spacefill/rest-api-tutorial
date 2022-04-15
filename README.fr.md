# Tutoriel d'utilisation de l'API REST de l'OMS de SpaceFill

Une version plus complète de cette documentation est disponible en anglais : [README.md](README.md).

* [FAQ](#faq)
  * [Quelle est la définition des différents statuts des "orders" ?](#quelle-est-la-définition-des-différents-statuts-des-"orders"-?)

## FAQ

### Quelle est la définition des différents statuts des "orders" ?

Voici les différents statuts possibles et leurs définitions :

- `WAREHOUSE_NEEDS_TO_CONFIRM_PLANNED_EXECUTION_DATE_STATE` : Statut utilisé uniquement lorsque l'option de "Prise de rendez-vous" est activé.<br />
  Quand un "order" est créé par un chargeur, l'entrepôt doit confirmer qu'il est disponible pour recevoir/expédier de la marchandise sur ce créneau.
- `SHIPPER_NEEDS_TO_SUGGEST_NEW_PLANNED_EXECUTION_DATE_STATE` : Statut utilisé uniquement lorsque l'option de "Prise de rendez-vous" est activé.<br />
  Quand un "order" est créé par un chargeur, si l'entrepôt n'est pas disponible au créneau intialement demandé par le chargeur, le chargeur doit proposer un nouveau créneau.
- `ORDER_IS_READY_TO_BE_EXECUTED_STATE` : Tout est prêt, l'ordre est en attente de complétion.
- `CANCELED_ORDER_STATE` : L'"order" est annulé par le chargeur.
- `COMPLETED_ORDER_STATE` : L'"order" a été complété (totalement ou partiellement avec ou sans ajustement) par l'entrepôt et la commande a bien été réceptionné ou expédié.
- `FAILED_ORDER_STATE` : Bien que l'"order" était prévu, pour une raison quelconque, l'"order" n'a pas pu être complété (le camion ne s'est pas présenté, refus du camion, ...)

