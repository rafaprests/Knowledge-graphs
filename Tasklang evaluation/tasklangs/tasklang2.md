# TaskLang : Un Modèle Universel de Description de Tâches (Inspiré de AROMTASK)

## 1. Structure Fondamentale

### PROBLEM <Problem_Name>
* **@RDFClass**: tasklang:Problem  
* **@URI**: <http://example.org/problems/ProblemName>  

**DESCRIPTION**: "<Description détaillée du problème à résoudre>"  
**GOAL**: "<Objectif principal ou résultat attendu>"  

**INPUTS**:
- **ingredients**: [
  * **@RDFClass**: tasklang:Ingredient  
  * "<Nom_Ingredient_1>: <Description> (<quantité>, <mesure>, <qualité>)"  
  * "<Nom_Ingredient_2>: <Description> (<quantité>, <mesure>, <qualité>)"
]

- **utensils**: [
  * **@RDFClass**: tasklang:Utensil  
  * "<Nom_Ustensile_1>: <Description>, <importance>"  
  * "<Nom_Ustensile_2>: <Description>, <importance>"
]

- **resources**: [
  * **@RDFClass**: tasklang:Resource  
  * "<Nom_Resource_1>: <Description> (<usage>, <disponibilité>, etc.)"
]

- **design**: "<Description ou schéma du procédé/approche>"  

- **context**: {
  * **@RDFClass**: tasklang:Context  
  domain: "<Domaine d'application>",  
  constraints: "<Contraintes spécifiques>",  
  reference: "<Référence ou source principale>",  
  parameters: [
    {
      * **@RDFClass**: tasklang:Parameter  
      name: "<Nom_Paramètre_1>",  
      value: <Valeur>,  
      unit: "<Unité>",  
      valid_range: "<Intervalle valide>"  
    },
    {
      name: "<Nom_Paramètre_2>",  
      value: <Valeur>,  
      unit: "<Unité>",  
      valid_range: "<Intervalle valide>"  
    }
  ]
}

**QUALITY_CRITERIA**:
- "<Critère_1>: <Description du critère et méthode de validation associée>"
- "<Critère_2>: <...>"

**OUTPUTS**:
- finalProduct: "<Description du résultat final attendu>"
- secondaryOutputs: [
  "<Output_Secondaire_1>: <Description>",
  "<Output_Secondaire_2>: <Description>"
]

### METHOD <Method_Name>
* **@RDFClass**: `tasklang:Method`
* **@URI**: `<http://example.org/methods/MethodName>`
* **@DomainReference**: `<http://domain-specific-ontology.org/concept/ReferenceConcept>`

**DOMAIN**: "<Domaine d'application>"
**DESCRIPTION**: "<Description détaillée de la méthode>"
**REFERENCE**: "<Sources, références, ou origine de la méthode>"

**PREREQUISITES**:
- "<Prérequis_1>" [**@Importance**: "<Critique/Important/Recommandé>"]
- "<Prérequis_2>" [**@Importance**: "<Critique/Important/Recommandé>"]

**STEPS**:
1. **TASK** "<Nom_Tâche_1>"
   * **@RDFClass**: `tasklang:Task`
   * **@DomainTechnique**: `<http://domain-specific-ontology.org/techniques/TechniqueName>`
   
   **INPUTS**: [<liste des entrées requises>]
   **ACTION**: "<Description détaillée de l'action à effectuer>"
   **NOTES**: "<Informations complémentaires, astuces, conseils>"
   **DURATION**: "<Estimation du temps requis>"
   **OUTPUT**: "<Description du résultat de cette tâche>"
   **VALIDATION_RULES**: [
     * **@RDFClass**: `tasklang:ValidationRule`
     "<Règle_Validation_1>: <Description de la règle>"
   ]
   **PARAMETERS**: [
     {
       name: "<Nom_Paramètre>",
       value: "<Valeur>",
       measurement: "<Méthode de mesure ou vérification>"
     }
   ]

2. **TASK** "<Nom_Tâche_2>"
   * **@RDFClass**: `tasklang:Task`
   
   **ACTION**: "<Description détaillée de l'action à effectuer>"
   **NOTES**: "<Informations complémentaires>"
   **DURATION**: "<Estimation du temps requis>"
   **OUTPUT**: "<Description du résultat de cette tâche>"

3. **DECISION** "<Nom_Décision>"
   * **@RDFClass**: `tasklang:Decision`
   
   **CONDITION**: "<Condition à évaluer>"
   **OPTIONS**:
   - **OPTION** "<Nom_Option_1>":
     **WHEN**: "<Condition spécifique>"
     **THEN**: "Aller à TASK <Nom_Tâche_Cible_1>"
     **REASON**: "<Justification du choix>"
   
   - **OPTION** "<Nom_Option_2>":
     **WHEN**: "<Condition spécifique>"
     **THEN**: "Aller à TASK <Nom_Tâche_Cible_2>"
     **REASON**: "<Justification du choix>"

