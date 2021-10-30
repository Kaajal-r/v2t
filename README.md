# v2t
 Python3 program to print a given number in words. The program handles till 9 digits numbers and  can be easily extended to 20 digit number
# Python3 program to print a given number in words.
import re
# strings at index 0 is not used, it is to make array indexing simple
one = [ "", "one ", "two ", "three ", "four ",
		"five ", "six ", "seven ", "eight ",
		"nine ", "ten ", "eleven ", "twelve ",
		"thirteen ", "fourteen ", "fifteen ",
		"sixteen ", "seventeen ", "eighteen ",
		"nineteen "]

# strings at index 0 and 1 are not used,they is to make array indexing simple
ten = [ "", "", "twenty ", "thirty ", "forty ",
		"fifty ", "sixty ", "seventy ", "eighty ",
		"ninety "]

# i is 1- or 2-digit number
def numToWords(i, s):

	str = ""
	
	# if i is more than 19, divide it
	if (i > 19):
		str += ten[int(i) // 10] + one[int(i) % 10]
	else:
		str += one[int(i)]

	# if n is non-zero
	if (i):
		str += s
    
	return str

# Function to print a given number in words
def convertToWords(i):

	# stores word representation of given number i
	out = ""

	# handles digits at ten millions and hundred millions places (if any)
	out += numToWords((i // 10000000),
							"crore ")
    
	# handles digits at hundred thousands and one millions places (if any)
	out += numToWords(((i // 100000) % 100),
								"lakh ")

	# handles digits at thousands and tens thousands places (if any)
	out += numToWords(((i // 1000) % 100),
							"thousand ")

	# handles digit at hundreds places (if any)
	out += numToWords(((i // 100) % 10),
							"hundred ")

	if (i > 100 and i % 100):
		out += "and " 


	# handles digits at ones and tens places (if any)
	out += numToWords((i % 100), "")
    

	return out

# Driver code

# long handles upto 9 digit no
# change to unsigned long long
i = float(input("enter the number :  "))

if '.' in str(i):
    num1 = re.search("\.(.*)",str(i)).group(1)

# convert given number in words
var1 = convertToWords(i) + f"{num1}/100 only"

print(var1)
