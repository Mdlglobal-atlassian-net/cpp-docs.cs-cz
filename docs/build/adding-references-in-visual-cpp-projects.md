---
title: Využívání knihoven a komponent v projektech C++
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: c7facb82054eed4ef28c52830b8a3079eecb7fdc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169952"
---
# <a name="consuming-libraries-and-components"></a>Využívání knihoven a komponent

Projekt C++ potřebuje často volat funkce nebo získat přístup k datům v binárním souboru, jako je statická knihovna (soubory. lib), knihovna DLL, prostředí Windows Runtime komponenty, komponenta modelu COM nebo sestavení .NET. V těchto případech je nutné nakonfigurovat projekt tak, aby mohl najít tento binární soubor v čase sestavení. Konkrétní postup závisí na typu vašeho projektu, typu binárního souboru a na tom, zda je binární soubor sestaven ve stejném řešení jako váš projekt.

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>Využívání knihoven stažených prostřednictvím vcpkg

Pokud chcete využít knihovnu, kterou jste stáhli pomocí Správce balíčků **vcpkg** , můžete následující pokyny ignorovat. Další informace najdete v tématu [vcpkg: Správce balíčků C++ pro Windows, Linux a MacOS](vcpkg.md#integrate-with-visual-studio-windows) .

## <a name="consuming-static-libraries"></a>Spotřebovávání statických knihoven

Pokud je váš projekt statické knihovny sestaven ve stejném řešení:

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>Zahrňte hlavičkové soubory pro statickou knihovnu pomocí uvozovek. V typickém řešení bude cesta začínat `../<library project name>`. IntelliSense vám pomůže ho najít.
2. Přidejte odkaz na projekt statické knihovny. Klikněte pravým tlačítkem na **odkazy** v uzlu projekt aplikace v **Průzkumník řešení** a vyberte možnost **Přidat odkaz**.

Pokud Statická knihovna není součástí řešení:

1. Klikněte pravým tlačítkem myši na uzel projekt aplikace v **Průzkumník řešení** a pak zvolte **vlastnosti**.
2. Na stránce vlastností **adresářů VC + +** přidejte cestu k adresáři, kde se nachází soubor. lib v **cestě knihovny** a přidejte cestu k hlavičkovým souborům knihovny v **adresáři include**.  
3. Na stránce vlastnosti **linkeru > Input** přidejte název souboru. lib do **dalších závislostí**.

## <a name="dynamic-link-libraries"></a>Knihovny dynamického propojení

Pokud je knihovna DLL sestavena jako součást stejného řešení jako aplikace, použijte stejný postup jako u statické knihovny.

Pokud knihovna DLL není součástí řešení aplikace, budete potřebovat soubor DLL, hlavičky s prototypy pro exportované funkce a třídy a soubor. lib, který poskytuje nezbytné informace pro propojení.

1. Zkopírujte knihovnu DLL do výstupní složky vašeho projektu nebo do jiné složky ve standardní cestě hledání Windows pro knihovny DLL. Viz [pořadí hledání dynamické knihovny](/windows/win32/dlls/dynamic-link-library-search-order).
2. Použijte kroky 1-3 pro statické knihovny k poskytnutí cest k souborům Headers a. lib.

## <a name="com-objects"></a>COM – objekty

Pokud vaše nativní aplikace C++ potřebuje spotřebovat objekt COM a tento objekt je *zaregistrován*, pak vše, co musíte udělat, je zavolat funkci CoCreateInstance a předat identifikátor CLSID objektu. Systém ho najde v registru Windows a načte ho. Projekt C++/CLI může spotřebovat objekt modelu COM stejným způsobem nebo přidáním odkazu na odkaz **> seznamu com** a jeho využívání prostřednictvím obálky s možností volání [za běhu](/dotnet/framework/interop/runtime-callable-wrapper).

## <a name="net-assemblies-and-windows-runtime-components"></a>.NET – sestavení a součásti prostředí Windows Runtime

V projektech UWP nebo C++/CLI můžete využívat sestavení .NET nebo prostředí Windows Runtime komponenty přidáním *odkazu* na sestavení nebo komponentu. Pod uzlem **odkazy** v projektu UWP nebo C++/CLI vidíte odkazy na běžně používané komponenty. Kliknutím pravým tlačítkem na uzel **odkazy** v **Průzkumník řešení** otevřete **Správce odkazů** a procházejte dalšími komponentami, které systém zná. Kliknutím na tlačítko **Procházet** přejděte do složky, ve které je umístěna vlastní komponenta. Vzhledem k tomu, že komponenty sestavení a prostředí Windows Runtime .NET obsahují vestavěné informace o typu, můžete zobrazit své metody a třídy kliknutím pravým tlačítkem a výběrem možnosti **Zobrazit v prohlížeč objektů**.

## <a name="reference-properties"></a>Vlastnosti odkazu

Každý druh odkazu má vlastnosti. Vlastnosti můžete zobrazit tak, že vyberete odkaz v Průzkumník řešení a stisknete **ALT + ENTER**nebo jinak kliknete pravým tlačítkem a kliknete na **vlastnosti**. Některé vlastnosti jsou jen pro čtení a některé můžou být upravené. Tyto vlastnosti však obvykle není nutné měnit.

### <a name="activex-reference-properties"></a>Vlastnosti odkazu ActiveX

Vlastnosti odkazu ActiveX jsou k dispozici pouze pro odkazy na komponenty modelu COM. Tyto vlastnosti jsou zobrazeny pouze v případě, že je v podokně **odkazy** VYBRÁNA komponenta com. Vlastnosti nelze upravovat.

- **Úplná cesta ovládacího prvku**

   Zobrazuje cestu k adresáři odkazovaného ovládacího prvku.

- **Identifikátor GUID ovládacího prvku**

   Zobrazuje identifikátor GUID pro ovládací prvek ActiveX.

- **Verze ovládacího prvku**

   Zobrazuje verzi odkazovaného ovládacího prvku ActiveX.

- **Název knihovny typů**

   Zobrazuje název odkazované knihovny typů.

- **Nástroj Obálka**

   Zobrazuje nástroj, který se používá k sestavení definičního sestavení z odkazované knihovny COM nebo ovládacího prvku ActiveX.

### <a name="assembly-reference-properties-ccli"></a>Vlastnosti odkazu na sestavení (C++/CLI)

Vlastnosti odkazu na sestavení jsou k dispozici pouze pro odkazy na .NET Framework sestavení v projektech C++/CLI. Tyto vlastnosti jsou zobrazeny pouze v případě, že je vybráno sestavení .NET Framework v podokně **odkazy** . Vlastnosti nelze upravovat.

- **Relativní cesta**

   Zobrazuje relativní cestu z adresáře projektu k odkazovanému sestavení.

### <a name="build-properties"></a>Vlastnosti sestavení

Následující vlastnosti jsou k dispozici na různých druzích odkazů. Umožňují určit, jak se mají vytvářet odkazy.

- **Kopírovat místní**

   Určuje, zda se má odkazované sestavení během sestavení automaticky kopírovat do cílového umístění.

- **Kopírovat místní satelitní sestavení (C++/CLI)**

   Určuje, zda se mají při sestavení automaticky kopírovat satelitní sestavení odkazovaného sestavení do cílového umístění. Používá se jenom v případě, že je **místní kopie** **true**.

- **Výstup referenčního sestavení**

   Určuje, že toto sestavení se používá v procesu sestavení. Při **hodnotě true**se sestavení používá v příkazovém řádku kompilátoru během sestavení.

### <a name="project-to-project-reference-properties"></a>Vlastnosti odkazu z projektu na projekt

Následující vlastnosti definují odkaz typu *projekt-projekt* z projektu, který je vybrán v podokně **odkazy** , na jiný projekt ve stejném řešení. Další informace naleznete v tématu [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).

- **Propojit závislosti knihoven**

   Je-li tato vlastnost **pravdivá**, projektový systém odkazuje do závislého projektu na soubory. lib, které jsou vytvářeny nezávislým projektem. Obvykle zadáte **hodnotu true**.

- **Identifikátor projektu**

   Jednoznačně identifikuje nezávislý projekt. Hodnota vlastnosti je interní GUID systému, který nelze změnit.

- **Použít vstupy závislosti knihoven**

   Pokud je tato vlastnost **false**, projektový systém nebude propojen se soubory. obj knihovny, které jsou vytvářeny nezávislým projektem, do závislého projektu. V důsledku toho tato hodnota zakáže přírůstkové propojování. Obvykle zadáte **hodnotu false** , protože sestavování aplikace může trvat dlouhou dobu, pokud existuje mnoho nezávislých projektů.

### <a name="read-only-reference-properties-com--net"></a>Vlastnosti odkazu jen pro čtení (COM & .NET)

Následující vlastnosti jsou nalezeny v odkazech na sestavení COM a .NET a nelze je upravit.

- **Název sestavení**

   Zobrazí název sestavení pro odkazované sestavení.

- **Kultura**

   Zobrazí jazykovou verzi vybraného odkazu.

- **Popis**

   Zobrazí popis vybraného odkazu.

- **Úplná cesta**

   Zobrazuje cestu k adresáři odkazovaného sestavení.

- **Identita**

   V případě rozhraní .NET Frameworkassemblies zobrazí úplnou cestu. V případě komponent modelu COM zobrazuje identifikátor GUID.

- **Popisek**

   Zobrazí popisek odkazu.

- **Název**

   Zobrazí název odkazu.

- **Token veřejného klíče**

   Zobrazí token veřejného klíče, který se používá k identifikaci odkazovaného sestavení.

- **Silný název**

   `true`, pokud má odkazované sestavení silný název. Silné pojmenované sestavení má jedinečnou verzi.

- **Verze**

   Zobrazuje verzi odkazovaného sestavení.

## <a name="see-also"></a>Viz také

[Referenční dokumentace stránky vlastností projektu C++](reference/property-pages-visual-cpp.md)<br>
[Nastavení vlastností kompilátoru a sestavení C++ v sadě Visual Studio](working-with-project-properties.md)
