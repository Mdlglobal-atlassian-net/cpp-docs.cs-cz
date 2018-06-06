---
title: Vlastnosti stránky XML pravidlo soubory | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcee2c416fba6a959785826781aefd96b0d06d75
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339641"
---
# <a name="property-page-xml-rule-files"></a>Soubory pravidlo XML stránky vlastností
Soubory XML ve složce VCTargets jsou nakonfigurované na stránkách vlastností projektu v prostředí IDE. Přesnou cestu závisí na které edition(s) sady Visual Studio jsou nainstalované a jazyk produktu. Pro Visual Studio 2017 Enterprise Edition, v angličtině, cesta je `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Soubory XML popisují názvy pravidel, kategorie a jednotlivé vlastnosti, jejich datový typ, výchozí hodnoty, a způsob jejich zobrazení. Když nastavíte vlastnost v prostředí IDE, nová hodnota je uložena v souboru projektu.

Jenom scénáře, ve kterých je potřeba pochopit, že jste do interní chodu tyto soubory a Visual Studio IDE (a) si chcete vytvořit vlastní stránka vlastností, nebo (b) chcete upravit vlastnosti projektu tak, že některé způsobem než prostřednictvím prostředí Visual Studio IDE. 

Nejprve umožňuje otevření stránek vlastností pro projekt (klikněte pravým tlačítkem na uzel projektu v **Průzkumníku řešení** a vyberte možnost Vlastnosti):
   
![Vlastnosti projektu Visual C++](media/cpp-property-page-2017.png)

Každý uzel v rámci **vlastnosti konfigurace** se označuje jako pravidlo. Pravidlo někdy představuje jeden nástroje, jako je kompilátor, ale obecně výraz odkazuje na něco, co má vlastnosti, která spustí a který může vytvořit některé výstup. Každé pravidlo se naplní ze souboru xml ve složce VCTargets. Například C/C++ pravidlo, které se zobrazí nad nebude naplněn sadou 'cl.xml'.

Jako v příkladu nahoře, každé pravidlo obsahuje sadu vlastností, které jsou uspořádány do kategorií. Každý dílčí uzel v části pravidla představuje kategorii. Například k optimalizaci uzlu pod C/C++ obsahuje všechny související optimalizace vlastnosti nástroj kompilátoru. Ve formátu mřížky v pravém podokně se vykreslují vlastnosti a jejich hodnoty sami.

Cl.xml můžete otevřít v programu Poznámkový blok nebo editoru XML (viz snímku níže). Zobrazí se kořenový uzel s názvem pravidla, která má stejný seznam vlastnosti definované v něm, jak se zobrazí v uživatelském rozhraní, společně s další metadata.

```xml  
<?xml version="1.0" encoding="utf-8"?>
<!--Copyright, Microsoft Corporation, All rights reserved.-->
<Rule Name="CL" PageTemplate="tool" DisplayName="C/C++" SwitchPrefix="/" Order="10" xmlns="http://schemas.microsoft.com/build/2009/properties" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.Categories>
    <Category Name="General" DisplayName="General" />
    <Category Name="Optimization" DisplayName="Optimization" />
    <Category Name="Preprocessor" DisplayName="Preprocessor" />
    <Category Name="Code Generation" DisplayName="Code Generation" />
    <Category Name="Language" DisplayName="Language" />
    <Category Name="Precompiled Headers" DisplayName="Precompiled Headers" />
    <Category Name="Output Files" DisplayName="Output Files" />
    <Category Name="Browse Information" DisplayName="Browse Information" />
    <Category Name="Advanced" DisplayName="Advanced" />
    <Category Name="All Options" DisplayName="All Options" Subtype="Search" />
    <Category Name="Command Line" DisplayName="Command Line" Subtype="CommandLine" />
  </Rule.Categories>
...
``` 

Neexistuje jeden soubor XML odpovídající každý uzel v části Vlastnosti konfigurace na stránkách vlastností uživatelského rozhraní. Můžete přidat nebo odebrat pravidla v uživatelském rozhraní, včetně nebo odebráním umístění pro soubory odpovídající XML v projektu. Jedná se například jak Microsoft.CppBuild.targets (o jednu úroveň výš ze složky 1033) zahrnuje cl.xml:

```xml  
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>

``` 
Pokud jste pruhu cl.xml všechna data, budete mít s následující šablonou:
```xml  
<?xml version="1.0" encoding="utf-8"?>
<Rule>
  <Rule.DataSource />
  <Rule.Categories>
    <Category />
        ...
  </Rule.Categories>
  <BoolProperty />
  <EnumProperty />
  <IntProperty />
  <StringProperty />
  <StringListProperty />
</Rule>
``` 

Následující část popisuje každou hlavní prvky a některé z metadat, které lze připojit k nim.

1. **Pravidlo:** pravidlo je obecně kořenového uzlu v souboru xml; může mít mnoho atributů:

```xml    
<Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
          xmlns="http://schemas.microsoft.com/build/2009/properties"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.DisplayName>
    <sys:String>C/C++</sys:String>
  </Rule.DisplayName>
