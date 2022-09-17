import json
users_dictionary = {}  # Used to create a global variable


def file_opener():
    """Opens the Json file and adds the contents of it to the global dictionary and returns it"""
    global users_dictionary
    try:
        with open("user_dict.json") as file_reader:
            users_dictionary = json.load(file_reader)

    # To avoid the error if the file exists and there is no such dictionary in it
    except json.decoder.JSONDecodeError:
        users_dictionary = {}

    return users_dictionary


def file_writer():
    """Writes the dictionary back to the Json file"""
    with open("user_dict.json", "w") as f:
        json.dump(users_dictionary, f)


def suggestion_giver():
    """Gives the user suggestions of other user based on the common tags used by both"""
    print("Suggestions for you are:")
    # for taking a single tag from the user's tag list to match across all other user's tags
    for tag in users_dictionary[user_name]:
        # to separately take the tag list and the username
        for name, items in users_dictionary.items():
            # If the user name matches with the name in the dictionary then skip checking the tag list related to it
            if name == user_name:
                pass
            else:
                # if any tag is common in two users print the name og the 2nd user
                if tag in users_dictionary[name]:
                    print(f"\t{name.title()}")


# A continues loop for running the program  l
while True:
    user_name = input("Enter your name: ").lower().strip()  # Takes the user name
    users_dictionary = file_opener()
    if user_name in users_dictionary.keys():
        suggestion_giver()
        edit_tags = input("Do you want to edit the tags?(y/n) ")
        if edit_tags=='n':
            continue
    if user_name=="q":
        break
    else:
        if user_name in users_dictionary.keys():
            print("Your Current Tags are:")
            for individual_tag in users_dictionary[user_name]:
                print(f"#{individual_tag}")
        tags = input("Enter the related tags, separated by '#':\n#").lower().strip().split("#")
        users_dictionary[user_name] = tags
    file_writer()
