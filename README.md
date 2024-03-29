# kaiju2-data-parser  - Metagenomic classification of reads/MAGs/Scaffolds

- Authors: PhD, Leandro de Mattos Pereira, Supervisor: PhD, Gisele Nunes, Vale Institute of Technology (ITV), Brazil, Belem - Pará.

- Put all your scaffolds.fasta metagenomes (from MetaSpades) in the directory (All-assemblies), same location of the script: run_kaiju2-phyloseq.py 
- Example: All_assembly/run_kaiju2-phyloseq.py
- run_kaiju2-phyloseq.py takes all fasta scaffolds (Ex: All-assemblies) generates from Spades and performed all steps of kaiju classification (https://github.com/bioinformatics-centre/kaiju)
- kaiju-run-parser output: 

  kaiju files summary, OTU and Taxonomy tables format to be imported into R (Ex: Phyloseq) or Python.
 
- The run_kaiju2-phyloseq.py use kaiju-multi, kaiju2table and kaiju-addTaxonNames which is need to be in your PATH: these programs are part of the kaiju.

 *Before to follow to perform run_kaiju2-phyloseq.py.
 
- Metaspades installation
- Run metaspades to get the Scaffolds.fasta for each sample.
- mkdir All-assemblies
- Save all scaffolds in the dir: All-assemblies
- Run the CDS (*.fna) prediction with gene prediction program such as Prodigal: (https://github.com/hyattpd/prodigal/wiki/gene-prediction-modes).
- kaiju installation
- kaiju databased files download (including: names.dmp and nodes.dmp from taxonomy database of NCBI and kaiju.fmi)
- kaiju.fmi: its is the indexed files of ncbi in kaiju format.
- Theses cited database files can be obtained with kaiju: kaiju-makedb -s nr_euk (more info here: https://github.com/bioinformatics-centre/kaiju).
- python3 -m venv kaiju2-parser
- source kaiju2-parser/bin/activate
- cd All-assemblies
- Download requeriments.txt to dir: All-assemblies
- pip3 install -r /path/to/All-assemblies/requirements.txt
- python3 run_kaiju2-phyloseq.py -h 
- Example for run the script: python run_kaiju2-phyloseq.py  -t 24 -m /bio_temp/share_bio/softwares/kaiju/kaiju-db-nr/nodes.dmp -n /bio_temp/share_bio/softwares/kaiju/kaiju-db-nr/names.dmp -f /bio_temp/share_bio/softwares/kaiju/kaiju-db-nr_euk/nr_euk/kaiju_db_nr_euk.fmi -i /bio_temp/c0232/all_fastq/BIN_REASSEMBLY_Metawrap/reassembled_bins/ -o result.otu.table

- Required arguments to run_kaiju2-phyloseq.py:

- -t (number of cpus), -m (nodes.dmp from kaiju nr_euk database), -n (names.dmp from kaiju nr_euk database), -f (kaiju_db_nr_euk.fmi from kaiju index generated from nr_euk database), -i ./ (dir with .fna files), -o (name of OTU table).

- OBS: The script have as -i argument all the .fna files. The .fna files are the CDS (coding DNA sequence) files obtained from each scaffold.fasta using a program of gene prediction such as Prodigal.
- make sure kaiju's scripts from kaiju dir bin is in the path of run_kaiju2-phyloseq.py
       



