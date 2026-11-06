# Reference protein annotation tables for CoVsurver

Annotation tables (protein name + start-stop position on a reference genome) used to extend Episurver-style

Generated:
1. [Seasonal human coronaviruses](#1-seasonal-human-coronaviruses)
   - [1.1 General features of the four viruses](#11-general-features-of-the-four-viruses)
   - [1.2 HCoV-229E](#12-hcov-229e)
   - [1.3 HCoV-NL63](#13-hcov-nl63)
   - [1.4 HCoV-OC43](#14-hcov-oc43)
   - [1.5 HCoV-HKU1](#15-hcov-hku1)
2. [Human metapneumovirus (hMPV)](#2-human-metapneumovirus-hmpv) (stub)

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
**Distinctive features.**
 
- **Split ORF4a / ORF4b.** The prototype has two accessory ORFs between S and E. Dijkman et al. showed that this is a
  laboratory artefact: the cell-culture-adapted prototype carries a 2-nucleotide deletion, whereas all clinical isolates they
  examined carry a single 660-nt ORF encoding a 219-residue protein, a homologue of the ORF3 proteins of NL63 and PEDV [13].
  Practical consequence: the table follows the NC_002645.1 annotation (ORF4a, ORF4b), but mutations in clinical sequences in
  this region may be better described on a single ORF4. **[confirm]**
- **No HE gene.** The genome organisation of 229E matches that of NL63 and PEDV: replicase, S, one accessory gene region, E, M, N [13].
- **Receptor and spike.** Aminopeptidase N is the receptor [12]. The 1,173-residue spike is the shortest of the four [5].
- **Legacy replicase annotation.** The GenBank record uses pre-standard product names (p9, p87, p195/p210, p44, ...).
  The standard numbering was checked against experimental cleavage data: p9 (nsp1) is released from the N-terminus of
  pp1a/pp1ab by the papain-like protease at Gly111|Asn112 [14], and the main protease cuts at Q2965/A2966, Q3267/S3268,
  Q3546/S3547, Q3629/S3630, Q3824/N3825 and Q3933/A3934 [15]. These correspond to the starts of NSP2, NSP5, NSP6, NSP7,
  NSP8, NSP9 and NSP10 in the table.


**Summary of the four references.**

| | HCoV-229E | HCoV-NL63 | HCoV-OC43 | HCoV-HKU1 |
|---|---|---|---|---|
| Genus / subgenus | Alpha / Duvinacovirus | Alpha / Setracovirus | Beta / Embecovirus | Beta / Embecovirus |
| Reference record | NC_002645.1 | NC_005831.2 | NC_006213.1 | NC_006577.2 |
| Reference strain | Wuerzburg (prototype) | Amsterdam I | ATCC VR-759 | HKU1 (genotype A) |
| Genome length (nt) | 27,317 | 27,553 | 30,741 | 29,926 |
| Spike length (aa) | 1,173 | 1,356 | 1,353 | 1,356 |
| Receptor | Aminopeptidase N [12] | ACE2 [12] | 9-O-acetylated sialic acid [12] | 9-O-acetylated sialic acid [12] |
| HE gene | No | No | Yes | Yes |
| Virus-specific genes in the tables | ORF4a, ORF4b | ORF3 | NS2, HE, NS12.9, I | HE, ORF4, N2 |

Genome and spike lengths are taken from the reference GenBank records. Receptor assignments are from the review
table cited in [12].

**Naming rules used in the tables.**

| Rule | Reason |
|---|---|
| Upper-case `NSP1`...`NSP16` | matches the CoVsurver SARS-CoV-2 report (`NSP12_P323L`) |
| `S`, `E`, `M`, `N` for the structural genes | shared names across all four viruses |
| Accessory genes keep the name used for that virus in the literature | no cross-virus equivalent exists |
| No separate ORF1a / ORF1ab rows | the OROV example lists one row per product |
| NSP11 included | NSP11 appears in the SARS-CoV-2 report |

---

### 1.2 HCoV-229E

**Reference.** NC_002645.1, the Wuerzburg prototype (27,317 nt). 

**Distinctive features.**

- **Split ORF4a / ORF4b.** The prototype has two accessory ORFs between S and E. Dijkman et al. showed that this is a
  laboratory artefact: the cell-culture-adapted prototype carries a 2-nucleotide deletion, whereas all clinical isolates they
  examined carry a single 660-nt ORF encoding a 219-residue protein, a homologue of the ORF3 proteins of NL63 and PEDV [13].
  Practical consequence: the table follows the NC_002645.1 annotation (ORF4a, ORF4b), but mutations in clinical sequences in
  this region may be better described on a single ORF4. **[confirm]**
- **No HE gene.** The genome organisation of 229E matches that of NL63 and PEDV: replicase, S, one accessory gene region, E, M, N [13].
- **Receptor and spike.** Aminopeptidase N is the receptor [12]. The 1,173-residue spike is the shortest of the four [5].
- **Legacy replicase annotation.** The GenBank record uses pre-standard product names (p9, p87, p195/p210, p44, ...).
  The standard numbering was checked against experimental cleavage data: p9 (nsp1) is released from the N-terminus of
  pp1a/pp1ab by the papain-like protease at Gly111|Asn112 [14], and the main protease cuts at Q2965/A2966, Q3267/S3268,
  Q3546/S3547, Q3629/S3630, Q3824/N3825 and Q3933/A3934 [15]. These correspond to the starts of NSP2, NSP5, NSP6, NSP7,
  NSP8, NSP9 and NSP10 in the table.

---

### 1.3 HCoV-NL63

**Reference.** NC_005831.2, strain Amsterdam I (27,553 nt).

- **Gene order 1a-1b-S-ORF3-E-M-N.** One accessory gene, ORF3, between S and E; the genome has a very low GC content
  (34%) [16]. There is no HE gene [10].
- **ACE2 receptor.** NL63 uses angiotensin-converting enzyme 2, the same receptor as SARS-CoV [12].
- **Large spike.** The 1,356-residue spike is longer than that of 229E (1,173); the S1 region carries an insert not
  found in 229E [17].
- **Papain-like protease processing.** Two papain-like protease domains, PLP1 and PLP2, process the N-terminal region:
  PLP1 releases nsp1 and PLP2 releases nsp2 and nsp3 [18].
- **No nsp annotation in the RefSeq record.** The NSP rows come from UniProt P0C6X5 residue ranges (NSP1 1-110, NSP2 111-898,
  NSP3 899-2462, NSP4 2463-2939, NSP5 2940-3242, ... NSP16 6430-6729), converted to genome positions across the frameshift [12].
  UniProt did not give the NSP16 end in the source used, so NSP16 runs to the end of pp1ab. NSP11 is inferred as the last 17 residues
  of ORF1a (12416-12466), the same length as in 229E. **[confirm]**

---

### 1.4 HCoV-OC43

**Reference.** NC_006213.1, strain ATCC VR-759 (30,741 nt); the record is identical to AY585228.
| NSP12 | 13317-16099 | I | 29140-29322 |

**Distinctive features.**

- **HE gene.** As a lineage A betacoronavirus (Embecovirus), OC43 carries an HE gene between ORF1b and S [19]; HE is an
  additional virion surface protein [7, 8].
- **Accessory genes NS2 and NS12.9.** The 3' region encodes NS2, HE, S, NS12.9, E, M and N in that order. NS12.9 overlaps the
  start of E [20]. Some papers call these genes ns2a and ns5a [21]; the table uses NS2 and NS12.9. **[confirm]** which naming
  CoVsurver prefers.
- **NS12.9 is a viroporin.** It forms ion channels and is needed for efficient virion morphogenesis and pathogenesis [19].
- **Internal I protein.** An internal accessory gene overlaps N in a different reading frame in betacoronaviruses; OC43's is
  designated ORF 8b in one recent study [22]. It is listed as `I` (29140-29322, inside N).
- **Receptor.** 9-O-acetylated sialic acid [12].
- **Largest NSP1.** At 246 residues, OC43 NSP1 sets the upper end of the cross-species range (110-246) [5].

---

### 1.5 HCoV-HKU1

**Reference.** NC_006577.2 (29,926 nt), isolate HKU1, genotype A, derived from AY597011. 
**Distinctive features.**

- **Group 2 features.** HKU1 has HE, an ORF4 accessory gene between S and E, and an ORF8 / N2 gene inside N [10, 23].
- **Three genotypes from recombination.** Comparison of 22 genomes showed three genotypes (A, B, C), with genotype C arising
  from recombination between A and B near the nsp16 / HE junction [24]. The reference is genotype A. HKU1 genomes range from
  29,295 to 30,097 nt [25].
- **Lowest GC content.** HKU1 genomes are 32% GC, the lowest of known coronaviruses with complete genomes at the time [25].
- **Receptor.** 9-O-acetylated sialic acid [12].
- **Isolate-specific protein databases.** UniProt holds separate HKU1 entries for different isolates. Ma et al. 2022 [5] appear
  to use a different isolate from the reference here: its NSP3 maximum of 1,979 residues is 50 shorter than the 2,029 in
  NC_006577.2, and UniProt N1 gives NSP3 as 810-2838. This is not an error in the table. **[confirm]** if HKU1 will be
  compared against another isolate.
- **Naming.** The internal gene in N is called N2 / ORF8 in the genome papers [23] and ORF 7b in a recent study of I proteins [22];
  these are probably the same internal ORF, but the naming differs between papers.

---

## 2. Human metapneumovirus (hMPV) - IN progress. 

Stub. hMPV is not a coronavirus: it is a negative-sense, non-segmented virus (family Pneumoviridae) with no nsps and no
S/E/M/N set. The reference is NC_039199.1 (isolate 00-1, provisional RefSeq, identical to AF371337).

| Product | Position | Product | Position |
|---|---|---|---|
| N | 40-1224 | M2-2 | 5248-5463 |
| P | 1248-2132 | SH | 5494-6045 |
| M | 2165-2929 | G | 6247-6957 |
| F | 3052-4671 | L | 7167-13184 |
| M2-1 | 4737-5300 | | |

M2-1 and M2-2 overlap by design (one gene, two reading frames). The strain ID `hMPV_Human_2000_Netherlands-00-1` is inferred from
the isolate name and needs checking. F is cleaved into F1 and F2, which the record does not annotate.
Literature and the section text are still to be written.

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
