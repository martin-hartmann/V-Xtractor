# V-Xtractor
Extract hypervariable regions from ribosomal marker gene sequences

V-Xtractor: An open-source, high-throughput software tool to identify and extract hypervariable regions of small and large subunit ribosomal RNA gene sequences of bacterial, archaeal, and fungal origin. 

V-Xtractor is a Perl-based, high-throughput software tool that locates, verifies, and extracts defined segments of sequence information from sequence datasets. Hidden Markov Models are used to detect the conserved boundaries of the target region and to extract the interjacent sequence information (that is for example the hyper-variable regions of the rRNA gene or the internal transcribed spacer regions of the rRNA operon). This tool extracts phylogenetically comparable regions without prior multiple sequence alignments and improves reliability of the data by confirming basic authenticity of the sequence.

Source code also available at:
http://www.microbiome.ch/software

Version		2.1
Purpose		Extraction of variable subregions from SSU or LSU rRNA sequences
Copyright	Hartmann et al. 2010
Contact		Martin Hartmann, contact(at)microbiome.ch
Affiliation	Swiss Federal Institute of Technology, Zurich
Programmer	Charles Howes (vxtractor(at)ch.pkts.ca)

The full installation instructions can be found in the Users Guide.

Install dependencies prior to usage
Perl is available at http://www.perl.org/
HMMER is available at http://hmmer.janelia.org/

```
V-Xtractor v. 2.1. Copyright (c) Hartmann et al. 2010.

Usage: /usr/local/bin/vxtractor.pl [-a] [-b] [-d] [-e evalue] [-s score] [-r region] [-i (long|short)] [-h hmmdirectory] [-c csvoutput] [-o outputfile] inputfiles

  This program will analyze each sequence in each input file, looking
  for the HMMs in the hmm directory.

  Options:    
    -o outputfile: Write the HMM region information to a FASTA file
    -c csvoutput: Write the HMM region information to a CSV file

    -h hmmdirectory: The directory containing HMM files named
       V[1-x]leftlong.HMM   V[1-x]leftshort.HMM
       V[1-x]rightlong.HMM  V[1-x]rightshort.HMM

    -r region: The regions to extract, in the following format:
      -r V1       -- the V1 region only
      -r .V1-V2.  -- the region from the left of V1 to the right of V2
      -r V1.-.V2  -- the region from the right of V1 to the left of V2
      -r .V3-.V7  -- the region from the left of V3 to the left of V7

    -i (long|short): Include HMM regions in the fasta output (default: exclude)
      The long or short HMM region will be chosen where applicable.

    -b: Use bitscore instead of evalue threshold (only use one or the other)
    -e evalue: Set the global evalue threshold (default: 0.01)
    -s score: Set the global score threshold (default: 0)

    -a: Check that HMMs occur in alphabetical order in each sequence

    Example:
    /usr/local/bin/vxtractor.pl -a -r .V1-V3. -h HMMs/SSU/bacteria/ -o out.fasta  in.fasta
    --this will extract V1 through V3, for SSU bacteria, from the file in.fasta
    and save the results to out.fasta, checking correct order of V1, V2, and V3.
```
