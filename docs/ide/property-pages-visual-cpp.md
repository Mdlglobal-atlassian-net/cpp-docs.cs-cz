---
title: Stránky vlastností (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.NotAProp.Edit
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- Visual C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
ms.openlocfilehash: 4058f6574dcaa6d383295b63bfd27c5c1a0056aa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526446"
---
# <a name="property-pages-visual-c"></a>Stránky vlastností (Visual C++)

Pomocí stránky vlastností, můžete zadat nastavení pro projekty aplikace Visual Studio. Chcete-li otevřít **stránky vlastností** dialogové okno pro Visual Studio na projekt **projektu** nabídce zvolte **vlastnosti**.

Můžete zadat nastavení projektu tak, aby se vztahují všechny konfigurace sestavení, nebo můžete zadat vlastnosti jiného projektu pro každou konfiguraci sestavení. Můžete například zadat určitá nastavení pro konfiguraci vydané verze a další nastavení pro konfiguraci ladění.

Ne všechny stránky k dispozici jsou však nemusí být zobrazeny v **stránky vlastností** dialogové okno. Se zobrazují stránky, které závisí na typech souborů v projektu.

Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

Projekty bez Windows, naleznete v tématu [odkaz na stránku vlastností Linux C++](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="default-properties-vs-modified-properties"></a>Výchozí vlastnosti vs. Upravené vlastnosti

Při použití **nový projekt** dialogové okno Vytvořit projekt sady Visual Studio používá šablony zadaný projekt k inicializaci vlastnosti projektu. Proto hodnoty vlastností v šabloně lze chápat jako výchozí hodnoty pro daný typ projektu. V jiných typech projektů vlastnosti můžou mít různé výchozí hodnoty.

Hodnotu vlastnosti projektu se zobrazí tučně, pokud se změní. Vlastnost projektu můžete upravit z následujících důvodů:

- Průvodce aplikací změní vlastnost, protože vyžaduje hodnotu vlastnosti jiné než ten, který je zadán v šabloně projektu.

- Zadejte hodnotu jiné vlastnosti v **nový projekt** dialogové okno.

- Zadejte hodnotu jinou vlastnost na stránce vlastností projektu.

> [!TIP]
> Pokud chcete zobrazit poslední sadu hodnot vlastností, které používá MSBuild k sestavení projektu, zkontrolujte preprocesoru výstupního souboru, který můžete vytvořit pomocí tohoto příkazového řádku: **MSBuild / předzpracování:** *preprocessor_output_ Název souboru*<sub>optimalizované</sub> *project_filename*<sub>optimalizované</sub>

## <a name="resetting-properties"></a>Obnovení vlastnosti

Při prohlížení **stránky vlastností** dialogové okno pro projekt a projekt uzlu vybrána v **Průzkumníka řešení**, mnoho vlastností, můžete vybrat **Zdědit z nadřazené nebo projektu výchozí hodnoty** nebo změnit hodnotu jiným způsobem.

Při prohlížení **stránky vlastností** dialogové okno pro projekt a soubor je vybraný v **Průzkumníka řešení**, mnoho vlastností, můžete vybrat **Zdědit z nadřazené hodnoty nebo projektu výchozích hodnot** nebo změnit hodnotu jiným způsobem. Ale pokud projekt obsahuje mnoho souborů, které mají hodnoty vlastností, které se liší od výchozích hodnot projektu, projekt bude trvat déle vytvářet.

> [!TIP]
> Chcete-li aktualizovat **stránky vlastností** dialogové okno tak, aby zobrazil nejnovější voleb, zvolte **použít**.

Většinu výchozích hodnot projektu jsou výchozí nastavení systému (platforma). Některé výchozí vlastnosti projektu jsou odvozeny z šablony stylů, které se použijí při aktualizaci vlastností v **výchozí vlastnosti projektu** část **Obecné** konfigurace vlastností pro projekt. Další informace najdete v tématu [Obecná stránka vlastností (projekt)](../ide/general-property-page-project.md).

## <a name="specifying-user-defined-values"></a>Zadání uživatelem definované hodnoty

Je nutné zadat hodnotu pro určité vlastnosti. Alfanumerické znaky nebo názvy maker soubor projektu může obsahovat hodnotu definovanou uživatelem. Některé z těchto vlastností můžete provést pouze jednu hodnotu definovanou uživatelem, ale jiná přijímají seznam oddělený středníkem více hodnot.

K určení uživatelem definovanou hodnotu pro vlastnost nebo seznam, pokud vlastnost může trvat více uživatelem definované hodnoty ve sloupci vpravo od názvu vlastnosti, proveďte jednu z následujících akcí:

- Zadejte hodnotu nebo seznam hodnot.

- Klikněte na šipku rozevíracího seznamu. Pokud **upravit** je k dispozici, zvolte jej a poté do textového pole zadejte hodnotu nebo seznam hodnot. Alternativní způsob pro zadání seznamu je na samostatném řádku v textovém poli zadejte jednotlivé hodnoty. Na stránce vlastnosti se zobrazí hodnoty jako seznam oddělený středníkem.

   Chcete-li vložit jako hodnotu makro souboru projektu, zvolte **makra** a potom dvakrát klikněte na název makra.

- Klikněte na šipku rozevíracího seznamu. Pokud **Procházet** je k dispozici, zvolte jej a pak vyberte jednu nebo více hodnot.

Pro více Vážíme si toho vlastnost **Zdědit z nadřazené nebo projektu výchozích nastavení** možnost je k dispozici, když vyberte šipku dolů ve sloupci vpravo od názvu vlastnosti a pak zvolte **upravit**. Standardně je vybrána možnost.

Všimněte si, že stránka vlastností na aktuální úrovni pro více Vážíme si toho vlastnost, která dědí z jiné úrovně zobrazí pouze nastavení. Například, pokud je vybrán soubor v **Průzkumníka řešení** a výběr jazyka C/C++ **Definice preprocesoru** vlastnosti souborů definic se zobrazí, ale zděděné definice na úrovni projektu nejsou zobrazeny. K zobrazení aktuální úrovně a zděděné hodnoty, klikněte na šipku rozevíracího seznamu ve sloupci vpravo od názvu vlastnosti a klikněte na tlačítko **upravit**. Pokud používáte [model projektu Visual C++](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine), toto chování platí také pro objekty na souborech a projektech. To znamená když odešlete dotaz na hodnoty vlastnosti na úrovni souboru, nezískáte hodnoty této vlastnosti na úrovni projektu. Na úrovni projektu musíte explicitně získat hodnoty vlastnosti. Kromě toho některé zděděné hodnoty vlastnosti mohou pocházet z šablony stylů, která není přístupná prostřednictvím kódu programu.

## <a name="in-this-section"></a>V tomto oddílu

[Upřesnit, Nástroj Manifest, vlastnosti konfigurace, \<Projectname > dialogové okno stránky vlastností projektu](../ide/advanced-manifest-tool.md)

[Stránky vlastností příkazového řádku](../ide/command-line-property-pages.md)

[Stránka vlastností vlastního kroku sestavení: Obecné](../ide/custom-build-step-property-page-general.md)

[Přidávání odkazů na](../ide/adding-references-in-visual-cpp-projects.md)

[Obecná stránka vlastností (soubor)](../ide/general-property-page-file.md)

[Obecná stránka vlastností (projekt)](../ide/general-property-page-project.md)

[Obecné, Nástroj Manifest, vlastnosti konfigurace, \<Projectname > dialogové okno stránky vlastností projektu](../ide/general-manifest-tool-configuration-properties.md)

[HLSL – stránky vlastností](../ide/hlsl-property-pages.md)

[HLSL – stránky vlastností: Upřesnit](../ide/hlsl-property-pages-advanced.md)

[HLSL – stránky vlastností: Obecné](../ide/hlsl-property-pages-general.md)

[HLSL – stránky vlastností: Výstupní soubory](../ide/hlsl-property-pages-output-files.md)

[Vstup a výstup, Nástroj Manifest, vlastnosti konfigurace, \<Projectname > dialogové okno stránky vlastností projektu](../ide/input-and-output-manifest-tool.md)

[Izolované modely COM, Nástroj Manifest, vlastnosti konfigurace, \<Projectname > dialogové okno stránky vlastností projektu](../ide/isolated-com-manifest-tool.md)

[Stránky vlastností linkeru](../ide/linker-property-pages.md)

[Stránka vlastností spravovaných prostředků](../ide/managed-resources-property-page.md)

[Stránky vlastností nástroje manifest](../ide/manifest-tool-property-pages.md)

[MIDL – stránky vlastností](../ide/midl-property-pages.md)

[MIDL – stránky vlastností: Upřesnit](../ide/midl-property-pages-advanced.md)

[MIDL – stránky vlastností: Obecné](../ide/midl-property-pages-general.md)

[MIDL – stránky vlastností: Výstup](../ide/midl-property-pages-output.md)

[NMake – stránka vlastností](../ide/nmake-property-page.md)

[Stránky vlastností prostředků](../ide/resources-property-pages.md)

[Stránka vlastností adresářů VC++](../ide/vcpp-directories-property-page.md)

[Stránka vlastností webových odkazů](../ide/web-references-property-page.md)

[Stránka vlastností nástroje Generátor dat XML](../ide/xml-data-generator-tool-property-page.md)

[Stránky vlastností nástroje Generátor dokumentů XML](../ide/xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>Viz také:

[Postupy: Vytváření a odebrání závislostí projektu](/visualstudio/ide/how-to-create-and-remove-project-dependencies)<br>
[Postupy: Vytvoření a úprava konfigurací](/visualstudio/ide/how-to-create-and-edit-configurations)
