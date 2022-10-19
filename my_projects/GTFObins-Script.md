---
layout: default
title: Projelerim
permalink: /my-projects/gtfobins-script
---

<nav>
      <ul style="display: flex;list-style:none">
        {% for item in site.data.menu %}
        <li style="margin-right: 50px"><a style="text-decoration:none" class="{% if page.url == item.link %}active{% endif %}" href="{{ item.link }}">{{ item.title }}</a></li>
        {% endfor %}
      </ul>
</nav>

## My Projects

Bu kısımda github'daki projelerimi açıklayacağım.

```python
def banner():
	print("  ____ _____ _____ ____")                  
	print(" / ___|_   _|  ___/ ___|  ___ __ _ _ __ ") 
	print("| |  _  | | | |_  \\___ \\ / __/ _` | '_ \\ ")
	print("| |_| | | | |  _|  ___) | (_| (_| | | | |")
	print(" \\____| |_| |_|   |____/ \\___\\__,_|_| |_|\n")
```

Kod bolumu hakkinda birtakim bilgiler

```python
def scan_binary(binary_):
	func = []
	code = []
	p_code = []

	bin_ = binary_
	url = requests.get(f"https://gtfobins.github.io/gtfobins/{bin_}")
	soup = BeautifulSoup(url.content, 'html.parser')
	
	for element in soup.find_all('h2'):
		func.append(element.text)
	print(f"{Style.BRIGHT}[!] {Back.RED}Function List")
	for element in range(len(func)):
		print(f"{Fore.RED}[*] {Fore.WHITE}{Style.BRIGHT}{func[element]}")
	print()

	for element in soup.select('.language-plaintext'):
		p_code.append(element.text)

	for element in soup.find_all('code'):
		if element.text not in p_code:
			code.append(element.text)

	for element in range(len(code)):
		print(f"{Style.BRIGHT}* {Back.RED}[{func[element].upper()}]")
		print()
		print(code[element])
		print(f'{Style.BRIGHT}----------------------------------------------')
```

Kod bolumu hakkinda birtakim bilgiler

```python
def scan_function(binary_, function_):
	func = []
	code = []
	p_code = []

	bin_ = binary_
	url = requests.get(f"https://gtfobins.github.io/gtfobins/{bin_}")
	soup = BeautifulSoup(url.content, 'html.parser')
	
	for element in soup.find_all('h2'):
		func.append(element.text)
	print(f"{Style.BRIGHT}[!] {Back.RED}Function List")
	for element in range(len(func)):
		print(f"{Fore.RED}[*] {Fore.WHITE}{Style.BRIGHT}{func[element]}")
	print()

	for element in soup.select('.language-plaintext'):
		p_code.append(element.text)

	for element in soup.find_all('code'):
		if element.text not in p_code:
			code.append(element.text)

	for element in range(len(func)):
		if func[element] == function_:
			print(f"{Style.BRIGHT}* {Back.RED}[{func[element].upper()}]")
			print()
			print(code[element])
			print(f'{Style.BRIGHT}----------------------------------------------')
```

Kod bolumu hakkinda birtakim bilgiler

```python
def scan():
	url = requests.get(f"https://gtfobins.github.io/")
	soup = BeautifulSoup(url.content, 'html.parser')
	binaries = soup.find_all(class_="bin-name")
	print(f"{Back.RED}{Style.BRIGHT}Binaries in GTFObins")
	for i in binaries:
		print(f"{Fore.RED}[-] {Fore.WHITE}{Style.BRIGHT}" + i.text)

	print("----------------------")
	binary_ = input(f"{Fore.RED}[!] {Fore.GREEN}BINARY> ")

	func = []
	code = []
	p_code = []

	url = requests.get(f"https://gtfobins.github.io/gtfobins/{binary_}")
	soup = BeautifulSoup(url.content, 'html.parser')

	for element in soup.find_all('h2'):
		func.append(element.text)
	print(f"{Style.BRIGHT}[!] {Back.RED}Function List")
	for element in range(len(func)):
		print(f"{Fore.RED}[*] {Fore.WHITE}{Style.BRIGHT}{func[element]}")
	print()

	for element in soup.select('.language-plaintext'):
		p_code.append(element.text)

	for element in soup.find_all('code'):
		if element.text not in p_code:
			code.append(element.text)

	for element in range(len(code)):
		print(f"{Style.BRIGHT}* {Back.RED}[{func[element].upper()}]")
		print()
		print(code[element])
		print(f'{Style.BRIGHT}----------------------------------------------')
```

Kod bolumu hakkinda birtakim bilgiler

```python
argument_parser = argparse.ArgumentParser(description="GTFOBINS binary scan.")
argument_parser.add_argument('-b', '--binary', required=False, help='Binary name')
argument_parser.add_argument('-f', '--function', required=False, help='Function name')
arguments = argument_parser.parse_args()

if arguments.binary and not arguments.function:
	banner()
	scan_binary(arguments.binary)
elif arguments.binary and arguments.function:
	banner()
	scan_function(arguments.binary, arguments.function)
else:
	banner()
	scan()
```

Projenin Github sayfasına gitmek için aşağıdaki butona basıp gidebilirsiniz.

<button style="background-color: white;color: black;border: 2px solid #4CAF50;width: 250px" href="https://github.com/thealper2/GTFOBins-Script">Kodun tam haline gitmek için Tiklayiniz</button>

---

<footer style="float:left;"><small>&copy; 2022 thealper2</small></footer>
<footer style="float:right;"><small><a href="https://github.com/thealper2">My Github</a></small></footer>