# WordDictionary
import json
from difflib import get_close_matches
data = json.load(open("data.json"))

def translate(word):
    word = word.lower()
    if word in data:
        return data[word]
    elif word.title() in data:
        return data[word.title()]
    elif word.upper() in data:
        return data[word.upper()]
    elif len(get_close_matches(word , data.keys())) > 0 :
        print("Did you mean %s instead?" %get_close_matches(word, data.keys())[0])
        decide = input("Press y for yes or n for no:")
        if decide == "y"or decide=="Y":
            return data[get_close_matches(word , data.keys())[0]]
        elif decide == "n" or decide=="N":
            return("Please enter a valid word or try entering something else... ")
        else:
            return("You have entered wrong input please enter just y or n:")
    else:
        print("Please enter a valid word or try entering something else...")

word = input("Enter the word whose meaning you want to search:")
output = translate(word)
if type(output) == list:
    print("Umm...lets see what it means... ")
    for item in output:
       
        print(item)
else:
    print("Umm...lets see what it means... ",output)

