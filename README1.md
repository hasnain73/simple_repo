#1
Likith Kumar@DESKTOP-8N6978G MINGW64 ~
$ mkdir MITdemo
Likith Kumar@DESKTOP-8N6978G MINGW64 ~
$ cd MITdemo
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo
$ ls
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo
$ touch index.html index2.html index3.html
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo
$ vim index.html
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo
$ cat index.html
Hello! This is the first program from DevOps Training.
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo
$ ls -l
total 1
-rw-r--r-- 1 Likith Kumar 197609 55 Apr 17 19:13 index.html
-rw-r--r-- 1 Likith Kumar 197609 0 Apr 17 19:12 index2.html
-rw-r--r-- 1 Likith Kumar 197609 0 Apr 17 19:12 index3.html
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo
$ git init
Initialized empty Git repository in C:/Users/Likith Kumar/MITdemo/.git/
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (master)
$ git add .
warning: in the working copy of 'index.html', LF will be replaced by CRLF the next time Git
touches it
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (master)
$ git commit -m "Initial Commit"
[master (root-commit) 0b3c527] Initial Commit
3 files changed, 1 insertion(+)
create mode 100644 index.html

create mode 100644 index2.html
create mode 100644 index3.html
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (master)
$ git remote add origin https://github.com/LikithKumar0112/Mod1P1-Demo.git
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (master)
$ git branch -M main
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (main)
$ git push -u origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 311 bytes | 155.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/LikithKumar0112/Mod1P1-Demo.git
* [new branch] main -> main
branch 'main' set up to track 'origin/main'.
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (main)
$

#2
Likith Kumar@DESKTOP-8N6978G MINGW64 ~
$ git clone https://github.com/LikithKumar0112/Mod1P1-Demo.git
Cloning into 'Mod1P1-Demo'...
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 4 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (4/4), done.
Likith Kumar@DESKTOP-8N6978G MINGW64 ~
$ git branch -m master
fatal: not a git repository (or any of the parent directories): .git
Likith Kumar@DESKTOP-8N6978G MINGW64 ~
$ cd MITdemo
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (main)
$ git branch -m master
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (master)
$ git branch ls
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (master)
$ git branch
ls
* master
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (master)
$ git branch -a
ls
* master
remotes/origin/main
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (master)
$ git rebase master
Current branch master is up to date.
Likith Kumar@DESKTOP-8N6978G MINGW64 ~/MITdemo (master)
$


#3
pipeline {
agent any
stages {
stage('Clone Repository') {
steps {
git branch: 'main',
url: 'https://github.com/your-username/your-repo.git'
}
}
stage('Status') {
steps {
echo "Sucessfully fetched the repo"
}
}

#4
pipeline {
agent any
tools {
maven 'Maven-3'
}
stages {
stage('Checkout') {
steps {
git branch: 'main', url: 'https://github.com/LikithKumar0112/Jenkins-demo.git'
}
}
stage('Build') {
steps {
sh 'mvn clean compile'
}
}
stage('Test') {
steps {
sh 'mvn test'
}
}
stage('Package') {
steps {
sh 'mvn package'
}
}
}
}
#5
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
print("Starting Test...")
driver = webdriver.Chrome()
print("Opening Google...")
driver.get("https://www.google.com")
print("Locating search box...")
search = driver.find_element(By.NAME, "q")
print(" Typing 'MIT college'...")
search.send_keys("MIT college")
search.send_keys(Keys.RETURN)
print("Search executed successfully!")
input("Press ENTER to close the browser...")
print("Closing browser...")
driver.quit()
print("Test Completed!")

Output:
Run: python3 test_google2.py
🚀 Starting Test...
🌐 Opening Google...
🔍 Locating search box...
⌨️ Typing 'MIT college'...
✅ Search executed successfully!
⏸️ Press ENTER to close the browser...
🛑 Closing browser...
🎉 Test Completed!
#6
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time
print("Continuous XPath Search Demo Starting...")
driver = webdriver.Chrome()
driver.get("https://www.google.com")
time.sleep(3)
search_terms = [
"XPath examples",
"Selenium XPath tutorial",
"XPath contains example"
]
for term in search_terms:
print(f" Searching for: {term}")
# Always re-find element fresh (important)
search = driver.find_element(By.NAME, "q")
# Clear properly
search.clear()
time.sleep(1)
# Type slowly (avoid bot detection)
for char in term:
search.send_keys(char)
time.sleep(0.1)
time.sleep(1)
search.send_keys(Keys.RETURN)
print("Search executed")
time.sleep(5)
# Go back to Google homepage (IMPORTANT FIX)
driver.get("https://www.google.com")

time.sleep(3)

input("Press ENTER to close browser...")
driver.quit()

Output:
run python3 test_xpath.py
Continuous XPath Search Demo Starting...
Searching for: XPath examples
Search executed
Searching for: Selenium XPath tutorial
Search executed
Searching for: XPath contains example
Search executed
Press ENTER to close browser...

#7
pipeline {
agent any
tools {
maven 'M3'
}
stages {
stage('Checkout') {
steps {
git branch: 'master',
url: 'https://github.com/AravindRohit/simple-java-project'
}
}
stage('Build') {
steps {
sh 'mvn clean package -DskipTests'
}
}
stage('Test') {
steps {
sh 'mvn test'
}
}
}
}
#8
# application file
from flask import Flask
app = Flask(__name__)

@ flask main.py file
from app import app
@app.route('/')
def home():
return 'Hello from Docker! Flask app is running inside a container.'
@app.route('/health')
def health():
return 'OK', 200
if __name__ == '__main__':
app.run(host='0.0.0.0', port=5000)

# dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "main.py"]

# requirements file
flask==2.3.2
#9
#10
