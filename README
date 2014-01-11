################################################################################
Mosaik-1.1.0014 VS MOSAIK-2.1.73
(Inconsistency Issues flagged in RED, Resolutions in BLUE)

# Path used
	PATH=$PATH:/Users/Sid/Projects/

Mosaik Reference Archives

# Used MosaikBuild to make MOSAIK sequence reference archive, needs to be in .fasta format to make reference archives.

Mosaik-1.1.0014

	$./Mosaik-1.1.0014/bin/MosaikBuild -fr CRM_files/UniqueCRM2.fasta -oa CRM_files/	UniqueCRM2_Mosaik1.dat 

Output
------------------------------------------------------------------------------
MosaikBuild 1.1.0014                                                2010-10-01
Michael Stromberg & Wan-Ping Lee  Marth Lab, Boston College Biology Department
------------------------------------------------------------------------------

- converting CRM_files/UniqueCRM2.fasta to a reference sequence archive.

- parsing reference sequences:
ref seqs: 1 (1.99 ref seqs/s)

- writing reference sequences:
100%[======================================================]      1.00 ref seqs/s        in  1 s  

- calculating MD5 checksums:
100%[======================================================]      1.00 ref seqs/s        in  1 s  

- writing reference sequence index:
100%[======================================================]      1.00 ref seqs/s        in  1 s  

- creating concatenated reference sequence:
100%[======================================================]      1.00 ref seqs/s        in  1 s  

- writing concatenated reference sequence...        finished.
- creating concatenated 2-bit reference sequence... finished.
- writing concatenated 2-bit reference sequence...  finished.

MosaikBuild CPU time: 0.005 s, wall time: 1.009 s

###############################################

MOSAIK-2.1.73

	$MOSAIK-2.1.73-mac-binary/MosaikBuild -fr CRM_mapping/CRM_files/UniqueCRM2.fasta -oa 	CRM_files/UniqueCRM2.dat

Output
------------------------------------------------------------------------------
MosaikBuild 2.1.73                                                  2012-11-08
Michael Stromberg & Wan-Ping Lee  Marth Lab, Boston College Biology Department
------------------------------------------------------------------------------

- converting CRM_files/UniqueCRM2.fasta to a reference sequence archive.

- parsing reference sequences:
ref seqs: 1 (1.99 ref seqs/s)

- writing reference sequences:
100%[======================================================]      1.00 ref seqs/s        in  1 s  

- calculating MD5 checksums:
100%[======================================================]      1.00 ref seqs/s        in  1 s  

- writing reference sequence index:
100%[======================================================]      1.00 ref seqs/s        in  1 s  

- creating concatenated reference sequence:
100%[======================================================]      1.00 ref seqs/s        in  1 s  

- writing concatenated reference sequence...        finished.
- creating concatenated 2-bit reference sequence... finished.
- writing concatenated 2-bit reference sequence...  finished.

MosaikBuild CPU time: 0.005 s, wall time: 2.509 s

###############################################
###############################################

Mosaik Read Archives

# Used MosaikBuild to make MOSAIK read archive, needs to be in .fastq format to make read archives.

MosaikBuild 1.1.0014 

	$./Mosaik-1.1.0014/bin/MosaikBuild -q CRM_mapping/CRM_files/SRR023594_1.fastq -out CRM_mapping/CRM_files/	SRR023594_1_Mosaik1.dat -st illumina

 Output
------------------------------------------------------------------------------
MosaikBuild 1.1.0014                                                2010-10-01
Michael Stromberg & Wan-Ping Lee  Marth Lab, Boston College Biology Department
------------------------------------------------------------------------------

- setting read group ID to: ZMCETWL9EN4
- setting sample name to: unknown
- setting sequencing technology to: illumina
- trimming leading and lagging N's. Mates with >4 interior N's will be deleted.

- parsing FASTQ file:
reads: 299,512 (149,457.1 reads/s)

Filtering statistics:
============================================
# reads deleted:            149762 ( 50.0 %)
# leading N's trimmed:           1
# lagging N's trimmed:           5
--------------------------------------------
# reads written:            149750
# bases written:          24133563

MosaikBuild CPU time: 1.803 s, wall time: 2.046 s

##############################################

MosaikBuild 2.1.73  

	$MOSAIK-2.1.73-mac-binary/MosaikBuild -q CRM_mapping/CRM_files/SRR023594_1.fastq -out 	CRM_mapping/CRM_files/SRR023594_1.dat -st illumina

Output
------------------------------------------------------------------------------
MosaikBuild 2.1.73                                                  2012-11-08
Michael Stromberg & Wan-Ping Lee  Marth Lab, Boston College Biology Department
------------------------------------------------------------------------------

- setting read group ID to: ZMC4EDW9UVI
- setting sample name to: unknown
- setting sequencing technology to: illumina

- parsing FASTQ file:
reads: 299,512 (149,457.1 reads/s)

Filtering statistics:
============================================
# reads written:            299512
# bases written:          24733604

MosaikBuild CPU time: 1.767 s, wall time: 2.065 s

##############################################

Mate Pair Issues

#Splitting the SRR023594.fastq into 2 mates revealed that mate 1 was incompatible.
#mate_1.fastq had only 4 base pairs
#mate_2.fastq has read lengths in excess of 200 bp.

 Used egrep  with extended regular expressions to check lengths.

$egrep "^@.*length=[0-9]$" mate_1.fastq | cut -d ' ' -f 3 | sort -n -r | uniq -c | less
$egrep "^@.*length=[0-9]{1,3}$" mate_2.fastq | cut -d ' ' -f 3 | sort -n -k 2 -r | uniq -c | less