4. **LOOP** "<Nom_Boucle>"
   * **@RDFClass**: `tasklang:Loop`
   
   **CONDITION**: "<Condition de sortie>"
   **BLOCK**:
   a) **TASK** "<Nom_Sous_Tâche_1>"
      **ACTION**: "<Description détaillée de l'action à effectuer>"
      **DURATION**: "<Estimation du temps requis>"
      **OUTPUT**: "<Description du résultat>"
   
   b) **TASK** "<Nom_Sous_Tâche_2>"
      **ACTION**: "<Description détaillée de l'action à effectuer>"
      **NOTES**: "<Informations complémentaires>"
      **DURATION**: "<Estimation du temps requis>"
      **OUTPUT**: "<Description du résultat>"
   
   c) **MEASUREMENT** "<Nom_Mesure>"
      **ACTION**: "<Comment effectuer la mesure>"
      **CONDITION**:
      - **EXPRESSION**: "<Expression conditionnelle basée sur la mesure>"
      - **CONSEQUENCE**: "<Action à entreprendre si la condition est vraie>"
      **OUTPUT**: "<Résultat de la mesure>"

5. **PARALLEL** "<Nom_Tâches_Parallèles>"
   * **@RDFClass**: `tasklang:ParallelTasks`
   
   **DESCRIPTION**: "<Description des tâches à exécuter en parallèle>"
   **TASKS**:
   - **TASK** "<Nom_Tâche_Parallèle_1>"
     **ACTION**: "<Description détaillée>"
     **DURATION**: "<Estimation du temps requis>"
   
   - **TASK** "<Nom_Tâche_Parallèle_2>"
     **ACTION**: "<Description détaillée>"
     **DURATION**: "<Estimation du temps requis>"
   
   **SYNCHRONIZATION**: "<Condition ou point de synchronisation>"

6. **TASK** "<Nom_Tâche_Finale>"
   **ACTION**: "<Description détaillée de l'action à effectuer>"
   **NOTES**: "<Informations complémentaires>"
   **DURATION**: "<Estimation du temps requis>"
   **OUTPUT**: "<Description du résultat final>"

**RISKS**:
- "<Risque_1>: <Description du risque>" [**@Severity**: "<Haute/Moyenne/Basse>", **@Mitigation**: "<Stratégie d'atténuation>"]
- "<Risque_2>: <Description du risque>" [**@Severity**: "<Haute/Moyenne/Basse>", **@Mitigation**: "<Stratégie d'atténuation>"]

**VALIDATION_RULES**:
* **@RDFClass**: `tasklang:ValidationRule`
* "SI <condition> ALORS <conséquence>"
* "SI <condition> ALORS <conséquence>"

### STRATEGY <Strategy_Name>
* **@RDFClass**: `tasklang:Strategy`
* **@URI**: `<http://example.org/strategies/StrategyName>`

**PROBLEM**: <Problem_Name>
**METHODS**:
- <Method_Name_1> [**@Domain**: "<Domaine>", **@Context**: "<Contexte d'application>"]
- <Method_Name_2> [**@Domain**: "<Domaine>", **@Context**: "<Contexte d'application>"]
- <Method_Name_3> [**@Domain**: "<Domaine>", **@Context**: "<Contexte d'application>"]

**SELECTION_RULES**:
- **RULE**:
  **CONDITION**: "<Expression conditionnelle basée sur le contexte>"
  **METHOD**: <Method_Name_1>
  **JUSTIFICATION**: "<Justification du choix de cette méthode>"

- **RULE**:
  **CONDITION**: "<Expression conditionnelle basée sur le contexte>"
  **METHOD**: <Method_Name_2>
  **JUSTIFICATION**: "<Justification du choix de cette méthode>"

- **RULE**:
  **CONDITION**: "default"
  **METHOD**: <Method_Name_3>
  **JUSTIFICATION**: "<Justification du choix de cette méthode par défaut>"

**STRATEGY_NOTES**:
- "<Note_1>: <Information complémentaire sur la stratégie>"
- "<Note_2>: <Information complémentaire sur la stratégie>"

**DOMAIN_CONTEXT**:
* **@RDFClass**: `tasklang:DomainContext`
* "<Contexte_1>: <Information sur le contexte domaine-spécifique>"
* **PROVENANCE**: {
  source: "<Source d'information>",
  confidence: "<Niveau de confiance>",
  expert: "<Expert du domaine ou source d'expertise>"
}


