
    
   <p align="center">

<img src="https://img.shields.io/badge/STAGE%20DE%20MÉMOIRE%20DE%20MASTER%201-ANALYSE%20BIOINFORMATIQUE%20DES%20DONNÉES%20DE%20SÉQUENÇAGE%20WHOLE%20GENOME%20SEQUENCING%20(WGS)-8A2BE2?style=for-the-badge&logo=github&logoColor=white" height="200"/>

</p>  


    
[**© 2026 Mamadou Demba BA** ](Demba)


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
Cette étude portant sur le microbiote des enfants atteints de malnutrition aigue sévère en République Démocratique du Congo (RDC) avait pour but d'isoler et de caractériser des clones d'*Escherichia coli* multirésistants (le whole génome sequencing, WGS) grâce au séqençage de  leur génome entier.     

Dans le contexte de la malnutrition aiguë sévère chez les enfants de moins de cinq ans, Organisation mondiale de la Santé recommande l'administration systématique d'antibiotiques, en raison du risque élevé d'infections bactériennes et de la forte mortalité associée à cette pathologie.

Toutefois, l'utilisation répétée ou inappropriée des antibiotiques favorise une pression de sélection qui peut conduire à l'émergence et à la dissémination de bactéries multirésistantes.  

Par ailleurs, de nombreuses études menées à travers le monde ont montré que les souches d'E. coli productrices de β-lactamases à spectre étendu (BLSE), en particulier celles porteuses du gène blaCTX-M-15 figurent parmi les entérobactéries multirésistantes les plus fréquemment isolées en milieu communautaire et hospitalier.

Ainsi, les enfants atteints de malnutrition aiguë sévère pourraient constituer un réservoir de clones multirésistants d'E. coli, susceptibles de favoriser la propagation de la résistance aux antibiotiques. Ces observations soulignent l'importance d'une surveillance génomique continue de ces souches et du développement de stratégies thérapeutiques plus efficaces et adaptées à cette population particulièrement vulnérable.

Cela suppose que les enfants atteints de malnutrition aiguë sévère pourraient être un réservoir de clones multirésistants d’E. coli d’où la nécessité d’une surveillance accrue et de développement d’options thérapeutiques plus efficaces pour ces enfants, qui sont les plus vulnérables.  

#### [📌Objecif : ](objectif)   
Ainsi l'objectif de cette étude est d'd’investiguer le portage fécal de clones d’Escherichia coli porteurs de gène de β-lactamases à spectre étendu (BLSE) chez des enfants atteints de malnutrition aiguë sévère.

 #### [📍Echantillons  ](echanti)
 Nos échantillons ont été selectionnées sur la base d'un précédent shotgun qui a montré une fréquence élevée en *Escherichia coli*

 Sur cette repository, nous avons chargé l'ensemble des fichiers et scripts nécessaires pour analyser ces données.  
 Les reads sont téléchargeables sur zenodo en cliquant [**ici**]()
## [__TABLE DES MATIERES__](Table)   
*  [__Contrôle qualité__](contrôle)
   * fastqc  
*  [__Correction des reads__](correction)
   * fastp v.1.3.3
*  [__Assemblage__](assemblage)
   * spades
* [__Contrôle qualité assemblage et complétude__](cc)
   * Quast
   * Busco
*  [__Annotation du génome__](annotation)
   * prokka
*  [__Recherche de gène(s) et/ou de plasmide(s) de virulence__](virulence)
   * Abricate
   * VFDB
   * Plasmidfinder
*  [__Taxonomie__](taxonomie)
   * Kraken2
*  [__pangenome__](pan)
   * roary
*  [__Average Nucleotidique identity et Hybridation ADN-ADN___](average)
   * EzBioCloud (ANI)
   * TYGS : Hybridation ADN-ADN (dDDH)
