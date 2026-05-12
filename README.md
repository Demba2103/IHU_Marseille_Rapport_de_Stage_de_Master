[__STAGE DE MEMOIRE DE MASTER 1 : ANALYSE BIOINFORMATIQUE DES DONNEES DE SEQUENCAGE SHOTGUN__](Mémoire)  

[![install with bioconda](https://img.shields.io/badge/install%20with-bioconda-brightgreen.svg?style=flat)](http://bioconda.github.io/recipes/megahit/README.html)

__IHU Méditerranée Infection de MARSEILLE__      

__EQUIPE CULTUROMICS__  

<img width="827" height="244" alt="Image" src="https://github.com/user-attachments/assets/3a0e89ab-5b22-4879-ab3d-3a637e070ddb" />

__Caractérisation génomique de souches *Escherichia marmotae* chez des enfants atteints de malnutrition aiguë sévère en République Démocratique du Congo (RDC) grâce à la culturomique et à la métagénomique__.  

[__Table des matières__](Table)   
*  [__Contrôle qualité__](contrôle)  
*  [__Correction des reads__](correction) 
*  [__Assemblage__](assemblage)
*  [__Annotation du génome__](annotation)
*  [__Recherche de gène(s) et/ou de plasmide(s) de virulence__](virulence) 
*  [__Average Nucleotidique identity__](average)  
*  [__Typage des souches d'*Escherichia*__](typage) 
*  [__Construire d'arbre phylogénétique__](tree)
 


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
