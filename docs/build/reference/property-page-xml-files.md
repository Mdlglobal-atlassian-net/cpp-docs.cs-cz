---
title: Soubory pravidel XML stránky vlastností
ms.date: 05/06/2019
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
ms.openlocfilehash: 76378dc5ef9d7443045c329579cfa3c410dc262f
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630744"
---
# <a name="property-page-xml-rule-files"></a>Soubory pravidel XML stránky vlastností

Stránky vlastností projektu v integrovaném vývojovém prostředí jsou konfigurovány pomocí souborů XML ve složce VCTargets. Přesná cesta závisí na tom, jaké edice sady Visual Studio jsou nainstalovány a jazyk produktu. V případě sady Visual Studio 2019 Enterprise Edition je `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033`cesta v angličtině. Soubory XML popisují názvy pravidel, kategorie a jednotlivé vlastnosti, jejich datový typ, výchozí hodnoty a způsob jejich zobrazení. Při nastavení vlastnosti v integrovaném vývojovém prostředí je nová hodnota uložena v souboru projektu.

Jedinými scénáři, ve kterých potřebujete pochopit interní pracovní postupy těchto souborů a integrované vývojové prostředí (IDE) sady Visual Studio, je vytvořit vlastní stránku vlastností, nebo (b) chcete přizpůsobit vlastnosti projektu jiným způsobem než prostřednictvím integrovaného vývojového prostředí sady Visual Studio.

Nejprve otevřete stránky vlastností projektu (klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte vlastnosti):

![Visual Studio C++ Project Properties](../media/cpp-property-page-2017.png)

Každý uzel v části **Vlastnosti konfigurace** se nazývá pravidlo. Pravidlo může někdy představovat jeden nástroj jako kompilátor, ale obecně platí, že se jedná o něco, co má vlastnosti, které se spustí a který může vytvořit nějaký výstup. Každé pravidlo je vyplněné ze souboru XML ve složce VCTargets. Například C/C++ pravidlo, které je uvedeno výše, je vyplněno "CL. XML".

Jak je uvedeno výše, každé pravidlo obsahuje sadu vlastností, které jsou uspořádány do kategorií. Každý dílčí uzel v rámci pravidla představuje kategorii. Například uzel optimalizace pod položkou C/C++ obsahuje všechny vlastnosti, které souvisí s optimalizací nástroje kompilátoru. Vlastnosti a jejich hodnoty samy se vykreslují v tabulkovém formátu v pravém podokně.

Soubor CL. XML můžete otevřít v programu Poznámkový blok nebo editoru XML (viz snímek níže). Zobrazí se kořenový uzel s názvem Rule, který má v uživatelském rozhraní stejný seznam vlastností, jak je zobrazen v uživatelském rozhraní společně s dalšími metadaty.

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

Existuje jeden soubor XML odpovídající každému uzlu v části vlastnosti konfigurace v uživatelském rozhraní stránky vlastností. V uživatelském rozhraní můžete přidat nebo odebrat pravidla zahrnutím nebo odebráním umístění do odpovídajících souborů XML v projektu. Například to znamená, že Microsoft. CppBuild. TARGETS (jedna úroveň ze složky 1033) zahrnuje CL. XML:

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

Pokud provedete proložení souboru CL. XML všech dat, skončíte s následujícím kostrou:

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

Následující část popisuje jednotlivé hlavní prvky a některá metadata, která se jim dají připojit.

