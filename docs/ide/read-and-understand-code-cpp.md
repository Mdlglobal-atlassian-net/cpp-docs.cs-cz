---
title: Čtení a pochopení kódu Jazyka C++ v sadě Visual Studio
description: Pomocí editoru kódu C++ ve Visual Studiu naformátujte a pochopte svůj kód.
ms.date: 05/28/2019
ms.openlocfilehash: 9ed0a20fb73e4cc976392bc5e5f698f9658a0b48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377292"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Čtení a pochopení kódu Jazyka C++ v sadě Visual Studio

Editor kódu Jazyka C++ a ide sady Visual Studio poskytují mnoho kódovacích pomůcek. Některé jsou jedinečné pro C++ a některé jsou v podstatě stejné pro všechny jazyky sady Visual Studio. Další informace o sdílených funkcích naleznete [v tématu Zápis kódu v kódu a textovém editoru](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Colorization

Visual Studio vybarví prvky syntaxe a rozlišuje mezi typy symbolů, jako jsou klíčová slova jazyka, názvy typů, názvy proměnných, parametry funkce, řetězcové literály a tak dále.

![Zbarvení kódu](../ide/media/code-outline-colorization.png "C++ vybarvení")

Nepoužívaný kód (například kód pod #if 0) je více vybledlé barvy.

![Neaktivní kód](../ide/media/inactive-code-cpp.png "Neaktivní kód jazyka C++")

Barvy můžete přizpůsobit zadáním "Písma" v **okně Snadné spuštění**a výběrem **možnosti Písma a barvy**. V dialogovém okně **Písma a barvy** přejděte dolů na volby C/C++ a pak zvolte vlastní písmo nebo barvu.

## <a name="outlining"></a>Sbalování

Klikněte pravým tlačítkem myši na libovolné místo v souboru zdrojového kódu a zvolte **Osnova** sbalit nebo rozbalit bloky kódu nebo vlastní oblasti, abyste usnadnili procházení pouze kódu, který vás zajímá. Další informace naleznete [v tématu Osnova](/visualstudio/ide/outlining).

![C&#43;&#43; Osnova](../ide/media/vs2015_cpp_outlining.png "Sbalování")

Když umístíte kurzor před složenou složenou závorku ,{nebo '}', editor zvýrazní svůj odpovídající protějšek.

Další možnosti osnovy jsou umístěny v části **Upravit** > **osnovu** v hlavní nabídce.

## <a name="line-numbers"></a>Čísla řádků

Čísla řádků můžete do projektu přidat tak, že přejdete do**textového editoru** > **možnosti** >  **nástrojů** > **Všechny jazyky** > **obecné** nebo vyhledáte "číslo řádku" pomocí funkce Snadné **spuštění (Ctrl + Q).** Čísla řádků lze nastavit pouze pro všechny jazyky nebo pro určité jazyky, včetně jazyka C++.

## <a name="scroll-and-zoom"></a>Posouvání a zvětšování

Přiblížení nebo oddálení editoru můžete přiblížit stisknutím **klávesy Ctrl** a posouváním kolečkem myši. Zvětšení můžete také pomocí nastavení lupy v levém dolním rohu.

![C&#43;&#43; Ovládání přiblížení](../ide/media/zoom-control.png "Ovládací prvek Lupa")

Režim **mapy** posuvníku umožňuje rychle procházet soubor kódu a procházet jej, aniž byste museli opustit aktuální umístění. Můžete kliknout kdekoli na mapě kódu a přejít přímo na toto místo.

![Mapa kódu v&#43;&#43;C](../ide/media/vs2015-cpp-code-map.png "Mapa kódu")

Chcete-li zapnout **režim mapy**, zadejte do vyhledávacího pole **Snadné spuštění** na hlavním panelu nástrojů příkaz "mapa" a zvolte Použít režim **mapy posouvání**. Další informace najdete v [tématu Postup: Sledování kódu přizpůsobením posuvníku](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Když je **režim mapy** vypnutý, posuvník stále zvýrazní změny, které jste v souboru provedli. Zelená označuje uložené změny a žlutá neuložené změny.

## <a name="quick-info-and-parameter-info"></a>Rychlé informace a informace o parametrech

Najeďte na libovolnou proměnnou, funkci nebo jiný symbol, abyste získali informace o ní, včetně deklarace, a všechny komentáře, které jsou umístěny těsně před ním.

::: moniker range="vs-2019"

![Rychlé informace v c&#43;&#43;](../ide/media/quick-info-vs2019.png "Rychlé informace")

Popisek **Rychlých informací** má odkaz **Online vyhledávání.** Přejděte na**možnosti** >  **nástrojů** > **Textové editoru** > **C++** > **Zobrazení** určit poskytovatele vyhledávání.

Pokud je v kódu chyba, můžete na něj najet najet a **rychlé informace** se zobrazí chybová zpráva. Chybovou zprávu najdete také v okně Seznam chyb.

![Rychlé informace o chybě](../ide/media/quickinfo-on-error.png "Rychlé informace o chybě")

::: moniker-end

::: moniker range="<=vs-2017"

![Rychlé informace v c&#43;&#43;](../ide/media/quick-info.png "Rychlé informace")

Pokud je v kódu chyba, můžete na něj najet najet a **rychlé informace** se zobrazí chybová zpráva. Chybovou zprávu najdete také v okně **Seznam chyb.**

![Rychlé informace o chybě](../ide/media/quickinfo-on-error.png "Rychlé informace o chybě")

::: moniker-end

Při volání **funkce, Informace o parametrech** zobrazuje typy parametrů a pořadí, ve kterém jsou očekávány.

![Informace o parametrech v&#43;&#43;C](../ide/media/parameter-info.png "Informace o parametrech")

## <a name="peek-definition"></a>Náhled definice

Najeďte přes proměnnou nebo deklaraci funkce, klikněte pravým tlačítkem myši a pak zvolte **Náhled Definice** zobrazíte včleněné zobrazení jeho definice, aniž byste se museli vzdalovat od aktuální polohy. Další informace naleznete v [tématu Náhled Definice (Alt+ F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![C&#43;&#43; náhled definice](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="f1-help"></a>F1 – nápověda

Umístěte kurzor na nebo těsně za libovolný typ, klíčové slovo nebo funkci a stisknutím **klávesy F1** přejděte přímo k příslušnému referenčnímu tématu na docs.microsoft.com. **F1** funguje také na položkách v seznamu chyb a v mnoha dialogových oknech.

## <a name="class-view"></a>zobrazení tříd

**Zobrazení tříd** zobrazuje prohledávatelnou sadu stromů všech symbolů kódu a jejich obora a nadřazené/podřízené hierarchie uspořádané na základě jednotlivého projektu. **Zobrazení tříd** můžete nakonfigurovat v nastavení **zobrazení třídy** (klikněte na ikonu pole ozubeného kola v horní části okna).

![Zobrazení tříd v&#43;&#43;C](../ide/media/class-view.png "zobrazení tříd")

## <a name="generate-graph-of-include-files"></a>Generovat graf zahrnutí souborů

Klikněte pravým tlačítkem myši na soubor kódu v projektu a zvolte **Generovat graf zahrnout souborů** zobrazíte graf, které soubory jsou zahrnuty do jiných souborů.

![C&#43;&#43; graf zahrnutí souborů](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Zobrazit hierarchii volání

Klikněte pravým tlačítkem myši na libovolné volání funkce a zobrazte rekurzivní seznam všech funkcí, které volá, a všech funkcí, které jej volají. Každá funkce v seznamu může být rozbalena stejným způsobem. Další informace naleznete v [tématu Call Hierarchy](/visualstudio/ide/reference/call-hierarchy).

![C&#43;&#43; hierarchie volání](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Viz také

[Upravit a refaktorovat kód (C++)](writing-and-refactoring-code-cpp.md)</br>
[Navigace v základu kódu Jazyka C++ v sadě Visual Studio](navigate-code-cpp.md)</br>
[Spolupráce s live share pro C++](live-share-cpp.md)
