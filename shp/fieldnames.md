# field names

To reduce size of attributes, several fields were dropped from the original file. Dropped fields are either duplicates or contain unnecessary information. Dropped fields are delineated with a ~~strikethrough~~.

- OBJECTID
- ~~Shape~~
- ~~HUC_8~~
- ~~HUC_10~~
- HUC_12
- ~~ACRES~~
- ~~NCONTRB_A~~
- ~~HU_10_GNIS~~
- ~~HU_12_GNIS~~
- ~~HU_10_DS~~
- ~~HU_10_NAME~~
- ~~HU_10_MOD~~
- ~~HU_10_TYPE~~
- ~~HU_12_DS~~
- HU_12_NAME
- ~~HU_12_MOD~~
- ~~HU_12_TYPE~~
- ~~META_ID~~
- STATES
- ~~native_qc_richness~~
- ~~native_qc_historic_richness~~
- nonnative_qc_richness
- ~~all_qc_richness~~
- sens_nat_qc_rich
- sens_nat_assem
- ~~sens_nat_qc_assem~~
- ~~avg_qc_sensitivity_score~~
- ~~avg_qc_sensitivity_under3~~
- ~~avg_qc_sensitivity_under2~~
- ~~avg_qc_sensitivity_under1~~
- current_richness_Native_Fish
- current_assemblage_Native_Fish
- historic_richness_Native_Fish
- historic_assemblage_Native_Fish
- ~~losses_Native_Fish~~
- ~~losses_Native_Fish_list~~
- ~~gains_Native_Fish~~
- ~~gains_Native_Fish_list~~
- ~~richness_difference_Native_Fish~~
- current_richness_Fish
- current_assemblage_Fish
- ~~historic_richness_Fish~~
- ~~historic_assemblage_Fish~~
- losses_Fish
- losses_Fish_list
- gains_Fish
- gains_Fish_list
- richness_difference_Fish
- div_native_qc
- ~~assemblage_native_qc~~
- div_all_qc
- ~~assemblage_all_qc~~
- downstream_assemblage
- downstream_count
- ~~Shape_Length~~
- ~~Shape_Area~~

### Key

- assem = assemblage which is a list of species
- count = number of species
- n = native species
- h = historic (only native species)
- nn = nonnative species
- a = all species (nonnative plus native)
- s = sensitive species
- ds = downstream
- loss = species that are extirpated in HUC_12
- gain = species that are introduced to a HUC_12



## Truncated fieldnames
Fieldnames were renamed since converting the files from a geodatabase to a shapefiles resulting in a truncation of field names (max 10 chararcters).


| Original                        | New        |
|---------------------------------|------------|
| OBJECTID                        | OBJECTID   |
| HUC_12                          | HUC_12     |
| HU_12_NAME                      | HU_12_NAME |
| STATES                          | STATES     |
| nonnative_qc_richness           | nn_count   |
| sens_nat_qc_rich                | s_count    |
| sens_nat_assem                  | s_assem    |
| current_richness_Native_Fish    | n_count    |
| current_assemblage_Native_Fish  | n_assem    |
| historic_richness_Native_Fish   | h_count    |
| historic_assemblage_Native_Fish | h_assem    |
| current_richness_Fish           | a_count    |
| current_assemblage_Fish         | a_assem    |
| losses_Fish                     | loss_count |
| losses_Fish_list                | loss_assem |
| gains_Fish                      | gain_count |
| gains_Fish_list                 | gain_assem |
| richness_difference_Fish        | rich_diff  |
| div_native_qc                   | n_jacr     |
| div_all_qc                      | a_jacr     |
| downstream_assemblage           | ds_assem   |
| downstream_count                | ds_count   |



## Projection
Desired projection is EPSG: 4326.



## Code snippets

### GDB to shp
```
arcpy.FeatureClassToFeatureClass_conversion(in_features="C:/Users/Andy/Desktop/mapservices/pisces_diversity.gdb/diversities_latest", out_path="C:/Users/Andy/Documents/ca-fish-diversity/shp", out_name="diversity_11162015.shp", where_clause="", field_mapping="""HUC_12 "HUC_12" true true false 12 Text 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,HUC_12,-1,-1;HU_12_NAME "HU_12_NAME" true true false 80 Text 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,HU_12_NAME,-1,-1;STATES "STATES" true true false 20 Text 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,STATES,-1,-1;nn_count "nn_count" true true false 4 Long 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,nonnative_qc_richness,-1,-1;s_count "s_count" true true false 4 Long 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,sens_nat_qc_rich,-1,-1;s_assem "s_assem" true true false 10000 Text 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,sens_nat_assem,-1,-1;n_count "n_count" true true false 4 Long 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,current_richness_Native_Fish,-1,-1;n_assem "n_assem" true true false 10000 Text 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,current_assemblage_Native_Fish,-1,-1;h_count "h_count" true true false 4 Long 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,historic_richness_Native_Fish,-1,-1;h_assem "h_assem" true true false 10000 Text 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,historic_assemblage_Native_Fish,-1,-1;a_count "a_count" true true false 4 Long 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,current_richness_Fish,-1,-1;a_assem "a_assem" true true false 10000 Text 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,current_assemblage_Fish,-1,-1;loss_count "loss_count" true true false 4 Long 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,losses_Fish,-1,-1;loss_assem "loss_assem" true true false 10000 Text 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,losses_Fish_list,-1,-1;gain_count "gain_count" true true false 4 Long 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,gains_Fish,-1,-1;gain_assem "gain_assem" true true false 10000 Text 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,gains_Fish_list,-1,-1;rich_diff "rich_diff" true true false 4 Long 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,richness_difference_Fish,-1,-1;n_jacr "n_jacr" true true false 8 Double 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,div_native_qc,-1,-1;a_jacr "a_jacr" true true false 8 Double 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,div_all_qc,-1,-1;ds_assem "ds_assem" true true false 10000 Text 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,downstream_assemblage,-1,-1;ds_count "ds_count" true true false 8 Double 0 0 ,First,#,C:\Users\Andy\Desktop\mapservices\pisces_diversity.gdb\diversities_latest,downstream_count,-1,-1""", config_keyword="")

```
