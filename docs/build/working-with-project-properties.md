---
title: Nastavení vlastností kompilátoru a sestavení C++ v sadě Visual Studio
description: Pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio můžete změnit kompilátor C++ a možnosti linkeru a další nastavení sestavení.
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
ms.openlocfilehash: 6c05dd00324113819dd145e46bf10dfeb96a66a3
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078240"
---
# <a name="set-compiler-and-build-properties"></a>Nastavení vlastností kompilátoru a sestavení

V integrovaném vývojovém prostředí jsou všechny informace, které jsou nutné k sestavení projektu, zpřístupněny jako *vlastnosti*. Tyto informace zahrnují název aplikace, rozšíření (například knihovnu DLL, LIB, EXE), možnosti kompilátoru, Možnosti linkeru, nastavení ladicího programu, vlastní kroky sestavení a mnoho dalších věcí. Pro zobrazení a úpravu těchto vlastností obvykle používáte *stránky vlastností* . Chcete-li získat přístup ke stránkám vlastností, vyberte z hlavní nabídky vlastnosti **projekt** > **_ProjectName_ ** , nebo klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **vlastnosti**.

## <a name="default-properties"></a>Výchozí vlastnosti

Když vytvoříte projekt, systém přiřadí hodnoty pro různé vlastnosti. Výchozí hodnoty se mírně liší v závislosti na typu projektu a na možnostech, které zvolíte v Průvodci aplikací. Například projekt ATL má vlastnosti týkající se souborů MIDL, ale ty nejsou v základní konzolové aplikaci přítomny. Výchozí vlastnosti jsou zobrazeny v podokně obecné na stránkách vlastností:

