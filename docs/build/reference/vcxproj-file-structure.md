---
title: Struktura souborů .vcxproj a .props
ms.date: 09/18/2018
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 3b7c7bdad8848a3755db4ea565117459c72e939b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317117"
---
# <a name="vcxproj-and-props-file-structure"></a>Struktura souborů .vcxproj a .props

[Nástroj MSBuild](../msbuild-visual-cpp.md) je výchozí systém projektu v sadě Visual Studio; při výběru **souboru** > **nový projekt** vytváření projekt MSBuild, jehož nastavení se ukládají v jazyce Visual C++ v souboru projektu XML, který má příponu `.vcxproj`. Soubor projektu může také importovat souborech .props a souborech .targets ukládat nastavení. Ve většině případů nikdy muset ručně upravit soubor projektu a ve skutečnosti byste neměli upravovat ho ručně Pokud nemáte dostatečné povědomí o MSBuild. Kdykoli je to možné používejte stránky vlastností sady Visual Studio k úpravě nastavení projektu (viz [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md). Nicméně v některých případech budete muset ručně upravit seznam souborů nebo vlastnosti projektu. U scénářů tento článek obsahuje základní informace o struktuře souboru.

**Důležité:**

Pokud budete chtít ručně upravit soubor .vcxproj, mějte na paměti tyto skutečnosti:

1. Struktura souboru musí následovat předepsané formulář, který je popsaný v tomto článku.

1. Systém projektu Visual C++ aktuálně nepodporuje zástupné znaky v položkách projektu. Například to není podporováno:

   ```xml
   <ClCompile Include="*.cpp"/>
   ```

1. Systém projektu Visual C++ aktuálně nepodporuje makra v cesty položky projektu. Například to není podporováno:

   ```xml
   <ClCompile Include="$(IntDir)\generated.cpp"/>
   ```

   "Není podporován" znamená, že makra zaručené fungování pro všechny operace v rozhraní IDE. Makra, které se nezmění jejich hodnoty v různých konfiguracích by měla fungovat, ale nemusí být zachována, pokud položka se přesune na jiný filtr nebo projektu. Makra, změnit jejich hodnoty pro různé konfigurace způsobí problémy, protože rozhraní IDE neočekává cesty položky projektu jiný konfigurací jiného projektu.

1. Pokud chcete mít vlastnosti projektu správně přidat, odebrat nebo upravit při úpravách v **vlastnosti projektu** dialogovém okně soubor musí obsahovat samostatné skupiny pro každou konfiguraci projektu a podmínky musí být v tomto formuláři:

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

1. Každá vlastnost musí být zadaná ve skupině s správný popisek, jak je uvedeno v souboru pravidel vlastnost. Další informace najdete v tématu [soubory pravidlo xml stránky vlastností](property-page-xml-files.md).

## <a name="vcxproj-file-elements"></a>prvky souborů .vcxproj

Obsah souboru .vcxproj si můžete prohlédnout pomocí jakékoli textovém editoru nebo editoru XML. Můžete ji zobrazit v sadě Visual Studio kliknutím pravým tlačítkem myši na projekt v Průzkumníku řešení výběr **uvolnit projekt** a následným výběrem možnosti **upravit Foo.vcxproj**.

Všimněte si, že prvním krokem je nejvyšší úrovně prvky, které se zobrazí v určitém pořadí. Příklad:

- Po dokončení importu pro Microsoft.Cpp.Default.props dojde k vlastnosti skupin a skupinách definic položek maximum.

- Na konci souboru jsou importovány všechny cíle.

- Existuje více skupin pro vlastnost, každá má jedinečný popisek, a k nim dojde v určitém pořadí.

Pořadí prvků v souboru projektu je velmi důležité, protože nástroj MSBuild je založena na sekvenční vyhodnocení modelu.  Pokud soubor projektu, včetně všech importovaných .props a souborech .targets, obsahuje několik definic vlastnosti, přepíše poslední definice ta předchozí. Vzhledem k tomu, že zjistí jeho poslední během jeho vyhodnocení ke stroji MSBUild, se v následujícím příkladu se nastaví hodnota "xyz" během kompilace.

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

Následující fragment kódu ukazuje minimální .vcxproj soubor. Jakýkoli soubor .vcxproj vygenerované sadou Visual Studio bude obsahovat tyto prvky nejvyšší úrovně nástroje MSBuild a zobrazí se v tomto pořadí (i když mohou obsahovat více kopií každé takové element nejvyšší úrovně). Všimněte si, že `Label` atributy jsou libovolné značky, které se používají pouze pomocí sady Visual Studio jako výstražných tabulek pro úpravy, nemají žádné další funkce.

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

Následující části popisují účel každé z těchto prvků a proč jsou řazeny tímto způsobem:

### <a name="project-element"></a>Project – element

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` je kořenový uzel. Určuje verze nástroje MSBuild se má použít a také výchozí cíl, který se spustí, když tento soubor je předán MSBuild.exe.

### <a name="projectconfigurations-itemgroup-element"></a>ProjectConfigurations itemgroup – element

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` obsahuje popis konfigurace projektu. Mezi příklady patří ladění | Win32, Release | Win32, ladění | ARM a tak dále. Mnoho nastavení projektu jsou specifická pro danou konfiguraci. Například bude pravděpodobně chcete nastavit vlastnosti optimalizace pro sestavení pro vydání, ale nikoli sestavení pro ladění.

`ProjectConfigurations` Skupiny položek se nepoužívá v okamžiku sestavení. Visual Studio IDE vyžaduje-li načíst projekt. Tato skupina položek můžete přesunout do souboru props a importovat soubor .vcxproj. Ale v takovém případě pokud je potřeba přidat nebo odebrat konfigurace, musíte ručně upravit soubor PROPS; nelze použít integrovaném vývojovém prostředí.

### <a name="projectconfiguration-elements"></a>ProjectConfiguration elementy

Následující fragment kódu ukazuje konfiguraci projektu. V tomto příkladu "Debug | x 64 je název konfigurace. Název konfigurace projektu musí být ve formátu $(Configuration)|$(Platform). Konfigurace projektu uzel může mít dvě vlastnosti: Konfigurace a platforma. Tyto vlastnosti se automaticky nastaví hodnotami, které jsou tady zadané, když je aktivní konfigurace.

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

Integrované vývojové prostředí očekává konfigurace projektu pro libovolnou kombinaci konfigurace a platforma hodnot použitých ve všech položkách ProjectConfiguration. To často znamená, že projekt může být konfigurace nemá význam projektu ke splnění tohoto požadavku. Například pokud projekt obsahuje tyto konfigurace:

- Debug|Win32

- Maloobchodní | Win32

- Speciální 32-bit optimalizace | Win32

i když je pro x64 "Speciální 32-bit optimalizace" pak musí mít rovněž těchto konfigurací:

- Debug|x64

- Maloobchodní | x64

- Speciální 32-bit optimalizace | x64

Můžete zakázat sestavení a nasazení příkazů pro všechny konfigurace v **Správci konfigurace řešení**.

### <a name="globals-propertygroup-element"></a>Globals PropertyGroup – element

```xml
<PropertyGroup Label="Globals" />
```

`Globals` obsahuje nastavení úrovně projektu jako je například ProjectGuid RootNamespace a ApplicationType / ApplicationTypeRevision. Poslední dva často definují cílový operační systém. Projekt můžete cílit pouze jeden operační systém, skutečnost, že odkazy a položky projektu nelze nyní k dispozici podmínky. Tyto vlastnosti nejsou obvykle přepsána jinde v souboru projektu. Tato skupina není závislá na konfiguraci a proto obvykle jenom jedné skupiny Globals existuje v souboru projektu.

### <a name="microsoftcppdefaultprops-import-element"></a>Microsoft.Cpp.default.props Import – element

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

**Microsoft.Cpp.default.props** seznamu vlastností je součástí sady Visual Studio a nelze ji změnit. Obsahuje výchozí nastavení projektu. Výchozí nastavení se může lišit v závislosti na tom, ApplicationType.

### <a name="configuration-propertygroup-elements"></a>PropertyGroup – elementy konfigurace

```xml
<PropertyGroup Label="Configuration" />
```

A `Configuration` skupiny vlastností má podmínku připojené konfigurace (například `Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”`) a je k dispozici ve více kopií, jeden pro každou konfiguraci. Tato skupina vlastností hostitelem vlastnosti, které jsou nastavené pro konkrétní konfiguraci. Vlastnosti konfigurace zahrnují PlatformToolset a také řídit zahrnutí vlastností systému v **souboru Microsoft.Cpp.props**. Například pokud definujete vlastnost `<CharacterSet>Unicode</CharacterSet>`, pak seznam vlastností systému **microsoft. Cpp.unicodesupport.props** budou zahrnuty. Je-li si prohlédnout **souboru Microsoft.Cpp.props**, zobrazí se řádek: `<Import Condition=”'$(CharacterSet)' == 'Unicode'”   Project=”$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props”/>`.

### <a name="microsoftcppprops-import-element"></a>Import souboru Microsoft.Cpp.props – element

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

**Souboru Microsoft.Cpp.props** seznam vlastností (přímo nebo prostřednictvím importy) definuje výchozí hodnoty pro mnoho nástrojově specifické vlastnosti, jako je optimalizace a úroveň upozornění kompilátoru vlastnosti, TypeLibraryName nástroj MIDL Vlastnost a tak dále. Importuje také různé seznamy vlastností systému podle vlastnosti konfigurace, které jsou definovány ve skupině vlastností okamžitě výše.

### <a name="extensionsettings-importgroup-element"></a>ExtensionSettings importgroup – element

```xml
<ImportGroup Label="ExtensionSettings" />
```

`ExtensionSettings` Skupina obsahuje importy pro seznamy vlastností, které jsou součástí přizpůsobení sestavení. Přizpůsobení sestavení je definován až tři soubory: souboru .targets, .props souboru a souboru .xml. Tato skupina import obsahuje importy pro soubor PROPS.

### <a name="propertysheets-importgroup-elements"></a>Importgroup PropertySheets – elementy

```xml
<ImportGroup Label="PropertySheets" />
```

`PropertySheets` Skupina obsahuje importy pro uživatelských seznamů vlastností. Toto jsou seznamy vlastností, které jste přidali v rámci Správce vlastností zobrazení v sadě Visual Studio. Pořadí, ve kterém jsou uvedeny tyto importy je důležité a výpočtu je zapsán v Správce vlastností. Soubor projektu obvykle obsahuje víc instancí tohoto druhu importovat skupiny, jeden pro každou konfiguraci projektu.

### <a name="usermacros-propertygroup-element"></a>UserMacros PropertyGroup – element

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` obsahuje vlastnosti vytvoříte jako proměnné, které se používají k přizpůsobení procesu sestavení. Můžete například definovat uživatelské makro k definování vlastní výstupní cestu jako $(CustomOutputPath) a použijte jej k definování jiné proměnné. Tato skupina vlastností jsou uloženy tyto vlastnosti. Všimněte si, že v sadě Visual Studio této skupině automaticky nezadají informace v souboru projektu protože Visual C++ nepodporuje uživatelská makra pro konfigurace. Uživatelská makra jsou podporovány v seznamu vlastností.

### <a name="per-configuration-propertygroup-elements"></a>Elementy PropertyGroup podle konfigurace

```xml
<PropertyGroup />
```

Existuje víc instancí této vlastnosti skupiny, jeden pro každou konfiguraci pro všechny konfigurace projektu. Každá vlastnost skupina musí mít jednu podmínku konfigurace připojené. Pokud žádné konfigurace, které chybí, **vlastnosti projektu** dialogového okna nebude fungovat správně. Na rozdíl od výše uvedených skupin vlastností tohohle nemá popisek. Tato skupina obsahuje nastavení konfigurace na úrovni projektu. Tato nastavení platí pro všechny soubory, které jsou součástí skupiny zadané položky. Přizpůsobení položky definice sestavení metadata se inicializuje tady.

Tato PropertyGroup musí být pozdější než `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` a musí být žádné jiné PropertyGroup bez popisku před (jinak úpravy vlastností projektu nebude správně fungovat).

### <a name="per-configuration-itemdefinitiongroup-elements"></a>ItemDefinitionGroup – prvky podle konfigurace

```xml
<ItemDefinitionGroup />
```

Obsahuje definice položek. Tyto musí řídit stejnými pravidly podmínky jako elementy PropertyGroup popiskem podle konfigurace.

### <a name="itemgroup-elements"></a>Itemgroup – elementy

```xml
<ItemGroup />
```

Obsahuje položky (zdrojových souborů, atd.) v projektu. Podmínky nejsou podporovány pro položky projektu (to znamená, typy položek, které jsou považovány za položky projektu podle definice pravidla).

Metadata by měl mít konfigurace podmínek pro každou konfiguraci, i když jsou všechny byly stejné. Příklad:

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

Odkazy jsou uvedeny v ItemGroup a mají tato omezení:

- Odkazy na podmínky nepodporují.

- Odkazuje na metadata nepodporuje podmínky.

### <a name="microsoftcpptargets-import-element"></a>Microsoft.Cpp.targets Import – element

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Definuje (přímo nebo prostřednictvím importy) cíle Visual C++, jako je například sestavení, vyčištění, atd.

### <a name="extensiontargets-importgroup-element"></a>ExtensionTargets importgroup – element

```xml
<ImportGroup Label="ExtensionTargets" />
```

Tato skupina obsahuje importy pro cílové soubory vlastního nastavení sestavení.

## <a name="impact-of-incorrect-ordering"></a>Dopad nesprávnému řazení

Integrované vývojové prostředí sady Visual Studio závisí na projektu soubor having řazení popsané výše. Například při definování hodnotu vlastnosti na stránkách vlastností rozhraní IDE se obecně umístit definici vlastnosti ve skupině vlastností s popiskem prázdný. Tím se zajistí, že se hodnoty definované uživatelem přepisují výchozí hodnoty, které jsou uvedeny v seznamu vlastností systému. Obdobně cílové soubory jsou importovány na konci vzhledem k tomu, že využívat vlastnosti určené výše, a protože jsou obecně nedefinují vlastnosti sami. Obdobně uživatelských seznamů vlastností se importují po seznamech vlastností, které systém (zahrnuté prostřednictvím **souboru Microsoft.Cpp.props**). Tím se zajistí, že uživatel může přepsat výchozí hodnoty získaných vlastností systému.

Pokud soubor .vcxproj nedodržuje toto rozložení, nemusí být čekáte výsledků sestavení. Například Pokud omylem importovat seznam vlastností systému po seznamech vlastností, které jsou definované uživatelem, nastavení uživatele přepsat podle vlastností systému.

Dokonce i prostředí čas IDE návrh některých míry závisí na správné pořadí prvků. Například, pokud váš soubor .vcxproj nemá `PropertySheets` skupiny import, integrovaném vývojovém prostředí nemusí být schopní určit, kam umístit nový seznam vlastností, které uživatel vytvořil v **Správce vlastností**. To může způsobit uživatel list přepisované seznamem systému. I když heuristiky používá integrované vývojové prostředí může tolerovat možnost, podverze nekonzistence v rozložení souboru .vcxproj, důrazně doporučujeme dodržet struktura uvedené dříve v tomto článku.

## <a name="how-the-ide-uses-element-labels"></a>Použití popisků element integrovaného vývojového prostředí

V prostředí IDE, při nastavení **UseOfAtl** vlastnosti na stránce Obecné vlastnosti, která jsou zapsána do skupiny vlastností konfigurace v souboru projektu, zatímco **TargetName** stejné stránce vlastností je zapsán do skupiny vlastností popiskem podle konfigurace. Visual Studio zjistí soubor xml stránky vlastností pro informace, ve kterém můžete napsat každou vlastnost. Pro **Obecné** stránka vlastností (za předpokladu, že máte anglickou verzi Visual Studio Enterprise Edition), je tento soubor `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`. Pravidla souboru XML stránky vlastností definuje statické informace o pravidle a všechny její vlastnosti. Jeden takový část informací je upřednostňovaný pozice vlastnost pravidla v cílovém souboru (souboru, kam se budou zapisovat jeho hodnotu). Preferované umístění je určen atribut Label v elementech souborů projektu.

## <a name="property-sheet-layout"></a>Vlastnosti rozložení tabulky

Následující fragment kódu XML je minimální rozložení vlastností (.props) soubor. Je podobný soubor .vcxproj a funkce .props prvky lze odvodit z předchozích diskuse.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

Chcete-li vlastní seznam vlastností, zkopírujte jeden z souborech .props ve složce VCTargets a upravovat pro účely. Pro Visual Studio 2017 Enterprise edition, je výchozí cestu VCTargets `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets`.

## <a name="see-also"></a>Viz také:

[Nastavení vlastností kompilátoru a sestavení C++ v sadě Visual Studio](../working-with-project-properties.md)<br/>
[Soubory XML stránky vlastností](property-page-xml-files.md)
