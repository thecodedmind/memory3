# Memory
A simple smart config manager.

##Simple usage

```py
from memory import Memory

cfg = Memory()
#Creates or reads a file called config.json in the current working directory

#When creating the class, you can define the config parsing engine to use. Currently supported are 'json' and 'toml'.
#Json is available built-in to Python3, toml requires an extra library, which you can get from `pip3 install toml`
#The engine used doesnt change the use of the class, it just changes the output file.
#Toml has some benefits over json in readability and other aspects, but json is more supported and hardened, its personal preference really.

#When creating the class, you can define a specific path for the config file too

cfg = Memory(path='/home/kaiser/MyApp') 
#Creates a file called config.json in the directory if it doesnt exist, otherwise reads the file

cfg = Memory(path='/home/kaiser/MyApp/stuff.json')
#Same as above but makes the filename stuff.json instead

#The Memory class also has a logging var for if you want debug logs in console for each operation

cfg = Memory(logging=True)

cfg._set('score', 1)
#Sets a config variable of score to 1

v = cfg._get('score')
#Returns the config variable for score

v = cfg._get('score', 0)
#Same as above, but defaults to 0 if score does not exist in config

#You can access the config object directly too

cfg['score'] = 10

#But if you edit the object, make sure to save after to save it to the config

cfg.save()

#If the config file was edited, you can reload it in memory

cfg.load()
```
