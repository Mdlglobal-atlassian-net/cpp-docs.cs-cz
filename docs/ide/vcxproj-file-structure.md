---
title: "Struktura souborů VCXPROJ a props | Microsoft Docs"
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
caps.latest.revision: "1"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bc57a69b71bd7fbdbf97d5c34e7e6ec0694bb5df
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vcxproj-and-props-file-structure"></a>Struktura souborů VCXPROJ a props
MSBuild je výchozí systém projektu v sadě Visual Studio; Pokud vyberete **souboru | Nový projekt** v jazyce Visual C++ při vytváření projektu MSBuild, jehož nastavení jsou uložené v souboru projektu XML, který má příponu `.vcxproj`. Soubory .targets uložení nastavení a soubory props, může také importovat soubor projektu. Ve většině případů potřebujete nikdy ruční úpravy souboru projektu a ve skutečnosti byste neměli upravovat ji ručně Pokud nemáte dostatečné povědomí o MSBuild. Kdykoli je to možné, používejte stránky vlastností sady Visual Studio upravte nastavení projektu (viz [práce s vlastnostmi projektu](working-with-project-properties.md). V některých případech můžete však ručně upravit seznam souborů nebo vlastnosti projektu. U scénářů tento článek obsahuje základní informace o struktuře souboru. 

**Důležité:** Pokud zvolíte ruční úpravy souboru, mějte na paměti tyto skutečnosti:
1. Struktura souboru si musejí podle předepsaných formulář, který je popsaný v tomto článku.
2. Systém projektu Visual C++ aktuálně nepodporuje zástupné znaky v položkách projektu. Například to není podporováno:
```xml
<ClCompile Include="*.cpp"/>
```
3. Systém projektu Visual C++ aktuálně nepodporuje makra v projektu položky cesty. Například to není podporováno:
```xml
<ClCompile Include="$(IntDir)\generated.cpp"/>
```
4. Aby bylo možné používat správně přidat, odebrat nebo změnit, když upravit v okně Vlastnosti projektu **vlastnosti projektu** dialogové okno, soubor musí obsahovat samostatné skupiny pro každý projekt konfigurace a podmínky musí mít tento tvar:

```xml
Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”
```
 
5. Každou vlastnost je třeba zadat ve skupině s správný popisek zadané v souboru s pravidly vlastnost. Další informace najdete v tématu [vlastnost stránky xml pravidlo soubory] (https://review.docs.microsoft.com/en-us/cpp/ide/property-page-xml-files). 


## <a name="vcxproj-file-elements"></a>elementy VCXPROJ souboru
Obsah souboru si můžete prohlédnout pomocí jakékoli textového editoru nebo editoru XML. Můžete ji zobrazit v sadě Visual Studio kliknete pravým tlačítkem na projekt v Průzkumníku řešení, výběr **uvolnit projekt** a pak vyberete **upravit Foo.vcxproj**. 

Nejprve si všimněte si je, že nejvyšší úrovně prvky objeví v určitém pořadí. Příklad:
-  Většina vlastnosti skupin a skupin definice položky následovat po importu pro Microsoft.Cpp.Default.props.
-  všechny cíle jsou importovány na konci souboru.
-  existuje více skupin vlastnost, každý s jedinečný popisek, a k nim dojde v určitém pořadí.

Pořadí prvků v souboru projektu je velmi důležité, protože MSBuild je založená na modelu sekvenční vyhodnocení.  Pokud soubor projektu, včetně všech importovaných props a soubory .targets, obsahuje několik definic vlastnosti, na poslední definici přepíše předchozí ty. Protože MSBUild modul komunikaci se poslední během jeho vyhodnocení, bude v následujícím příkladu, nastavit hodnotu "xyz" během kompilace. 

```xml 
 <MyProperty>abc</MyProperty>
 <MyProperty>xyz</MyProperty>
``` 
 
Následující fragment kódu ukazuje souboru minimální. Jakýkoli soubor VCXPROJ vytvořen sadou Visual Studio bude obsahovat tyto prvky nejvyšší úrovně nástroje MSBuild a objeví se v tomto pořadí (i když mohou obsahovat více kopií každé takové element nejvyšší úrovně). Všimněte si, že `Label` atributy jsou libovolné značky, které se používají pouze Visual Studio jako výstražných tabulek pro úpravy, mají žádné další funkce.

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
 
 Následující část popisuje účel každé z těchto elementů a proč jsou seřazené tímto způsobem:
  
```xml  
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```
`Project`je kořenový uzel. Určuje MSBuild verze se má použít a také výchozí cíl, který má být provedeny, když tento soubor je předána MSBuild.exe.

```xml  
<ItemGroup Label="ProjectConfigurations" />
```
`ProjectConfigurations`obsahuje popis konfigurace projektu. Příklady jsou ladění | Win32, verze | Win32, ladění | ARM a tak dále. Mnoho nastavení projektu jsou specifické pro danou konfiguraci. Například pravděpodobně můžete nastavit vlastnosti optimalizace pro sestavení pro vydání, ale není sestavení ladicí verze.  

Následující fragment kódu ukazuje konfigurace projektu. V tomto příkladu se ladění | x 64 se název konfigurace. Název konfigurace projektu musí být ve formátu $(Configuration)|$(Platform). Konfigurace projektu uzlu může mít dvě vlastnosti: Konfigurace a platformy. Tyto vlastnosti budou automaticky nastavit hodnoty zadané tady, když je aktivní konfigurace.

```xml
<ProjectConfiguration Include="Debug|x64">
    <Configuration>Debug</Configuration> 
    <Platform>x64</Platform>
</ProjectConfiguration>
```
`ProjectConfigurations` Skupiny položek se nepoužívá v čase vytvoření buildu. Visual Studio IDE vyžaduje, aby bylo možné načíst projekt. Tato skupina položek můžete přesunout do souboru props a importovat soubor VCXPROJ. Ale v takovém případě Pokud potřebujete přidávat nebo odebírat konfigurace, je nutné ručně upravit soubor PROPS; nelze použít rozhraní IDE.

Prostředí IDE očekává, že konfigurace projektu pro libovolnou kombinaci konfigurace a platformy hodnoty používané v všechny položky ProjectConfiguration nalezena. Často to znamená, že projektu může mít smysl projektu konfigurace ke splnění tohoto požadavku. Například pokud projekt má tyto konfigurace:

- Ladění | Win32
- Prodejní | Win32
- Speciální optimalizace 32-bit | Win32

i když je smysl pro x64 "Speciální 32-bit optimalizace" pak musí mít rovněž těchto konfigurací: 

- Ladění | x64
- Prodejní | x64
- Speciální optimalizace 32-bit | x64

Můžete zakázat sestavení a nasazení příkazy pro všechny konfigurace ve Správci konfigurace řešení.

```xml  
 <PropertyGroup Label="Globals" />
```
 `Globals`obsahuje nastavení úrovně projektu, například ProjectGuid, RootNamespace a ApplicationType / ApplicationTypeRevision. Poslední dva často definovat cílového operačního systému. Projektu můžete vybrat pouze jeden operačního systému, vzhledem k tomu, že odkazy a položky projektu nelze nyní k dispozici podmínky. Tyto vlastnosti nejsou obvykle přepsat jinde v souboru projektu. Tato skupina není závislá na konfiguraci a proto obvykle jenom jedné skupiny Globals existuje v souboru projektu.

```xml
 <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

**Microsoft.Cpp.default.props** vlastností se dodává s Visual Studio a nelze jej změnit. Obsahuje výchozí nastavení pro projekt. Výchozí hodnoty se můžou lišit v závislosti na ApplicationType.

```xml
<PropertyGroup Label="Configuration" />
```
 `Configuration` Vlastnost skupina má podmínku připojené konfigurace (například `Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”`) a dodává se ve více kopií, jeden pro každou konfiguraci. Tato vlastnost Skupina hostitelů vlastnosti, které jsou nastavené pro konkrétní konfiguraci. Vlastnosti konfigurace zahrnují PlatformToolset a také řídit zahrnutí vlastností systému v **Microsoft.Cpp.props**. Například, pokud je definovat vlastnost `<CharacterSet>Unicode</CharacterSet>`, pak vlastností systému **společnosti microsoft. Cpp.unicodesupport.props** budou zahrnuty. Je-li si prohlédnout **Microsoft.Cpp.props**, zobrazí se na řádku: `<Import Condition=”'$(CharacterSet)' == 'Unicode'”   Project=”$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props”/>`. 

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```
**Microsoft.Cpp.props** seznam vlastností (přímo nebo prostřednictvím importy) definuje výchozí hodnoty pro mnoho vlastnosti specifické pro nástroj například optimalizace a úroveň pro upozornění kompilátoru vlastnosti, nástroj MIDL TypeLibraryName Vlastnost a tak dále. Importuje také různé seznamy vlastností systému podle vlastnosti konfigurace, které jsou definované ve skupině vlastností okamžitě výše. 

```xml
<ImportGroup Label="ExtensionSettings" />
```
`ExtensionSettings` Skupina obsahuje importy pro vlastností, které jsou součástí sestavení vlastní nastavení. Přizpůsobení sestavení je definována až tři soubory: soubor .targets, soubor PROPS a souboru .xml. Tato skupina importu obsahuje importy props souboru.

```xml
<ImportGroup Label="PropertySheets" />
```
 `PropertySheets` Skupina obsahuje importy pro uživatele vlastností. Jedná se o vlastností, které můžete přidat pomocí Správce vlastností zobrazení v sadě Visual Studio. Pořadí, ve kterém jsou uvedeny tyto importy je důležité a se projeví ve Správci vlastností. Soubor projektu obvykle obsahuje více instancí tento druh importovat skupiny, jeden pro každou konfigurací projektu.  
   
```xml   
<PropertyGroup Label="UserMacros" />
```
`UserMacros`jsou jako proměnné, které slouží k přizpůsobení procesu sestavení. Můžete například definovat uživatelské makro definovat vlastní výstupní cesta jako $(CustomOutputPath) a použijte jej k definování jiné proměnné. Tato skupina vlastnost ve uložený tyto vlastnosti. Všimněte si, že v sadě Visual Studio, této skupině automaticky nezadají informace v souboru projektu protože Visual C++ nepodporuje makra uživatele pro konfigurace. Makra uživatele jsou podporovány v seznamu vlastností. 

```xml
<PropertyGroup />
``` 
 Tato vlastnost skupina musí mít podmínku konfigurace pro všechny konfigurace projektu. Pokud některé chybí, dialogové okno Vlastnosti projektu nebude fungovat správně. Existuje více instancí skupiny vlastností, jeden pro každou konfiguraci. Na rozdíl od výše uvedených skupin vlastnost tato nemá štítek. Tato skupina obsahuje nastavení konfigurace na úrovni projektu. Toto nastavení platí pro všechny soubory, které jsou součástí skupiny zadanou položku. Sestavení přizpůsobení položky definice metadat je zde inicializovány. Tato PropertyGroup – musí být pozdější `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` a musí být žádné PropertyGroup – bez popisku před ním (jinak úpravy vlastností projektu nebude správně fungovat.).  

```xml
 <ItemDefinitionGroup />
```
Obsahuje definice položek. Tyto musí následovat stejná pravidla podmínky jako PropertyGroup popiskem.

```xml
<ItemGroup />
```  
Obsahuje položky (zdrojové soubory atd.) v projektu. Podmínky nejsou podporované pro položky projektu (tj. typy položek, které jsou považovány za položky projektu podle definice pravidla).

Metadata by měl mít Konfigurace podmínky pro každé konfiguraci i v případě theyare stejné. Příklad:

  ```xml
  <ItemGroup>
     <ClCompile Include="stdafx.cpp">
       <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
       <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|x64’">true</TreatWarningAsError>
     </ClCompile>
  </ItemGroup>
  ```
Systém projektu Visual C++ aktuálně nepodporuje zástupné znaky v položkách projektu. 
```xml  
  <ItemGroup>
     <ClCompile Include="*.cpp"> <!--Error-->
  </ItemGroup>
```
Systém projektu Visual C++ aktuálně nepodporuje makra v položkách projektu. 
```xml  
  <ItemGroup>
     <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
  </ItemGroup>
```
Odkazy jsou zadány v ItemGroup a mají tato omezení:
- Odkazy na nepodporují podmínky. 
- Odkazy na metadata nepodporují podmínky.

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```
Definuje (přímo nebo prostřednictvím importy) cíle Visual C++, například sestavení, vyčistit atd.

```xml
<ImportGroup Label="ExtensionTargets" />
```
Tato skupina obsahuje importy pro cílové soubory sestavení vlastní nastavení.
 
 ## <a name="impact-of-incorrect-ordering"></a>Dopad nesprávné řazení
 Visual Studio IDE závisí na projektu souboru nutnosti, které řazení popsané výše. Například když definujete hodnotu vlastnosti na stránkách vlastností, rozhraní IDE obecně umístí definici vlastnosti ve skupině vlastností s popiskem prázdný. Tím se zajistí, že výchozí hodnoty do vlastností systému jsou přepsány hodnotám definovaným uživatelem. Cílové soubory podobně importují na konci vzhledem k tomu, že budou využívat vlastnosti definované výše, a vzhledem k tomu, že obecně nedefinují vlastnosti sami. Podobně se importovat uživatele vlastností po vlastností systému (zahrnuté prostřednictvím **Microsoft.Cpp.props**). Tím se zajistí, že uživatel může přepsat všechny výchozí hodnoty získaných vlastností systému.
  
 Pokud souboru nedodrží toto rozložení, nemusí být výsledky sestavení očekávat. Například Pokud omylem import vlastností systému po vlastností definovaných uživatelem, nastavení uživatele přepsat pomocí vlastností systému.
  
 I prostředí čas IDE návrhu některé míry závisí na správné řazení elementů. Například, pokud váš soubor VCXPROJ nemá `PropertySheets` importovat skupiny, rozhraní IDE nemusí být schopní určit, kam umístit nový seznam vlastností vytvořený uživatel v **Správce vlastností**. Výsledkem může být uživatel list probíhá elementem listem systému. I když heuristiky používané IDE tolerovat menší nekonzistence v rozložení souboru VCXPROJ, důrazně doporučujeme dodržet strukturu uvedené dříve v tomto článku.

## <a name="how-the-ide-uses-element-labels"></a>Používání popisků element prostředí IDE
  
V prostředí IDE když nastavíte vlastnost UseOfAtl na stránce Obecné vlastnosti je zapsán do konfigurace vlastností skupiny v souboru projektu při vlastnost TargetName na stejné stránce vlastnost je zapsán do skupiny vlastností popiskem. Visual Studio vypadá na stránce vlastností souboru xml informace, ve kterém můžete zapsat každou vlastnost. Pro stránku Obecné vlastnosti (za předpokladu, že máte anglickou verzi Visual Studio Enterprise Edition), že soubor je `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`. Pravidlo souboru XML stránky vlastností definuje statických informací o pravidlo a všechny její vlastnosti. Jeden takový část informace je vlastnost Rule upřednostňované pozice v cílový soubor (soubor zápis svou hodnotu). Upřednostňované pozice je zadána v atributu Label u elementů souboru projektu. 


 ## <a name="property-sheet-layout"></a>Vlastnost list rozložení
  
 Následující fragment kódu XML je minimální rozložení souboru seznamu vlastností (props) vlastnost. Je podobná souboru a funkce elementů props lze odvodit z dřívějších diskuzi. 

```xml
 <Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <ImportGroup Label="PropertySheets" />
   <PropertyGroup Label="UserMacros" />
   <PropertyGroup />
   <ItemDefinitionGroup />
   <ItemGroup />
 </Project>
```
Chcete-li seznam vlastnosti, zkopírujte jeden ze souborů PROPS ve složce VCTargets a upravit pro vaše záměry. Pro Visual Studio 2017 Enterprise edition, je výchozí cesta VCTargets `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets`. 

## <a name="see-also"></a>Viz také
[Práce s vlastnostmi projektu](working-with-project-properties.md)
[soubory XML stránky vlastností](property-page-xml-files.md)