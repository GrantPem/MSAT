import re
import os

#User information
inputfile = str(input("Insert the file name including extension number "))
taga = str(input("Insert The Pattern "))
low = int(input("Please enter the minimum boundary (w/o tails): "))
high = int(input("Please enter the maximum boundary (w/o tails): "))

#Fasta to text file
fasta = open(inputfile)
red = fasta.read()
fasta.close()
oh = open('data.txt', 'w')
oh.write(red)
oh.close()


with open('data.txt', 'r') as file:
    lines = file.readlines()

header = ""
concatenated_string = ""


for line in lines:  
    if line.startswith('>'):
        header = line.strip()
    else:
        concatenated_string += line.strip() 


#Right Flank
right_flank = ""
pattern = r'([A-Za-z]+)' + taga + r'([A-Za-z]+)'
match = re.search(pattern, concatenated_string)
if match:
    right_flank = match.group(2)

#Left Flank
patt = taga
first_occurrence_index = re.search(patt, concatenated_string).start()
left_flank = concatenated_string[:first_occurrence_index]

#Central Pattern
first_occurrence_index = re.search(patt, concatenated_string).start()
last_occurrence_index = [match.end() for match in re.finditer(patt, concatenated_string)][-1]

central_variable = concatenated_string[first_occurrence_index:last_occurrence_index + len('taga')]


print(header)
def MappingMSAT(header, pattern, left, right, center, lowran, highran):
    full = left + center + right
    size = len(full)
    length = size
    center1 = center
    center2 = center

    #Filename
    filename = header
    file_name = filename.replace(">", "")
    finalfile = file_name + "_output.fasta"

    with open(finalfile, 'w') as  f:
              while int(length) < highran:
                  last_index = center2.rfind(pattern)
                  if last_index != -1:
                      center2 = center2[:last_index + len(pattern)] + pattern
                      total = left + center2 + right
                      length = len(total)
                      f.write(f'>{header}_{length}\n')
                      f.write(total + "\n")
                  else:
                      break  

        
              while int(length) >= lowran:
                  last_index = center1.rfind(pattern)
                  if last_index != -1:
                      center1 = center1[:last_index] + center1[last_index + len(pattern):]
                      total = left + center1 + right
                      length = len(total)
                      f.write(f'>{header}_{length}\n')
                      f.write(total + "\n")
                  else:
                      break  

                  




MappingMSAT(header, patt, left_flank, right_flank, central_variable, low, high)
os.remove("data.txt")
