# wordle

def five_letters(file_name):
  with open (file_name, 'r', encoding = 'utf-8') as file:
    my_words = file.readlines()
    
#   five_letters = [i.lower() if len(i) ==6 and i[:-1].isalpha() for i in my_words]
    
    five_letters = []
    for i in my_words:
      if len(i) ==6 and i[:-1].isalpha():
        five_letters.append(i.lower())

  file_name = f'{file_name[:-4]}_5letters.txt'
  with open (file_name, 'w', encoding = 'utf-8') as f:
    f.writelines(five_letters)
  return f"Five letter words written to {file_name}"


five_letters('words.txt')

---------------------------

def frequency_analysis(file_name):
  with open (file_name, 'r', encoding = 'utf-8') as file:
    five_letters = file.readlines()
    my_dict = {}
  for i in five_letters:
    for j in i:
      if j not in my_dict:
        my_dict[j] = 1
      else:
        my_dict[j] += 1
  
  frequency = sorted(my_dict.items(), key=lambda x: x[1], reverse=True)

  file_name = f'{file_name[:-4]}_frequency.txt'
  with open (file_name, 'w', encoding = 'utf-8') as f:
    f.writelines(str(frequency))
  return f"Frequency results are saved to {file_name}"

frequency_analysis('words_5letters.txt') 
