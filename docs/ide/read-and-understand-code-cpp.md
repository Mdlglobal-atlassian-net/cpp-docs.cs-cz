---
title: Čtení a pochopení C++ kódu v aplikaci Visual Studio
description: Použijte Editor C++ kódu v aplikaci Visual Studio k formátování a pochopení kódu.
ms.date: 05/28/2019
ms.openlocfilehash: 2ddeabd9d70ebb344fe6d14abe520ee51a42eebb
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416120"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Čtení a pochopení C++ kódu v aplikaci Visual Studio

Editor C++ kódu a integrované vývojové prostředí sady Visual Studio poskytují mnoho pomůcek pro kódování. Některé jsou jedinečné pro C++a některé jsou v podstatě stejné pro všechny jazyky sady Visual Studio. Další informace o sdílených funkcích naleznete v tématu [psaní kódu v editoru kódu a textu](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Zabarvení

Prvky syntaxe sady Visual Studio vybarvuje k rozlišení mezi typy symbolů, jako jsou klíčová slova jazyka, názvy typů, názvy proměnných, parametry funkce, řetězcové literály a tak dále.

![Barevné zabarvení kódu](../ide/media/code-outline-colorization.png "C++zabarvení")

Nepoužitý kód (například kód pod #if 0) je barevně vybledlější.

![Neaktivní kód](../ide/media/inactive-code-cpp.png "C++Neaktivní kód")

Barvy můžete přizpůsobit tak, že v okně **Snadné spuštění**zadáte "písma" a pak zvolíte **písma a barvy**. V dialogovém okně **písma a barvy** se posuňte dolů k možnostem C/C++ a pak zvolte vlastní písmo a barvu.

## <a name="outlining"></a>Sbalování

Kliknutím pravým tlačítkem myši kdekoli v souboru zdrojového kódu a **výběrem možnosti sbalení** sbalíte nebo rozbalíte bloky kódu a/nebo vlastní oblasti. Tím usnadníte procházení pouze kódu, který vás zajímá. Další informace najdete v tématu [popisujícím sbalení](/visualstudio/ide/outlining).

![Osnova jazyka C&#43; &#43;](../ide/media/vs2015_cpp_outlining.png "Sbalování")

Když umístíte kurzor před složenou závorku, "{" nebo "}", Editor zvýrazní svůj odpovídající protějšek.

Další možnosti sbalení najdete v části **upravit** > **sbalení** v hlavní nabídce.

## <a name="line-numbers"></a>Čísla řádků

Čísla řádků do projektu můžete přidat tak, že přejdete na **nástroje** > možnosti > **textový editor** > **všechny jazyky** > **Obecné** nebo vyhledáte "číslo řádku" s **možností** **snadného spuštění (CTRL + Q)** . Čísla řádků můžete nastavit pro všechny jazyky nebo jenom pro konkrétní jazyky, včetně C++.

## <a name="scroll-and-zoom"></a>Posouvání a přiblížení

V editoru můžete přiblížit nebo oddálit stisknutím klávesy **CTRL** a posouváním kolečkem myši. Můžete také zvětšit pomocí nastavení přiblížení v levém dolním rohu.

![Ovládací&#43; &#43; prvek lupy v jazyce C](../ide/media/zoom-control.png "Ovládací prvek Lupa")

**Režim mapy** ScrollBar umožňuje rychle procházet a procházet soubor kódu, aniž byste opustili aktuální polohu. Kliknutím kamkoli na mapu kódu můžete přejít přímo do tohoto umístění.

![Mapa kódu v jazyce C&#43;&#43;](../ide/media/vs2015-cpp-code-map.png "Mapa kódu")

Pokud chcete zapnout **režim mapování**, zadejte do pole **Snadné spuštění** na hlavním panelu nástrojů "map" a vyberte **použít režim posouvání mapy**. Další informace najdete v tématu [Postupy: sledování kódu přizpůsobením posuvníku](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Když je **režim mapování** vypnutý, posuvník stále zvýrazní změny, které jste udělali v souboru. Zelená označuje uložené změny a žlutá indikuje neuložené změny.

## <a name="quick-info-and-parameter-info"></a>Rychlé informace a informace o parametrech

Najeďte myší na jakoukoli proměnnou, funkci nebo jiný symbol, abyste získali informace o tom, včetně deklarace, a všech komentářů, které se nachází těsně před ní.

::: moniker range="vs-2019"

![Rychlé informace v jazyce C&#43;&#43;](../ide/media/quick-info-vs2019.png "Rychlé informace")

Popis **rychlá informace** obsahuje online odkaz pro **hledání** . Chcete-li zadat poskytovatele vyhledávání, použijte možnost **C++** **nástroje** > **možnosti** > **textový editor** >  > **zobrazení** . 

Pokud v kódu dojde k chybě, můžete na něj umístit ukazatel myši a **rychlé informace** zobrazí chybovou zprávu. Chybovou zprávu můžete najít také v okně Seznam chyb.

![Rychlé informace o chybě](../ide/media/quickinfo-on-error.png "Rychlé informace o chybě")

::: moniker-end

::: moniker range="<=vs-2017"

![Rychlé informace v jazyce C&#43;&#43;](../ide/media/quick-info.png "Rychlé informace")

Pokud v kódu dojde k chybě, můžete na něj umístit ukazatel myši a **rychlé informace** zobrazí chybovou zprávu. Chybovou zprávu můžete najít také v okně **Seznam chyb** .

![Rychlé informace o chybě](../ide/media/quickinfo-on-error.png "Rychlé informace o chybě")

::: moniker-end

Při volání funkce jsou v **informacích o parametrech** zobrazeny typy parametrů a pořadí, ve kterém jsou očekávány.

![Informace o parametrech v jazyce C&#43;&#43;](../ide/media/parameter-info.png "Informace o parametrech")

## <a name="peek-definition"></a>Náhled definice

Najeďte myší na proměnnou nebo deklaraci funkce, kliknutím pravým tlačítkem myši a zvolením možnosti **Náhled definice** zobrazíte vložené zobrazení jeho definice bez přechodu z aktuálního umístění. Další informace najdete v tématu [Náhled definice (Alt + F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![Náhled&#43; &#43; definice jazyka C](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

##  <a name="f1-help"></a>F1 – nápověda

Umístěte kurzor na nebo hned za libovolný typ, klíčové slovo nebo funkci a stisknutím klávesy **F1** přejděte přímo k příslušnému referenčnímu tématu v docs.Microsoft.com. **F1** také funguje na položkách v seznamu chyb a v mnoha dialogových oknech.

## <a name="class-view"></a>zobrazení tříd

**Zobrazení tříd** zobrazuje sadu stromů všech symbolů kódu a jejich rozsah a hierarchie nadřazených a podřízených prvků uspořádaných podle jednotlivých projektů. Můžete nakonfigurovat, co **zobrazení tříd** zobrazovat z **Nastavení zobrazení tříd** (klikněte na ikonu ozubeného kolečka v horní části okna).

![Zobrazení tříd v jazyce C&#43;&#43;](../ide/media/class-view.png "zobrazení tříd")

## <a name="generate-graph-of-include-files"></a>Generovat graf souborů zahrnutí

Klikněte pravým tlačítkem na soubor kódu v projektu a vyberte možnost **Generovat graf souborů k zahrnutí** . zobrazí se graf, ve kterém jsou soubory zahrnuté do jiných souborů.

![Graf&#43; &#43; souborů zahrnutí v jazyce C](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Zobrazit hierarchii volání

Klikněte pravým tlačítkem na libovolné volání funkce a zobrazte rekurzivní seznam všech funkcí, které volá, a všechny funkce, které ji volají. Jednotlivé funkce v seznamu lze rozbalí stejným způsobem. Další informace najdete v tématu věnovaném [hierarchii volání](/visualstudio/ide/reference/call-hierarchy).

![Hierarchie&#43; &#43; volání jazyka C](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Viz také

[Upravit a Refaktorovat kód (C++)](writing-and-refactoring-code-cpp.md)</br>
[Procházení základu C++ kódu v aplikaci Visual Studio](navigate-code-cpp.md)</br>
[Spolupráce s Live Share proC++](live-share-cpp.md)
