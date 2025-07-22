library(readxl)
df <- read_excel("D:/R project/Y vs A vs RSV/DEG_All_Condition_All_CellType 1.xlsx", sheet = 1)

young_vs_aged <- df %>%
  filter(Cluster %in% c("Endothelial_cells", "Macrophages", "T_cells"),
         ident.1 == "G2_old",
         ident.2 == "G1_young")


library(dplyr)

significant_deg <- young_vs_aged %>%
  filter(p_val_adj < 0.05)

top_genes_by_cluster <- significant_deg %>%
  group_by(Cluster) %>%
  top_n(10, wt = abs(avg_log2FC))

top_genes_by_cluster

if (!requireNamespace("BiocManager", quietly = TRUE))
  install.packages("BiocManager")

BiocManager::install("EnhancedVolcano")

library(EnhancedVolcano)