*  [__Typage des souches d'*Escherichia*__](typage)
   * mlst
*  [__Phylogroupes des souches d'*Escherichia*__](phylogroupes)
   *  ClermonTyping
*  [__Construire d'arbre phylogénétique__](tree)
   * MEGA v.11
 

  # Workflow  


  <p align="center">
<img width="1672" height="941" alt="Image" src="https://github.com/user-attachments/assets/dbbe6036-02ec-46c8-873b-cb50e852d138" />

</p>  

  
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

# [Installation](installation)    
*  __Conda__
```
conda install bioconda::fastqc
```
# [__Téléchargement__ ](téléchargement)  
__Lien__ : [**FASTQC**](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.12.1.zip)


#  [__Correction des reads__](correction) :  
Un outil conçu pour fournir un prétraitement et un contrôle qualité ultrarapides et tout-en-un pour les données FastQ.  
  
Cet outil est conçu pour le traitement de lectures courtes (par exemple Illumina NovaSeq, MGI). Si vous recherchez des outils pour traiter des lectures longues (par exemple Nanopore, PacBio, Cyclone)      

# [Installation](Installation )   

 ```
conda install -c bioconda fastp
```

# [Execution](Execution)  

```
fastp -i in.R1.fq.gz -I in.R2.fq.gz -o out.R1.fq.gz -O out.R2.fq.gz
```

Par défaut, le rapport HTML est enregistré dans fastp.html(peut être spécifié avec -hl'option), et le rapport JSON est enregistré dans fastp.json(peut être spécifié avec -jl'option).  

 *   [**Citations :**](citation)
 
Chen, S., Zhou, Y., Chen, Y., & Gu, J. (2018). fastp: an ultra-fast all-in-one FASTQ preprocessor. Bioinformatics, 34(17), i884–i890. https://doi.org/10.1093/bioinformatics/bty560. 

#   [__Assemblage__](assemblage)
   
🧬SPAdes est une boîte à outils bioinformatique polyvalente dédiée à l’assemblage et à l’analyse des données de séquençage.  

Initialement développé pour les données Illumina, SPAdes prend également en charge les données Ion Torrent ainsi que les approches hybrides intégrant des lectures longues issues de PacBio ou Oxford Nanopore Technologies (ONT).  

Le package SPAdes comprend d'autres outils pour le comptage efficace des k-mers et le filtrage des lectures basé sur les k-mers, la construction et la simplification de graphes d'assemblage, l'alignement séquence-graphe et l'amélioration du regroupement métagénomique.

- [Manuel d'utilisation complet de SPAdes](https://ablab.github.io/spades/)

- [Page de téléchargement de SPAdes](https://github.com/ablab/spades/releases/latest/)

# [Démarrage rapide](démarrage)

Le manuel d'utilisation complet est disponible [ici](https://ablab.github.io/spades/). Les informations ci-dessous sont fournies à titre indicatif uniquement et ne constituent pas un guide d'utilisation.

- L'assembleur SPAdes prend en charge :
  - Assemblage des données de séquençage de deuxième génération (Illumina ou IonTorrent) ;
  - Lectures PacBio et Nanopore utilisées uniquement à titre de données supplémentaires.


# [__Contrôle qualité assemblage et complétude__](cc)  
  * [__Quast__](quast)
  
QUAST (Quality ASsessment Tool) est un outil d'évaluation de la qualité d'assemblage.   
QUAST évalue les assemblages en calculant diverses métriques, notamment le nombre de contigs, les rapports N50/75 et L50/75, la teneur en GC, le nombre de bases non appelées (N<sub>N</sub>) et les gènes prédits. Il prend en entrée un ou plusieurs objets Assembly et génère ensuite un rapport contenant les statistiques de tous les assemblages fournis.

Le logiciel QUAST fonctionne avec ou sans génomes de référence. Cependant, il est beaucoup plus informatif si un génome de référence proche est fourni avec les assemblages. L'outil accepte plusieurs assemblages et se prête donc à la comparaison.   

# [Installation](installation)  

```
conda install bioconda::quast
```
# [Execution](execute)   

```
./quast.py test_data/contigs_1.fasta \
           test_data/contigs_2.fasta \
        -r test_data/reference.fasta.gz \
        -g test_data/genes.txt \
        -1 test_data/reads1.fastq.gz -2 test_data/reads2.fastq.gz \
        -o quast_test_output
```

  * [**Busco**](busco)
  
BUSCO (Benchmarking Universal Single-Copy Orthologs) fournit des mesures pour l'évaluation quantitative de l'assemblage du génome, de l'ensemble des gènes et de l'exhaustivité du transcriptome, basées sur des attentes évolutives concernant le contenu génique d'orthologues quasi universels à copie unique.
# [Installation](installation)  

```
conda install bioconda::busco
```
# Execution   

```
# Lancer l'analyse busco
busco -i S1_assembled/scaffolds.fasta -o busco -l bacteria_odb10 -m genome
```



#  [__Annotation du génome__](annotation)  
Prokka est outil rapide d'annotation de génome de bactérie, de virus et d'archée et génére des fichiers de sortie standardisés aux formats GenBank, EMBL et GFF. Son dépôt github [ici](https://github.com/tseemann/prokka)   


  # [Installation](installation)      

  ```
conda create -n prokka bioconda::prokka
conda activate prokka
prokka --version
```

# [Commande ](commande)      

```
prokka --outdir mydir --prefix mygenome contigs.fa --locustag
```

```
General:
  --help            This help
  --version         Print version and exit
  --citation        Print citation for referencing Prokka
  --quiet           No screen output (default OFF)
  --debug           Debug mode: keep all temporary files (default OFF)
Setup:
  --listdb          List all configured databases
  --setupdb         Index all installed databases
  --cleandb         Remove all database indices
  --depends         List all software dependencies
Outputs:
  --outdir [X]      Output folder [auto] (default '')
  --force           Force overwriting existing output folder (default OFF)
  --prefix [X]      Filename output prefix [auto] (default '')
  --addgenes        Add 'gene' features for each 'CDS' feature (default OFF)
  --locustag [X]    Locus tag prefix (default 'PROKKA')
  --increment [N]   Locus tag counter increment (default '1')
  --gffver [N]      GFF version (default '3')
  --compliant       Force Genbank/ENA/DDJB compliance: --genes --mincontiglen 200 --centre XXX (default OFF)
  --centre [X]      Sequencing centre ID. (default '')
Organism details:
  --genus [X]       Genus name (default 'Genus')
  --species [X]     Species name (default 'species')
  --strain [X]      Strain name (default 'strain')
  --plasmid [X]     Plasmid name or identifier (default '')
Annotations:
  --kingdom [X]     Annotation mode: Archaea|Bacteria|Mitochondria|Viruses (default 'Bacteria')
  --gcode [N]       Genetic code / Translation table (set if --kingdom is set) (default '0')
  --prodigaltf [X]  Prodigal training file (default '')
  --gram [X]        Gram: -/neg +/pos (default '')
  --usegenus        Use genus-specific BLAST databases (needs --genus) (default OFF)
  --proteins [X]    Fasta file of trusted proteins to first annotate from (default '')
  --hmms [X]        Trusted HMM to first annotate from (default '')
  --metagenome      Improve gene predictions for highly fragmented genomes (default OFF)
  --rawproduct      Do not clean up /product annotation (default OFF)
Computation:
  --fast            Fast mode - skip CDS /product searching (default OFF)
  --cpus [N]        Number of CPUs to use [0=all] (default '8')
  --mincontiglen [N] Minimum contig size [NCBI needs 200] (default '1')
  --evalue [n.n]    Similarity e-value cut-off (default '1e-06')
  --rfam            Enable searching for ncRNAs with Infernal+Rfam (SLOW!) (default '0')
  --norrna          Don't run rRNA search (default OFF)
  --notrna          Don't run tRNA search (default OFF)
  --rnammer         Prefer RNAmmer over Barrnap for rRNA prediction (default OFF)
```


 *   [__Citation__](citation)   

    
Torsten Seemann Prokka: rapid prokaryotic genome annotation Bioinformatics 2014 Jul 15;30(14):2068-9. DOI: [https://doi.org/10.1093/bioinformatics/btu153](https://academic.oup.com/bioinformatics/article/30/14/2068/2390517)



#  [__Recherche de gène(s) et/ou de plasmide(s) de virulence__](virulence)  
ABRIcate est outil permettant un dépistage massif de contigs pour la recherche de gènes de résistance aux antimicrobiens ou de virulence uniquement.   

Ce logiciel interroge de nommbreuses bases de données notamment NCBI, CARD, ARG-ANNOT, Resfinder, EcOH, PlasmidFinder, Ecoli_VF et VFDB.  
Il prend comme fichier d'éntré les contigs et utilise une base de données de séquences d'ADN.  

Ce logiciel ne détecte pas la résistance mutationnelle, seulement les gènes acquis.

# [Installation](Installation)    

```
# Installation d'abricate
conda install -c bioconda -c conda-forge abricate

# Mise à jour des bases de données d'abricate
abricate --setupdb

# Affiche les bases de données d'abricate
abricate --list
```

# [__Commande__](commande)  
```
# Lance abricate avec la base de données par défaut (ncbi)
abricate S1_assembled/scaffolds.fasta > abricate.csv

# Lance abricate avec la base de données resfinder
abricate --db resfinder S1_assembled/scaffolds.fasta > abricate.csv

# Lancer abricate sur plusieurs fichiers fasta
abricate --db resfinder *.fasta > resfinder.csv

# Recherche la présence de plasmides
abricate --db plasmidfinder S1_assembled/scaffolds.fasta

# Lance abricate avec la base vfdb (virulence factors database)
abricate --db vfdb S1_assembled/scaffolds.fasta > abricate_virulence.csv
```

#  [__Pangenome__](pan)      
Roary est un pipeline de séquençage pangénomique autonome et ultrarapide. Il prend en entrée des assemblages annotés au format GFF3 (produits par Prokka (Seemann, 2014) et calcule le pangénome. Sur un PC de bureau standard, il peut analyser des jeux de données contenant des milliers d'échantillons, une tâche impossible à réaliser avec les méthodes existantes, sans compromettre la qualité des résultats.      

Tous les fichiers GFF3 créés par Prokka sont compatibles avec Roary et cette méthode est recommandée pour générer les fichiers d'entrée. Chaque fichier d'entrée doit comporter une étiquette de locus unique pour les identifiants de gènes (--locustag) afin de faciliter l'identification de leur origine (Andrew et al., 2015).  

# [Installation](installation)  

```
conda install bioconda::roary
```

# [Execution](execution)  

```
roary -e --mafft -p 8 –f output_dir *.gff
```

  ```
Usage:   roary [options] *.gff

Options: -p INT    number of threads [1]
         -o STR    clusters output filename [clustered_proteins]
         -f STR    output directory [.]
         -e        create a multiFASTA alignment of core genes using PRANK
         -n        fast core gene alignment with MAFFT, use with -e
         -i        minimum percentage identity for blastp [95]
         -cd FLOAT percentage of isolates a gene must be in to be core [99]
         -qc       generate QC report with Kraken
         -k STR    path to Kraken database for QC, use with -qc
         -a        check dependancies and print versions
         -b STR    blastp executable [blastp]
         -c STR    mcl executable [mcl]
         -d STR    mcxdeblast executable [mcxdeblast]
         -g INT    maximum number of clusters [50000]
         -m STR    makeblastdb executable [makeblastdb]
         -r        create R plots, requires R and ggplot2
         -s        dont split paralogs
         -t INT    translation table [11]
         -ap       allow paralogs in core alignment
         -z        dont delete intermediate files
         -v        verbose output to STDOUT
         -w        print version and exit
         -y        add gene inference information to spreadsheet, doesnt work with -e
         -iv STR   Change the MCL inflation value [1.5]
         -h        this help message
````

*   [**Citations :**](citation)


Andrew J. Page, Carla A. Cummins, Martin Hunt, Vanessa K. Wong, Sandra Reuter, Matthew TG Holden, Maria Fookes, Daniel Falush, Jacqueline A. Keane, Julian Parkhill, « Roary : analyse rapide à grande échelle du pan-génome des procaryotes », Bioinformatics, 2015 ; 31(22) : 3691-3693 [doi : 10.1093/bioinformatics/btv421](https://academic.oup.com/bioinformatics/article/31/22/3691/240757)


#  [__Average Nucleotidique identity__](average)   
L'ANI est largement utilisée pour comparer deux séquences de génomes procaryotes lors de la classification et de l'identification de bactéries, en calculant la valeur ANI de ces deux séquences. Notre calculateur d'ANI utilise l'algorithme OrthoANIu, une version améliorée de l'algorithme OrthoANI original, qui utilise USEARCH au lieu de BLAST (Lee et al., 2015). Pour les grands ensembles de données, veuillez consulter l'outil OrthoANIu autonome disponible [__ici__](https://www.ezbiocloud.net/)  



#  [__TYGS : Hybridation ADN-ADN (dDDH)__](dDDH)  

TYGS, le serveur de génomes de type (souche), est un serveur Web à haut débit convivial pour la taxonomie des procaryotes basée sur le génome, connecté à une base de données importante et en constante expansion d'informations génomiques, taxonomiques et nomenclaturales.    

Il vous permet d'identifier ou de classer les souches procaryotes et fournit des phylogénies basées sur le génome avec support de branche, délimitation des (sous-)espèces via DDH numérique, différences dans le contenu génomique G+C et bien plus encore.   

Consultable sur [**TYGS**](https://tygs.dsmz.de/user_requests/new)



*   [**Citations :**](citation)

Yoon, S. H., Ha, S. M., Lim, J. M., Kwon, S.J. & Chun, J. (2017). A large-scale evaluation of algorithms to calculate average nucleotide identity. Antonie van Leeuwenhoek. 110:1281–1286.  

Meier-Kolthoff JP & Göker M. (2019).TYGS is an automated high-throughput platform for state-of-the-art genome-based taxonomy.Nature Communications, 10, 2182.DOI : 10.1038/s41467-019-10210-3



# [__Phylogroupes des souches d'*Escherichia*__](phylogroupes)  
Clermont phylotyping est une méthode méthode de phylogroupage permettant de classer les souches d'Escherichia coli dans de grands groupes phylogénétiques (phylogroupes) en fonction de la présence ou de l'absence de certains marqueurs génétiques.  

Cette méthode renseigne sur les relations évolutives entre les souches et donne souvent des indices sur leur écologie ou leur potentiel de virulence.  

Consultable [__ici__](https://ezclermont.hutton.ac.uk/)  


*   [**Citations :**](citation)

Clermont O, Bonacorsi S, Bingen E. Rapid and simple determination of the Escherichia coli phylogenetic group. Applied and Environmental Microbiology. 2000;66(10):4555–4558.

#  [__Typage des souches d'*Escherichia*__](typage)  
Le typage par séquençage MLST (MultiLocus Sequencing Typing) est la technique de référence pour discriminer différentes souches. Cette méthode est basée sur le séquençage de « gènes de ménage » (house-keeping genes) codant pour des protéines essentielles de la bactérie.  



  # [Installation](installation)    

  ```
conda install bioconda::mlst
```

# [Execution](execution)    


```
# Lancer l'analyse de la mlst
mlst contigs.fasta > mlst.csv

# Lancer l'analyse MLST sur plusieurs fichiers fasta
mlst *.fasta > mlst.csv
```

*   [**Citations :**](citation)

Sadio O. Formation CDC Africa- Pasteur, 2025. [github Ousmane Sadio](https://github.com/Osadio95/AfricaCDC_Dakar2025)   




#  [__Construire d'arbre phylogénétique__](tree)  


<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/en/a/a0/MEGA7_logo.png" 
       alt="MEGA7 Logo" 
       width="500">
</p>


Logiciel d'analyse phylogénétique doté d'une interface graphique. Il permet la visualisation et la modification des données de séquences alignées et offre de nombreux outils pour l'analyse phylogénétique et statistique des alignements.  


  
    











[**© 2026 Mamadou Demba Ba — All rights reserved.**](droit)










          
━━━━━━━━━━━━━━━━━━━━━━
[**🔒 PROTECTED WORK**](protec)
━━━━━━━━━━━━━━━━━━━━━━





 










    


   
     












