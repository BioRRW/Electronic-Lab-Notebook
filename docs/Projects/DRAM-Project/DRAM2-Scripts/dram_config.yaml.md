dram_data_folder: /home/Database/DRAM/sep_12_22_dram1.4.0_full_db/
db_kits:
    kegg:
      mmsdb:
        location: "kegg.20221012.mmsdb"
      description_db:
        location: /home/projects-wrighton-2/DRAM/development_flynn/dram2_dev/jan_26_23_main_pipeline/split_sql_dbs/kegg.sqlite
    methyl:
      mmsdb:
        location: /home/Database/DRAM/methyl/methylotrophy.mmsdb
      genome_summary_form:
        location: /home/Database/DRAM/methyl/methylotrophy_distillate.tsv
    sulfur:
      hmmdb:
        location: sulfur.hmm
    kofam:
       hmmdb:
         location: kofam_profiles.hmm
       kofam_ko_list:
         location: kofam_ko_list.tsv
    uniref:
      mmsdb:
        location: uniref90.20220928.mmsdb 
      description_db:
        location: /home/projects-wrighton-2/DRAM/development_flynn/dram2_dev/jan_26_23_main_pipeline/dram_db/uniref.sqlite
    pfam:
      mmsdb:
        location: pfam.mmspro
      description_db:
        location: /home/projects-wrighton-2/DRAM/development_flynn/dram2_dev/jan_26_23_main_pipeline/dram_db/pfam.sqlite
    viral:
      mmsdb:
        location: refseq_viral.20220927.mmsdb
      description_db:
        location: /home/projects-wrighton-2/DRAM/development_flynn/dram2_dev/jan_26_23_main_pipeline/dram_db/viral.sqlite
    vogdb:
      hmmdb:
        location: vog_latest_hmms.txt
      description_db:
        location: "06/16/2022, 12:00:51"
    merops:
      mmsdb:
        location: peptidases.20220928.mmsdb
      description_db:
        location: /home/projects-wrighton-2/DRAM/development_flynn/dram2_dev/jan_26_23_main_pipeline/dram_db/peptidase.sqlite
    fegenie:
      cutoffs:
        location: fegenie_iron_cut_offs.txt
      hmmdb:
        location: fegenie_iron_oxidation_reduction.hmm
    camper:
      camper_distillate:
        location: /home/Database/DRAM/apr_10_22_dram2.0.0b2_part_up/CAMPER_distillate.tsv
      genome_summary_form:
        location: /home/Database/DRAM/apr_10_22_dram2.0.0b2_part_up/CAMPER_distillate.tsv
      camper_fa_db:
        location: /home/Database/DRAM/apr_10_22_dram2.0.0b2_part_up/CAMPER_blast.mmsdb
      camper_fa_db_cutoffs:
        location: /home/Database/DRAM/apr_10_22_dram2.0.0b2_part_up/CAMPER_blast_scores.tsv
      camper_hmm:
        location: /home/Database/DRAM/apr_10_22_dram2.0.0b2_part_up/CAMPER.hmm
      camper_hmm_cutoffs:
        location: /home/Database/DRAM/apr_10_22_dram2.0.0b2_part_up/CAMPER_hmm_scores.tsv
    cant_hyd:
      cant_hyd_hmmdb:
        location: /home/Database/DRAM/apr_10_22_dram2.0.0b2_part_up/CANT_HYD.hmm
      cant_hyd_hmmdb_cutoffs:
        location: /home/Database/DRAM/apr_10_22_dram2.0.0b2_part_up/CANT_HYD_HMM_scores.tsv
      genome_summary_form:
        location: /home/Database/DRAM/apr_10_22_dram2.0.0b2_part_up/engineeredsys_dram_module.tsv
      mmsdb:
        location: /home/Database/DRAM/apr_10_22_dram2.0.0b2_part_up/CANT_HYD.msdb
      mmsdb_cutoffs:
        location: /home/Database/DRAM/apr_10_22_dram2.0.0b2_part_up/CANT_HYD_BLAST_scores.tsv
    dbcan:
      description_db:
        location: /home/projects-wrighton-2/DRAM/development_flynn/dram2_dev/jan_26_23_main_pipeline/dram_db/dbcan.sqlite
      hmmdb:
        location: dbCAN-HMMdb-V11.txt
dram_sheets:
    genome_summary_form:
      location: null
    module_step_form:
      location: null
    etc_module_database:
      location: null
    function_heatmap_form:
      location: null
dram_version: "2.0.rc-1"
log_file_path: "db_builder.log"

