# Reference protein annotation tables for CoVsurver
 
Annotation tables (protein name + start-stop position on a reference genome) used to extend CoVsurver (Episurver-style annotation) to the seasonal human coronaviruses and hMPV.
 
## Contents
 
1. [Seasonal human coronaviruses](#1-seasonal-human-coronaviruses)
   - [1.1 HCoV-229E](#11-hcov-229e)
   - [1.2 HCoV-NL63](#12-hcov-nl63)
   - [1.3 HCoV-OC43](#13-hcov-oc43)
   - [1.4 HCoV-HKU1](#14-hcov-hku1)
2. [Human metapneumovirus (hMPV)](#2-human-metapneumovirus-hmpv) (stub)
3. [References](#references)
## File format
 
One tab-separated file per virus, no header, CRLF line endings, modelled on `oro_refstrain_prot_startToStopPos.tsv`.
 
| Col | Content | Example |
|---|---|---|
| 1 | Reference strain ID | `229E_Human_2000_Wuerzburg229E` |
| 2 | Protein / product name | `NSP5` |
| 3 | `start-stop`, 1-based, inclusive, on the reference genome | `9188-10093` |
| 4 | Strand | `positive` |
 
Files in this folder:
 
| File | Virus | Reference record |
|---|---|---|
| `229E_refstrain_prot_startToStopPos.tsv` | HCoV-229E | NC_002645.1 |
| `NL63_refstrain_prot_startToStopPos.tsv` | HCoV-NL63 | NC_005831.2 |
| `OC43_refstrain_prot_startToStopPos.tsv` | HCoV-OC43 | NC_006213.1 |
| `HKU1_refstrain_prot_startToStopPos.tsv` | HCoV-HKU1 | NC_006577.2 |
| `hMPV_refstrain_prot_startToStopPos.tsv` | hMPV | NC_039199.1 |
 
Ref templates were extracted from NCBI Virus database, uploaded to [Ref template folder](./NCBI_ref_templates)
 
## 1. Seasonal human coronaviruses
 
Coordinate conventions used in every file:
 
- Open reading frames (S, E, M, N, accessory genes, hMPV genes) include the stop codon, as in the GenBank CDS feature.
- Replicase products (NSP1-NSP16) end before the stop codon of ORF1a / ORF1ab.
- Products that span the -1 ribosomal frameshift (NSP12) are listed first-nucleotide to last-nucleotide on the genome.
  The single overlapping nucleotide at the frameshift is therefore counted once, so NSP12 spans one nucleotide fewer
  than three times its length.
**Distinctive features.**
 
| | 229E | NL63 | OC43 | HKU1 |
|---|---|---|---|---|
| Reference | NC_002645.1 | NC_005831.2 | NC_006213.1 | NC_006577.2 |
| Subgenus | Duvinacovirus | Setracovirus | Embecovirus | Embecovirus |
| NSP1-16 + S, E, M, N | yes | yes | yes | yes |
| HE gene | no | no | yes | yes |
| Accessory genes in table | ORF4a, ORF4b | ORF3 | NS2, NS12.9 | ORF4 |
| Internal gene inside N | no | no | I | N2 |
| Rows in table | 22 | 21 | 24 | 23 |
| NSPs annotated in the record | legacy names | none | yes | yes |
| Main adjustment | legacy names to NSPs; NSP11 added | NSPs from UniProt; NSP11 inferred | I added; names capitalised | reference swapped; ORF4 named from gene |
 
Genome and spike lengths are taken from the reference GenBank records. Receptor assignments (229E: aminopeptidase N; NL63: ACE2; OC43 and HKU1: 9-O-acetylated sialic acid) are from the review
table cited in [12].
 
---
 
### 1.1 HCoV-229E
 
**Reference.** NC_002645.1, the Wuerzburg prototype (27,317 nt).
 
**Literature support:**
 
§ Dijkman R, Jebbink MF, Wilbrink B, et al. Human coronavirus 229E encodes a single ORF4 protein between the spike and the envelope genes.
§ 2006
§ https://doi.org/10.1186/1743-422X-3-106
 
The 229E prototype has two small genes between S and E (ORF4a, ORF4b). Clinical isolates carry one ORF4 gene instead; the split in the prototype comes from a 2-nt deletion. Either way the region encodes accessory protein(s) and is part of the feature table.
 
§ Herold J, Gorbalenya AE, Thiel V, Schelle B, Siddell SG. Proteolytic processing at the amino terminus of human coronavirus 229E gene 1-encoded polyproteins.
§ 1998
§ https://doi.org/10.1128/jvi.72.2.910-918.1998
 
First product of pp1a/pp1ab (p9 in the old GenBank naming = NSP1) is released by cleavage at Gly111|Asn112. This is the boundary between NSP1 and NSP2 in the table.
 
§ Ziebuhr J, Siddell SG. Processing of the human coronavirus 229E replicase polyproteins by the virus-encoded 3C-like proteinase.
§ 1999
§ https://doi.org/10.1128/jvi.73.1.177-185.1999
 
Main-protease cleavage sites mapped experimentally (Q2965/A2966, Q3267/S3268, Q3546/S3547, Q3629/S3630, Q3824/N3825, Q3933/A3934). These match the starts of NSP5, NSP6, NSP7, NSP8, NSP9, NSP10 in the table.
 
§ Ziebuhr J. The coronavirus replicase: insights into a sophisticated enzyme machinery.
§ 2006
§ https://pmc.ncbi.nlm.nih.gov/articles/PMC7123892/
 
Standard description of pp1a (nsp1-11) and pp1ab (nsp1-10, nsp12-16) and of the -1 ribosomal frameshift between ORF1a and ORF1b. Basis for the NSP1-NSP16 naming.
 
§ Schamoni-Kast K, Krichel B, Damjanovic T, et al. The kinetics of nsp7-11 polyprotein processing and impact on complexation with nsp16 among human coronaviruses.
§ 2025
§ https://doi.org/10.1038/s41467-025-61554-y
 
Treats nsp11 as a short peptide at the end of pp1a for 229E and the other seasonal HCoVs.
 
**Adjustments and justification:**
 
1. **Legacy replicase names converted to NSP1-NSP16.** The GenBank record uses pre-standard names (p9, p87, p195/p210, p44, ...). For a table that CoVsurver matches against SARS-CoV-2-style output, the NSP names are the common vocabulary. Boundaries were not changed; only names. Checked against the cleavage sites above and UniProt P0C6X1 (all 15 residue ranges match).
2. **NSP11 added (12497-12547).** The record annotates a 17-residue peptide at the end of ORF1a; NSP11 is reported in the SARS-CoV-2 CoVsurver output, so it is kept. Its span is 51 nt = 17 codons, ending at the ORF1a stop.
3. **NSP12 starts at the same nucleotide as NSP11 (12497).** NSP12 is the first protein of ORF1b, but in the genome the shared NSP11/NSP12 start is the same residue. NSP12 is 12497-15276, which is 1 nt shorter than 3 x length because the frameshift overlap is counted once. An earlier draft started NSP12 at 12520 (the frameshift site); that was changed.
4. **NSP11 end corrected from 12660 to 12547.** 12497-12660 is 164 nt, not a multiple of 3, and runs past the ORF1a stop.
5. **ORF4a / ORF4b kept as two rows** because this follows the reference record. A single ORF4 row may be preferable for clinical sequences (open item).
6. **ORF1a and ORF1ab rows omitted.** They are polyproteins, not mature products, and the OROV example does not list them.
7. **Stop codons.** ORFs (S, ORF4a, ORF4b, E, M, N) include the stop codon, NSPs do not, matching the OROV table convention.
---
 
### 1.2 HCoV-NL63
 
**Reference.** NC_005831.2, strain Amsterdam I (27,553 nt).
 
**Literature support:**
 
§ Pyrc K, Jebbink MF, Berkhout B, van der Hoek L. Genome structure and transcriptional regulation of human coronavirus NL63.
§ 2004
§ https://doi.org/10.1186/1743-422X-1-7
 
Describes the NL63 gene order: ORF1a, ORF1b, S, ORF3, E, M, N. ORF3 is the single accessory gene and is part of the feature table.
 
§ Review of human coronavirus spike proteins, receptors and UniProt IDs (Table 3, UniProtKB ranges).
§ 2020
§ https://pmc.ncbi.nlm.nih.gov/articles/PMC7604128/
 
Gives NL63 pp1ab chain ranges (UniProt P0C6X5): NSP1 1-110, NSP2 111-898, NSP3 899-2462, ..., NSP16 6430-6729. Used as the source of NSP boundaries because the RefSeq record has no NSP annotation. **[confirm authors and title]**
 
§ Chen Z, Wang Y, Ratia K, Mesecar AD, Wilkinson KD, Baker SC. Proteolytic processing and deubiquitinating activity of papain-like proteases of human coronavirus NL63.
§ 2007
§ https://doi.org/10.1128/JVI.02747-06
 
Two papain-like protease domains cut the N-terminal region of the replicase; consistent with NSP1, NSP2, NSP3 being separate products at the start of the table.
 
§ Ma M, Yang Y, Wu L, et al. Conserved protein targets for developing pan-coronavirus drugs based on sequence and 3D structure similarity analyses.
§ 2022
§ https://doi.org/10.1016/j.compbiomed.2022.105455
 
Table 1 gives length ranges for every NSP and structural protein across the human coronaviruses. All NL63 rows fall inside those ranges.
 
**Adjustments and justification:**
 
1. **NSP rows derived from UniProt, not from the record.** The NC_005831.2 record annotates only ORF1a and ORF1ab as polyproteins. Residue ranges from UniProt P0C6X5 were converted to genome positions with the frameshift taken into account (residues before the frameshift: 3 nt each; after: shifted by 1 nt). Check: every NSP is a whole number of codons, consecutive NSPs are contiguous, NSP1 starts at the ORF1ab start and NSP16 ends one stop codon before the ORF1ab end.
2. **NSP11 inferred (12416-12466).** UniProt does not list it as a chain. It is taken as the last 17 residues of ORF1a (same length as 229E) so that the table has the same 16 NSPs as the others. This is the one NL63 row not backed by a source. **[confirm]**
3. **NSP12 starts at the NSP11 start (12416)**, same logic as 229E.
4. **NSP14 P1 residue is His, not Gln.** The residue before NSP14 is His (the 3CL protease usually cuts after Gln). The boundary matches UniProt and is kept; it is an exception, not an error.
5. **Spike 1,356 aa is the upper limit of the Ma range**; it is the longest of the four, so no adjustment.
6. **ORF3 named as in the record.** It is the accessory gene between S and E and is kept under the record's name.
7. **No HE row**: the record has no HE gene, so none is added.
---
 
### 1.3 HCoV-OC43
 
**Reference.** NC_006213.1, strain ATCC VR-759 (30,741 nt); the record is identical to AY585228.
 
**Literature support:**
 
§ Genome organisation of HCoV-OC43 (Table 3). PMC479063.
§ 2004
§ https://pmc.ncbi.nlm.nih.gov/articles/PMC479063/
 
Gene order 5'-ORF1a-ORF1b-NS2-HE-S-NS12.9-E-M-N-3'. NS2, HE and NS12.9 are listed as genes and are part of the feature table. **[confirm title, authors, year]**
 
§ Zhang R, et al. The ns12.9 accessory protein of human coronavirus OC43 is a viroporin involved in virion morphogenesis and pathogenesis.
§ 2015
§ https://doi.org/10.1128/JVI.01986-15
 
NS12.9 is a protein encoded in the OC43 genome (gene overlapping the start of E). **[confirm author list]**
 
§ Antiviral gene expression profile during HCoV-OC43 infection.
§ 2018
§ https://doi.org/10.1007/s00705-018-3832-8
 
Uses the alternative names ns2a and ns5a for the same accessory genes. **[confirm authors]**
 
§ Study of the I (internal) accessory proteins of HCoV-HKU1 (ORF 7b) and HCoV-OC43 (ORF 8b).
§ 2025
§ PMID 41348903
 
An internal gene within N encodes the I protein in OC43. **[confirm title, journal, year]**
 
§ Everest H, et al. Known cellular and receptor interactions of animal and human coronaviruses: a review.
§ 2022
§ Viruses 14:351
 
OC43 carries an HE gene in addition to S.
 
§ Ziebuhr J (2006) and Ma M et al. (2022), as in 1.1.
 
OC43 NSP1 (246 aa) is the largest of the four and sets the upper end of the Ma range (110-246); OC43 NSP11 is 14 aa (Ma range 13-17).
 
**Adjustments and justification:**
 
1. **NSP boundaries from the record.** The OC43 record already annotates the mature NSPs, including a 14-residue NSP11. Positions were taken from the record and checked as in 1.2. UniProt (P0C6U7) agrees for NSP1-NSP10 and NSP12; NSP13-NSP16 are contiguous and in frame but were not independently matched to UniProt.
2. **NSP11 kept (13317-13358, 42 nt).** Present in the record; same start as NSP12 (13317).
3. **Accessory names written NS2 and NS12.9.** The record uses lower case (ns2, ns12.9); these were changed to match the capitalisation used in the literature. Some papers call the same genes ns2a and ns5a (see the 2018 Arch Virol entry above); the table keeps NS2 and NS12.9. **[confirm]** which naming CoVsurver prefers.
4. **NS12.9 overlaps E** (27792-28121 vs E 28108-28362). Both rows are kept; each is a separate CDS in the record. Same situation as NSP11/NSP12: overlapping rows are a normal feature of the table.
5. **I protein added (29140-29322, 60 aa)** although it is not a separate CDS in the record. It is a documented gene inside N in a different frame, so it appears as its own row, in the same way the internal gene is listed for HKU1 (N2). The span is a whole number of codons and lies inside N. **[confirm]** whether CoVsurver should list I.
6. **HE kept (22354-23628).** Present in the record; HE is absent from 229E and NL63, so it is one of the distinctive features in the summary table.
---
 
### 1.4 HCoV-HKU1
 
**Reference.** NC_006577.2 (29,926 nt), isolate HKU1, genotype A, derived from AY597011.
 
**Literature support:**
 
§ Woo PCY, Lau SKP, Chu CM, et al. Characterization and complete genome sequence of a novel coronavirus, coronavirus HKU1, from patients with pneumonia.
§ 2005
§ https://doi.org/10.1128/JVI.79.2.884-895.2005
 
First HKU1 genome. Gene order: ORF1a, ORF1b, HE, S, ORF4, E, M, N, with an additional ORF (N2/ORF8) inside N. All of these are in the feature table.
 
§ Woo PCY, Lau SKP, Huang Y, et al. Comparative analysis of 22 coronavirus HKU1 genomes reveals a novel genotype and evidence of natural recombination in coronavirus HKU1.
§ 2006
§ https://doi.org/10.1128/JVI.00509-06 **[confirm DOI]**
 
Defines genotypes A, B, C; the reference is genotype A, so coordinates are specific to this genotype.
 
§ Study of the I (internal) accessory proteins of HCoV-HKU1 (ORF 7b) and HCoV-OC43 (ORF 8b). PMID 41348903.
§ 2025
§ (see 1.3)
 
Calls the internal gene in N "ORF 7b" for HKU1; same ORF as N2/ORF8 in the genome papers. **[confirm]**
 
§ Ma M, et al. Conserved protein targets for developing pan-coronavirus drugs based on sequence and 3D structure similarity analyses.
§ 2022
§ https://doi.org/10.1016/j.compbiomed.2022.105455
 
Length ranges. HKU1 rows fall inside them except NSP3 (see adjustment 4).
 
**Adjustments and justification:**
 
1. **Reference swapped from AY884001.1 to NC_006577.2.** Raphael's list gave AY884001.1; the NCBI record is superseded by the RefSeq NC_006577.2 (genotype A, from AY597011). The RefSeq record is the one that annotates the genes used here.
2. **Accessory ORF4 named from the gene qualifier.** The record's product field for this gene reads "non-structural protein"; the gene qualifier (ORF4) was used instead so that the row has a meaningful name.
3. **N2 added as its own row (28342-28959, 205 aa).** It is a gene inside N (28320-29645), in a different frame; listed because it is annotated in the record.
4. **NSP3 length differs from Ma Table 1.** NC_006577.2 gives NSP3 = 2,029 aa (810-2838); Ma gives a maximum of 1,979 aa. This indicates a different isolate was used in Ma. The table follows the reference record.
5. **NSP14 P1 residue is His**, as in NL63. Boundary kept (contiguous with NSP13 and NSP15; in frame).
6. **NSP11 kept (13577-13618, 14 aa).** Same start as NSP12 (13577).
7. **UniProt cross-check limited to NSP1-NSP9** (P0C6X2). NSP10-NSP16 are contiguous and in frame with the record but were not matched to UniProt.
---
 
## 2. Human metapneumovirus (hMPV)
 
Stub. Reference NC_039199.1; table `hMPV_refstrain_prot_startToStopPos.tsv` (N, P, M, F, M2-1, M2-2, SH, G, L). Literature section to follow.
 
---
 
## References
 
1. Ziebuhr J. The coronavirus replicase: insights into a sophisticated enzyme machinery. *Adv Exp Med Biol.* 2006;581:3-11. doi:10.1007/978-0-387-33012-9_1. PMC7123892.
2. Snijder EJ, Decroly E, Ziebuhr J. The nonstructural proteins directing coronavirus RNA synthesis and processing. *Adv Virus Res.* 2016. PMC7112286.
3. Decroly E, Imbert I, Coutard B, et al. Coronavirus nonstructural protein 16 is a cap-0 binding enzyme possessing (nucleoside-2'O)-methyltransferase activity. *J Virol.* 2008. PMC2519555.
4. Ulferts R, Imbert I, Canard B, Ziebuhr J. Book chapter on the coronavirus replicase gene (PMC7124140, editor S. K. Lal). **[confirm title, book and year]**
5. Ma M, Yang Y, Wu L, et al. Conserved protein targets for developing pan-coronavirus drugs based on sequence and 3D structure similarity analyses. *Comput Biol Med.* 2022;145:105455. doi:10.1016/j.compbiomed.2022.105455.
6. Wilson R, Kovacs D, Crosby M, Ho A. Global epidemiology and seasonality of human seasonal coronaviruses: a systematic review. *Open Forum Infect Dis.* 2024;11(8):ofae418. doi:10.1093/ofid/ofae418.
7. Everest H, Stevenson-Leggett P, Bailey D, Bickerton E, Keep S. Known cellular and receptor interactions of animal and human coronaviruses: a review. *Viruses.* 2022;14:351.
8. A comparison of conserved features in the human coronavirus family shows that studies of viruses less pathogenic than SARS-CoV-2, such as HCoV-OC43, are good model systems. *Viruses.* 2025;17:256. **[confirm authors]**
9. Schamoni-Kast K, Krichel B, Damjanovic T, et al. The kinetics of nsp7-11 polyprotein processing and impact on complexation with nsp16 among human coronaviruses. *Nat Commun.* 2025;16:8244. doi:10.1038/s41467-025-61554-y.
10. Pyrc K, Berkhout B, van der Hoek L. The novel human coronaviruses NL63 and HKU1. *J Virol.* 2007;81(7):3051-3057. doi:10.1128/JVI.01466-06.
11. SARS-CoV nsp13 helicase paper (Fig. 1: processing products of pp1a and pp1ab). *J Virol.* 2004;78(11):5619-5632. PMC415832. **[confirm authors]**
12. Review of human coronavirus spike proteins, receptors and UniProt IDs. *Prog Biophys Mol Biol.* 2020;161:39-53. doi:10.1016/j.pbiomolbio.2020.10.006. PMC7604128 (Table 3: UniProtKB ranges). Receptor table: PMC8594256 (Table 2). **[confirm authors and titles]**
13. Dijkman R, Jebbink MF, Wilbrink B, Pyrc K, Zaaijer HL, Minor PD, Franklin S, Berkhout B, Thiel V, van der Hoek L. Human coronavirus 229E encodes a single ORF4 protein between the spike and the envelope genes. *Virol J.* 2006;3:106. doi:10.1186/1743-422X-3-106.
14. Herold J, Gorbalenya AE, Thiel V, Schelle B, Siddell SG. Proteolytic processing at the amino terminus of human coronavirus 229E gene 1-encoded polyproteins: identification of a papain-like proteinase and its substrate. *J Virol.* 1998;72(2):910-918. doi:10.1128/jvi.72.2.910-918.1998.
15. Ziebuhr J, Siddell SG. Processing of the human coronavirus 229E replicase polyproteins by the virus-encoded 3C-like proteinase: identification of proteolytic products and cleavage sites common to pp1a and pp1ab. *J Virol.* 1999;73(1):177-185. doi:10.1128/jvi.73.1.177-185.1999.
16. Pyrc K, Jebbink MF, Berkhout B, van der Hoek L. Genome structure and transcriptional regulation of human coronavirus NL63. *Virol J.* 2004;1:7. doi:10.1186/1743-422X-1-7.
17. Pyrc K, Dijkman R, Deng L, et al. Mosaic structure of human coronavirus NL63, one thousand years of evolution. *J Mol Biol.* 2006. PMID 17054987. PMC7094706. **[confirm journal details]**
18. Chen Z, Wang Y, Ratia K, Mesecar AD, Wilkinson KD, Baker SC. Proteolytic processing and deubiquitinating activity of papain-like proteases of human coronavirus NL63. *J Virol.* 2007;81(11):6007-6018. doi:10.1128/JVI.02747-06.
19. Zhang R, et al. The ns12.9 accessory protein of human coronavirus OC43 is a viroporin involved in virion morphogenesis and pathogenesis. *J Virol.* 2015;89(22):11383-11395. doi:10.1128/JVI.01986-15. **[confirm author list]**
20. Genome organisation of HCoV-OC43 (Table 3). *J Virol.* PMC479063. **[confirm title, authors, year]**
21. Antiviral gene expression profile during HCoV-OC43 infection. *Arch Virol.* 2018. doi:10.1007/s00705-018-3832-8. **[confirm authors]**
22. Study of the I (internal) accessory proteins of HCoV-HKU1 (ORF 7b) and HCoV-OC43 (ORF 8b) in a mouse hepatitis virus model. PMID 41348903. **[confirm title and journal]**
23. Woo PCY, Lau SKP, Chu CM, et al. Characterization and complete genome sequence of a novel coronavirus, coronavirus HKU1, from patients with pneumonia. *J Virol.* 2005;79(2):884-895. doi:10.1128/JVI.79.2.884-895.2005.
24. Woo PCY, Lau SKP, Huang Y, et al. Comparative analysis of 22 coronavirus HKU1 genomes reveals a novel genotype and evidence of natural recombination in coronavirus HKU1. *J Virol.* 2006;80:7136-7145. **[confirm title wording]**
25. Woo PCY, Lau SKP, Yip CCY, Huang Y, Yuen KY. More and more coronaviruses: human coronavirus HKU1. *Viruses.* 2009;1(1):57-71.
