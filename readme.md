

# Prérequis

Ce projet est réalisé à l'aide de talend 6.1.

## Limation du projet 

Talend ne permet pas de parcourir de façon dynamique les colonnes d'un fichier Excel, nous avons du fixer les colonnes sur lesquelles travailler dans l'onglet permissions_tableau. Dans notre cas nous utilisons les colonnes B à K. Si vous avez plus de colonnes il suffit d'en rajouter dans le schéma du fichier excel et de l'onglet permissions_tableau accessible dans les métadonnées:

![](/assets/config_metadonnees.png)



rajouter les colonnes manquante, puis cliquer sur le bouton "Finish" , cela propagera l'ensemble des modifications dans le projet.

![](/assets/ajout_colonne.png)

Ensuite dans le composant t_javaRow_1: modifier le code afin d'ajouter les colonnes manquantes  comme ci-dessous :

![](/assets/tJavaRow.png)

```
java.util.List<String> hab =new java.util.ArrayList<String>();

hab.add(input_row.roleB);
hab.add(input_row.roleC);
hab.add(input_row.roleD);
hab.add(input_row.roleE);
hab.add(input_row.roleF);
hab.add(input_row.roleG);
hab.add(input_row.roleH);
hab.add(input_row.roleI);
hab.add(input_row.roleJ);
hab.add(input_row.roleK);

context.habilitations_roles = hab;
```

# Utilisation en ligne de commande

Une fois le projet exporté depuis talend, il vous suffit d'exécuter la ligne de commande suivante:

.\traitement_habilitations_1.3\traitement_habilitations\traitement_habilitations_run.bat --context_param onglet_traitements="traitements_vX.Y" --context_param fichier="d:\\temp\\habilitations.xlsx"

Ou X.Y correspond au numéro de version de voter fichier d'habilitations.