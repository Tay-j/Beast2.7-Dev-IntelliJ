# Beast2.7-Dev-IntelliJ
Developer tutorial for Beast 2.7.x using IntelliJ

## Required software
Create a directory for IntelliJ dev and clone BEAST2 and BEASTFX.
```
mkdir ~/intellij
cd ~/intellij
git clone https://github.com/CompEvol/beast2 # will get beast2.7
git clone https://github.com/CompEvol/BeastFX
```
Azul JDK 17 (Java 17)

https://www.azul.com/downloads/?version=java-17-lts&package=jdk-fx

IntelliJ IDE (Community Edition)

https://www.jetbrains.com/idea/download/

## Create Project
`File > New > Project`

Set the JDK to Zulu 17

![image](https://user-images.githubusercontent.com/52638982/220499283-1814a99e-15e4-43b2-b254-7a93bff2e63b.png)

## Configure modules and dependencies
`File > Project Structure` or `Ctrl+Alt+Shift+S`

![image](https://user-images.githubusercontent.com/52638982/220517701-6ca74881-ce05-4e8e-bc98-2682ebee69a8.png)

Import the module beast2 by selecting the directory

`Modules > + > Import Module`

Import BeastFX with the same procedure

![image](https://user-images.githubusercontent.com/52638982/220517805-44af65bc-d9a3-45f2-978e-c471ba370566.png)
