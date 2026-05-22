
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
Cette étude portant sur le microbiote des enfants atteints de malnutrition aigue sévère en République Démocratique du Congo (RDC) a pour but de caractériser le génome d'*Escherichia marmotae*  grâce au séqençage du génome entier(le whole génome sequencing, WGS) et à une culture sélective sur Mac Conkey (MC). Cette bactérie Gram négative de la famille des *Enterobacteriaceae* a été décrite commme une nouvelle espèces en 2015 suite à de son isolement de féces de marmotte d'ou son nom *Escherichia marmotae*. Elle est souvent confondue à *E. coli* du fait de sa promiximité génomique ne présentant que 10% de différence sur l'ensemble de leur génome. De plus, des études récentes portant notamment sur la résistance aux antibiotiques et la colonisation du digestif ont montré la présence de génes de résistance aux antibiotiques notamment de la famille des bétalactamines mais également une capacité à coloniser le tube de l'homme de maniére silencieuse. De plus, des cas de septiémies chez l'homme ont été récemment décrites d'où la nécessité d'une surveillance accrue.

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


 #    [__Contrôle qualité__](fastqc) :
  
FastQC est un outil de contrôle qualité conçu pour analyser les données de séquençage brutes issues des technologies de séquençage à haut débit (High Throughput Sequencing).

Il permet d’évaluer rapidement la qualité des fichiers FASTQ en exécutant plusieurs tests statistiques et graphiques afin de générer un rapport de qualité détaillé.

Les résultats sont classés en trois catégories :  
❌ : Fail  
✅ : Pass  
🟨 : Warning  
FastQC peut être utilisé :

* en mode graphique interactif pour visualiser plusieurs rapports simultanément ;
  
* en mode ligne de commande pour une intégration dans des pipelines bioinformatiques automatisés.

Les rapports générés incluent notamment :

  * la qualité des bases ;
  * le contenu en GC ;
  * la présence d’adaptateurs ;
  * les séquences dupliquées ;
  * la distribution des longueurs de lectures

# Installation   
*  __Conda__
```
conda install bioconda::fastqc
```
# __Téléchargement__   
__Lien__ : [FASTQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.12.1.zip)


#  [__Correction des reads__](correction) :  
Trimmomatic est un outil bioinformatique largement utilisé pour le prétraitement des données de séquençage nouvelle génération (NGS) Illumina. Il élimine les bases de faible qualité, les adaptateurs de séquençage et les régions indésirables des fichiers FASTQ.   

Trimmomatic prend en charge les données de séquençage à double extrémité et à extrémité unique, ce qui le rend adapté à un large éventail de projets de recherche.  Ces fonctionnalités contribuent à garantir des séquences de lecture plus nettes et de meilleurs résultats analytiques.            

# Installation    
L'option la plus simple consiste à télécharger le fichier ZIP contenant les données binaires et à l'extraire dans un emplacement approprié. Vous devrez modifier les exemples de lignes de commande ci-dessous pour qu'ils fassent référence au fichier JAR de Trimmomatic et à l'emplacement des fichiers FASTA de l'adaptateur.  

  # Téléchargement
 [Trimmomatic v.O.39. zip](https://github.com/usadellab/Trimmomatic/releases)   

# Execution   

```
java -jar trimmomatic-0.39.jar PE \
input_forward.fq.gz input_reverse.fq.gz \
output_forward_paired.fq.gz output_forward_unpaired.fq.gz \
output_reverse_paired.fq.gz output_reverse_unpaired.fq.gz \
ILLUMINACLIP:TruSeq3-PE.fa:2:30:10:2:True LEADING:3 TRAILING:3 MINLEN:36
```

 *   [**Citations :**](citation)  
Bolger, AM, Lohse, M., & Usadel, B. (2014). Trimmomatic : un outil de nettoyage flexible pour les données de séquences Illumina. Bioinformatics , btu170. 

#   [__Assemblage__](assemblage)
   
🧬SPAdes : est une boîte à outils bioinformatique polyvalente dédiée à l’assemblage et à l’analyse des données de séquençage.
Initialement développé pour les données Illumina, SPAdes prend également en charge les données Ion Torrent ainsi que les approches hybrides intégrant des lectures longues issues de PacBio ou Oxford Nanopore Technologies (ONT).
Le package SPAdes comprend d'autres outils pour le comptage efficace des k-mers et le filtrage des lectures basé sur les k-mers, la construction et la simplification de graphes d'assemblage, l'alignement séquence-graphe et l'amélioration du regroupement métagénomique.

- [Manuel d'utilisation complet de SPAdes](https://ablab.github.io/spades/)

- [Page de téléchargement de SPAdes](https://github.com/ablab/spades/releases/latest/)

# Démarrage rapide

Le manuel d'utilisation complet est disponible [ici](https://ablab.github.io/spades/). Les informations ci-dessous sont fournies à titre indicatif uniquement et ne constituent pas un guide d'utilisation.

- L'assembleur SPAdes prend en charge :
  - Assemblage des données de séquençage de deuxième génération (Illumina ou IonTorrent) ;
  - Lectures PacBio et Nanopore utilisées uniquement à titre de données supplémentaires.


#  [__Annotation du génome__](annotation)  
Prokka est outil rapide d'annotation de génome de bactérie,de virus et d'archée et de générer des fichiers de sortie standardisés aux formats GenBank, EMBL et GFF.   
Son dépôt github [ici](https://github.com/tseemann/prokka)   



* __Citation__   
Torsten Seemann Prokka: rapid prokaryotic genome annotation Bioinformatics 2014 Jul 15;30(14):2068-9. DOI: [https://doi.org/10.1093/bioinformatics/btu153](https://academic.oup.com/bioinformatics/article/30/14/2068/2390517)



 










    


   
     












