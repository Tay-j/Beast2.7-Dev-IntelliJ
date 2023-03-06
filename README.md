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

![image](https://user-images.githubusercontent.com/52638982/222627863-14ca2f97-433c-4252-8546-e58a2c488d5b.png)

Set the JDK to Zulu 17

![image](https://user-images.githubusercontent.com/52638982/220499283-1814a99e-15e4-43b2-b254-7a93bff2e63b.png)

### Create global libraries for beast2, beast2 junit test, and BeastFX
 
`File > Project Structure > Global Libraries > + > Java` or `Ctrl+Alt+Shift+S`

![image](https://user-images.githubusercontent.com/52638982/222628023-6442000a-9269-4a91-a8eb-fa9bd2645ff0.png)

![image](https://user-images.githubusercontent.com/52638982/222628784-48577171-6f6f-494d-8c9d-41eb42bd30ba.png)

Select all files under `BeastFX/locallib`

![image](https://user-images.githubusercontent.com/52638982/221716049-42a22750-354e-47dd-aefd-7e337b361479.png)

![image](https://user-images.githubusercontent.com/52638982/220791714-61746b8f-2f9a-4742-8d42-7b80e83a5ff7.png)

Rename the library to `b2fx-lib`

Select the `beast2/lib` directory

![image](https://user-images.githubusercontent.com/52638982/220791866-2b020e51-7c17-4b1d-ae36-8c3e3858be5a.png)

Rename the library to `b2-lib`

Select the `beast2/junit` directory

![image](https://user-images.githubusercontent.com/52638982/220791809-50d939b9-5cdb-4567-9708-14fbb9957360.png)

Rename the library to `b2-junit`

## Configure modules and dependencies

`File > Project Structure` 

![image](https://user-images.githubusercontent.com/52638982/220517701-6ca74881-ce05-4e8e-bc98-2682ebee69a8.png)

Import the module beast2 by selecting the directory, selecting next.

In the Libraries window, edit change 'lib' to 'beast-lib' and untick DensiTree.

`Modules > + > Import Module`

Import BeastFX with the same procedure 

![image](https://user-images.githubusercontent.com/52638982/220517805-44af65bc-d9a3-45f2-978e-c471ba370566.png)

### beast2

`File > Project Structure > Modules > beast2 > Sources`

Select test folder and mark as `Tests`

![image](https://user-images.githubusercontent.com/52638982/220792547-a88afd85-0924-444d-a531-a3180ff5a35f.png)

`File > Project Structure > Modules > beast2 > Dependencies`

Add the beast2 library and beast2 junit test library, setting `Scope` to `Compile`.

`+ > 2 Library > Global Libraries`

![image](https://user-images.githubusercontent.com/52638982/220792674-82b32053-6d07-40d4-8b78-820af9c8a458.png)


### BeastFX

`File > Project Structure > Modules > BeastFX > Sources`

Select src/test folder and mark as `Tests`

![image](https://user-images.githubusercontent.com/52638982/220792971-afeb4c6e-ba5b-4b98-a350-9805a8bdaaff.png)

`File > Project Structure > Modules > BeastFX > Dependencies`

Add a `Module Dependency` for `beast2` and the BeastFX library, setting `Scope` to `Compile`.

![image](https://user-images.githubusercontent.com/52638982/220793088-12622f77-4fcc-486a-8c9a-dff8f1236d5c.png)

## Beauti debug

In the `Project` tab, navigate to `BeastFX > src > beastfx.app > beauti` and select `Beauti`.

Right click `Beauti` and select `Modify Run Configuration`. 

![image](https://user-images.githubusercontent.com/52638982/222629839-f38a89a2-75e9-40dc-b26b-845012c83c16.png)


![image](https://user-images.githubusercontent.com/52638982/220799073-0f28c854-5fde-4c39-96ae-345b14cc8444.png)

To run `Beauti`, `Run > Debug > Beauti`.

![image](https://user-images.githubusercontent.com/52638982/222630065-be606b8d-eaf2-428b-90a9-eb8da74f6f49.png)


## beastMCMC debug

In the `Project` tab, navigate to `BeastFX > src > beastfx.app > beast` and select `BeastMCMC`.

Right click `BeastMCMC` and select `Modify Run Configuration`. 

In `Program Arguments`, locate the xml you wish to run, e.g. `src/testHKY.xml`

![image](https://user-images.githubusercontent.com/52638982/222629355-98e4bab0-0ae3-4148-b8cf-8c848f4e8728.png)

To run `Beast2`, `Run > Debug > BeastMCMC`.

## TreeStat

```
cd ~/intellij
git clone https://github.com/alexeid/TreeStat2
```

`File > Project Structure > Modules > + > Import Module > TreeStat2`

![image](https://user-images.githubusercontent.com/52638982/223002633-a24d9ab3-0122-469f-a3b1-bf6eb0726e0b.png)

To run `TreeStat2`, `Run > Debug > TreeStatApp`.
