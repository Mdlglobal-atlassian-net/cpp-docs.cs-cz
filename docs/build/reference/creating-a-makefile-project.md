---
title: Vytvoření projektu souboru pravidel C++ v sadě Visual Studio
ms.date: 12/08/2018
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: 9c2edfe35233672e8117d336ba40cfea497b1a22
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272344"
---
# <a name="create-a-c-makefile-project"></a>Vytvoření projektu souboru pravidel C++

A *makefile* je textový soubor, který obsahuje pokyny, jak kompilovat a propojení (nebo *sestavení*) sadu souborů zdrojového kódu jazyka C++. A *zkontrolujte* program přečte soubor pravidel a vyvolá kompilátoru, linkeru a pravděpodobně další programy, aby spustitelný soubor. Implementace společnosti Microsoft *zkontrolujte* program se nazývá [NMAKE](nmake-reference.md);

Pokud máte existujícího projektu souboru pravidel, pokud chcete kód a/nebo ladění v rozhraní IDE sady Visual Studio mají tyto možnosti:

- Vytvoření projektu souboru pravidel v sadě Visual Studio, který používá vaše existující soubor pravidel ke konfiguraci souboru, který bude používat Visual Studio pro technologii IntelliSense. (Není nutné všechny funkce integrovaného vývojového prostředí, které jste získali s nativní projektu nástroje MSBuild.) Zobrazit [vytvoření projektu souboru pravidel](#create_a_makefile_project) níže.
- Použití **vytvořit nový projekt z existujících souborů kódu** průvodce vytvořit nativní projekt MSBuild ze zdrojového kódu. Potom se nepoužije původní soubor pravidel. Další informace najdete v tématu [jak: Vytvoření projektu jazyka C++ z existujícího kódu](../how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 a novější**: Použití **otevřít složku** funkci upravit a sestavit projekt makefile jako-je bez jakékoli zapojení systém MSBuild. Další informace najdete v tématu [projekty otevřít složku pro jazyk C++](../open-folder-projects-cpp.md).

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Vytvoření projektu souboru pravidel se šablonou projektu souboru pravidel

V sadě Visual Studio 2017 nebo novější je k dispozici šablonu projektu Makefile, když je nainstalovaná úloha vývoj v jazyce C++ Desktop.

Postupujte podle pokynů průvodce a zadat příkazy a prostředí, které používá váš soubor pravidel. Potom můžete tento projekt k sestavení vašeho kódu v sadě Visual Studio.

Ve výchozím projektu makefile nezobrazí žádné soubory v Průzkumníku řešení. Projekt makefile určuje nastavení sestavení, která se projeví na stránce vlastností projektu.

Výstupní soubor zadaný v projektu nemá žádný vliv na název, který generuje skript sestavení; deklaruje pouze záměr. Váš soubor pravidel stále řídí proces sestavení a určuje cílů pro sestavení.

1. Na úvodní stránce sady Visual Studio, zadejte "makefile" **nový projekt** vyhledávacího pole. Nebo v **nový projekt** dialogového okna rozbalte **Visual C++** > **Obecné** (Visual Studio 2015) nebo **jiných** (Visual Studio 2017) a pak vyberte **projektu Makefile** v podokně šablon a spusťte Průvodce projektu.

1. V **nastavení aplikace** zadejte výstupu příkazu vyčistit a informace o opětovné sestavení pro ladění a prodejní sestavení.

1. Klikněte na tlačítko **Dokončit** zavřete průvodce a otevřete nově vytvořený projekt v **Průzkumníka řešení**.

Na stránce vlastností projektu můžete zobrazit a upravit jeho vlastnosti. Zobrazit [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md) informace o zobrazení stránky vlastností.

## <a name="makefile-project-wizard"></a>Průvodce projektem souboru pravidel

Po vytvoření projektu souboru pravidel, můžete zobrazit a upravit každé z následujících možností v **Nmake** stránky ze stránky vlastností projektu.

- **Příkazový řádek sestavení:** Určuje příkazový řádek pro spuštění, když uživatel vybere sestavení v nabídce sestavení. Zobrazí v poli sestavení příkazového řádku na stránce Nmake ze stránky vlastností projektu.

- **Výstup:** Určuje název souboru, který bude obsahovat výstup do příkazového řádku. Ve výchozím nastavení tato možnost je podle názvu projektu. Zobrazí v poli výstup v NMake – stránka ze stránky vlastností projektu.

- **Vyčištění příkazy:** Určuje příkazový řádek spustit, když uživatel vybere vyčistit v nabídce sestavení. Zobrazí v poli příkazový řádek vyčištění na NMake – stránka ze stránky vlastností projektu.

- **Opětovné sestavení příkazového řádku:** Určuje příkazový řádek pro spuštění, když uživatel vybere opětovné sestavení v nabídce sestavení. Zobrazí v sestavení všechna pole příkazového řádku v NMake – stránka ze stránky vlastností projektu.

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>Postupy: Povolení technologie IntelliSense pro projekty souborů pravidel

Technologie IntelliSense se nezdaří v projekty souborů pravidel při určitých nastavení projektu a možnosti kompilátoru jsou správně nastavená. Postupujte podle těchto kroků a nakonfigurujte projekty souborů pravidel tak, aby IntelliSense funguje podle očekávání:

1. Otevřít **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Vyberte **NMake** vlastnost stránce a potom změňte vlastnosti v rámci **IntelliSense** podle potřeby.

   - Nastavte **Definice preprocesoru** vlastnost pro definování preprocesoru symbolů ve vašem projektu souboru pravidel. Zobrazit [/D (Definice preprocesoru)](d-preprocessor-definitions.md), další informace.

   - Nastavte **zahrnout cestu vyhledávání** vlastnosti a určit tak seznam adresářů, které kompilátor prohledá, chcete-li vyřešit odkazy na soubory, které jsou předány do direktivy preprocesoru ve vašem projektu souboru pravidel. Zobrazit [/I (další vložené adresáře)](i-additional-include-directories.md), další informace.

    - Pro projekty, které se vytvářejí pomocí CL. EXE z příkazové okno, nastavte **zahrnout** proměnnou prostředí k určení adresáře, které kompilátor prohledá, chcete-li vyřešit odkazy na soubory, které jsou předány do direktivy preprocesoru ve vašem projektu souboru pravidel.

   - Nastavte **vynucené zahrnuje** vlastnosti a určit, které hlavičkové soubory proces, při vytváření projektu souboru pravidel. Zobrazit [/FI (vynucené soubor zahrnutí názvu)](fi-name-forced-include-file.md), další informace.

   - Nastavte **cesta pro vyhledávání sestavení** vlastnosti a určit tak seznam adresářů, které kompilátor bude hledat odkazy na sestavení rozhraní .NET ve vašem projektu. Zobrazit [/AI (zadat adresáře metadat)](ai-specify-metadata-directories.md), další informace.

   - Nastavte **vynucené používání sestavení** vlastnosti a určit tak sestavení .NET pro zpracování při vytváření projektu souboru pravidel. Zobrazit [/FU (vynuceným názvem #using souboru)](fu-name-forced-hash-using-file.md), další informace.

   - Nastavte **další možnosti** vlastnosti a určit další přepínače kompilátoru pro použití technologií IntelliSense při analýze souborů C++.

1. Klikněte na tlačítko **OK** stránku vlastností zavřete.

1. Použití **Uložit vše** příkazu k uložení nastavení projektu.

Při příštím otevření projektu makefile ve vývojovém prostředí sady Visual Studio, spusťte **Vyčistit řešení** příkaz a potom **sestavit řešení** v projektu makefile příkaz. Technologie IntelliSense by měly fungovat správně v integrovaném vývojovém prostředí.

## <a name="see-also"></a>Viz také:

[Používání atributu IntelliSense](/visualstudio/ide/using-intellisense)<br>
[NMAKE – referenční zdroje](nmake-reference.md)<br>
[Postupy: Vytvoření projektu jazyka C++ z existujícího kódu](../how-to-create-a-cpp-project-from-existing-code.md)
[speciální znaky v souboru pravidel](special-characters-in-a-makefile.md)<br/>
[Obsah souboru pravidel](contents-of-a-makefile.md)<br/>
