#### STAGE DE MEMOIRE DE MASTER 1 : ANALYSE BIOINFORMATIQUE DES DONNEES DE SEQUENCAGE SHOTGUN DE SPOUCHES D'*ESCHERICHIA* PROVENANT D' ENFANTS MALNUTRIS 
#### IHU Méditerranée Infection DE MARSEILLE  
#### EQUIPE CULTUROMICS
<img width="827" height="244" alt="Image" src="https://github.com/user-attachments/assets/3a0e89ab-5b22-4879-ab3d-3a637e070ddb" />

#### Titre Mémoire : Caractérisation d’*Escherichia marmotae* chez des enfants atteints de malnutrition aiguë sévère en République Démocratique du Congo (RDC) grâce à la culturomique et à la métagénomique.

  
###Table des matières    
 * __ Contrôle qualité__  
 * __ Correction des reads__  
 * __ Assemblage__  
 * __ Annotation du génome__  
 * __ Recherche de gène(s) et/ou de plasmide(s) de virulence__  
 * __ Average Nucleotidique identity__  
 * __ Typage des souches de *Escherichia*__  
 * __ Construire d'arbre phylogénétique__  


### 1) Création des environnements conda 
````
conda create -n amr -c bioconda -c conda-forge -y
conda create -n busco -c bioconda -c conda-forge -y
conda create -n abricate -c bioconda -c conda-forge -y
conda create -n mlst -c bioconda -c conda-forge -y
````
Explication des paramètres :

  conda create : Permet de créer un environnement conda  
  -n : donne le nom de l'environnement  
  -c : ajoute un channel dans l'environnement  
  -y : répondre "yes" à tout