################################################################################

Issues Resolved?

# Used awk to split paired end file into single ended reads. 

awk '0 == ((NR+4) % 8)*((NR+5) % 8)*((NR+6) % 8)*((NR+7) %8)' SRR023594_1.fastq > mate_1.fastq &
awk '0 == (NR % 8)*((NR+1) % 8)*((NR+2) % 8)*((NR+3) %8)' SRR023594_1.fastq > mate_2.fastq 

New Read Archives

$./Mosaik-1.1.0014/bin/MosaikBuild -q CRM_mapping/CRM_files/mate_2.fastq -out CRM_mapping/CRM_files/single_Mosaik1.dat -st illumina

------------------------------------------------------------------------------
MosaikBuild 1.1.0014                                                2010-10-01
Michael Stromberg & Wan-Ping Lee  Marth Lab, Boston College Biology Department
------------------------------------------------------------------------------

- setting read group ID to: ZMOBUT4FMZS
- setting sample name to: unknown
- setting sequencing technology to: illumina
- trimming leading and lagging N's. Mates with >4 interior N's will be deleted.

- parsing FASTQ file:
reads: 149,756 (74,728.5 reads/s)

Filtering statistics:
============================================
# reads deleted:                 6 (  0.0 %)
# leading N's trimmed:           1
# lagging N's trimmed:           5
--------------------------------------------
# reads written:            149750
# bases written:          24133563

MosaikBuild CPU time: 1.537 s, wall time: 2.042 s

##############################################

$MOSAIK-2.1.73-mac-binary/MosaikBuild -q CRM_mapping/CRM_files/mate_2.fastq -out CRM_mapping/CRM_files/singleMosaik2.dat -st illumina

------------------------------------------------------------------------------
MosaikBuild 2.1.73                                                  2012-11-08
Michael Stromberg & Wan-Ping Lee  Marth Lab, Boston College Biology Department
------------------------------------------------------------------------------

- setting read group ID to: ZMOC1YSGE8Q
- setting sample name to: unknown
- setting sequencing technology to: illumina

- parsing FASTQ file:
reads: 149,756 (99,638.1 reads/s)

Filtering statistics:
============================================
# reads written:            149756
# bases written:          24134580

MosaikBuild CPU time: 1.446 s, wall time: 2.596 s


##############################################

Alignment 

$Mosaik-1.1.0014/bin/MosaikAligner -in CRM_mapping/CRM_files/single_Mosaik1.dat -ia CRM_mapping/CRM_files/UniqueCRM2.dat -out CRM_mapping/CRM_files/reads.dat -hs 10 -act 11 -mmp 0.2 -bw 41 -mhp 200 -a all

------------------------------------------------------------------------------
MosaikAligner 1.1.0014                                              2010-10-01
Michael Stromberg & Wan-Ping Lee  Marth Lab, Boston College Biology Department
------------------------------------------------------------------------------

- Using the following alignment algorithm: all positions
- Using the following alignment mode: aligning reads to all possible locations
- Using a maximum mismatch percent threshold of 0.2
- Using a hash size of 10
- Using a Smith-Waterman bandwidth of 41
- Using an alignment candidate threshold of 11bp.
- Setting hash position threshold to 200
- loading reference sequence... finished.

Hashing reference sequence:
3,057.0 ref bases/s        in  1 s  


Aligning read library (149750):
 5,864.3 reads/s        in 25 s  

Alignment statistics (mates):
===================================
# failed hash:      79487 ( 53.1 %)
# filtered out:     66585 ( 44.5 %)
# unique:            1636 (  1.1 %)
# non-unique:        2042 (  1.4 %)
-----------------------------------
total:             149750
total aligned:       3678 (  2.5 %)

MosaikAligner CPU time: 25.341 s, wall time: 26.680 s

##############################################

$MOSAIK-2.1.73-mac-binary/MosaikAligner -in CRM_mapping/CRM_files/single_Mosaik2.dat -ia CRM_mapping/CRM_files/UniqueCRM2.dat -out CRM_mapping/CRM_files/reads.dat -annpe MOSAIK-2.1.73-mac-binary/2.1.26.pe.100.0065.ann -annse MOSAIK-2.1.73-mac-binary/2.1.26.se.100.005.ann -hs 10 -act 11 -mmp 0.2 -bw 41 -mhp 200 -a all

------------------------------------------------------------------------------
MosaikAligner 2.1.73                                                2012-11-08
Michael Stromberg & Wan-Ping Lee  Marth Lab, Boston College Biology Department
------------------------------------------------------------------------------

- Using the following alignment algorithm: all positions
- Using the following alignment mode: aligning reads to all possible locations
- Using a maximum mismatch percent threshold of 0.2
- Using a hash size of 10
- Using a Smith-Waterman bandwidth of 41
- Using an alignment candidate threshold of 11bp.
- Setting hash position threshold to 200
- loading reference sequence... finished.

Hashing reference sequence:
3,057.0 ref bases/s        in  1 s  


Aligning read library (149756):
5,069.9 reads/s        in 29 s  

- cleaning up temp files...finished.

Alignment statistics (mates):
================================================
   # failed hash:                79491 ( 53.1 %)
------------------------------------------------
# unaligned mates(X):            79491 ( 53.1 %)
# filtered out(F):               66540 ( 44.4 %)
# uniquely aligned mates(U):      1653 (  1.1 %)
# multiply aligned mates(M):      2072 (  1.4 %)
================================================
total aligned:                    3725 (  2.5 %)
total:                          149756

MosaikAligner CPU time: 29.786 s, wall time: 31.657 s
