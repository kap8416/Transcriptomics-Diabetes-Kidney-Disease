# Transcriptomics-Diabetes-Kidney-Disease

# Bioinformatics pipeline that uses transcriptomic data to identify predictive hub genes involved in Diabetic Kidney Disease DKD complications by COVID-19 infection
#Microarray expression dataset (GSE30529) was obtained from the NCBI GEO database (https://www.ncbi.nlm.nih.gov/geo/). This  dataset is based on the GPL571 platform and comprises human samples from patients with DKD (n = 10) and healthy (non-diabetic) controls (n = 12).

#Differential gene expression analysis
Raw data was processed with affy package available in Bioconductor using the function robust multi-array average (RMA) for converts an AffyBatch object into an ExpressionSet object. Data normalization was performed after that removing the “batch effect” using  ComBat from the sva and Weighted Gene Co-Expression Network Analysis (WGCNA) for identify outliers from our dataset and remove it. Also, the collapseRows function available in the WGCNA package for collapsing gene expression of several probes in a single measurement per gene. Finally, differential analyses were analyzed by the limma package. Log2- fold change > 1 and FDR < 0.05 were considered as differentially expressed genes (DEGs). Genes having significant p-values with positive log2– fold change represent an increased expression (UP), those with negative log2-fold change values are considered as downregulated (DN), while those with p-values above 0.05 do not have changes between stages (NC)
 
#Functional enrichment analysis for common pathogenetic DEGs 
The functional enrichment was assesed using the Gene Set Enrichment Analysis (GSEA) of DEGs.. Enrichment includes all the Gene Ontology (GO) terms , as well as the Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway.. The cluster profiler R package (Yu, et al 2012) was employed for data analysis and visualization.
Further, we considered to focus on those genes that are in hsa05171 common pathogenetic processes. This functional enrichment analysis was performed using Metascape (http://metascape.org/) for the biological proccess category including KEGG and Reactome pathways.

#PPI network and   identification of hub genes
The list of DE-human genes previously identified in the common pathogenetic process were analyzed to deep insight into their interactomic roles.
Network analysis and visualization were performed using Cytoscape version 3.9.0 software. STRINGDB plataform was used to obtain physical and functional experimental validated data. For this study, high confidence scores (0.7) and no adittional interactors were filtered, keeping only experimental, co-expression and, database characterized interactions.Each node in the protein protein interaction (PPI) network represents a protein whereas edges are interactions and connections between them. Finally, the predictive hub genes were obtained using cytoHubba selecting the top five nodes employing the topological algorithm of Maximal Clique Centrality (MCC).  

#In silico validationn of predictive hub genes in COVID-19 dataset
Gene expression data was accessed at the Coronascape repository (Zhou et al., Nature Commun. 2019 10(1):1523.). Coronascape is a resource for the analysis of systems level datasets. The top 8 most statistically overlapped COVID reference lists datasets were analized against our gene list (26 UP-DEGs). DEGs conserved among the COVID databases were identified and visualized in Circle Plot (https://genome.cshlp.org/content/early/2009/06/15/gr.092759.109.abstract) using Circos visualization tool for comparative genomics analysis.
 

