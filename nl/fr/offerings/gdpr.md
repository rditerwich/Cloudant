---

copyright:
  years: 2018
lastupdated: "2018-06-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

<!-- Acrolinx: 2018-04-28 -->

# Règlement général sur la protection des données (RGPD)

Le Règlement général sur la protection des données cherche à créer un cadre juridique harmonisé pour la protection des données dans l'UE et vise à redonner aux citoyens le contrôle de leurs données personnelles, tout en imposant des règles strictes à ceux qui hébergent et 'traitent' ces données partout dans le monde. Ce règlement introduit également des règles relatives à la libre circulation des données à caractère personnel à l'intérieur et à l'extérieur de l'UE. 

Grâce au [Règlement général sur la protection des données ![Icône de lien externe](../images/launch-glyph.svg "Icône de lien externe")](https://www.eugdpr.org/){:new_window}, les clients {{site.data.keyword.cloudantfull}} peuvent se fier à la compréhension et à la conformité de l'équipe
{{site.data.keyword.cloudant_short_notm}} par rapport aux nouvelles normes et lois liées à la confidentialité des données, mais aussi à la capacité croissante d'{{site.data.keyword.IBM}} de fournir une
suite complète de solutions destinées à assister les entreprises de toutes tailles quant à la conformité à leurs propres exigences gouvernementales en matière de données internes.


## Comment puis-je effectuer un audit de l'accès à {{site.data.keyword.cloudant_short_notm}} ?

Vous trouverez des informations sur le processus d'audit dans la rubrique [Consignation dans le journal d'audit](../offerings/audit.html#audit-logging){:new_window}. 

## Classifications de données personnelles prises en charge

Les catégories suivantes de données personnelles sont prises en charge par {{site.data.keyword.cloudant_short_notm}} pour le Règlement général sur la protection des données
(RGPD) :

**Données personnelles**, par exemple :
 * Identité/état civil
 * Vie personnelle
 * Vie professionnelle
 * Informations économiques et financières
 * Données d'emplacement
 * Données de connectivité/d'appareil

**Données personnelles sensibles**, limitées à :
  * Données sur la santé. Des conditions supplémentaires s'appliquent. Seront abordées dans une description de service.

Si vous stockez des données de soins de santé, vous *devez* effectuer les tâches suivantes :
 - Prévenir {{site.data.keyword.cloudant_short_notm}} avant d'écrire des données. 
 - Demander un cluster dédié conforme à HIPAA.

Pour plus d'informations sur les classifications de données personnelles prises en charge, voir
[{{site.data.keyword.cloudant_short_notm}} detailed system requirements sous 2. Personal Data ![Icône de lien externe](../images/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=2EBB5860B34311E7A9EB066095601ABB){:new_window}.

## Données me concernant

{{site.data.keyword.cloudant_short_notm}} enregistre certaines des données relatives à ses utilisateurs, et est un contrôleur de données pour
lesdites informations personnelles. Les données que nous enregistrons dépendent du type de compte dont vous disposez. 

Si vous avez un cluster {{site.data.keyword.cloudant_short_notm}} dédié/cluster {{site.data.keyword.cloudant_short_notm}}
d'entreprise, nous enregistrons des données vous concernant et nous sommes considéré comme un contrôleur de données pour vos données dans le
contexte du Règlement général sur la protection des données. Si vous avez un cluster {{site.data.keyword.cloudant_short_notm}} dédié/cluster {{site.data.keyword.cloudant_short_notm}} d'entreprise,
nous avons vos :

 * Nom
 * Adresse électronique

Les données que nous conservons peuvent être consultées et mises à jour via le tableau de bord {{site.data.keyword.cloudant_short_notm}}. 

Si vous possédez un compte mis à disposition par {{site.data.keyword.cloud_notm}} (incluant une instance dédiée),
{{site.data.keyword.cloudant_short_notm}} _ne_ collecte pas les données personnelles mentionnées précédemment. Ces données sont conservées par {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloudant_short_notm}} traite des informations personnelles client limitées durant l'exécution du service et l'optimisation de
l'expérience utilisateur de ce dernier.
Nous utilisons l'adresse électronique pour contacter les clients si besoin. Nous nous servons également de la surveillance des interactions client
avec le tableau de bord {{site.data.keyword.cloudant_short_notm}} pour traiter les informations personnelles. 

### Restriction de traitement

Nous envoyons les données d'interaction avec le tableau de bord à Segment. Il est possible de demander à {{site.data.keyword.cloudant_short_notm}} de limiter le
traitement des informations personnelles client de cette façon en créant une [demande de support {{site.data.keyword.cloudant_short_notm}}](mailto:support@cloudant.com). Lorsque
cette demande est reçue, {{site.data.keyword.cloudant_short_notm}} supprime les informations associées au client telles qu'elles ont été
envoyées à Segment, et empêche l'envoi d'autres données.
Nous devons conserver la possibilité de pouvoir contacter des clients dédiés par courrier électronique et de leur fournir une interface leur permettant de maintenir ces informations à jour directement ou via leur configuration des détails de leurs contacts via les détails de leur compte {{site.data.keyword.cloud_notm}}. 

## Notre base de données {{site.data.keyword.cloudant_short_notm}} est-elle chiffrée ?

Tous les clusters comportent un système de fichiers chiffrés (chiffrement au repos) utilisant Linux Unified Key Setup (LUKS). Les données contenues dans la base de données sont visibles pour nos équipes de support et des opérations (voir ci-dessous). 

Les données sensibles devant rester invisibles pour {{site.data.keyword.cloudant_short_notm}} doivent être chiffrées ou protégées (pseudonymisées) avant de nous être envoyées. Vous devez éviter d'utiliser des informations personnelles dans un `_id` de document, car dans ce cas, elles sont toujours visibles et écrites dans les journaux d'accès. 

## Emplacements des données

Les emplacements où {{site.data.keyword.cloudant_short_notm}} traite les données personnelles seront mises à disposition et tenues à jour via DPA (Data Sheet Addendum). 

Pour plus d'informations sur les emplacements des données, voir
[{{site.data.keyword.cloudantfull}} detailed system requirements sous 7. {{site.data.keyword.IBM_notm}} Hosting and Processing Locations ![Icône de lien externe](../images/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=2EBB5860B34311E7A9EB066095601ABB){:new_window}.

## Sécurité des services

### Utilisation de {{site.data.keyword.cloudant_short_notm}} en toute sécurité

En tant qu'utilisateur de {{site.data.keyword.cloudant_short_notm}}, vous devez :

 * Utiliser la configuration CORS par défaut pour empêcher tout accès non autorisé. 
 * Utiliser des clés d'API généreusement, de sorte que les composants aient des "accès avec le moindre privilège", conjointement avec le journal d'audit. Cette pratique vous permet de comprendre qui a accédé à quelles données. 
 * Chiffrer ou protéger (pseudonymiser) les données sensibles avant de nous les envoyer.

### Mesures de sécurité physique et environnementale

La sécurité physique de nos centres de données est gérée par nos fournisseurs d'infrastructure : SoftLayer,
AWS et 21Vianet. Ils conservent tous des certifications auditées en externe pour leur sécurité physique. Nous ne fournirons pas d'autres détails sur les contrôles de sécurité physique en vigueur dans nos centres de données.


La sécurité physique des bureaux utilisés par notre personnel est gérée par {{site.data.keyword.IBM_notm}} Corporate.
Les détails de certification et les rapports d'attestation (par exemple, ISO et SOC2) sont disponibles sur demande du client.


### Mesures techniques et organisationnelles

Des mesures techniques et organisationnelles (TOM) sont employées par {{site.data.keyword.cloudant_short_notm}} pour garantir la sécurité des données personnelles.
Nous conservons des certifications auditées en externe pour les contrôles que nous effectuons.
Les détails de certification et les rapports d'attestation (par exemple, ISO et SOC2) sont disponibles sur demande du client.


### Accès de service aux données

L'équipe de support et des opérations {{site.data.keyword.cloudant_short_notm}} a accès aux données client et peut y accéder durant des opérations de routine.
Les équipes n'accèdent aux données que si cela est nécessaire, afin d'exploiter et de prendre en charge le service.
De plus, l'accès repose sur la *nécessité de savoir* et il est consigné, surveillé et audité. 

## Suppression de données

### Suppression d'un document

Lorsqu'un document est supprimé, la base de données crée un 'tombstone'. Ce que contient le tombstone dépend de la façon dont vous le supprimez :

 - Si vous effectuez un appel `DELETE`, le tombstone inclut les zones `_id`, `_rev` et `_deleted`. 
 - Si vous supprimez le document en le mettant à jour avec une zone `_deleted: true` et en exécutant une action `PUT` ou `POST` dessus, le tombstone inclut ce que vous définissez dans le corps du document. Cette pratique peut être utile dans certains cas, par exemple, lorsque vous enregistrez la raison de la suppression d'un document dans son tombstone.

Pour plus d'informations sur la suppression de tombstones, voir [Retrait simple de documents 'tombstone'](../api/document.html#-tombstone-documents){:new_window}.

### A quel moment un document supprimé est-il retiré ?

La compression s'exécute automatiquement et retire régulièrement les anciennes révisions (supprimées ou non) de la base de données,
en écrivant uniquement les révisions 'feuille' dans un nouveau fichier.
Nous conservons un historique de
`_id` et `_rev` pour activer la réplication, mais pas les anciens corps de document. 

> **Remarque** : {{site.data.keyword.cloudant_short_notm}} n'expose pas l'API de compression CouchDB. 

Nous ne pouvons pas garantir le moment précis auquel la compression d'une base de données se produira. Les clusters peuvent héberger
plus de 10000 comptes, contenant chacun un grand nombre de bases de données. La compression est effectuée en arrière-plan
sur l'ensemble du cluster, et les bases de données sont toujours compressées ; simplement, il est impossible de garantir que les
données que vous venez de supprimer/modifier sont en train d'être compressées. 

{{site.data.keyword.cloudant_short_notm}} accepte les demandes de *droit à l'oubli* créées par le [bureau délégué à la protection des données (DPO) {{site.data.keyword.IBM_notm}} ![Icône de lien externe](../images/launch-glyph.svg "Icône de lien externe")](http://w3-03.ibm.com/ibm/privacy/index.html){:new_window}.
Lorsqu'une demande de *droit à l'oubli* est émise par le bureau délégué à la protection des données (DPO) {{site.data.keyword.IBM_notm}}, nous vérifions cette demande, nous déclenchons explicitement la compression de base de données et nous nous assurons que cette opération a bien eu lieu.
A la fin de ce processus, la seule version du document qui subsiste est son tombstone (`_id`, `_rev`, `_deleted`, et les autres zones éventuellement incluses par votre application). 

### Retrait de tombstones

{{site.data.keyword.cloudant_short_notm}} peut retirer complètement toutes les références et données d'un document si nécessaire.
Cette tâche est un processus géré par un opérateur appelé purge.
Avant de demander que des documents soient purgés, il est essentiel de bien comprendre que les documents purgés *ne peuvent pas être récupérés* par
{{site.data.keyword.cloudant_short_notm}} une fois le processus terminé. 

> **Remarque** : la purge d'API CouchDB n'est pas prise en charge par {{site.data.keyword.cloudant_short_notm}}.

Dans le contexte du Règlement général sur la protection des données, la purge est requise uniquement si des informations personnelles sont utilisées dans un ID document. Il existe plein de raisons de ne pas stocker des informations personnelles dans un `_id`, mais il existe une petite poignée de cas d'utilisation plus ou moins valides (par exemple, une adresse électronique unique).
Dans la mesure du possible, chiffrez ou pseudonymisez vos données afin de les rendre opaques pour {{site.data.keyword.cloudant_short_notm}}.

Si un document doit être retiré via une demande de *droit à l'oubli* :

1. Déposez une demande auprès du [bureau délégué à la protection des données (DPO) {{site.data.keyword.IBM_notm}}![Icône de lien externe](../images/launch-glyph.svg "Icône de lien externe")](http://w3-03.ibm.com/ibm/privacy/index.html){:new_window} afin de demander qu'un `_id` de document spécifique soit purgé et indiquez le motif de cette demande. 
1. A la réception d'une demande formelle émise par le bureau délégué à la protection des données (DPO) {{site.data.keyword.IBM_notm}}, l'équipe des opérations {{site.data.keyword.cloudant_short_notm}} vérifie
la demande afin de s'assurer que l'`id` contient bien des informations personnelles. Nous ne purgeons pas de données dont l'`_id` ne comporte pas d'informations personnelles. 
1. {{site.data.keyword.cloudant_short_notm}} déclenche l'action de purge afin de retirer définitivement les données demandées. 

Ce processus est uniquement utilisé pour les demandes de suppression d'urgence (par exemple, pour les demandes de *droit à l'oubli*) et ne peut pas être invoqué sur le long terme. Si votre application
utilise intentionnellement des informations personnelles dans des ID de document, vous devez la modifier de sorte que ces informations personnelles soient pseudonymisées ou qu'aucune information personnelle
ne soit utilisée dans les ID de document. Vous ne pouvez pas vous en remettre régulièrement au processus de purge déclenché par
l'équipe des opérations {{site.data.keyword.cloudant_short_notm}} pour éviter cela.
Par conséquent, {{site.data.keyword.cloudant_short_notm}} rejette les demandes de purge suivantes :

1. La demande porte sur une purge régulière, par exemple, *tous les 30 jours*.
1. La demande porte sur plus de 100 documents.

Même en ayant recours à une purge, les informations personnelles contenues dans la zone `_id` s'immiscent dans des endroits non désirés, par exemple, dans des journaux
{{site.data.keyword.cloudant_short_notm}}, par conséquent, il est préférable d'éviter cette opération. Nous avons une raison métier de conserver ces journaux et nous ne retirons
pas les lignes contenant des valeurs `_id` de document. 

### Que dire de la suppression d'une base de données ?

Lorsqu'elle est supprimée, une base de données est placée dans une corbeille pendant 48 heures maximum, puis elle est retirée du système de fichiers.
L'équipe {{site.data.keyword.cloudant_short_notm}} *ne crée pas* de copies de sauvegarde de vos bases de données ;
cette tâche *incombe au client*. Vous devez vous assurer que toutes le copies de votre base de données
sont retirées de votre système.
Pour plus d'informations, voir
[Sauvegarde et restauration de {{site.data.keyword.cloudant_short_notm}}](../guides/backup-cookbook.html#cloudant-nosql-db-backup-and-recovery){:new_window}. 

Pour obtenir de l'aide supplémentaire, contactez le
[support {{site.data.keyword.cloudant_short_notm}} ![Icône de lien externe](../images/launch-glyph.svg "Icône de lien externe")](mailto:support@cloudant.com).

