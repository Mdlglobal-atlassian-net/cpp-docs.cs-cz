---
title: Používání knihovny a komponenty v projektech C++
ms.date: 12/10/2018
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: dff057977e6b6ff0c36d3a888bc4d5c3aa778576
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038759"
---
# <a name="consuming-libraries-and-components"></a>Používání knihovny a součásti

Často projektu C++ musí volat funkce nebo přístup k datům v binárním souboru, například statické knihovny (soubory .lib), knihovny DLL, součást prostředí Windows Runtime, komponenty modelu COM nebo sestavení .NET. V těchto případech budete muset nakonfigurovat projekt tak, aby bylo možné najít tento binární soubor v okamžiku sestavení. Konkrétní kroky závisí na typu projektu, typ binárního souboru, a zda má být sestaven binární soubor ve stejném řešení jako váš projekt. 

## <a name="consuming-libraries-downloaded-via-vcpkg"></a>Použití knihovny stáhli prostřednictvím vcpkg

Používat knihovnu, kterou jste si stáhli s použitím **vcpkg** Správce balíčků, můžete ignorovat podle následujících pokynů. See [vcpkg: Správce balíčků jazyka C++ pro Windows, Linux a MacOS](vcpkg.md#integrate-with-visual-studio-windows) pro další informace.

## <a name="consuming-static-libraries"></a>Použití statické knihovny

Pokud váš projekt statické knihovny se vytváří ve stejném řešení:

1. #<a name="include-the-header-files-for-the-static-library-using-quotation-marks-in-a-typical-solution-the-path-will-start-with-library-project-name-intellisense-will-help-you-find-it"></a>Zahrnout soubory hlaviček pro statické knihovny pomocí uvozovek. V typické řešení bude cesta začínat `../<library project name>`. Technologie IntelliSense vám pomůže ho najít.
2. Přidejte odkaz na projekt statické knihovny. Klikněte pravým tlačítkem na **odkazy** pod uzlem projektu aplikace v **Průzkumníka řešení** a zvolte **přidat odkaz**. 

Pokud se statickou knihovnou není součástí řešení:

1. Klikněte pravým tlačítkem na uzel projektu aplikace v **Průzkumníka řešení** a klikněte na tlačítko **vlastnosti**. 
2. V **adresáře VC ++** vlastnosti stránky, přidejte cestu k adresáři, kde je umístěn soubor .lib v **cesty knihoven** a přidejte cestu pro soubory hlaviček knihovny v **adresáře souborů k zahrnutí** .  
3. V **Linker > vstup** vlastnost stránce, přidejte název .lib soubor **Další závislosti**.

## <a name="dynamic-link-libraries"></a>Dynamické knihovny

Pokud knihovna DLL se vytváří v rámci stejného řešení jako aplikace, postupujte podle stejných kroků jako u statické knihovny.

Pokud knihovna DLL není součástí řešení aplikací, musíte soubor knihovny DLL, záhlaví s prototypy exportovaných funkcí a tříd a .lib soubor, který obsahuje nezbytné informace o propojení.

1. Kopírovat knihovnu DLL do výstupní složky vašeho projektu nebo do jiné složky v cestě pro vyhledávání standardní Windows pro knihovny DLL. Zobrazit [pořadí hledání knihoven DLL](/windows/desktop/dlls/dynamic-link-library-search-order).
2. Postupujte podle kroků 1-3 pro statické knihovny k poskytování cesty k záhlaví a .lib soubor.

## <a name="com-objects"></a>COM – objekty

Pokud vaše nativní aplikace C++ potřebuje používat objekt modelu COM a je *zaregistrovaný*, pak vše, co musíte udělat je volání funkce CoCreateInstance a předejte mu identifikátor CLSID objektu. Systém se ji najít v registru Windows a načtěte jej. A C++/CLI projektu může spotřebovat objekt modelu COM, stejným způsobem, nebo tak, že přidáte odkaz na z **Add References > COM** seznamu a pracovat s nimi prostřednictvím jeho [obálka volatelná za běhu](/dotnet/framework/interop/runtime-callable-wrapper). 

## <a name="net-assemblies-and-windows-runtime-components"></a>Sestavení .NET a součásti Windows Runtime

V UPW nebo C++vyhodnocovací projekty, využívají sestavení .NET nebo součástí prostředí Windows Runtime tak, že přidáte *odkaz* k sestavením nebo komponentou. V části **odkazy** uzel v UPW nebo C++vyhodnocovací projektu se zobrazí odkazy na běžně používané komponenty. Klikněte pravým tlačítkem na **odkazy** uzel v **Průzkumníka řešení** zobrazíte **správce odkazů** a projděte si další součásti, které jsou známé systému. Klikněte na tlačítko **Procházet** tlačítko Přejít na libovolnou složku, kde se nachází vlastní komponentu. Protože sestavení .NET a součásti prostředí Windows Runtime obsahují informace o předdefinovaných typech, můžete zobrazit jejich metod a tříd kliknutím pravým tlačítkem a vyberete **zobrazit v prohlížeči objektů**. 

## <a name="reference-properties"></a>Vlastnosti odkazu

Každý druh odkazu má vlastnosti. Vlastnosti můžete zobrazit výběrem odkazu v Průzkumníku řešení a stisknutím klávesy **Alt + Enter**, nebo pravým tlačítkem myši a zvolíte možnost **vlastnosti**. Některé vlastnosti jsou jen pro čtení a některé je možné upravit. Však obvykle není nutné ručně upravit tyto vlastnosti.

### <a name="activex-reference-properties"></a>Vlastnosti odkazu ActiveX

Vlastnosti odkazu ActiveX jsou dostupné pouze pro odkazy na komponenty modelu COM. Tyto vlastnosti se zobrazí, jenom když vyberete komponenty modelu COM v **odkazy** podokně. Vlastnosti nelze změnit.

- **Úplná cesta ovládacího prvku**

   Zobrazuje cestu k adresáři odkazovaného ovládacího prvku.

- **GUID ovládacího prvku**

   Zobrazuje identifikátor GUID pro ovládací prvek ActiveX.

- **Verze ovládacího prvku**

   Zobrazuje verze odkazovaného ovládacího prvku ActiveX.

- **Název knihovny typů**

   Zobrazí název odkazované knihovny typů.

- **Nástroj obálky**

   Zobrazí nástroj, který se používá k vytvoření sestavení interop z odkazované knihovny COM nebo ovládacího prvku ActiveX.

### <a name="assembly-reference-properties-ccli"></a>Vlastnosti odkazu na sestavení (C++vyhodnocovací)

Vlastnosti odkazu na sestavení jsou k dispozici pouze pro odkazy na sestavení rozhraní .NET Framework v C++vyhodnocovací projekty. Tyto vlastnosti se zobrazí jenom v případě, že je vybraná sestavení rozhraní .NET Framework v **odkazy** podokně. Vlastnosti nelze změnit.

- **Relativní cesta**

   Zobrazuje relativní cesta z adresáře projektu k odkazovanému sestavení.

### <a name="build-properties"></a>Vlastnosti sestavení

Následující vlastnosti jsou k dispozici na různé typy odkazů. Umožňují určit, jak sestavení s odkazy.

- **Kopírovat místní**

   Určuje, jestli se mají automaticky kopírovat odkazované sestavení do cílového umístění během sestavení.

- **Zkopírovat místní satelitní sestavení (C++vyhodnocovací)**

   Určuje, jestli se mají automaticky kopírovat satelitní sestavení odkazovaného sestavení do cílového umístění během sestavení. Použít jenom v případě **Kopírovat místně** je **true**.

- **Výstup referenčního sestavení**

   Určuje, že toto sestavení se používá v procesu sestavení. Pokud **true**, sestavení se používá na příkazový řádek kompilátoru během sestavení.

### <a name="project-to-project-reference-properties"></a>Vlastnosti odkazu typu projekt projekt

Definujte následující vlastnosti *odkaz typu projekt projekt* z projektu, který je vybraný v **odkazy** podokno do jiného projektu ve stejném řešení. Další informace najdete v tématu [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).

- **Propojit závislé položky knihoven**

   Pokud je tato vlastnost **True**, systém projektu propojeny do závislý projekt lib souborů, které jsou vytvářeny nezávislé projektem. Obvykle můžete zadat **True**.

- **Project Identifier**

   Jednoznačně identifikuje nezávislé projektu. Hodnota vlastnosti je interní systém identifikátor GUID, který nemůže být upraven.

- **Použít vstupy závislých položek knihoven**

   Pokud je tato vlastnost **False**, systém projektu nebude propojení do závislého projektu soubory .obj pro knihovnu vytvářených nezávislé projektu. V důsledku toho tato hodnota zakáže přírůstkové propojení. Obvykle můžete zadat **False** protože vytváření aplikace může trvat dlouhou dobu, pokud existují mnoho nezávislé projektů.

### <a name="read-only-reference-properties-com--net"></a>Vlastnosti jen pro čtení odkazu (COM a .NET)

Následující vlastnosti se nacházejí na odkazy na sestavení modelu COM a .NET a nejde změnit.

- **Název sestavení**

   Zobrazí název sestavení pro odkazované sestavení.

- **Jazyková verze**

   Zobrazí jazyková verze vybraného odkazu.

- **Popis**

   Zobrazí popis vybraného odkazu.

- **Úplná cesta**

   Zobrazuje cestu k adresáři odkazovaných sestavení.

- **Identita**

   .NET Frameworkassemblies zobrazí úplnou cestu. Pro komponenty modelu COM zobrazuje identifikátor GUID.

- **Popisek**

   Zobrazí popisek odkazu.

- **Název**

   Zobrazí název odkazu.

- **Token veřejného klíče**

   Zobrazí token veřejného klíče, který se používá k identifikaci odkazovaného sestavení.

- **Silným názvem**

   `true` Pokud má odkazované sestavení silný název. Silně pojmenované sestavení mají je jedinečné verze.

- **Verze**

   Verze odkazovaného sestavení zobrazí.

## <a name="see-also"></a>Viz také:

[Odkaz na stránku vlastností projektu jazyka C++](reference/property-pages-visual-cpp.md)<br>
[Nastavení vlastností kompilátoru a sestavení C++ v sadě Visual Studio](working-with-project-properties.md)