![Výchozí hodnoty projektu Visual C&#43;&#43; ](media/visual-c---project-defaults.png "Výchozí nastavení projektu Visual C++")

## <a name="applying-properties-to-build-configurations-and-target-platforms"></a>Použití vlastností pro sestavení konfigurací a cílových platforem

Některé vlastnosti, například název aplikace, se vztahují na všechny varianty sestavení, bez ohledu na cílovou platformu nebo na sestavení pro ladění nebo vydání. Ale většina vlastností je závislá na konfiguraci. Důvodem je, že kompilátor musí znát, na jaké konkrétní platformě bude program běžet, a jaké konkrétní možnosti kompilátoru použít k vygenerování správného kódu. Proto když nastavíte vlastnost, je důležité věnovat pozornost, na kterou konfiguraci a platformu má nová hodnota platit. Měl by se použít jenom pro ladění sestavení Win32, nebo by se měl vztahovat taky na ladění ARM a ladění x64? Například vlastnost **optimalizace** ve výchozím nastavení je nastavena na hodnotu **maximalizovat rychlost (/O2)** v konfiguraci vydané verze, ale v konfiguraci ladění je zakázána.

Stránky vlastností jsou navržené tak, aby se vždy zobrazila a v případě potřeby změnila konfigurace a platforma, na které se má hodnota vlastnosti vztahovat. Následující obrázek znázorňuje stránky vlastností s informacemi o konfiguraci a platformě v seznamech v horní části. Pokud je zde nastavena vlastnost **optimalizace** , bude použita pouze pro ladění sestavení Win32, což se stane aktivní konfigurací, jak je znázorněno na červené šipky.

![Stránky vlastností&#43;&#43; jazyka Visual C ukazující aktivní konfiguraci](media/visual-c---property-pages-showing-active-configuration.png "Visual C++ stránek vlastností zobrazujících aktivní konfiguraci")

Následující ilustrace znázorňuje stejnou stránku vlastností projektu, ale konfigurace byla změněna na Release. Všimněte si jiné hodnoty vlastnosti optimalizace. Všimněte si také, že aktivní konfigurace je stále ladit. Tady můžete nastavit vlastnosti pro jakoukoli konfiguraci. nemusí být aktivní.

![Stránky vlastností&#43;&#43; v jazyce Visual C++ znázorňující konfiguraci vydané verze](media/visual-c---property-pages-showing-release-config.png "Visual C++ stránky vlastností zobrazující konfiguraci vydané verze")

## <a name="target-platforms"></a>Cílové platformy

*Cílová platforma* odkazuje na druh zařízení nebo operačního systému, na kterém se spustitelný soubor spustí. Projekt můžete sestavit pro více než jednu platformu. Dostupné cílové platformy pro projekty C++ závisí na typu projektu. zahrnují, ale nejsou omezené na Win32, x64, ARM, Android a iOS.     Cílová platforma **x86** , která se může zobrazit v **Configuration Manager** , je v nativních projektech C++ shodná s **Win32** . Win32 znamená 32 Windows a **x64** znamená 64 bitových oken. Další informace o těchto dvou platformách najdete v tématu [spouštění 32CH aplikací](/windows/win32/WinProg64/running-32-bit-applications).

Hodnota **libovolné** cílové platformy procesoru, která se může zobrazit v **Configuration Manager** nemá žádný vliv na nativní projekty C++; je relevantní pro C++/CLI a jiné typy projektů .NET. Další informace najdete v tématu [/CLRIMAGETYPE (určení typu image CLR)](reference/clrimagetype-specify-type-of-clr-image.md).

Další informace o nastavení vlastností pro sestavení pro ladění naleznete v tématu:

- [Nastavení projektu pro konfiguraci ladění jazyka C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)
- [Nastavení a příprava ladicího programu](/visualstudio/debugger/debugger-settings-and-preparation)
- [Příprava ladění: Visual C++ typy projektů](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)
- [Zadání symbolu (.pdb) a zdrojových souborů v ladicím programu sady Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)

## <a name="c-compiler-and-linker-options"></a>Kompilátor C++ a možnosti linkeru

Kompilátor jazyka C++ a možnosti linkeru jsou umístěny pod uzlem **C/C++** a **linker** v levém podokně v části **Vlastnosti konfigurace**. Tyto překlady přímo do možností příkazového řádku, které budou předány kompilátoru. Pokud si chcete přečíst dokumentaci ke konkrétní možnosti, vyberte možnost v prostředním podokně a stiskněte klávesu **F1**. Nebo můžete procházet dokumentaci pro všechny možnosti na [MSVC možnosti kompilátoru](reference/compiler-options.md) a [Možnosti linkeru MSVC](reference/linker-options.md).

Dialogové okno **stránky vlastností** zobrazuje pouze stránky vlastností, které jsou relevantní pro aktuální projekt. Pokud například projekt nemá soubor .idl, stránka s vlastnostmi MIDL se nezobrazí. Další informace o nastavení na jednotlivých stránkách vlastností naleznete na [stránce vlastností (C++)](reference/property-pages-visual-cpp.md).

## <a name="directory-and-path-values"></a>Hodnoty adresáře a cesty

Nástroj MSBuild podporuje použití konstant v čase kompilace nazývaných "makra" pro určité řetězcové hodnoty, včetně adresářů a cest. Tyto stránky jsou zpřístupněny na stránkách vlastností, kde je můžete odkazovat a upravovat pomocí [editoru vlastností](#property_editor).

Následující obrázek znázorňuje stránky vlastností projektu Visual Studio C++. V levém podokně je vybráno *pravidlo* **adresáře VC + +** a v pravém podokně jsou uvedeny vlastnosti, které jsou spojeny s tímto pravidlem. `$(...)` Hodnoty se nazývají *makra*. *Makro* je konstanta v čase kompilace, která může odkazovat na hodnotu, která je definována v aplikaci Visual Studio nebo v systému MSBuild, nebo na hodnotu definovanou uživatelem. Pomocí maker namísto pevně zakódovaných hodnot, jako jsou například cesty k adresářům, lze snadněji sdílet nastavení vlastností mezi počítači a mezi verzemi sady Visual Studio a můžete lépe zajistit, aby se nastavení projektu správně účastnilo v [dědičnosti vlastností](project-property-inheritance.md).

![Stránky vlastností projektu](media/project_property_pages_vc.png "Project_Property_Pages_VC")

Pomocí editoru vlastností můžete zobrazit hodnoty všech dostupných maker.

### <a name="predefined-macros"></a>Předdefinovaná makra

*globální makra*<br/>
Platí pro všechny položky v konfiguraci projektu. Má syntaxi `$(name)`. Příkladem globálního makra je `$(VCInstallDir)`, který ukládá kořenový adresář instalace sady Visual Studio. Globální makro odpovídá `PropertyGroup` v nástroji MSBuild.

*makra položky*<br/>
Má syntaxi `%(name)`. V případě souboru se makro položky vztahuje pouze na tento soubor – například můžete použít `%(AdditionalIncludeDirectories)` k určení adresářů include, které se vztahují pouze na konkrétní soubor. Tento druh makra položky odpovídá `ItemGroup` metadatům v nástroji MSBuild. Pokud se používá v kontextu konfigurace projektu, platí makro položky pro všechny soubory určitého typu. Například **vlastnost konfigurace** preprocesoru C/C++ může využít makro `%(PreprocessorDefinitions)` položky, které se vztahuje na všechny soubory. cpp v projektu. Tento druh makra položky odpovídá `ItemDefinitionGroup` metadatům v nástroji MSBuild. Další informace naleznete v tématu [Definice položek](/visualstudio/msbuild/item-definitions).

### <a name="user-defined-macros"></a>Uživatelsky definovaná makra

Můžete vytvořit *uživatelsky definovaná makra* , která chcete použít jako proměnné v sestaveních projektu. Můžete například vytvořit uživatelem definované makro poskytující hodnotu pro vlastní krok sestavení nebo pro vlastní nástroj sestavení. Uživatelem definované makro je pár název/hodnota. V souboru projektu použijte při přístupu k hodnotě zápis **$ (**<em>Name</em>**)** .

Uživatelem definované makro je uloženo v seznamu vlastností. Pokud projekt ještě neobsahuje seznam vlastností, můžete ho vytvořit pomocí postupu v části [sdílení nebo opětovné použití nastavení projektu sady Visual Studio](create-reusable-property-configurations.md).

#### <a name="to-create-a-user-defined-macro"></a>Vytvoření uživatelem definovaného makra

1. Otevřete okno **Správce vlastností** . (Na panelu nabídek vyberte možnost **Zobrazit** > **Správce vlastností** nebo **Zobrazit** > **Další Správce vlastností systému Windows** > **Property Manager**.) Otevřete místní nabídku pro seznam vlastností (jeho název končí na. uživatel) a pak zvolte **vlastnosti**. Otevře se dialogové okno **stránky vlastností** pro tento seznam vlastností.

1. V levém podokně dialogového okna vyberte **uživatelská makra**. V pravém podokně klikněte na tlačítko **Přidat makro** a otevřete dialogové okno **Přidat uživatelské makro** .

1. V dialogovém okně zadejte název a hodnotu makra. Volitelně můžete zaškrtnout políčko **nastavit toto makro jako proměnnou prostředí v prostředí sestavení** .

## <a name=""></a><a name="property_editor">Editor vlastností</a>

Editor vlastností můžete použít ke změně některých vlastností řetězce a k výběru maker jako hodnot. Editor vlastností otevřete tak, že vyberete vlastnost na stránce vlastností a pak kliknete na šipku dolů na pravé straně. Pokud rozevírací seznam obsahuje ** \<>úprav **, můžete ho zvolit pro zobrazení editoru vlastností pro danou vlastnost.

![&#95;– rozevírací seznam&#95;editoru vlastností](media/property_editor_dropdown.png "Property_Editor_Dropdown")

V editoru vlastností můžete kliknutím na tlačítko **makra** zobrazit dostupná makra a jejich aktuální hodnoty. Následující ilustrace znázorňuje Editor vlastností pro vlastnost **Další adresáře include** po výběru tlačítka **makra** . Když je zaškrtnuto políčko **Zdědit z nadřazené hodnoty nebo výchozí hodnoty projektu** a přidáte novou hodnotu, připojí se ke všem hodnotám, které jsou v současné době zděděné. Pokud zaškrtnutí políčka zrušíte, nahradí nová hodnota zděděné hodnoty. Ve většině případů ponechte políčko zaškrtnuté.

![Editor vlastností, Visual C&#43;&#43;](media/propertyeditorvc.png "PropertyEditorVC")

## <a name="add-an-include-directory-to-the-set-of-default-directories"></a>Přidání adresáře include do sady výchozích adresářů

Přidáváte-li do projektu adresář vkládaných souborů, je důležité, abyste nepřepsali všechny výchozí adresáře. Správný způsob přidání adresáře je připojit novou cestu, například "C:\MyNewIncludeDir\"", a pak připojit makro **$ (IncludePath)** k hodnotě vlastnosti.

## <a name="quickly-browse-and-search-all-properties"></a>Rychlé procházení a hledání všech vlastností

Stránka vlastností **všechny možnosti** (pod uzlem **Vlastnosti konfigurace &#124; uzlu C/C++** v dialogovém okně **stránky vlastností** ) nabízí rychlý způsob procházení a vyhledávání vlastností, které jsou k dispozici v aktuálním kontextu. Obsahuje speciální vyhledávací pole s jednoduchou syntaxí umožňující filtrovat výsledky:

Bez předpony:<br/>
Prohledávat pouze názvy vlastností (podřetězec bez rozlišení velkých a malých písmen)

'/' nebo '-':<br/>
Prohledávat pouze přepínače kompilátoru (předpona nerozlišující velká a malá písmena)

v:<br/>
Prohledávat pouze hodnoty (podřetězec bez rozlišení velkých a malých písmen)

## <a name="set-environment-variables-for-a-build"></a>Nastavení proměnných prostředí pro sestavení

Kompilátor MSVC (CL. exe) rozpoznává určité proměnné prostředí, konkrétně LIB, LIBPATH, PATH a INCLUDE. Při sestavování pomocí integrovaného vývojového prostředí (IDE) jsou pro nastavení těchto proměnných prostředí použity vlastnosti, které jsou nastaveny na stránce vlastností [adresářů VC + +](reference/vcpp-directories-property-page.md) . Pokud jsou hodnoty proměnných LIB, LIBPATH a INCLUDE již nastaveny, například pomocí příkazového řádku pro vývojáře, nahradí se hodnotami odpovídajících vlastností MSBuild. Sestavení poté připojí k proměnné PATH hodnotu vlastnosti spustitelných adresářů Adresáře VC++. Uživatelsky definovanou proměnnou prostředí můžete nastavit vytvořením uživatelsky definovaného makra a následným zaškrtnutím políčka **nastavit toto makro jako proměnnou prostředí v prostředí sestavení**.

## <a name="set-environment-variables-for-a-debugging-session"></a>Nastavení proměnných prostředí pro relaci ladění

V levém podokně dialogového okna **stránky vlastností** projektu rozbalte položku **Vlastnosti konfigurace** a poté vyberte možnost **ladění**.

V pravém podokně upravte nastavení projektu **prostředí** nebo **Sloučit prostředí** a pak klikněte na tlačítko **OK** .

## <a name="in-this-section"></a>V tomto oddílu

[Sdílení a opakované použití nastavení projektu sady Visual Studio](create-reusable-property-configurations.md)<br/>
Jak vytvořit soubor. props s vlastním nastavením sestavení, které lze sdílet nebo znovu použít.

[Dědičnost vlastností projektu](project-property-inheritance.md)<br/>
Popisuje pořadí vyhodnocování pro soubory. props,. targets,. vcxproj a proměnné prostředí v procesu sestavení.

[Změna vlastností a cílů beze změny souboru projektu](modify-project-properties-without-changing-project-file.md)<br/>
Jak vytvořit dočasné nastavení sestavení bez nutnosti upravovat soubor projektu.

## <a name="see-also"></a>Viz také

[Projekty sady Visual Studio – C++](creating-and-managing-visual-cpp-projects.md)<br/>
[Struktura souborů .vcxproj a .props](reference/vcxproj-file-structure.md)<br/>
[Soubory XML stránky vlastností](reference/property-page-xml-files.md)<br/>