```  

   a. **Název:** id pravidla je atribut Name. Musí se jednat o jedinečný mezi všechny vlastnosti stránky soubory xml pro projekt.

   b. **PageTemplate:** hodnota tohoto atributu je používané uživatelského rozhraní vybrat z kolekce šablon uživatelského rozhraní. Šablonu "tool" vykreslí vlastností ve formátu standardní mřížky. Ostatní hodnoty v vytvořená pro tento atribut jsou "ladicí program" a "Obecné". Další informace najdete v ladění uzel a obecné uzel, v uvedeném pořadí, najdete v části formát uživatelského rozhraní vyplývající z zadání těchto hodnot. Uživatelské rozhraní pro šablony "ladicí program" stránka používá rozevíracího seznamu pro přepínání vlastnosti různých ladicí programy, zatímco "Obecné" šablony zobrazí kategorie jinou vlastnost vše na jedné stránce oproti s více uzly dílčí kategorie v rámci pravidlo uzel. Tento atribut je právě návrhu rozhraní; soubor xml je navržený jako uživatelského rozhraní, které jsou nezávislé. Různé uživatelského rozhraní může použít tento atribut pro jiné účely.

  c. **SwitchPrefix:** Toto je Předpona použitá v příkazovém řádku přepínače. Hodnota "/" by způsobilo přepínače, které vypadají/zi, / nologo, /W3 atd.

  d. **Pořadí:** to se označuje návrh na potenciální uživatelského rozhraní klienta na relativní umístění tohoto pravidla ve srovnání s jinými pravidly v systému.

  e. **atribut xmlns:** jde standardní element XAML. Můžete zobrazit tři obory názvů uvedené. Tyto obory názvů pro deserializaci XAML odpovídají třídy, schéma a systému oboru názvů jazyka XAML, v uvedeném pořadí.

  f. **DisplayName:** Toto je název, který se zobrazí na stránce vlastností uživatelského rozhraní pro pravidlo uzel. Tato hodnota je lokalizované. Jsme vytvořili DisplayName jako podřízený element pravidla a nikoli jako atribut (např. název nebo SwitchPrefix) z důvodu vnitřní lokalizace požadavky na nástroj. Z hlediska XAML pro obě jsou ekvivalentní. Ano je možné vytvořit ji atribut přehlednost nebo necháte, protože se jedná.

  g. **Zdroj dat:** to je velmi důležité vlastnost, která informuje systém projektu umístění, ze kterého by měla hodnotu vlastnosti číst z a zapisovat do a jeho seskupování (vysvětlení níže). Pro cl.xml jsou tyto hodnoty:

```xml  
       <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
```  
   - `Persistence="ProjectFile` informuje o všech vlastnostech pro pravidlo, které mají být zapsána do souboru projektu systému projektu nebo soubor seznamu vlastností (v závislosti na uzlu byla použita k spawn – stránky vlastností). Možná hodnota je "UserFile", která hodnotu zapíše do souboru .uživatel.

   - `ItemType="ClCompile"` uvádí, že vlastnosti se uloží jako ItemDefinition metadata nebo metadata položky (k tomu jenom v případě, že byly stránek vlastností vytvořený z uzlu soubor v Průzkumníku řešení) tohoto typu položky. Pokud toto pole není nastavena, je vlastnost zapisují jako běžnou vlastností v PropertyGroup.

   - `Label=""` informuje, že při vlastnosti se zapisují jako `ItemDefinition` metadata, bude popisek nadřazené ItemDefinitionGroup prázdný (každý element MSBuild může mít štítek). Visual Studio 2017 používá s popiskem skupiny přejděte VCXPROJ souboru projektu. Všimněte si, zda mají skupiny, které obsahují většinu vlastností pravidla prázdný řetězec jako popisek.

   - `HasConfigurationCondition="true"` říká systému projektu připojovat podmínku konfigurace na hodnotu tak, že bude platit pouze pro aktuální konfigurací projektu (podmínka může být umístěny do nadřazené skupiny nebo vlastní hodnota). Například otevření stránek vlastností projektu uzel a nastavte hodnotu vlastnosti **považovat upozornění jako chyby** pod **vlastnosti konfigurace > C/C++ Obecné** "Ano". Následující hodnota je zapsán do souboru projektu. Všimněte si, podmínku konfigurace připojené k nadřazené ItemDefinitionGroup.

