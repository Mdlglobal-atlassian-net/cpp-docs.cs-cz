---
title: "Psaní a refaktoring kódu (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e9cdff53e6c8cfcfdd6c44a72b539e9567e680e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="writing-and-refactoring-code-c"></a>Psaní a refaktoring kódu (C++)
Editor kódu Visual C++ a IDE nabízí mnoho kódování pomůcky. Některé jsou jedinečné pro C++ a některé jsou v podstatě, stejné pro všechny jazyky, Visual Studio. Další informace o sdílené funkce, najdete v části [psaní kódu v editoru kódu a textovém editoru](/visualstudio/ide/writing-code-in-the-code-and-text-editor). Možnosti pro povolení a konfigurace funkce specifické pro C++ jsou umístěny v [textového editoru C++ Upřesnit](/visualstudio/ide/reference/options-text-editor-c-cpp-advanced) dialogové okno (**nástroje &#124; Možnosti &#124; Textový Editor &#124; C/C++ &#124; Rozšířené** nebo zadejte "C++ Advanced" v **Snadné spuštění**). Po výběru možnosti, kterou chcete nastavit, můžete získat další pomoc stisknutím **F1** dialogové okno když je aktivní. Pro obecné kód možnosti formátování, zadejte `Editor C++` do **QuickLaunch**.  

Povolenými experimentálními funkcemi, které mohou nebo nemusí být zahrnuty v budoucí verzi sady Visual Studio, jsou součástí [experimentální C++ textového editoru](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) dialogové okno. V aplikaci Visual Studio 2017 můžete povolit **prediktivní Intellisense** v tomto dialogu.
  
## <a name="adding-new-code"></a>Přidání nového kódu  
 Po vytvoření projektu, můžete začít kódování v souborech, které byly vygenerovány pro vás. Chcete-li přidat nové soubory, klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a zvolte **Přidat &#124; Nové**.  
  
 Pokud chcete nastavit možnosti například odsazení, dokončení závorek a zabarvení formátování, zadejte `C++ Formatting` do **QuickLaunch** okno.  
  
### <a name="intellisense"></a>IntelliSense  
 IntelliSense je název pro sadu funkcí, které poskytují vložené informace o členy, typy a přetížení funkce. Následující obrázek znázorňuje seznamu členů rozevíracího seznamu, který se zobrazí při psaní. Lze stisknutím klávesy tab můžete zadat text vybrané položky do souboru kódu.  
  
 ![C & č. 43; & č. 43; člen seznamu rozevíracího seznamu](../ide/media/vs2015_cpp_statement_completion.png "vs2015_cpp_statement_completion")  
  
 Úplné informace najdete v části [Visual C++ Intellisense](/visualstudio/ide/visual-cpp-intellisense).  
  
### <a name="insert-snippets"></a>Vložit fragmenty kódu  
 Fragment je předdefinované zdrojového kódu. Klikněte pravým tlačítkem na jednom místě nebo na vybraný text vložte fragment nebo obklopit fragmentem kódu vybraný text. Následující obrázek znázorňuje tři kroky obklopit vybraný příkaz s pro smyčky. Žlutý označuje ve finální image jsou upravitelné pole, které přistupujete pomocí klávesy tab. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
 ![Visual C & č. 43; & č. 43; Vložit fragment kódu vyřadit & č. 45; dolů](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")  
  
### <a name="add-class"></a>Přidat třídu  
 Přidejte novou třídu z **projektu** nabídky pomocí Průvodce třídou.  
  
 ![Přidejte novou třídu v Visual C & č. 43; & č. 43; ] (../ide/media/vs2015_cpp_add_class.png "vs2015_cpp_add_class")  
  
### <a name="class-wizard"></a>Průvodce třídou  
 Upravit nebo zkontrolujte existující třídy, nebo přidejte novou třídu, pomocí Průvodce třídou. Další informace najdete v tématu [přidání funkce pomocí průvodců kódem (C++)](../ide/adding-functionality-with-code-wizards-cpp.md).  
  
 ![Visual C & č. 43; & č. 43; Třídy průvodce](../ide/media/vs2015_cpp_class_wizard.png "vs2015_cpp_class_wizard")  
  
## <a name="refactoring"></a>Refaktoring  
 Refaktoring jsou k dispozici v místní nabídce rychlý akce, nebo kliknutím na [žárovky](/visualstudio/ide/perform-quick-actions-with-light-bulbs) v editoru.  Některé jsou také najdete v **Upravit > Refaktorovat** nabídky.  Tyto funkce patří:

* [Přejmenování](refactoring/rename.md)
* [Extrahování – funkce](refactoring/extract-function.md)
* [Čistý Virtuals implementace](refactoring/implement-pure-virtuals.md)
* [Vytvoření deklarace nebo definice](refactoring/create-declaration-definition.md)
* [Přesunout definice funkce](refactoring/move-definition-location.md)
* [Převést na nezpracovaná řetězcový literál](refactoring/convert-to-raw-string-literal.md)
* [Změna podpisu](refactoring/change-signature.md)
 
## <a name="navigate-and-understand"></a>Přejděte a pochopit
 Visual C++ sdílí mnoho funkcí navigační kód s jinými jazyky. Další informace najdete v tématu 
### <a name="quickinfo"></a>QuickInfo  
 Podržte ukazatel nad proměnné zobrazíte informace o jeho typu.
  
 ![Visual C & č. 43; & č. 43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")  
  
### <a name="open-document-navigate-to-header"></a>Otevřete dokument (přejde na hlavičky)  
 Klikněte pravým tlačítkem na název hlavičky v `#include` – direktiva a otevřete soubor hlaviček.  
  
 ![Visual C & č. 43; & č. 43; Otevřete dokument nabídky](../ide/media/vs2015_cpp_open_document.png "vs2015_cpp_open_document")  
  
### <a name="peek-definition"></a>Funkce Náhled definice  
 Pozastavte ukazatel myši nad proměnné nebo funkce deklaraci, klikněte pravým tlačítkem, poté zvolte **funkce Náhled definice** zobrazení vložené jeho definice. Další informace najdete v tématu [funkce Náhled definice (Alt + F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).  
  
 ![Visual C & č. 43; & č. 43; Funkce Náhled definice](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")  
  
### <a name="go-to-definition"></a>Přechod na definici  
 Pozastavte ukazatel myši nad proměnné nebo funkce deklaraci, klikněte pravým tlačítkem, poté zvolte **přejít k definici** o otevření dokumentu, kde je definován objekt.  
  
### <a name="view-call-hierarchy"></a>Zobrazení hierarchie volání  
 Klikněte pravým tlačítkem na žádném volání, funkce a zobrazení seznamu resursive všechny funkce, které volá a všechny funkce, které ji volat. Jednotlivé funkce v seznamu lze rozšířit stejným způsobem. Další informace najdete v tématu [hierarchie volání](/visualstudio/ide/reference/call-hierarchy).  
  
 ![Visual C & č. 43; & č. 43; Hierarchie volání](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")  
  
### <a name="toggle-header--code-file"></a>Přepněte záhlaví / kódu souboru  
 Klikněte pravým tlačítkem a vyberte záhlaví přepínač / souboru kódu a zpět přepínat mezi záhlaví souboru a jeho přidružený kód souboru.  
  
### <a name="outlining"></a>Sbalování  
 Klikněte pravým tlačítkem na libovolné místo v souboru zdrojového kódu a vyberte **Osnova** sbalit nebo rozbalte definice nebo vlastní oblasti, aby bylo snazší procházet pouze ty části, které vás zajímají. Další informace najdete v tématu [Osnova](/visualstudio/ide/outlining).  
  
 ![Visual C & č. 43; & č. 43; Osnova](../ide/media/vs2015_cpp_outlining.png "vs2015_cpp_outlining")  
  
### <a name="scroll-bar-map-mode"></a>Posuv panelu mapy režimu  
 ScrollBar – mapa režim umožňuje rychle přejděte a procházejte souboru kódu ve skutečnosti neopouštějte vaše aktuální umístění. Nebo klikněte na libovolné místo na mapě kódu přejdete přímo do tohoto umístění.  
  
 ![Mapy kódu ve Visual C & č. 43; & č. 43; ] (../ide/media/vs2015_cpp_code_map.png "vs2015_cpp_code_map")  
  
### <a name="generate-graph-of-include-files"></a>Generování grafů zahrnout soubory  
 Klikněte pravým tlačítkem na soubor kódu ve vašem projektu a zvolte **Generovat graf zahrnout soubory** zobrazíte graf, které jsou zahrnuty soubory a jiné soubory.  
  
 ![Visual C & č. 43; & č. 43; graf zahrnout soubory](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")  
  
### <a name="f1-help"></a>F1 – nápověda  
 Umístěte kurzor na nebo bezprostředně za jakéhokoli typu, – klíčové slovo nebo funkce a po stisknutí klávesy F1 přejít přímo na relevantní téma v referenční dokumentace MSDN. F1 funguje taky na položky v seznamu chyb a v mnoha dialogových oken.  
  
### <a name="quick-launch"></a>Snadné spuštění  
 Chcete-li snadno přejít k jakékoli okno nebo nástroje v sadě Visual Studio, jednoduše zadejte jeho název v okně Snadné spuštění v pravém horním rohu uživatelského rozhraní. Automatické dokončování seznam bude filtrovat během psaní.  
  
 ![Snadné spuštění sady Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "vs2015_cpp_quick_launch")
