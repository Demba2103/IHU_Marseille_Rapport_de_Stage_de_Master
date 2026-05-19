
<p align="center">
  <strong style="color:red">
    STAGE DE MÉMOIRE DE MASTER 1 : ANALYSE BIOINFORMATIQUE DES DONNÉES DE SÉQUENCAGE SHOTGUN
  </strong>
</p>

 <img width="414" height="122" alt="image" src="https://github.com/user-attachments/assets/0ea6c372-5c49-4cb4-9afa-5731d155801b" /> <img align="right" width="250" height="103" alt="image" src="https://github.com/user-attachments/assets/6198ae93-0de2-43a4-8a68-aa808c83b899" />   

      
<p align="center">
  <strong>EQUIPE 1 Culturomics de Professeur MILLION</strong>
</p>    
<p align="center">
  <strong>Encadré par Dr. Maryam Tidjani ALOU </strong>
</p>   

Culture bacterienne                |  Extraction ADN
:------------------------------:|:-------------------------:
<img align="left" width="420" height="353" alt="Image" src="https://github.com/user-attachments/assets/002d21a4-f70e-44fd-bb4f-4b96e2884d04" />                |   <img align="right" width="500" height="300" alt="Image" src="https://github.com/user-attachments/assets/ff3a5b98-1ae5-45d4-9696-b099728895ca" />
<img width="1872" height="1140" alt="image" src="https://github.com/user-attachments/assets/83846db8-40b4-4d00-9195-4d71463fed8d" />



## [🔵Description : ](description)    
Cette étude portant sur le microbiote des enfants atteints de malnutrition aigue sévère en République Démocratique du Congo (RDC) a pour but de pouvoir caractériser le génome d'*Escherichia marmotae*  grâce au séqençage du génome entier(le whole génome sequencing, WGS) et à une culture sélective sur Mac Conkey (MC). Cette bactérie Gram négative de la famille des *Enterobacteriaceae* a été décrite commme une espèces en 2015 à partir de son isolement de féces de marmotte d'ou son nom *Escherichia marmotae*. Elle est souvent confondue à *E. coli* du fait de sa promiximité génomique ne présentant que 10% de différence sur l'ensemble de leur génome. De plus, des études récentes portant notamment sur la résistance aux antibiotiques et la colonisation du digestif ont montré la présence de génes de resistance aux antibiotiques notamment de la famille des betalactamines mais également une capacité à coloniser le tube de l'homme de maniére silencieuse. De plus, des cas de septiémies chez l'homme ont été récemment décrites d'où la nécessité d'une surveillance accrue.

#### [📌Objecif : ](objectif)   
Ainsi l'objectif de cette étude est d'isoler cette bactérie en culture pour pouvoir caractériser son génome grâce à l'analyse bioinformatique.  

 #### [📍Echantillons : ](echanti)
 Nos échantillons ont été selectionnées sur la base d'un précédent shotgun qui a montré une fréquence élevée en *Escherichia coli*, *Escherichia marmotae* et *Escherichia fergusonii*.      

 Sur cette repository, nous avons chargé l'ensemble des fichiers et scripts nécessaires pour analyser ces données.
## [__TABLE DES MATIERES__](Table)   
*  [__Contrôle qualité__](contrôle)
   * fastqc  
*  [__Correction des reads__](correction)
   * Trimmomatic v.0.39
*  [__Assemblage__](assemblage)
   * spades
*  [__Annotation du génome__](annotation)
   * prokka
*  [__Recherche de gène(s) et/ou de plasmide(s) de virulence__](virulence)
   * Abricate
   * VFDB
   * Plasmidfinder
*  [__pangenome__](pan)
   * roary
*  [__Average Nucleotidique identity__](average)
   * FastANI
*  [__Typage des souches d'*Escherichia*__](typage)
   * mlst
*  [__Construire d'arbre phylogénétique__](tree)
   * IQtree
   * MEGA v.11
 


  
**1) Création des environnements conda**
````
conda create -n amr -c bioconda -c conda-forge -y
conda create -n busco -c bioconda -c conda-forge -y
conda create -n abricate -c bioconda -c conda-forge -y
conda create -n mlst -c bioconda -c conda-forge -y
````
Explication des paramètres :
  conda create : permet de créer un environnement conda  
  -n : donne le nom de l'environnement  
  -c : ajoute un channel dans l'environnement  
  -y : répondre "yes" à tout