```xml  
     <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
           <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
     </ItemDefinitionGroup>
 ```
   Pokud tato hodnota nastavená na stránce vlastností pro konkrétní soubor, jako je například stdafx.cpp, hodnota vlastnosti by byla zapsána v položce stdafx.cpp v souboru projektu jak je uvedeno níže. Všimněte si, jak podmínku konfigurace přímo připojené k metadata sám sebe.

 ```xml  
<ItemGroup>
   <ClCompile Include="stdafx.cpp">
      <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
   </ClCompile>
</ItemGroup>
 ```
   Jiný atribut **DataSource** nejsou uvedené výše je **PersistedName**. Tento atribut slouží k představovat vlastnost v souboru projektu s jiným názvem. Ve výchozím nastavení je tento atribut hodnotu vlastnosti **název**. 

   Jednotlivé vlastnosti můžete přepsat nadřazené pravidlo DataSource. V takovém případě bude umístění pro tuto vlastnost hodnota liší od dalších vlastností v pravidle.

   h. Existují další atributy pravidlo například popis, SupportsFileBatching atd., které nejsou zobrazeny zde. Je možné získat úplnou sadu atributů, které se vztahuje na pravidlo nebo na jakýkoli další prvek procházení v dokumentaci pro tyto typy. Alternativně můžete zkontrolovat veřejné vlastnosti na typy v `Microsoft.Build.Framework.XamlTypes` oboru názvů v `Microsoft.Build.Framework .dll` sestavení.

   i. **DisplayName**, **PageTemplate**, a **pořadí** jsou vlastnosti související s uživatelského rozhraní, které se nacházejí v tomto jinak nezávislé uživatelského rozhraní datového modelu. Tyto vlastnosti jsou téměř určité má být používána žádné uživatelské rozhraní, které se používá k zobrazení stránky vlastností. **DisplayName** a **popis** jsou dvě vlastnosti, které se nacházejí na téměř všechny elementy v souboru xml. Jsou to jenom dva vlastnosti, které jsou lokalizované (lokalizace tyto řetězce bude podrobně novější post).

2.  **Kategorie:** pravidlo může mít více kategorií. Pořadí, ve kterém jsou uvedeny kategorie v souboru xml je návrh do rozhraní k zobrazení kategorií ve stejném pořadí. Například pořadí kategorií pod uzlem C/C++, jak je vidět v uživatelském rozhraní – Obecné, optimalizace, preprocesor,...  – je stejný jako tento v cl.xml. Ukázka kategorie vypadá takto:

```xml  
 <Category Name="Optimization">
    <Category.DisplayName>
        <sys:String>Optimization</sys:String>
    </Category.DisplayName>
 </Category>
```
Výše uvedené fragment kódu ukazuje **název** a **DisplayName** atributy, které bylo popsané před. Ještě jednou, existují další atributy **kategorie** může mít nepoužívají výše. Můžete víte o nich přečíst v dokumentaci nebo tak, že prověří sestavení pomocí ildasm.exe.

3. **Vlastnosti:** Toto je maso souboru xml a obsahuje seznam všech vlastností v tomto pravidle. Každá vlastnost může být jeden z pěti možné typy uvedené v XAML kostru výše. Samozřejmě můžete mít jenom některé z těchto typů v souboru. Vlastnost má několik atributů, které aby ji bylo možné bohatě popsané. I objasníme pouze **StringProperty** sem. Zbývající jsou velmi podobné.

```xml  
<StringProperty Subtype="file" Name="ObjectFileName" Category="Output Files" Switch="Fo">
  <StringProperty.DisplayName>
    <sys:String>Object File Name</sys:String>
  </StringProperty.DisplayName>
  <StringProperty.Description>
    <sys:String>Specifies a name to override the default object file name; can be file or directory name.(/Fo[name])</sys:String>
  </StringProperty.Description>
</StringProperty>
```
Před doporučené většinu atributy v tomto fragmentu kódu. Nové jsou podtypem, kategorie a přepínače.

   a. **Podtyp** je k dispozici pouze pro atribut **StringProperty** a **StringListProperty**; nabízí kontextové informace. Například hodnota "soubor" označuje, že vlastnost představuje cestu k souboru. Tyto kontextové informace slouží k vylepšení úpravy prostředí tím, že poskytuje Průzkumník Windows jako vlastnosti editor, který umožňuje uživateli vybrat soubor vizuálně.

   b. **Kategorie:** to deklaruje kategorie, pod kterým tato vlastnost spadá. Zkuste najít tuto vlastnost pod **výstupní soubory** kategorie v uživatelském rozhraní.

   c. **Přepínač:** když pravidlo představuje nástroj – například nástroj kompilátoru v tomto případě – většinu vlastností pravidla jsou předány jako přepínače v nástroji spustitelný soubor v době sestavení. Hodnota tohoto atributu označuje přepínač literál, který se má použít. Vlastnost výše Určuje, že by měl být jeho přepínač **Fo**. V kombinaci s **SwitchPrefix** atributu v nadřazené pravidlo, tato vlastnost je předána ke spustitelnému souboru jako **/Fo "ladění\"**  (viditelné v příkazovém řádku pro C/C++ na stránce vlastností uživatelského rozhraní).

   Ostatní atributy vlastnost patří:

   d. **Viditelný:** Pokud z nějakého důvodu nechcete, aby vaše vlastnost zobrazena v stránky vlastností (ale stále pravděpodobně k dispozici v době sestavení), nastavte tento atribut na hodnotu false.

   e. **Jen pro čtení:** Pokud byste chtěli poskytnout zobrazení jen pro čtení hodnoty této vlastnosti na stránkách vlastností, tento atribut nastavit na hodnotu true.

   f. **IncludeInCommandLine:** některé vlastnosti nemusí být nutné mají být předány nástroj během okamžiku sestavení. Nastavení tohoto atributu na hodnotu false zabraňují předávány.


