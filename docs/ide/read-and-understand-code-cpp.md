---
title: Čtení a pochopení C++ kódu v sadě Visual Studio
description: Použití C++ editoru kódu v sadě Visual Studio formátování a pochopení kódu.
ms.date: 05/28/2019
ms.openlocfilehash: c5e4d7f3e53ef37649e3635d11cf99b10cb8a7ee
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2019
ms.locfileid: "66743381"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Čtení a pochopení C++ kódu v sadě Visual Studio

C++ Editoru kódu a integrovaném vývojovém prostředí Visual Studio poskytuje mnoho kódování pomůcky. Některé jsou jedinečné pro C++, a některé v podstatě stejný pro všechny jazyky sady Visual Studio. Další informace o sdílených funkcích naleznete v tématu [psaní kódu v editoru kódu a textovém editoru](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Barevné zvýrazňování

Visual Studio vybarví prvky syntaxe k rozlišení mezi typy znamének, jako jsou klíčová slova jazyka, názvy typů, názvy proměnných, parametry funkce, řetězcové literály a tak dále.

![Zabarvení kódu](../ide/media/code-outline-colorization.png " C++ zabarvení")

 Nepoužitý kód (například kód v rámci #if 0) je více barevně barvou.

 ![Neaktivní kód](../ide/media/inactive-code-cpp.png " C++ neaktivního kódu")

Barvy můžete přizpůsobit tak, že zadáte "Písma" v **Snadné spuštění**a poté volbou **písma a barvy**. V **písma a barvy** dialogového okna přejděte dolů C /C++ možnosti a klikněte na tlačítko Vlastní písma a barvy.

## <a name="outlining"></a>Sbalování

Klikněte pravým tlačítkem na libovolné místo v souboru zdrojového kódu a zvolte **Osnova** sbalit nebo rozbalit bloky kódu a/nebo vlastní oblastech a usnadňují procházení pouze kódu, které vás zajímají. Další informace najdete v tématu [Osnova](/visualstudio/ide/outlining).

![C&#43; &#43; sbalování](../ide/media/vs2015_cpp_outlining.png "sbalování")

Když umístíte ukazatel myši před složenou závorku "{" nebo "}", jeho odpovídající protějšek zvýrazní editor.

Možnosti osnovy jsou umístěny v **upravit** > **Osnova** v hlavní nabídce.

## <a name="line-numbers"></a>Čísla řádků

Čísla řádků do svého projektu můžete přidat tak, že přejdete do **nástroje** > **možnosti** > **textový Editor** > **všechny Jazyky** > **Obecné** nebo tak, že "číslování řádků" s **Snadné spuštění (Ctrl + Q)** . Čísla řádků lze nastavit pro všechny jazyky, nebo pro konkrétní jazyky, včetně C++.

## <a name="scroll-and-zoom"></a>Posuňte a přiblížit

Přiblížení nebo oddálení v editoru stisknutím kombinace kláves **Ctrl** klíč a posouvání pomocí kolečko myši. Můžete také přiblížit, oddálit pomocí nastavení přiblížení či oddálení v levém dolním rohu.

![C&#43; &#43; Lupa](../ide/media/zoom-control.png "ovládací prvek Lupa")

Posuvník **režim mapování** vám umožní rychle přejděte a projděte si soubor s kódem, aniž byste museli opustit svoji aktuální polohu. Kliknutím kamkoli na mapě kódu přejdete přímo do tohoto umístění.

![Mapa v jazyce C kódu&#43;&#43;](../ide/media/vs2015-cpp-code-map.png "mapě kódu")

Zapnutí **režim mapování**, zadejte "mapy" **Snadné spuštění** pole vyhledávání na hlavním panelu nástrojů a zvolte **použít režim mapování posuvníku**. Další informace najdete v tématu [jak: Sledování kódu přizpůsobením posuvníku](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Když **režim mapování** je vypnutá, posuvník stále zvýrazňuje změny, které jste provedli v souboru. Zelená značí uložené změny a žlutá značí neuložené změny.

## <a name="quick-info-and-parameter-info"></a>Rychlé informace a informace o parametrech

Najeďte myší jakoukoli proměnnou, funkci nebo další symbol, který má získat informace o tom, včetně prohlášení a komentářů, které jsou umístěné jenom předchozí.

::: moniker range="vs-2019"

![Rychlé informace v jazyce C&#43;&#43;](../ide/media/quick-info-vs2019.png "rychlé informace")

**Rychlé informace** má popisek **vyhledávání Online** odkaz. Přejděte na **nástroje** > **možnosti** > **textový Editor**  >  **C++**  >  **Zobrazení** chcete zadat poskytovatele vyhledávání. 

Pokud dojde k chybě ve vašem kódu, můžete něj přejdete myší a **rychlé informace** zobrazí chybovou zprávu. Chybová zpráva může také najít v okně Seznam chyb.

![Rychlé informace o chybě](../ide/media/quickinfo-on-error.png "rychlé informace o chybě")

::: moniker-end

::: moniker range="<=vs-2017"

![Rychlé informace v jazyce C&#43;&#43;](../ide/media/quick-info.png "rychlé informace")

Pokud dojde k chybě ve vašem kódu, můžete něj přejdete myší a **rychlé informace** zobrazí chybovou zprávu. Můžete také získat chybovou zprávu v **seznam chyb** okna.

![Rychlé informace o chybě](../ide/media/quickinfo-on-error.png "rychlé informace o chybě")

::: moniker-end

Při volání funkce, **informace o parametru** ukazuje typy parametrů a pořadí, ve kterém se očekává.

![Informace o parametrech v jazyce C&#43;&#43;](../ide/media/parameter-info.png "informace o parametrech")

## <a name="peek-definition"></a>Náhled definice

Najeďte myší proměnnou nebo funkci deklaraci, klikněte pravým tlačítkem, poté zvolte **definice operace Peek** k vidět zobrazení jeho definice vložené bez navigaci pryč z aktuální polohu. Další informace najdete v tématu [náhled definice (Alt + F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![C&#43;&#43; Peek Definition](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

##  <a name="f1-help"></a>F1 – nápověda

Umístěte kurzor na slovo na nebo bezprostředně po libovolného typu, – klíčové slovo nebo funkce a stisknutím klávesy **F1** můžete přejít přímo na relevantní referenčním tématu na webu docs.microsoft.com. **F1** funguje taky na položky v seznamu chyb a mnoho dialogových oknech.

## <a name="class-view"></a>zobrazení tříd

**Zobrazení tříd** zobrazí prohledávatelná sadu stromů všechny symboly kódu a jejich rozsah a nadřazené a podřízené hierarchie uspořádané na základě jednotlivých projektů. Můžete nakonfigurovat co **zobrazení tříd** zobrazí z **zobrazení tříd – nastavení** (klikněte na ikonu ozubeného kola pole v horní části okna).

![Třídy zobrazení v jazyce C&#43;&#43;](../ide/media/class-view.png "zobrazení tříd")

## <a name="generate-graph-of-include-files"></a>Generovat graf souborů zahrnutí

Klikněte pravým tlačítkem na soubor kódu ve vašem projektu a zvolte **Generovat graf souborů zahrnutí** zobrazíte grafu, které soubory jsou zahrnuty v ostatních souborech.

![C&#43; &#43; grafu souborů zahrnutí](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Zobrazit hierarchii volání

Klikněte pravým tlačítkem na každé volání funkce a zobrazte seznam všech funkcí, které volá a všechny funkce, které ji volaly rekurzivní. Každá funkce v seznamu lze rozšířit stejným způsobem. Další informace najdete v tématu [hierarchie volání](/visualstudio/ide/reference/call-hierarchy).

![C&#43;&#43; Call Hierarchy](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Viz také

[Upravit a Refaktorovat kód (C++)](writing-and-refactoring-code-cpp.md)</br>
[Procházet vaše C++ kódové základny v sadě Visual Studio](navigate-code-cpp.md)</br>
[Spolupráce s živými sdílenou složkou proC++](live-share-cpp.md)
