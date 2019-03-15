---
title: Nastavení kompilátoru jazyka C++ a vlastnosti v sadě Visual Studio sestavení
description: Pomocí integrovaného vývojového prostředí sady Visual Studio můžete změnit možnosti kompilátoru a linkeru C++ a další nastavení buildu.
ms.date: 12/10/2018
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
ms.openlocfilehash: 55adb6dc91919bda9c2827a89e5de536667085c1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823401"
---
# <a name="set-compiler-and-build-properties"></a>Nastavení kompilátoru a vlastnosti sestavení

V integrovaném vývojovém prostředí, všechny informace potřebné k sestavení projektu vystavena jako *vlastnosti*. Tyto informace zahrnují název aplikace, rozšíření (například knihovny DLL, LIB, EXE), možnosti kompilátoru, možnosti linkeru, nastavení ladicího programu, vlastní kroky sestavení a mnoha dalším věcem. Obvykle použijete *stránky vlastností* ( **projektu &#124; vlastnosti**) k zobrazení a úpravě těchto vlastností. Chcete-li získat přístup k na stránkách vlastností, zvolte **Projekt > \<název projektu > vlastnosti** z hlavní nabídky, nebo klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a zvolte **Vlastnosti**.

## <a name="default-properties"></a>Výchozí vlastnosti

Při vytváření projektu systém přiřadí hodnoty pro různé vlastnosti. Výchozí hodnoty lišit v závislosti na typu projektu a jaké možnosti můžete vybrat v Průvodci vytvořením aplikace. Například projekt knihovny ATL má vlastnosti týkající se souborů MIDL, ale tyto chybí v základní Konzolová aplikace. Výchozí vlastnosti jsou uvedeny v podokně obecné na stránkách vlastností:

![Visual C&#43; &#43; výchozích hodnot projektu](media/visual-c---project-defaults.png "výchozí nastavení projektu Visual C++")

## <a name="applying-properties-to-build-configurations-and-target-platforms"></a>Použití vlastnosti k vytvoření, konfigurace a cílové platformy

Některé vlastnosti, jako je například název aplikace, platí pro všechny varianty sestavení, bez ohledu na cílovou platformu nebo zda je sestavení ladění nebo vydání. Ale většinu vlastností jsou závislé na konfiguraci. Je to proto, že má kompilátor vědět, jaké konkrétní platformy, se bude program spouštět v a jaké kompilátoru specifické možnosti použít, aby bylo možné generovat správný kód. Proto když nastavíte vlastnost, je důležité věnovat pozornost tomu, jaké konfigurace a platforma má použít novou hodnotu. By se měly používat jenom k sestavení ladění Win32, nebo by to platí také pro ladění ARM a ladění x64? Například **optimalizace** , ve výchozím nastavení, je nastavena na **maximalizovat rychlost (/ O2)** v konfiguraci vydané verze, ale je zakázané v konfiguraci ladění.

Stránky vlastností jsou navržené tak, aby se vždy zobrazí, a v případě potřeby upravit, které konfigurace a platforma hodnotu vlastnosti by se měly používat pro. Následující obrázek znázorňuje stránky vlastností s informacemi o platformy a konfigurace v seznamu polí v horní části. Když **optimalizace** vlastnost zde není nastavena, bude platit pouze pro ladění Win32 sestavení, který aktivní konfiguraci, jak je znázorněno red šipek.

![Visual C&#43; &#43; aktivní konfigurace pro zobrazení stránky vlastností](media/visual-c---property-pages-showing-active-configuration.png "aktivní konfigurace pro zobrazení stránky vlastností Visual C++")

Následující obrázek ukazuje stejné stránce vlastností projektu, ale konfigurace se změnil na vydání. Všimněte si jinou hodnotu pro vlastnost optimalizace. Všimněte si také, že je aktivní konfiguraci stále ladit. Můžete nastavit vlastnosti pro žádnou konfiguraci. nemusí být aktivní.

![Visual C&#43; &#43; konfigurace vydání zobrazení stránky vlastností](media/visual-c---property-pages-showing-release-config.png "konfigurace vydání zobrazení stránky vlastností Visual C++")

## <a name="target-platforms"></a>Cílové platformy

*Cílová platforma* odkazuje na typ zařízení a/nebo operační systém, který se spustí spustitelný soubor na. Můžete vytvářet projekt pro více než jednu platformu. Dostupné cílové platformy pro projekty C++ závisí na typu projektu. zahrnout, ale nejsou omezeny na Win32, x64, ARM, Android a iOS.     **X86** cílové platformy, který můžete vidět v **nástroje Configuration Manager** je stejný jako **Win32** v nativních projektů C++. Win32 znamená Windows 32-bit a **x64** znamená Windows 64-bit. Další informace o těchto dvou platforem, naleznete v tématu [spuštění 32bitových aplikací](/windows/desktop/WinProg64/running-32-bit-applications).

**Jakýkoli procesor** cílové platformy hodnoty, který můžete vidět v **nástroje Configuration Manager** nemá žádný vliv na nativních projektů C++; je relevantní pro C + +/ CLI a dalších .NET typy projektů. Další informace najdete v tématu [/CLRIMAGETYPE (zadat typ z bitové kopie modulu CLR)](reference/clrimagetype-specify-type-of-clr-image.md).


Další informace o nastavení vlastností pro sestavení pro ladění naleznete v tématu:

- [Nastavení projektu pro konfiguraci ladění jazyka C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)
- [Nastavení a příprava ladicího programu](/visualstudio/debugger/debugger-settings-and-preparation)
- [Příprava ladění: Typy projektů Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)
- [Zadání symbolu (.pdb) a zdrojových souborů v ladicím programu sady Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)

## <a name="c-compiler-and-linker-options"></a>Možnosti kompilátoru a linkeru C++

Možnosti kompilátoru a linkeru C++ jsou umístěny v **C/C++** a **Linkeru** uzlů v levém podokně v části **vlastnosti konfigurace**. Tyto přeložit přímo pro možnosti příkazového řádku, které budou předány kompilátoru. Si můžete přečíst dokumentaci o konkrétní možnosti, vyberte možnost v prostředním podokně a stiskněte klávesu **F1**. Nebo můžete procházet dokumentaci pro všechny možnosti v [– možnosti kompilátoru MSVC](reference/compiler-options.md) a [možnosti Linkeru MSVC](reference/linker-options.md). 

**Stránky vlastností** dialogové okno zobrazuje pouze stránky vlastností, které se vztahují k aktuálnímu projektu. Pokud například projekt nemá soubor .idl, stránka s vlastnostmi MIDL se nezobrazí. Další informace o nastavení na jednotlivých stránkách vlastností najdete v tématu [stránky vlastností (C++)](reference/property-pages-visual-cpp.md). 

## <a name="directory-and-path-values"></a>Adresář a cestu hodnoty

Nástroj MSBuild podporuje použití konstanty z doby kompilace označovány jako "makra" pro určité řetězcové hodnoty patří adresářů a cesty. Tyto jsou přístupné na stránkách vlastností, kde můžete odkazovat na a upravit pomocí [Editor vlastností](#property_editor). 

Následující obrázek znázorňuje stránky vlastností projektu jazyka Visual C++. V levém podokně **adresáře VC ++** *pravidlo* je vybraná, a v pravém podokně je uveden seznam vlastností, které jsou spojeny s tímto pravidlem. `$(...)` Hodnoty jsou označovány jako *makra*. A *– makro* kompilace konstanta, která může odkazovat na hodnotu, která je definována pomocí sady Visual Studio nebo systém MSBuild, nebo hodnotu definovanou uživatelem. Pomocí makra namísto pevně definovaných hodnot, jako je například cesty k adresářům, můžete snadněji sdílet nastavení vlastností mezi počítači a mezi verzemi sady Visual Studio a lépe tak zajistit správnou funkci v účasti nastavení projektu [ dědičnost vlastnosti](project-property-inheritance.md). 

![Stránky vlastností projektu](media/project_property_pages_vc.png "Project_Property_Pages_VC")

Chcete-li zobrazit hodnoty všech dostupných maker slouží Editor vlastností. Makra jsou popsány v [makra stránky vlastností](#bkmkPropertiesVersusMacros) části dále v tomto článku.)

### <a name="predefined-macros"></a>Předdefinovaná makra

*globální makra*<br/>
Platí pro všechny položky v konfiguraci projektu. Má syntaxi `$(name)`. Příkladem globálního makra je `$(VCInstallDir)`, který ukládá do kořenového adresáře instalace sady Visual Studio. Globální makro odpovídá `PropertyGroup` v nástroji MSBuild.

*makra položky*<br/>
Má syntaxi `%(name)`. U souboru je makro položky platné pouze pro daný soubor – můžete například použít `%(AdditionalIncludeDirectories)` k určení adresářů souborů, které platí pouze pro určitý soubor k zahrnutí. Tento druh položky makro odpovídá `ItemGroup` metadat v nástroji MSBuild. Pokud se používá v kontextu konfigurace projektu, platí makro položky pro všechny soubory určitého typu. Například C/C++ **Definice preprocesoru** vlastnost konfigurace `%(PreprocessorDefinitions)` makro položky, která se vztahuje na všechny soubory .cpp v projektu. Tento druh položky makro odpovídá `ItemDefinitionGroup` metadat v nástroji MSBuild. Další informace najdete v tématu [definice položek](/visualstudio/msbuild/item-definitions).

### <a name="user-defined-macros"></a>Uživatelská makra

Můžete vytvořit *uživatelská makra* pro použití jako proměnných při sestavování projektu. Můžete například vytvořit uživatelem definované makro poskytující hodnotu pro vlastní krok sestavení nebo pro vlastní nástroj sestavení. Uživatelem definované makro je pár název/hodnota. V souboru projektu, použijte **$(**<em>název</em>**)** zápisu pro přístup k hodnotě.

Uživatelem definované makro je uloženo v seznamu vlastností. Pokud váš projekt zatím neobsahuje seznam vlastností, můžete vytvořit podle pokynů v části [sdílené složky nebo resuse nastavení projektu Visual Studio C++](#bkmkPropertySheets).

#### <a name="to-create-a-user-defined-macro"></a>Vytvoření uživatelem definovaného makra

1. V **Správce vlastností** okna (v řádku nabídek zvolte **zobrazení**, **Správce vlastností**), otevřete místní nabídku pro seznam vlastností (název má koncovku .user) a klikněte na tlačítko Vlastnosti. **Stránky vlastností** otevře se dialogové okno pro tento seznam vlastností.

1. V levém podokně dialogového okna, vyberte **uživatelská makra**. V pravém podokně, vyberte **přidat makro** tlačítko Otevřít **přidat uživatelské makro** dialogové okno.

1. V dialogovém okně zadejte název a hodnotu makra. Volitelně můžete vybrat **nastavit toto makro jako proměnnou prostředí v prostředí pro sestavení** zaškrtávací políčko.

## <a name="property_editor">Editor vlastností</a>

Editor vlastností můžete použít ke změně některých vlastností řetězce a k výběru maker jako hodnot. Editor vlastností otevřete tak, že vyberete vlastnost na stránce vlastností a pak kliknete na šipku dolů na pravé straně. Pokud rozevírací seznam obsahuje  **\<Upravit >**, pak je můžete ji vybrat a zobrazit tak Editor vlastností pro danou vlastnost.

![Property&#95;Editor&#95;Dropdown](media/property_editor_dropdown.png "Property_Editor_Dropdown")

V editoru vlastností můžete použít **makra** tlačítko Zobrazit dostupná makra a jejich aktuálními hodnotami. Následující ilustrace zobrazuje Editor vlastností pro **další adresáře souborů k zahrnutí** vlastnost po **makra** výběru tlačítka. Když **Zdědit z nadřazené nebo projektu výchozí** zaškrtávací políčko zaškrtnuto a přidáte novou hodnotu, připojí se ke všem hodnotám, které jsou aktuálně děděny. Pokud zaškrtnutí políčka zrušíte, nahradí nová hodnota zděděné hodnoty. Ve většině případů ponechte políčko zaškrtnuté.

![Property editor, Visual C&#43;&#43;](media/propertyeditorvc.png "PropertyEditorVC")

## <a name="add-an-include-directory-to-the-set-of-default-directories"></a>Přidání adresáře vkládaných do sady výchozích adresářů

Přidáváte-li do projektu adresář vkládaných souborů, je důležité, abyste nepřepsali všechny výchozí adresáře. Správný způsob přidání adresáře je připojit novou cestu, například "C:\MyNewIncludeDir\"a potom připojit **$(IncludePath)** – makro do hodnoty vlastnosti.

## <a name="quickly-browse-and-search-all-properties"></a>Rychle procházet a vyhledat všechny vlastnosti

**Všechny možnosti** stránka vlastností (v části **vlastnosti konfigurace &#124; C/C++** uzlu v **stránky vlastností** dialogové okno) nabízí rychlý způsob procházení a vyhledávání vlastnosti, které jsou k dispozici v aktuálním kontextu. Obsahuje speciální vyhledávací pole s jednoduchou syntaxí umožňující filtrovat výsledky:

Bez předpony:<br/>
Prohledávat pouze názvy vlastností (podřetězec bez rozlišení velkých a malých písmen)

'/' nebo '-':<br/>
Prohledávat pouze přepínače kompilátoru (předpona nerozlišující velká a malá písmena)

v:<br/>
Prohledávat pouze hodnoty (podřetězec bez rozlišení velkých a malých písmen)

## <a name="set-environment-variables-for-a-build"></a>Nastavení proměnných prostředí pro sestavení

Kompilátor MSVC (cl.exe) rozpoznává určité proměnné prostředí, konkrétně LIB, LIBPATH, PATH či INCLUDE. Při sestavení s IDE vlastnosti, které jsou nastaveny [VC ++ Directories Property Page](reference/vcpp-directories-property-page.md) stránku vlastností se používají k nastavení těchto proměnných prostředí. Pokud jsou hodnoty proměnných LIB, LIBPATH a INCLUDE již nastaveny, například pomocí příkazového řádku pro vývojáře, nahradí se hodnotami odpovídajících vlastností MSBuild. Sestavení poté připojí k proměnné PATH hodnotu vlastnosti spustitelných adresářů Adresáře VC++. Můžete nastavit proměnné prostředí definované uživatelem vytvořené uživatelem definované makro a potom zaškrtnete políčko s textem **nastavit toto makro jako proměnnou prostředí v prostředí pro sestavení**.

## <a name="set-environment-variables-for-a-debugging-session"></a>Nastavení proměnných prostředí pro relaci ladění

V levém podokně projektu **stránky vlastností** dialogového okna rozbalte **vlastnosti konfigurace** a pak vyberte **ladění**.

V pravém podokně upravte **prostředí** nebo **sloučit prostředí** nastavení projektu a klikněte na tlačítko **OK** tlačítko.

## <a name="in-this-section"></a>V tomto oddílu

[Sdílené složky nebo resuse nastavení projektu Visual Studio](create-reusable-property-configurations.md)<br/>
Jak vytvořit soubor PROPS se nastavení vlastního sestavení, které je možné sdílet nebo resused.

[Dědičnost vlastnosti projektu](project-property-inheritance.md)<br/>
Popisuje pořadí vyhodnocování .props, .targets, souborů .vcxproj a proměnných prostředí v procesu sestavení.

[Úprava vlastností a cílů beze změny souboru projektu](modify-project-properties-without-changing-project-file.md)<br/>
Jak vytvořit dočasné sestavení nastavení, aniž byste museli upravovat soubor projektu. 

## <a name="see-also"></a>Viz také:

[Visual Studio Projects - C++](creating-and-managing-visual-cpp-projects.md)<br/>
[Struktura souborů .vcxproj a .props](reference/vcxproj-file-structure.md)<br/>
[Soubory XML stránky vlastností](reference/property-page-xml-files.md)<br/>
