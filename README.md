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

This tutorial was set up using zulu17.42.19-ca-fx-jdk17.0.7-linux_x64. Versions 17.0.4 and 17.0.5 did not work and are not recommended.

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

![image](https://user-images.githubusercontent.com/52638982/228098503-93a9c877-4beb-407f-a36a-060057276d31.png)

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

For MyPackage, add `Module Dependency` for both the `beast2` and `BeastFX`.

![image](https://user-images.githubusercontent.com/52638982/228100669-f6e8603b-0614-41ed-aae4-759176770510.png)

## Beauti debug

In the `Project` tab, navigate to `BeastFX > src > beastfx.app > beauti` and select `Beauti`.

Right click `Beauti` and select `Modify Run Configuration`. 

![image](https://user-images.githubusercontent.com/52638982/223002867-23a7039b-8b1e-4480-81b1-f41a3c233860.png)

![image](https://user-images.githubusercontent.com/52638982/220799073-0f28c854-5fde-4c39-96ae-345b14cc8444.png)

To run `Beauti`, `Run > Debug > Beauti`.

![image](https://user-images.githubusercontent.com/52638982/223002803-ea996558-a9ac-4009-b866-3e7159414faa.png)

## BeastMCMC debug

In the `Project` tab, navigate to `BeastFX > src > beastfx.app > beast` and select `BeastMCMC`.

Right click `BeastMCMC` and select `Modify Run Configuration`. 

In `Program Arguments`, locate the xml you wish to run, e.g. `beast2/examples/testHKY.xml`

![image](https://user-images.githubusercontent.com/52638982/222629355-98e4bab0-0ae3-4148-b8cf-8c848f4e8728.png)

To run `Beast2`, `Run > Debug > BeastMCMC`.

Alternatively, use the same debug configuration for `BeastMain`, which will bring up a window where an xml file can be selected. 

## Implementing a new substitution model

We are implementing the F84 substitution model.

Create a new `Package` called `beast.base.evolution.substitutionmodel`.

Right click `src > New > Package`.

![image](https://user-images.githubusercontent.com/52638982/228110033-4e1d8e1a-ebb6-4cdb-8a32-c6b943a9ba60.png)

### Create F84 class

Right click `beast.base.evolution.substitutionmodel` and create a new `Java Class` called `F84`.

![image](https://user-images.githubusercontent.com/52638982/228110323-6408a516-959c-46cf-80c9-304800e73d72.png)

Open the `F84.java` class.

Add `extends SubstitutionModel.Base` after `F84`.

```
public class F84 extends SubstitutionModel.Base {

}
```

Click on 

![image](https://user-images.githubusercontent.com/52638982/228111587-bcfce93a-c5db-4722-9f11-563de7bd509d.png)

Select the error to declare `F84` and click on the light bulb `Show Quick Fixes`.

![image](https://user-images.githubusercontent.com/52638982/228112101-372b59f1-e973-4b72-946f-0147dce7b196.png)

Select `Implement Methods` and click `OK`, adding in unimplemented methods.

![image](https://user-images.githubusercontent.com/52638982/228112241-7c5f91ff-d1f3-4b2c-9600-b72c453f1700.png)

![image](https://user-images.githubusercontent.com/52638982/228112321-7b7b7c32-2b9d-4189-84f1-51c673adb934.png)

The `F84.java` file should now look like this

![image](https://user-images.githubusercontent.com/52638982/228112981-81c70bcc-59c5-424d-89d3-0b7de462f47e.png)

### Add k parameter

Add the `extends SubstitutionModel.Base` after the class name.

```
public class F84 extends SubstitutionModel.Base{

    public Input<RealParameter> kF84 = new Input<RealParameter>("kF84", "k parameter in the F84 model", Validate.REQUIRED);
```

To resolve the errors, `Import Class` for each unimplemented method.

![image](https://user-images.githubusercontent.com/52638982/228113403-7b8260a6-39ac-4c2a-8359-78f7e3f21e54.png)

The following declarations should have been added.

```
import beast.base.core.Input;
import beast.base.inference.parameter.RealParameter;
```

### Implementing the canHandleDataType method

```
@Override
public boolean canHandleDataType(DataType dataType) {
   if (dataType instanceof Nucleotide) {
     return true;
   }
   return false;
}
```

Add the unimplement method, inserting the following code.

```
import beast.base.evolution.datatype.Nucleotide;
```

### Implementing the getTransitionProbabilities method

Fill in the `getTransitionProbabilities` method with the following:

```
@Override
public void getTransitionProbabilities(Node node, double fStartTime, double fEndTime, double fRate, double[] matrix) {
       double[] freqs = frequencies.getFreqs();
       double freqA = freqs[0];
       double freqC = freqs[1];
       double freqG = freqs[2];
       double freqT = freqs[3];
       double freqR = freqA + freqG;
       double freqY = freqC + freqT;

       double k = kF84.get().getValue();
       double sumPiSquared = freqA*freqA + freqC*freqC + freqG*freqG + freqT*freqT;
       double sumPiRatios = freqA*freqA/freqR + freqC*freqC/freqY + freqG*freqG/freqR + freqT*freqT/freqY;
       double mu = (1.0 - sumPiSquared) + k*(1.0 - sumPiRatios);

       double distance = (fStartTime - fEndTime) * fRate;
       double expTerm = Math.exp(-mu * distance);
       double expTermK = Math.exp(-mu * distance * (k + 1.0));

       matrix[0]  = freqA + freqA*(1.0/freqR - 1.0)*expTerm + ((freqR - freqA)/freqR)*expTermK; //AA
       matrix[1]  = freqC*(1.0 - expTerm); //AC
       matrix[2]  = freqG + freqG*(1.0/freqR - 1.0)*expTerm - (freqG/freqR)*expTermK; //AG
       matrix[3]  = freqT*(1.0 - expTerm); //AT

       matrix[4]  = freqA*(1.0 - expTerm); //CA
       matrix[5]  = freqC + freqC*(1.0/freqY - 1.0)*expTerm + ((freqY - freqC)/freqY)*expTermK; //CC
       matrix[6]  = freqG*(1.0 - expTerm); //CG
       matrix[7]  = freqT + freqT*(1.0/freqY - 1.0)*expTerm - (freqT/freqY)*expTermK; //CT

       matrix[8]  = freqA + freqA*(1.0/freqR - 1.0)*expTerm - (freqA/freqR)*expTermK; //GA
       matrix[9]  = freqC*(1.0 - expTerm); //GC
       matrix[10] = freqG + freqG*(1.0/freqR - 1.0)*expTerm + ((freqR - freqG)/freqR)*expTermK; //GG
       matrix[11] = freqT*(1.0 - expTerm); //GT

       matrix[12] = freqA*(1.0 - expTerm); //TA
       matrix[13] = freqC + freqC*(1.0/freqY - 1.0)*expTerm - (freqC/freqY)*expTermK; //TC
       matrix[14] = freqG*(1.0 - expTerm); //TG
       matrix[15] = freqT + freqT*(1.0/freqY - 1.0)*expTerm + ((freqY - freqT)/freqY)*expTermK; //TT
}
```
### Add description and citation

Paste the following lines before the `F84` class:

```
@Description("F84 substitution model")

@Citation("Kishino, H., and M. Hasegawa. 1989. Evaluation of the maximum likelihood estimate of the evolutionary tree topologies from DNA sequence data, and the branching order in Hominoidea. Journal of Molecular Evolution 29:170-179.")
```

Import the `Description` class from `beast.base.core`.

![image](https://user-images.githubusercontent.com/52638982/228114673-7a00e519-6536-49a2-8508-857e550aae42.png)

Import the class for `Citation`.

Create a new `File` in `MyPackage` called `version.xml` and copy the following lines.

```
<package name="MyPackage" version="0.0.1">
    <depends on='BEAST.base' atleast='2.7.0'/>
    <depends on='BEAST.app' atleast='2.7.0'/>

    <service type="beast.base.evolution.datatype.DataType">
        <provider classname="beast.base.evolution.datatype.Nucleotide"/>
    </service>

    <service type="beast.base.core.BEASTInterface">
        <provider classname="beast.base.evolution.substitutionmodel.F84"/>
        <provider classname="beast.base.evolution.alignment.Alignment"/>
        <provider classname="beast.base.evolution.alignment.Sequence"/>
        
        <provider classname="beast.base.evolution.datatype.Nucleotide"/>
        
        <provider classname="beast.base.evolution.sitemodel.SiteModel"/>



        <provider classname="beast.base.evolution.tree.Tree"/>
        <provider classname="beast.base.evolution.tree.TreeHeightLogger"/>
        <provider classname="beast.base.evolution.tree.TreeParser"/>

        <provider classname="beast.base.evolution.tree.coalescent.ConstantPopulation"/>
        <provider classname="beast.base.evolution.tree.coalescent.RandomTree"/>
        
        <provider classname="beast.base.inference.Logger"/>
        <provider classname="beast.base.inference.CompoundDistribution"/>
        <provider classname="beast.base.inference.MCMC"/>
        <provider classname="beast.base.inference.Operator"/>
        <provider classname="beast.base.inference.parameter.RealParameter"/>
        <provider classname="beast.base.inference.distribution.Prior"/>
        <provider classname="beast.base.inference.distribution.OneOnX"/>
        <provider classname="beast.base.inference.util.ESS"/>

        <provider classname="beast.base.evolution.likelihood.TreeLikelihood"/>]

        <provider classname="beast.base.evolution.operator.ScaleOperator"/>
        <provider classname="beast.base.evolution.operator.SubtreeSlide"/>
        <provider classname="beast.base.evolution.operator.Uniform"/>
        <provider classname="beast.base.evolution.operator.Exchange"/>
        <provider classname="beast.base.evolution.operator.WilsonBalding"/>

        <provider classname="beast.base.evolution.substitutionmodel.Frequencies"/>    
    </service>
</package>
```

Right click `BeastMain` under `BeastFX > src > beastfx.app > beast > BeastMain` to `Modify Run Configuration`.

Set the classpath to `-cp MyPackage`.

Add the following snippet to program arguments in debug: `examples/F84.xml -version_file version.xml`

## TreeStat

In this next step we will run a beast2 package, treestat2, that is deployed through a a graphical user interface from the applauncher.
Note that the current version of TreeStat2 does not work with non-Mac devices (pending solution).

```
cd ~/intellij
git clone https://github.com/alexeid/TreeStat2
```

Import the TreeStat2 module and add the beast2 and BeastFX modules as depedencies.

`File > Project Structure > Modules > + > Import Module > TreeStat2`

![image](https://user-images.githubusercontent.com/52638982/228100866-6c7f7cb2-c82e-4e05-9f11-a505ba3745ba.png)

Create a debug configuration for TreeStat2.

![image](https://user-images.githubusercontent.com/52638982/223002719-37a5b7db-7a48-4949-9114-19607a337ad1.png)

To run `TreeStat2`, `Run > Debug > TreeStatApp`.
