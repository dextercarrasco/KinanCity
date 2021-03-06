# KinanCity-core : CLI account creator

KinanCity-core main class accepts configuration from :
- a set of **Command Line parameters** given at runtime
- a **config.properties** file you can create and customize from **config.example.properties**

**Note :**  A usage help is shown if called without any parameters or an invalid set of parameters.

**About Captchas**  
KinanCity need to solve captchas. It currently uses [2captcha](https://2captcha.com) wich requires a **apiKey** that must be given each time or saved in the config file.

**Running in command line**  
the examples below only give the arguments that will follow the launch command : `java -jar KinanCity-core-<version>.jar` or `start.sh` for unix and `start.bat` for windows

Element written between angle brackets (< >) are example values. Remove the brackets and use your own value.

For all these examples, the usernames and password must follow theses rules :  
- username : between 6 and 16 characters with no spaces
- password : with lower and uppercase letters, numbers and at least a symbol


**create a sequence of accounts :**

`-m <email@domain.com> -f <aa***bb> -p <Passw0rd!> -c 20`  

will create 20 accounts using the pattern given replacing the stars by a incremental number, giving usernames from `aa001bb` to `aa020bb` with matching + trick emails `email+aa***bb@domain.com`

`-s 123` or `-startnum 123` will make the sequence start at 123 instead of 0.

**create a batch from a csv file with a list of accounts :**

`-a pathTo/accounts.csv`

will create 1 account per line the the csv file.

**create a single account :**

`-u <username> -m <email@domain.com> -p <password>`

will create 1 account with given parameters.

**Additional parameters :**

* `-ck <captchaKey>` or `-captchaKey <captchaKey>` to give a specific apiKey add
* `-px [proxy1,proxy2,...]` or `-proxies [proxy1,proxy2,...]` to use multiple proxies.  
Or set them in the config file as `proxies=`  
anonymous proxy format is `ip:port` like `127.0.0.1:80`
proxy with auth format is `login:pass@ip:port` like `root:admin@127.0.0.1:80`
* `-t <12>` or `-thread <12>` to change the number of thread to 12 (default 5)
* `-npc` or `-noProxyCheck` will skip proxy check step at startup
* `-nl` or `-noLimit` will remove the policy that limits to 5 accounts per IP per 10 minutes
