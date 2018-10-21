import requests
import json


def search_article(search_art, j):
    ''' Searches GDPR by Article number '''
    for line in j:
        if search_art == line['article']:
            print("\n{}({})\n{}".format(line['article'], line['num'], line['text']))
    

def search_text(search_term, j):
    ''' Searches GDPR by exact match '''
    result_string = ""
    for line in j:
        if search_term.upper() in line['text'].upper():
            if line['section'] != "Recitals":
                result_string += "Chapter {}\n{}\n{}\n{}({})\n{}\n\n".format(line['chapter'], line['section'], line['subtitle'], line['article'], line['num'], line['text'])
            else:
                result_string += "Recital\n{}\n\n".format(line['text'])              
    print(result_string)

    
gdpr_text = requests.get("http://enceladus.world/gdpr_json")
j = gdpr_text.json()

while True:
    search_term = input("\nSearch or [num] > ")
    if search_term:
        try:
            if search_term.upper() == "Q":
                quit()
        except TypeError:
            print("Type error - please use valid string")
            break

        if search_term.startswith("["):
            search_art = search_term.replace("[", "").replace("]", "")
            search_article(search_art, j)
        else:
            search_text(search_term, j)



            