1. **Pravidlo**  Pravidlo je obecně kořenový uzel v souboru XML; může mít mnoho atributů:

    ```xml
    <Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
              xmlns="http://schemas.microsoft.com/build/2009/properties"
              xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
              xmlns:sys="clr-namespace:System;assembly=mscorlib">
      <Rule.DisplayName>
        <sys:String>C/C++</sys:String>
      </Rule.DisplayName>
    ```

   a. **Jméno:** Atribut Name je identifikátor pro pravidlo. Musí být jedinečný mezi všemi soubory XML stránky vlastností pro projekt.

   b. **PageTemplate:** Hodnota tohoto atributu se používá v uživatelském rozhraní k výběru z kolekce šablon uživatelského rozhraní. Šablona nástroje vykresluje vlastnosti ve formátu standardní mřížky. Další sestavené hodnoty tohoto atributu jsou "Debugger" a "Generic". Pro zobrazení formátu uživatelského rozhraní, které je výsledkem zadání těchto hodnot, se podívejte na uzel ladění a obecný uzel. Uživatelské rozhraní pro šablonu stránky "Debugger" používá rozevírací nabídku pro přepínání mezi vlastnostmi různých ladicích programů, zatímco "Obecná" Šablona zobrazuje různé kategorie vlastností, které jsou všechny na jedné stránce, na rozdíl od jejich použití v rámci pravidla více podřízených uzlů kategorií. uzlu. Tento atribut je pouze návrhem uživatelského rozhraní. soubor XML je navržený tak, aby byl nezávislý na uživatelském rozhraní. Jiné uživatelské rozhraní může použít tento atribut pro různé účely.

   c. **SwitchPrefix:** Toto je předpona, která se používá na příkazovém řádku pro přepínače. Hodnota "/" by vedla k přepínačům, které vypadají jako/ZI,/nologo,/W3 atd.

   d. **Za** Toto je návrh pro potenciálního klienta uživatelského rozhraní na relativním umístění tohoto pravidla v porovnání se všemi ostatními pravidly v systému.

   e. **xmlns** Toto je standardní prvek XAML. Můžete vidět tři obory názvů uvedené. Tyto hodnoty odpovídají oborům názvů pro třídy deserializace XAML, schéma XAML a obor názvů System v uvedeném pořadí.

   f. **DisplayName** Toto je název, který se zobrazuje v uživatelském rozhraní stránky vlastností uzlu pravidla. Tato hodnota je lokalizovaná. V důsledku požadavků na nástroj pro interní lokalizaci jsme vytvořili DisplayName jako podřízený element pravidla, nikoli jako atribut (jako je název nebo SwitchPrefix). Z perspektivy XAML jsou oba ekvivalenty. To znamená, že je možné pouze vytvořit atribut, který omezí přehlednost nebo ponechá ho tak, jak je.

   g. **Datového** Jedná se o velmi důležitou vlastnost, která oznamuje systému projektu umístění, ze kterého by měla být hodnota vlastnosti čtena a zapsána do a její seskupení (vysvětlení níže). Pro CL. XML jsou tyto hodnoty:

      ```xml
      <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
      ```

   - `Persistence="ProjectFile`oznamuje systému projektu, že všechny vlastnosti pro pravidlo by měly být zapsány do souboru projektu nebo do souboru seznamu vlastností (v závislosti na tom, který uzel byl použit k vytvoření stránky vlastností). Další možnou hodnotou je "UserFile", která zapíše hodnotu do souboru. User.

   - `ItemType="ClCompile"`říká, že vlastnosti budou uloženy jako metadata ItemDefinition nebo metadata položky (za druhé, pokud byly stránky vlastností vytvořeny z uzlu souboru v Průzkumníku řešení) tohoto typu položky. Pokud toto pole není nastaveno, vlastnost je zapsána jako společná vlastnost ve vlastnosti skupiny.

   - `Label=""`označuje, že pokud jsou vlastnosti zapsány jako `ItemDefinition` metadata, bude popisek nadřazeného ItemDefinitionGroup prázdný (každý prvek MSBuild může mít popisek). Visual Studio 2017 a novější používá k procházení souboru projektu vcxproj skupiny s popisky. Všimněte si, že skupiny, které obsahují většinu vlastností pravidla, mají jako popisek prázdný řetězec.

   - `HasConfigurationCondition="true"`oznamuje systému projektu, aby připojil podmínku konfigurace k hodnotě tak, aby se projevil pouze pro aktuální konfiguraci projektu (podmínka může být připojena k nadřazené skupině nebo samotné hodnotě). Otevřete například stránky vlastností mimo uzel projektu a nastavte hodnotu vlastnosti **zpracovat upozornění jako chybu** v části **Vlastnosti konfigurace > CC++ /obecné** na "Ano". Následující hodnota je zapsána do souboru projektu. Všimněte si konfigurační podmínky připojené k nadřazenému ItemDefinitionGroup.

      ```xml
      <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
          <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
      </ItemDefinitionGroup>
      ```

      Pokud byla tato hodnota nastavena na stránce vlastností konkrétního souboru, například stdafx. cpp, pak bude hodnota vlastnosti zapsána do položky *stdafx. cpp* v souboru projektu, jak je znázorněno níže. Všimněte si, jak je konfigurační podmínka přímo připojena k samotným metadatům.

      ```xml
      <ItemGroup>
        <ClCompile Include="stdafx.cpp">
          <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
        </ClCompile>
      </ItemGroup>
      ```

   Další atribut **zdroje dat** , který není uveden výše, je **PersistedName**. Tento atribut lze použít k reprezentaci vlastnosti v souboru projektu s použitím jiného názvu. Ve výchozím nastavení je tento atribut nastaven na **název**vlastnosti.

   Jednotlivá vlastnost může přepsat své nadřazené pravidlo. V takovém případě bude hodnota této vlastnosti odlišná od ostatních vlastností v pravidle.

   h. Existují další atributy pravidla, včetně Description a SupportsFileBatching, které zde nejsou uvedeny. Úplnou sadu atributů vztahujících se na pravidlo nebo na jakýkoli jiný element lze získat procházením dokumentace pro tyto typy. Alternativně můžete prozkoumávat veřejné vlastnosti na typech v `Microsoft.Build.Framework.XamlTypes` oboru názvů `Microsoft.Build.Framework .dll` v sestavení.

   i. **DisplayName**, **PageTemplate**a **Order** jsou vlastnosti související s uživatelským rozhraním, které jsou k dispozici v tomto jiném datovém modelu nezávislém na uživatelském rozhraní. Tyto vlastnosti jsou skoro určité, aby je bylo možné použít v jakémkoli uživatelském rozhraní, které se používá k zobrazení stránek vlastností. **DisplayName** a **Description** jsou dvě vlastnosti, které jsou k dispozici na téměř všech prvcích v souboru XML. A jsou to jediné dvě vlastnosti, které jsou lokalizovány (lokalizace těchto řetězců bude vysvětleno v pozdějším příspěvku).

