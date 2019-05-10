---
title: Psaní a refaktoring kódu (C++)
description: Použití C++ editoru kódu v sadě Visual Studio k formátování, navigace, pochopit a Refaktorovat kód.
ms.date: 04/30/2018
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.openlocfilehash: ee506229584690cd4f7730011e0b5b50af0e27e0
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222315"
---
# <a name="writing-and-refactoring-code-c"></a>Psaní a refaktoring kódu (C++)

Editor kódu jazyka Visual C++ a prostředí IDE poskytují mnoho kódování pomůcky. Některé jsou jedinečné pro C++, a některé v podstatě stejný pro všechny jazyky sady Visual Studio. Další informace o sdílených funkcích naleznete v tématu [psaní kódu v editoru kódu a textovém editoru](/visualstudio/ide/writing-code-in-the-code-and-text-editor). Možnosti pro povolení a konfigurace funkce specifické pro C++ jsou umístěny v **nástroje &#124; možnosti &#124; textový Editor &#124; C/C++**. Po výběru možnosti, kterou chcete nastavit, můžete získat další nápovědu stisknutím kombinace kláves **F1** při dialogového okna je aktivní. Obecné možnosti formátování kódu, zadejte `Editor C++` do **rychlé spuštění**.

Seznámit s experimentálními funkcemi, které mohou nebo nemusí být zahrnuté v budoucí verzi systému Visual Studio, najdete v [textového editoru C++ experimentální](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) dialogového okna. V sadě Visual Studio 2017 můžete povolit **prediktivní IntelliSense** v tomto dialogovém okně.

## <a name="adding-new-files"></a>Přidání nových souborů

Chcete-li přidat nové soubory do projektu, klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a zvolte **přidat &#124; nový**.

## <a name="formatting-options"></a>Možnosti formátování

Pokud chcete nastavit možnosti, jako je například odsazení, uzavírání hranatých závorek a barevné zvýraznění formátování, zadejte "C++ formátování" do **rychlé spuštění** okna. Visual Studio 2017 verze 15.7 nebo novější podporuje ClangFormat. Můžete je nakonfigurovat v [C/C++, formátování stránky vlastností](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting) pod **nástroje &#124; možnosti &#124; textový Editor &#124; C/C++ &#124; formátování**.

![Možnosti formátování pro C++](media/cpp-formatting-options.png)

## <a name="intellisense"></a>IntelliSense

Technologie IntelliSense je název pro sadu funkcí, které poskytují vložené informace o členy, typy a funkce přetížení. Následující obrázek znázorňuje seznamu členů rozevíracího seznamu, který se zobrazí při psaní. Stisknutí klávesy tab k zadání textu vybrané položky do souboru s kódem.

![C&#43; &#43; rozevíracího seznamu členů seznamu](../ide/media/vs2015_cpp_statement_completion.png "vs2015_cpp_statement_completion")

Podrobnější informace najdete v části [Visual C++ IntelliSense](/visualstudio/ide/visual-cpp-intellisense).

## <a name="insert-snippets"></a>Vložte fragmenty kódu

Fragment kódu je předdefinovaný část zdrojového kódu. Klikněte pravým tlačítkem na jednom místě nebo vybraný text k vložení fragmentu kódu nebo obklopit fragmentem vybraný text. Následující obrázek ukazuje tři kroky ohraničit vybraný příkaz s smyčky for. Jsou žlutým zvýrazněním v konečném obrazu upravitelná pole, které přistupujete pomocí klávesy tab. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).

