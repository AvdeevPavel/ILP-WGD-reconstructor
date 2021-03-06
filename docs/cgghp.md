# Conserved Guided Genome Halving Problem
`cgghp.py` creates the ILP formulation for the Conserved Guided Genome Halving Problem
and runs Gurobi Solver.  

```
usage: cgghp.py [-h] [-r PATH] [-t PATH] -o PATH [-tl NUMBER] [-v]

ILP solver for the Conserved Guided Genome Halving Problem (CGGHP)

optional arguments:
  -h, --help            show this help message and exit
  -r PATH, --ordinary PATH
                        Ordinary genome in GRIMM format
  -t PATH, --two_dupl PATH
                        2-duplicated genome in GRIMM format
  -o PATH, --out-dir PATH
                        Output directory
  -tl NUMBER, --time_limit NUMBER
                        Time limit for Gurobi solver
  -v, --version         show program's version number and exit

Gurobi solver is required! Input genomes must be in GRIMM format.
```

### Examples
You can try `cgghp.py` on the provided ready-to-use examples:

```bash
 python cgghp.py --ordinary examples/ord.gen --two_dupl examples/a.gen -o test/
```

### Input
`cgghp.py` needs as input:

- Ordinary genome (i.e., each gene/synteny block is present in a single copy) **[[in GRIMM format](http://grimm.ucsd.edu/GRIMM/grimm_instr.html)]** 
- 2-duplicated genome (i.e., each gene/synteny block is present in two copies) **[[in GRIMM format](http://grimm.ucsd.edu/GRIMM/grimm_instr.html)]**
- Path to output directory

Optionally, a time limit may be set for Gurobi Solver (it is 2 hours by default). 

### Output
After running `cgghp.py`, the output directory will contain:
- `pre_dup.gen` - file with ancestral pre-duplicated genome in GRIMM format 
- `result.txt` - file with exit status (0 - stopped by reaching TL, 1 - optimal solution, 2 - other),
optimized value of the objective function, and ggh-score
(the distance between the ordinary genome and the pre-duplicated genome plus the distance between the 2-duplicated genome and the perfect 2-duplicated genome)
- several log files