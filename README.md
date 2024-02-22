# MSAT Python Script

  Used as an assistant tool to creating varing length for the ASAP mapping file. 

- This python script takes a fasta file
- The fasta file must contain only one sequence.
- When you activate the script you will be prompted to "Insert the file name including extension number." for an example you would enter 'TEST.fas'
- You will then be prompted to enter the MSAT pattern. This is case sensitive so confirm the correct casing the pattern is displayed in the fasta file. In the MSAT sequence as a test file it has the pattern "gaca"
- Next you enter the minimum and maximum boundary of the microsat. This input only takes numbers.
- A new file will then be created named 'TEST_output.fasta' with the pattern added and subtracted creating different sequences with length variations extending to both ends of the specified minimum and maximum.
