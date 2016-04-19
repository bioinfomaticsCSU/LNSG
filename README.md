# BOSS(Building Optimized Scaffold graph for Scaffolding)

A novel algorithm is used for scaffolding contigs produced by any assembler. 

License
=========

Copyright (C) 2014 Jianxin Wang(jxwang@mail.csu.edu.cn), Junwei Luo(luojunwei@csu.edu.cn)

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 3
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, see <http://www.gnu.org/licenses/>.

Jianxin Wang(jxwang@mail.csu.edu.cn), Junwei Luo(luojunwei@csu.edu.cn)
School of Information Science and Engineering
Central South University
ChangSha
CHINA, 410083


Scaffolder: BOSS
=================

1)Installing.

BOSS is written C++ and therefore will require a machine with GNU C++ pre-installed.

Create a main directory (eg:BOSS). Copy all source code to this directory.

Type "g++ main.cpp scaffoldgraph.cpp scaffolding.cpp -o boss ./lp/liblpsolve55.a -lm -ldl -I include/ -L lib/ -lbamtools" 

2)Running.

Run command line: 

"boss contigs.fa bamfile_left.bam bamfile_right.bam read_length insert_size std min_weight min_number is_paired_end scaffold_file_name"

contigs.fa is the file includes contigs produced by one assembler.

bamfile_left.bam and bamfile_right.bam are two bam files. Before scaffolding, users should using one mapping tool(bowtie2, bwa or bowtie) to map left read file and right read file to contigs respectively, and this will produce the two bam files.

read_length is the length of read.

insert_size is the insert size of read library.

std is standard deviation of insert size (such as, std = a*insert_size, 0.05<a<0.1).

min_weight is one cutoff for removing suprious edgs in scaffold graph (such as, min_weight = 0.2).

min_number is the minimum number of links between contigs (such as, min_number = 2).

is_paired_end is 0 or 1, 1 represents that read library is paired-end library, 0 represents that read library is mate-paired.

scaffold_file_name is the output file name, this file includes scaffolds produced by BOSS. 

If there two read libraries, the command line:
"boss contigs.fa bamfile1_left.bam bamfile1_2.bam read_length1 insert_size1 std1 min_weight1 min_number1 is_paired_end1 bamfile2_left.bam bamfile2_right.bam read_length2 insert_size2 std2 min_weight2 min_number2 is_paired_end2 scaffold_file_name"

3)Output.

scaffold_file_name is the file (fasta format) which includes scaffolds produced by BOSS.
