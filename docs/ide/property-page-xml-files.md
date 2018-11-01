---
title: Soubory pravidlo XML stránky vlastností
ms.date: 04/27/2017
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
ms.openlocfilehash: 7c2ce82cf13b9999102c5ac6df42ccb601e4e729
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467233"
---
# <a name="property-page-xml-rule-files"></a>Soubory pravidlo XML stránky vlastností

Soubory XML ve složce VCTargets jsou nakonfigurované na stránkách vlastností projektu v integrovaném vývojovém prostředí. Přesnou cestu závisí na které edicím sady Visual Studio jsou nainstalované a jazyk produktu. Pro Visual Studio 2017 Enterprise Edition, v angličtině, že cesta je `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Soubory XML popisují názvy pravidel, kategorie a jednotlivé vlastnosti, jejich datový typ, výchozí hodnoty a jak mají být zobrazeny. Při nastavení vlastnosti v rozhraní IDE, nová hodnota je uložena v souboru projektu.

Chcete vytvořit vlastní stránka vlastností pouze scénáře, ve kterých je potřeba pochopit, že jsou vnitřní fungování těchto souborů a integrovaném vývojovém prostředí sady Visual Studio (a), nebo (b) chcete upravit vlastnosti projektu tak, že některé prostředky jinak než pomocí integrovaného vývojového prostředí sady Visual Studio.

Nejprve můžeme otevření stránek vlastností pro projekt (klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a zvolit vlastnosti):

![Vlastnosti projektu Visual C++](media/cpp-property-page-2017.png)

Každý uzel v rámci **vlastnosti konfigurace** nazývá pravidlo. Pravidlo někdy představuje jeden nástroje, jako je kompilátor, ale obecně výraz odkazuje na něco, co má vlastnosti, který se spustí a, který může vytvořit některé výstup. Každé pravidlo se naplní ze souboru xml ve složce VCTargets. Například pravidla C/C++, který je zobrazen výše je vyplněn "cl.xml".

Jak uvádíme výš, každé pravidlo má sadu vlastností, které jsou uspořádány do kategorií. Každý dílčí uzlu pravidlo představuje kategorii. Například optimalizace uzlu C/C++ obsahuje všechny související optimalizace vlastnosti kompilátor. Ve formátu tabulky v pravém podokně jsou generovány vlastnosti a jejich samotné hodnoty.

Cl.xml lze otevřít v programu Poznámkový blok nebo editoru XML (viz snímku níže). Zobrazí se kořenový uzel s názvem pravidla, která má stejný seznam vlastností definovaných v něm, jak se zobrazuje v uživatelském rozhraní spolu s další metadata.

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

Existuje jeden soubor XML odpovídající na každý uzel v části Vlastnosti konfigurace na stránkách vlastností uživatelského rozhraní. Můžete přidat nebo odebrat pravidla v uživatelském rozhraní, včetně nebo odebráním umístění, kde se odpovídající soubory XML v projektu. Jedná se například jak Microsoft.CppBuild.targets (jednu úroveň výš ze složky 1033) zahrnuje cl.xml:

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

Pokud jste odstranili cl.xml všechna data, skončíte se následující kostra:

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

Následující část popisuje každé hlavní prvky a některé metadata, která lze připojit k nim.

1. **Pravidlo:** pravidel je obecně kořenového uzlu v xml souboru; může mít mnoho atributů:

    ```xml
    <Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
              xmlns="http://schemas.microsoft.com/build/2009/properties"
              xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
              xmlns:sys="clr-namespace:System;assembly=mscorlib">
      <Rule.DisplayName>
        <sys:String>C/C++</sys:String>
      </Rule.DisplayName>
    ```

   a. **Název:** atribut Name je id pro pravidlo. Musí být jedinečný mezi všechny vlastnosti stránky souborů xml pro projekt.

   b. **PageTemplate:** je hodnota tohoto atributu můžete vybírat z kolekce šablon uživatelského rozhraní, které používá uživatelské rozhraní. Šablona "nástroje" vykreslí vlastnosti ve formátu standardní mřížky. Ostatní integrované hodnoty pro tento atribut se "ladění" a "generic". Naleznete v části ladění uzlu a uzel Obecné, najdete v článku formát uživatelského rozhraní, výsledkem zadání těchto hodnot. Šablona stránky "ladění" v uživatelském rozhraní používá rozevíracího seznamu přepínat mezi vlastnostmi rozdílné ladicí programy, že "generic" šablona zobrazuje různé vlastnosti kategorie vše na jedné stránky na rozdíl od s více uzly dílčí kategorie v části pravidla uzel. Tento atribut je návrh v uživatelském rozhraní; soubor xml byla navržena jako nezávislé uživatelského rozhraní. Různé uživatelské rozhraní může použít tento atribut pro různé účely.

   c. **SwitchPrefix:** Toto je Předpona použitá na příkazovém řádku přepínače. Hodnota "/" výsledkem by byla přepínače, které vypadají jako/zi/nologo, w3, atd.

   d. **Pořadí:** jde návrh na potenciální zájemce uživatelského rozhraní klienta na relativní umístění toto pravidlo ve srovnání s jinými pravidly v systému.

   e. **atribut xmlns:** jedná se o standardní prvek XAML. Uvidíte tři obory názvů uvedené. Tyto weby odpovídají na obory názvů pro deserializaci XAML třídy, schéma a systém názvů XAML, v uvedeném pořadí.

   f. **Zobrazovaný název:** jde o název, který se zobrazí na stránce vlastností uživatelského rozhraní pro pravidlo uzel. Tato hodnota je lokalizován. Vytvořili jsme DisplayName jako podřízený element pravidla, nikoli jako atribut (např. název nebo SwitchPrefix) z důvodu interní lokalizace požadavky na nástroj. Z pohledu na XAML obě jsou ekvivalentní. Ano můžete jenom si je atribut pro přehlednost nebo ji nechte, jak je.

   g. **Zdroj dat:** to je velmi důležité vlastnost, která informuje systém projektu, umístění, ze kterého by měla hodnotu vlastnosti čte a zapisuje do a jeho seskupování (vysvětleno níže). Pro cl.xml jsou tyto hodnoty:

      ```xml
      <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
      ```

   - `Persistence="ProjectFile` informuje systém projektu, který by měly být všechny vlastnosti pro pravidlo zapsány do souboru projektu nebo soubor seznamu vlastností (podle toho, která uzel byl použit na stránkách vlastností nejde vytvořit podřízený). Možná hodnota je "UserFile", která hodnotu zapíše do souboru .user.

   - `ItemType="ClCompile"` říká, že vlastnosti se budou ukládat jako ItemDefinition metadaty nebo metadaty položky (druhá možnost pouze v případě, že byly stránky vlastností vytvořený z uzlu souboru v Průzkumníku řešení) tohoto typu položky. Pokud toto pole není nastavená, je vlastnost zapsán jako obecné vlastnosti v PropertyGroup.

   - `Label=""` Označuje, že když vlastnosti se zapisují jako `ItemDefinition` metadat, bude popisek nadřazeného ItemDefinitionGroup – prázdný (každý prvek MSBuild může mít štítek). Visual Studio 2017 používá k procházení souboru .vcxproj projektu s popiskem skupiny. Všimněte si, že skupiny, které obsahují většinu vlastností pravidla prázdný řetězec jako popisek.

   - `HasConfigurationCondition="true"` informuje systém projektu tak, aby se projeví pouze pro aktuální konfiguraci projektu (podmínka může být připojeno do nadřazené skupiny nebo vlastní hodnota) připojovat podmínky konfigurace se hodnotou. Například otevření stránek vlastností mimo uzel projektu a nastavte hodnotu vlastnosti **zpracovávat upozornění jako chyby** pod **vlastnosti konfigurace > C/C++ General** na "Ano". Následující hodnota zapsána do souboru projektu. Všimněte si, že podmínka konfigurace připojena k nadřazené ItemDefinitionGroup –.

      ```xml
      <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
          <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
      </ItemDefinitionGroup>
      ```

      Pokud tato hodnota byla nastavena na stránce vlastností pro konkrétní soubor, jako je například stdafx.cpp, hodnota vlastnosti by byla zapsána v položce stdafx.cpp v souboru projektu, jak je znázorněno níže. Všimněte si, jak Konfigurace podmínky je přímo připojený k samotné metadata.

      ```xml
      <ItemGroup>
        <ClCompile Include="stdafx.cpp">
          <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
        </ClCompile>
      </ItemGroup>
      ```

   Jiný atribut **DataSource** nejsou uvedené výše je **PersistedName**. Tento atribut slouží k reprezentaci vlastnost v souboru projektu pod jiným názvem. Ve výchozím nastavení je tento atribut nastaven na vlastnost **název**.

   Jednotlivých vlastností mohou přepsat její nadřazené pravidlo DataSource. V takovém případě umístění pro hodnota této vlastnosti bude liší od dalších vlastností v pravidle.

   h. Existují jiné atributy pravidla, třeba popis SupportsFileBatching, atd., které se tady nezobrazují. Nejde získat úplnou sadu atributů příslušné pravidlo nebo na libovolný element tak, že přejdete v dokumentaci pro tyto typy. Alternativně můžete prozkoumat veřejné vlastnosti na typy v `Microsoft.Build.Framework.XamlTypes` obor názvů v `Microsoft.Build.Framework .dll` sestavení.

   i. **DisplayName**, **PageTemplate**, a **pořadí** jinak se vlastnosti související s Uživatelským rozhraním, které jsou k dispozici v tomto uživatelském rozhraní nezávislé na datový model. Tyto vlastnosti jsou téměř jistý využívat všechny uživatelské rozhraní, které slouží k zobrazení stránky vlastností. **DisplayName** a **popis** jsou dvě vlastnosti, které se nacházejí na téměř všechny prvky v souboru xml. A jedná se o pouze dvě vlastnosti, které byly lokalizovány (lokalizace tyto řetězce se podrobně novější příspěvek).

