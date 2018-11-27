#Sample json file
{
    "quiz": {
        "sport": {
            "q1": {
                "question": "Which one is correct team name in NBA?",
                "options": [
                    "New York Bulls",
                    "Los Angeles Kings",
                    "Golden State Warriros",
                    "Huston Rocket"
                ],
                "answer": "Huston Rocket"
            }
        },
        "maths": {
            "q1": {
                "question": "5 + 7 = ?",
                "options": [
                    "10",
                    "11",
                    "12",
                    "13"
                ],
                "answer": "12"
            },
            "q2": {
                "question": "12 - 8 = ?",
                "options": [
                    "1",
                    "2",
                    "3",
                    "4"
                ],
                "answer": "4"
            }
        }
    }
}


#Sample Output
quiz.sport.q1.question = Which one is correct team name in NBA?
quiz.sport.q1.options[0] = New York Bulls
quiz.sport.q1.options[1] = Los Angeles Kings
quiz.sport.q1.options[2] = Golden State Warriros
quiz.sport.q1.options[3] = Huston Rocket
quiz.sport.q1.answer = Huston Rocket
quiz.maths.q1.question = 5 + 7 = ?
quiz.maths.q1.options[0] = 10
quiz.maths.q1.options[1] = 11
quiz.maths.q1.options[2] = 12
quiz.maths.q1.options[3] = 13
quiz.maths.q1.answer = 12
quiz.maths.q2.question = 12 - 8 = ?
quiz.maths.q2.options[0] = 1
quiz.maths.q2.options[1] = 2
quiz.maths.q2.options[2] = 3
quiz.maths.q2.options[3] = 4
quiz.maths.q2.answer = 4


#Code start from here ---------

#****** Packages*******
import json

#recursive function to flatten json
def flatten_json(par_json_data):
    def flatten(json_str, name=''):
        if type(json_str) is dict:
            for key in json_str:
                if len(name) != 0:
                    if name[len(name)-1] != '.':
                        name = name + '.'
                flatten(json_str[key], name + key)
                if type(json_str[key]) is str:
                    print(name + key + ' = ' + json_str[key])
                else:
                    None
        elif type(json_str) is list:
            i = 0
            for lstval in json_str:
                flatten(lstval, name + "[" + str(i) + '].')
                #print(type(a))
                if type(lstval) is str:
                    print(name + "[" + str(i) +"]" + ' = ' + lstval)
                else:
                    None
                i += 1
        else:
            None
    flatten(par_json_data)

#Your json file path
json_file = "/home/hemendra.gupta/workspace/Python/example.json"
#Open json file - handler file_data
file_data = open(json_file)
#load json file data in variable
json_data = json.load(file_data)
#Calling flattening function
flatten_json(json_data)
#Close file handler
file_data.close

#Code ends here---------------
