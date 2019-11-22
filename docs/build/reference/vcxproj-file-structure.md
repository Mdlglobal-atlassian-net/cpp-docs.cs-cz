---
title: Struktura souborů .vcxproj a .props
ms.date: 05/16/2019
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: a24349980e9395257f20fcfcc0987883060a7c1d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303134"
---
# <a name="vcxproj-and-props-file-structure"></a>Struktura souborů .vcxproj a .props

Nástroj [MSBuild](../msbuild-visual-cpp.md) je výchozím systémem projektu v aplikaci Visual Studio; Když zvolíte **soubor** > **Nový projekt** ve vizuálu C++ , vytváříte projekt MSBuild, jehož nastavení jsou uložena v souboru projektu XML, který má `.vcxproj`rozšíření. Soubor projektu může také importovat soubory. props a. targets, kde lze uložit nastavení. Ve většině případů nikdy nemusíte ručně upravovat soubor projektu a ve skutečnosti byste ho neměli upravovat ručně, pokud nebudete mít dobrý význam nástroje MSBuild. Kdykoliv je to možné, měli byste použít stránky vlastností sady Visual Studio pro úpravu nastavení projektu (viz [nastavení C++ kompilátoru a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md). V některých případech však může být nutné ručně upravit soubor projektu nebo seznam vlastností. V těchto scénářích obsahuje tento článek základní informace o struktuře souboru.

**Důležité:**

Pokud se rozhodnete ručně upravit soubor. vcxproj, pamatujte na tyto skutečnosti:

1. Struktura souboru musí odpovídat předepsanému formuláři, který je popsán v tomto článku.

1. Systém projektu sady C++ Visual Studio v současné době nepodporuje v položkách projektu zástupné znaky. Například to není podporováno:

   ```xml
   <ClCompile Include="*.cpp"/>
   ```

1. Systém projektu sady C++ Visual Studio aktuálně nepodporuje makra v cestách položek projektu. Například to není podporováno:

   ```xml
   <ClCompile Include="$(IntDir)\generated.cpp"/>
   ```

   "Není podporováno" znamená, že makra nejsou zaručena fungovat pro všechny operace v integrovaném vývojovém prostředí (IDE). Makra, která nemění svou hodnotu v různých konfiguracích by měla fungovat, ale nemusí být zachována, pokud je položka přesunuta do jiného filtru nebo projektu. Makra, která změní jejich hodnotu pro různé konfigurace, způsobí problémy, protože rozhraní IDE neočekává, že se cesty položek projektu pro různé konfigurace projektu liší.

1. Aby se správně přidaly, odebraly nebo upravily vlastnosti projektu při úpravách v dialogovém okně **Vlastnosti projektu** , soubor musí obsahovat samostatné skupiny pro každou konfiguraci projektu a podmínky musí být v tomto formátu:

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

1. Každá vlastnost musí být zadaná ve skupině se správným popiskem, jak je uvedeno v souboru pravidel vlastnosti. Další informace najdete v tématu [soubory pravidel XML stránky vlastností](property-page-xml-files.md).

## <a name="vcxproj-file-elements"></a>prvky souboru. vcxproj

Obsah souboru. vcxproj můžete zkontrolovat pomocí libovolného textu nebo editoru XML. Můžete ji zobrazit v aplikaci Visual Studio tak, že kliknete pravým tlačítkem na projekt v Průzkumník řešení, zvolíte **Uvolnit projekt** a pak zvolíte **Upravit foo. vcxproj**.

První věc, kterou je třeba si všimnout, je, že se prvky na nejvyšší úrovni zobrazují v určitém pořadí. Příklad:

- Většina skupin vlastností a skupin definic položek nastane po importu pro Microsoft. cpp. default. props.

- Všechny cíle jsou importovány na konci souboru.

- Existuje více skupin vlastností, z nichž každý má jedinečný popisek, a vyskytují se v určitém pořadí.

Pořadí prvků v souboru projektu je velmi důležité, protože nástroj MSBuild je založen na modelu sekvenčního vyhodnocení.  Pokud je soubor projektu, včetně všech importovaných souborů. props a. targets, tvořen více definicemi vlastnosti, poslední definice přepíše předchozí. V následujícím příkladu bude během kompilace nastavena hodnota "xyz", protože modul MSBUild během hodnocení zjistí jeho poslední.

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

Následující fragment kódu ukazuje minimální soubor VCXPROJ. Libovolný soubor. vcxproj generovaný v aplikaci Visual Studio bude obsahovat tyto prvky nástroje MSBuild nejvyšší úrovně a v tomto pořadí budou zobrazeny (i když mohou obsahovat více kopií každého takového prvku nejvyšší úrovně). Všimněte si, že `Label` atributy jsou libovolné značky, které používá aplikace Visual Studio jako signposts pro úpravy; nemají žádnou jinou funkci.

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003'>
  <ItemGroup Label="ProjectConfigurations" />
  <PropertyGroup Label="Globals" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup Label="Configuration" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings" />
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets" />
</Project>
```

Následující části popisují účel každého z těchto prvků a proč jsou uspořádány tímto způsobem:

### <a name="project-element"></a>Projektový element

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` je kořenovým uzlem. Určuje verzi nástroje MSBuild, která se má použít, a také výchozí cíl, který se má provést, když se tento soubor předává nástroji MSBuild. exe.

### <a name="projectconfigurations-itemgroup-element"></a>ProjectConfigurations – element Item

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` obsahuje popis konfigurace projektu. Příklady ladění | Win32, verze | Win32, ladění | ARM a tak dále. Mnoho nastavení projektu je specifické pro danou konfiguraci. Například pravděpodobně budete chtít nastavit vlastnosti optimalizace pro sestavení pro vydání, ale ne sestavení pro ladění.

Skupina položek `ProjectConfigurations` se v době sestavení nepoužívá. Rozhraní IDE sady Visual Studio vyžaduje, aby bylo možné načíst projekt. Tuto skupinu položek lze přesunout do souboru. props a importovat do souboru. vcxproj. V takovém případě, pokud potřebujete přidat nebo odebrat konfigurace, je však nutné ručně upravit soubor. props; rozhraní IDE nemůžete použít.

### <a name="projectconfiguration-elements"></a>ProjectConfiguration elementy

Následující fragment kódu ukazuje konfiguraci projektu. V tomto příkladu je název konfigurace ladit | x64. Název konfigurace projektu musí být ve formátu $ (konfigurace) | $ (platforma). Uzel Konfigurace projektu může mít dvě vlastnosti: konfiguraci a platformu. Tyto vlastnosti se automaticky nastaví s hodnotami, které tady určíte, když je konfigurace aktivní.

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

Rozhraní IDE očekává, že se pro libovolnou kombinaci konfigurací a hodnot platforem používaných ve všech ProjectConfiguration položkách najde konfigurace projektu. To často znamená, že projekt může mít nevýznamné konfigurace projektu pro splnění tohoto požadavku. Pokud má například projekt tyto konfigurace:

- Debug|Win32

- Maloobchodní prodej | Chyb

- Speciální optimalizace 32 – 32bitová verze | Chyb

pak musí mít také tyto konfigurace, i když "speciální optimalizace 32", která je pro platformu x64 nevýznamná:

- Debug|x64

- Maloobchodní prodej | x64

- Speciální optimalizace 32 – 32bitová verze | x64

Příkazy Build a deploy můžete zakázat pro jakoukoli konfiguraci v **řešení Configuration Manager**.

### <a name="globals-propertygroup-element"></a>Element vlastnosti globálních vlastností

```xml
<PropertyGroup Label="Globals" />
```

`Globals` obsahuje nastavení na úrovni projektu, jako jsou ProjectGuid, RootNamespace a typu ApplicationType/ApplicationTypeRevision. Poslední dvě často definují cílový operační systém. Projekt může cílit jenom na jeden operační systém z důvodu faktu, že odkazy a položky projektu nemůžou mít aktuálně nastavené podmínky. Tyto vlastnosti se obvykle nepřepisují jinde v souboru projektu. Tato skupina není závislá na konfiguraci, a proto v souboru projektu existuje jenom jedna skupina Globals.

### <a name="microsoftcppdefaultprops-import-element"></a>Import elementu Microsoft. cpp. default. props

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

Seznam vlastností **Microsoft. cpp. default. props** je součástí sady Visual Studio a nelze jej upravit. Obsahuje výchozí nastavení projektu. Výchozí hodnoty se mohou lišit v závislosti na typu ApplicationType.

### <a name="configuration-propertygroup-elements"></a>Prvky vlastností konfigurace

```xml
<PropertyGroup Label="Configuration" />
```

`Configuration` skupina vlastností má připojenu podmínku konfigurace (například `Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"`) a je k dispozici v několika kopiích, jedna na konfiguraci. Tato skupina vlastností je hostitelem vlastností, které jsou nastaveny pro konkrétní konfiguraci. Konfigurační vlastnosti zahrnují PlatformToolset a také řídí zahrnutí seznamů vlastností systému do **Microsoft. cpp. props**. Například pokud definujete vlastnost `<CharacterSet>Unicode</CharacterSet>`, zobrazí se seznam vlastností systému **Microsoft. Budou zahrnuty cpp cpp. unicodesupport. props** . Pokud provedete kontrolu **Microsoft. cpp. props**, zobrazí se řádek: `<Import Condition="'$(CharacterSet)' == 'Unicode'" Project="$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props" />`.

### <a name="microsoftcppprops-import-element"></a>Import elementu Microsoft. cpp. props

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

Seznam vlastností **Microsoft. cpp. props** (přímo nebo prostřednictvím importu) definuje výchozí hodnoty pro mnoho vlastností specifických pro nástroj, jako je optimalizace a vlastnosti úrovně upozornění kompilátoru, vlastnost NÁZEVKNIHOVNYTYPŮ nástroje MIDL a tak dále. Také importuje různé systémové seznamy vlastností na základě toho, které vlastnosti konfigurace jsou definovány ve skupině vlastností přímo výše.

### <a name="extensionsettings-importgroup-element"></a>Platný ExtensionSettings – element import

```xml
<ImportGroup Label="ExtensionSettings" />
```

Skupina `ExtensionSettings` obsahuje importy pro seznamy vlastností, které jsou součástí vlastního nastavení sestavení. Přizpůsobení sestavení je definováno až třemi soubory: soubor. targets, soubor. props a soubor. XML. Tato skupina pro import obsahuje importy pro soubor. props.

### <a name="propertysheets-importgroup-elements"></a>PropertySheets elementy import

```xml
<ImportGroup Label="PropertySheets" />
```

Skupina `PropertySheets` obsahuje seznamy vlastností uživatele. Jedná se o seznamy vlastností, které přidáte pomocí zobrazení Správce vlastností v aplikaci Visual Studio. Pořadí, ve kterém jsou tyto importy uvedené, je důležité a projeví se v Správce vlastností. Soubor projektu normálně obsahuje více instancí tohoto typu skupiny importů, jeden pro každou konfiguraci projektu.

### <a name="usermacros-propertygroup-element"></a>UserMacros – element vlastnosti

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` obsahuje vlastnosti, které vytvoříte jako proměnné, které se používají k přizpůsobení procesu sestavení. Můžete například definovat uživatelské makro pro definování vlastní výstupní cesty jako $ (CustomOutputPath) a použít je k definování dalších proměnných. Tato vlastnost slouží jako skupina vlastností. Všimněte si, že v aplikaci Visual Studio není tato skupina v souboru projektu naplněná C++ , protože vizuál nepodporuje uživatelská makra pro konfigurace. Uživatelská makra jsou podporována v seznamu vlastností.

### <a name="per-configuration-propertygroup-elements"></a>Prvky vlastností jednotlivých konfigurací

```xml
<PropertyGroup />
```

Existuje několik instancí této skupiny vlastností, jeden pro každou konfiguraci pro všechny konfigurace projektu. Každá skupina vlastností musí mít připojenu jednu podmínku konfigurace. Pokud chybí nějaké konfigurace, dialogové okno **vlastností projektu** nebude správně fungovat. Na rozdíl od výše uvedených skupin vlastností nemá tato jedna jmenovka. Tato skupina obsahuje nastavení na úrovni konfigurace projektu. Tato nastavení platí pro všechny soubory, které jsou součástí zadané skupiny položek. Metadata definice položky vlastního nastavení sestavení jsou inicializována zde.

Tato vlastnost musí být uvedena po `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` a nesmí obsahovat žádnou jinou vlastnost Property bez popisku (jinak úpravy vlastností projektu nebudou fungovat správně).

### <a name="per-configuration-itemdefinitiongroup-elements"></a>ItemDefinitionGroup prvků pro konfiguraci

```xml
<ItemDefinitionGroup />
```

Obsahuje definice položek. Ty musí splňovat pravidla stejných podmínek, jako jsou prvky Property, které jsou v jednotlivých konfiguracích bez popisku.

### <a name="itemgroup-elements"></a>Prvky položky

```xml
<ItemGroup />
```

Obsahuje položky (zdrojové soubory atd.) v projektu. Podmínky nejsou podporovány pro položky projektu (tj. typy položek, které jsou považovány za položky projektu podle definic pravidel).

Metadata by měla mít konfigurační podmínky pro každou konfiguraci, i když jsou všechny stejné. Příklad:

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

Systém projektu sady C++ Visual Studio v současné době nepodporuje v položkách projektu zástupné znaky.

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

Systém projektu sady C++ Visual Studio aktuálně nepodporuje makra v položkách projektu.

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

Odkazy jsou zadány ve více položkách a mají tato omezení:

- Odkazy nepodporují podmínky.

- Odkazy na metadata nepodporují podmínky.

### <a name="microsoftcpptargets-import-element"></a>Microsoft. cpp. targets – import elementu

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Definuje (přímo nebo prostřednictvím importu) vizuální C++ cíle, jako je sestavení, čištění atd.

### <a name="extensiontargets-importgroup-element"></a>ExtensionTargets – element import

```xml
<ImportGroup Label="ExtensionTargets" />
```

Tato skupina obsahuje importy pro cílové soubory vlastního nastavení sestavení.

## <a name="impact-of-incorrect-ordering"></a>Dopad nesprávného řazení

Rozhraní IDE sady Visual Studio závisí na souboru projektu, který má řazení popsané výše. Například při definování hodnoty vlastnosti na stránkách vlastností bude IDE obvykle umístit definici vlastnosti ve skupině vlastností s prázdným popiskem. Tím se zajistí, že se výchozí hodnoty přenesené do seznamů vlastností systému přepíšou uživatelsky definovanými hodnotami. Podobně jsou cílové soubory importovány na konec, protože spotřebovávají vlastnosti definované výše a protože všeobecně nedefinují vlastnosti samotné. Podobně se seznamy vlastností uživatele importují po seznamech systémových vlastností (zahrnutých přes **Microsoft. cpp. props**). Tím se zajistí, že uživatel může přepsat jakékoli výchozí hodnoty, které jsou součástí systémových vlastností systému.

Pokud soubor. vcxproj nedodržuje toto rozložení, výsledky sestavení nemusí být očekávaným způsobem. Pokud například omylem importujete seznam vlastností systému po seznamech vlastností definovaných uživatelem, bude nastavení uživatele přepsáno pomocí seznamů vlastností systému.

I prostředí pro dobu návrhu IDE závisí na určitém rozsahu pro správné řazení prvků. Například pokud váš soubor. vcxproj nemá `PropertySheets` skupinu pro import, rozhraní IDE nemusí být schopné určit, kam umístit nový seznam vlastností, který uživatel vytvořil v **Správce vlastností**. To může mít za následek přepsání seznamu uživatelů systémem. I když heuristická metoda používaná rozhraním IDE dokáže tolerovat drobné nekonzistence v rozložení souboru. vcxproj, důrazně se doporučuje odchýlit od struktury uvedené dříve v tomto článku.

## <a name="how-the-ide-uses-element-labels"></a>Jak IDE používá popisky elementů

V integrovaném vývojovém prostředí (IDE) když nastavíte vlastnost **UseOfAtl** na stránce Obecné vlastnosti, je zapsán do skupiny vlastností konfigurace v souboru projektu, zatímco vlastnost **TargetName** na stejné stránce vlastností je zapsána do skupiny vlastností bez popisku pro jednu konfiguraci. Visual Studio vyhledá v souboru XML stránky vlastností informace o tom, kde mají být jednotlivé vlastnosti napsány. Pro stránku vlastností **General** (za předpokladu, že máte anglickou verzi sady Visual Studio 2019 Enterprise Edition), je tento soubor `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`. Soubor pravidel XML stránky vlastností definuje statické informace o pravidle a všech jeho vlastnostech. Jedna z těchto informací je upřednostňovanou polohou vlastnosti pravidla v cílovém souboru (soubor, do kterého se má zapsat jeho hodnota). Upřednostňovaná poloha je určena atributem Label v prvcích souboru projektu.

## <a name="property-sheet-layout"></a>Rozložení seznamu vlastností

Následující fragment kódu XML je minimální rozložení souboru seznamu vlastností (. props). Je podobný souboru. vcxproj a funkce prvků. props lze odvodit z předchozí diskuze.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

Chcete-li vytvořit vlastní seznam vlastností, zkopírujte jeden ze souborů. props ve složce VCTargets a upravte jej pro vaše účely. Pro Visual Studio 2019 Enterprise Edition je výchozí cesta VCTargets `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets`.

## <a name="see-also"></a>Viz také:

[Nastavení vlastností kompilátoru a sestavení C++ v sadě Visual Studio](../working-with-project-properties.md)<br/>
[Soubory XML stránky vlastností](property-page-xml-files.md)