1. **Kategorií** Pravidlo může mít několik kategorií. Pořadí, ve kterém jsou kategorie uvedeny v souboru XML, je návrh uživatelského rozhraní k zobrazení kategorií ve stejném pořadí. Například pořadí kategorií pod uzlem C/C++ uzlu, jak je vidět v uživatelském rozhraní – Obecné, optimalizace, preprocesor,...  – je stejná jako v souboru CL. XML. Vzorová kategorie vypadá takto:

    ```xml
    <Category Name="Optimization">
      <Category.DisplayName>
        <sys:String>Optimization</sys:String>
      </Category.DisplayName>
    </Category>
    ```

   Výše uvedený fragment kódu ukazuje atributy **Name** a **DisplayName** , které byly popsány dříve. Potom existují další atributy, které **kategorie** může mít, které se nepoužívají výše. O tom, jak o nich získat informace, si můžete přečíst v dokumentaci nebo prozkoumáním sestavení pomocí programu Ildasm. exe.

1. **Vlastnosti** Toto je maso souboru XML a obsahuje seznam všech vlastností v tomto pravidle. Každá vlastnost může být jedním z pěti možných typů, které jsou uvedeny v kostre XAML výše. V souboru samozřejmě můžete mít jenom pár těchto typů. Vlastnost má několik atributů, které umožňují, aby byly popsány v bohatě. Vysvětlete jenom **StringProperty** . Zbytek je velmi podobný.

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

   Většina atributů ve fragmentu kódu byla popsána dříve. Nové jsou typu podtyp, kategorie a přepínač.

   a. **Podtyp** je atribut dostupný pouze pro **StringProperty** a **StringListProperty**; poskytuje kontextové informace. Například hodnota "File" označuje, že vlastnost představuje cestu k souboru. Tyto kontextové informace se používají ke zlepšení prostředí pro úpravu pomocí Průzkumníka Windows jako editoru vlastnosti, který umožňuje uživateli vizuálně zvolit soubor.

   b. **Kategorií** Tato deklarace deklaruje kategorii, pod kterou tato vlastnost spadá. Zkuste najít tuto vlastnost v kategorii **výstupní soubory** v uživatelském rozhraní.

   c. **Přepnutí** Když pravidlo představuje nástroj, jako je například nástroj kompilátoru v tomto případě – většina vlastností pravidla se předává jako přepínače do spustitelného souboru nástroje během sestavení. Hodnota tohoto atributu označuje literál přepínače, který se má použít. Výše uvedená vlastnost určuje, že její přepínač by měl být **FO**. V kombinaci s atributem **SwitchPrefix** nadřazeného pravidla je tato vlastnost předána spustitelnému souboru jako **/FO\" "debug"** (viditelné v příkazovém řádku pro C/C++ v uživatelském rozhraní stránky vlastností).

   Mezi další atributy vlastností patří:

   d. **Zobrazeny** Pokud z nějakého důvodu nechcete, aby se vaše vlastnost zobrazovala na stránkách vlastností (ale pravděpodobně stále k dispozici během sestavení), nastavte tento atribut na false.

   e. **ReadOnly** Pokud chcete zadat zobrazení hodnoty této vlastnosti na stránce vlastností jen pro čtení, nastavte tento atribut na hodnotu true.

   f. **IncludeInCommandLine:** Některé vlastnosti nemusí být v průběhu sestavení předány nástroji. Nastavením tohoto atributu na hodnotu false zabráníte jeho předání.