1. **Kategorie:** pravidlo může mít více kategorií. Pořadí, ve kterém kategorie jsou uvedeny v souboru xml je návrh na uživatelské rozhraní pro zobrazení kategorií ve stejném pořadí. Například pořadí kategorií pod uzlem jazyka C/C++, jak je vidět v uživatelském rozhraní – Obecné, optimalizace, preprocesor,...  – je stejný jako tento v cl.xml. Ukázka kategorie vypadá takto:

    ```xml
    <Category Name="Optimization">
      <Category.DisplayName>
        <sys:String>Optimization</sys:String>
      </Category.DisplayName>
    </Category>
    ```

   Výše uvedené fragment kódu ukazuje **název** a **DisplayName** atributy, které bylo popsané před. Ještě jednou, existují další atributy **kategorie** , který může mít nepoužívají výše. Můžete mít přehled o nich najdete v dokumentaci nebo prozkoumáním sestavení pomocí ildasm.exe.

1. **Vlastnosti:** Toto je maso souboru xml a obsahuje seznam všech vlastností v tomto pravidle. Každá vlastnost může být jeden z pěti možných typů uvedené výše zhruba XAML. Samozřejmě může mít pouze několik z těchto typů v souboru. Vlastnost má několik atributů, které mohla být popsány bohatě. Já zatím vysvětlím pouze **StringProperty** tady. Ostatní jsou velmi podobné.

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

   Před mají popsán většinu atributy v tomto fragmentu kódu. Nové značky jsou podtypem, kategorie a přepínač.

   a. **Podtyp** je k dispozici pouze pro atribut **StringProperty** a **StringListProperty**; poskytuje kontextové informace. Například hodnota "file" označuje, že vlastnost představuje cestu k souboru. Tyto kontextové informace slouží k vylepšit možnosti úprav poskytnutím Průzkumník Windows jako vlastnosti editor, který umožňuje uživateli zvolit soubor vizuálně.

   b. **Kategorie:** to deklaruje kategorie, pod kterou spadá tuto vlastnost. Pokuste se najít této vlastnosti v části **výstupní soubory** kategorie v uživatelském rozhraní.

   c. **Přepínač:** když pravidlo představuje nástroj – nástroj kompilátoru v tomto případě – většinu vlastností tohoto pravidla jsou předány jako přepínače do nástroje spustitelný soubor během doby sestavení. Hodnota tohoto atributu označuje přepínač literál, který se má použít. Výše uvedené vlastnosti určuje, že by měl být jeho přepínač **Fo**. V kombinaci s **SwitchPrefix** atributu v nadřazené pravidlo, tato vlastnost předána do spustitelného souboru jako **/Fo "ladění\"**  (zobrazí se na příkazovém řádku pro C/C++ na stránce vlastností uživatelského rozhraní).

   Ostatní atributy vlastnosti patří:

   d. **Visible:** Pokud z nějakého důvodu nechcete, aby vaše vlastnost zobrazí na stránkách vlastností (ale je během doby sestavení pravděpodobně stále k dispozici), tento atribut nastavte na hodnotu false.

   e. **Jen pro čtení:** Pokud chcete, abyste si mohli zobrazit jen pro čtení hodnoty této vlastnosti na stránkách vlastností, tento atribut nastavte na hodnotu true.

   f. **IncludeInCommandLine:** některé vlastnosti nemusí být předán nástroj během doby sestavení. Tento atribut nastavíte na hodnotu false, nebudou moct z předávána.