![Visual C&#43; &#43; Vložit fragment kódu vyřadit&#45;dolů](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

## <a name="add-class"></a>Přidat třídu

Přidejte novou třídu z **projektu** nabídek s použitím Průvodce třídami.

![Přidejte novou třídu v jazyce Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_class.png "vs2015_cpp_add_class")

Můžete také použít Průvodce třídami změnit nebo zkontrolovat existující třídy.

![Visual C&#43; &#43; třídy průvodce](../ide/media/vs2015_cpp_class_wizard.png "vs2015_cpp_class_wizard")

Další informace najdete v tématu [přidání funkce pomocí průvodců kódem (C++)](../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="refactoring"></a>Refaktoring

Refaktoring jsou k dispozici v místní nabídce rychlá akce, nebo kliknutím na [žárovky](/visualstudio/ide/perform-quick-actions-with-light-bulbs) v editoru.  Některé jsou taky součástí **Upravit > Refaktorovat** nabídky.  Tyto funkce patří:

* [Přejmenovat](refactoring/rename.md)
* [Extrahovat funkci](refactoring/extract-function.md)
* [Implementovat čistě virtuální](refactoring/implement-pure-virtuals.md)
* [Vytvořit deklaraci/definici](refactoring/create-declaration-definition.md)
* [Přesunout – definice funkce](refactoring/move-definition-location.md)
* [Převod na nezpracovaný řetězcový literál](refactoring/convert-to-raw-string-literal.md)
* [Změnit signaturu](refactoring/change-signature.md)

## <a name="navigate-and-understand"></a>Navigace a porozumět

Visual C++ sdílí řadu funkcí pro navigaci kódu s jinými jazyky. Další informace najdete v tématu [procházení kódu](/visualstudio/ide/navigating-code) a [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).

## <a name="quickinfo"></a>QuickInfo

Najeďte myší proměnné zobrazíte informace o typu.

![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")

## <a name="open-document-navigate-to-header"></a>Otevřít dokument (Navigovat do hlavičky)

Klikněte pravým tlačítkem na název hlavičky v `#include` směrnice a otevřete soubor hlaviček.

![Visual C&#43; &#43; otevřít dokument nabídky](../ide/media/vs2015_cpp_open_document.png "vs2015_cpp_open_document")

## <a name="peek-definition"></a>Náhled definice

Najeďte myší proměnnou nebo funkci deklaraci, klikněte pravým tlačítkem, poté zvolte **definice operace Peek** zobrazení vloženého jeho definice. Další informace najdete v tématu [náhled definice (Alt + F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![Visual C&#43; &#43; náhled definice](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="go-to-definition"></a>Přejít k definici

Najeďte myší proměnnou nebo funkci deklaraci, klikněte pravým tlačítkem, poté zvolte **přejít k definici** otevřete dokument, kde je definován objekt.

## <a name="view-call-hierarchy"></a>Zobrazit hierarchii volání

Klikněte pravým tlačítkem na každé volání funkce a zobrazte seznam všech funkcí, které volá a všechny funkce, které ji volaly rekurzivní. Každá funkce v seznamu lze rozšířit stejným způsobem. Další informace najdete v tématu [hierarchie volání](/visualstudio/ide/reference/call-hierarchy).

![Visual C&#43;&#43; Call Hierarchy](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="toggle-header--code-file"></a>Přepínač záhlaví / soubor kódu

Klikněte pravým tlačítkem a zvolte **přepínač záhlaví / soubor s kódem** přepínat vpřed a zpět mezi záhlaví souboru a jeho přidružen soubor kódu.

## <a name="outlining"></a>Sbalování

Klikněte pravým tlačítkem na libovolné místo v souboru zdrojového kódu a zvolte **Osnova** sbalit nebo rozbalit definice a/nebo vlastní oblastech a usnadňují procházení jen ty části, které vás zajímají. Další informace najdete v tématu [Osnova](/visualstudio/ide/outlining).

![Visual C&#43;&#43; Outlining](../ide/media/vs2015_cpp_outlining.png "vs2015_cpp_outlining")

## <a name="scrollbar-map-mode"></a>Režim mapování posuvníku

Režim mapování posuvníku umožňuje rychle přejděte a projděte si soubor kódu bez opuštění skutečně svoji aktuální polohu. Nebo klikněte na libovolné místo na mapě kódu přejdete přímo do tohoto umístění. Další informace najdete v tématu [jak: Sledování kódu přizpůsobením posuvníku](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

![Mapa v jazyce Visual C kódu&#43;&#43;](../ide/media/vs2015_cpp_code_map.png "vs2015_cpp_code_map")

## <a name="generate-graph-of-include-files"></a>Generovat graf souborů zahrnutí

Klikněte pravým tlačítkem na soubor kódu ve vašem projektu a zvolte **Generovat graf souborů zahrnutí** zobrazíte grafu, které soubory jsou zahrnuty v ostatních souborech.

![Visual C&#43; &#43; grafu souborů zahrnutí](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="f1-help"></a>F1 – nápověda

Umístěte kurzor na slovo na nebo bezprostředně po jakéhokoli typu, – klíčové slovo nebo funkce a stisknutím klávesy F1 přejít přímo na relevantní referenčním tématu na webu docs.microsoft.com. F1 funguje taky na položky v seznamu chyb a mnoho dialogových oknech.

## <a name="quick-launch"></a>Snadné spuštění

Chcete-li snadno přejít k jakékoli okno nebo nástroje v sadě Visual Studio, jednoduše zadejte jeho název v okně Snadné spuštění v pravém horním rohu uživatelského rozhraní. Automatické dokončování seznam bude filtrovat při psaní.

![Visual Studio Quick Launch](../ide/media/vs2015_cpp_quick_launch.png "vs2015_cpp_quick_launch")
