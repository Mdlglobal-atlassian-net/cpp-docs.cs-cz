---
title: Nastavení předvoleb C++ kódování v sadě Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, menus and more in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: 90c9f39135b90a2c5015861a78dd8760b9a8aeed
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686885"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Nastavení předvoleb C++ kódování v sadě Visual Studio

Přizpůsobením sady C++ Visual Studio můžete dosáhnout lepšího, produktivního a pleasurableho kódu. Nabídky a panely nástrojů můžete přizpůsobit, uspořádat rozložení okna, nastavit barevné motivy, zadat C++ pravidla formátování, včetně několika typů ClangFormat a vytvořit vlastní klávesové zkratky. Můžete synchronizovat předvolby napříč několika počítači a vytvořit a uložit několik sad předvoleb a sdílet je s ostatními týmu. Rozšíření můžete nainstalovat z Visual Studio Marketplace, která poskytují další vlastní chování. Mnohé z těchto možností jsou zdokumentovány v části [přizpůsobení prostředí IDE sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Uspořádat rozložení okna

V okně sady Visual Studio je místo rozděleno do hlavní nabídky, panelu nástrojů, editoru kódu (nebo okna dokumentu) a oken nástrojů (**Průzkumník řešení**, **Seznam chyb**atd.). Některá okna se vzájemně překrývají na stejné pozici. Například **Průzkumník řešení**, **zobrazení tříd**, **prostředky**a **Průzkumník správy zdrojových souborů** všechny sdílet stejné výchozí umístění. Přepínat mezi nimi můžete kliknutím na karty v dolní části rámečku. Chcete-li zobrazit dvě nebo více těchto oken současně, přetáhněte jednu z nich podle jejího záhlaví na novou pozici. Můžete ho ukotvit proti jednomu z ohraničení hlavního okna sady Visual Studio nebo ho můžete uvolnit. Následující ilustrace znázorňuje **Team Explorer** okno v procesu přetažení z výchozí pozice do nové ukotvené pozice na levé straně editoru kódu. Modře šedivá oblast zobrazuje, kde bude okno umístěno po uvolnění tlačítka myši.

![Změna rozložení okna](media/window-layout-move-team-explorer.png)

V okně dokumentu je každý otevřený soubor obsažený v rámečku s kartami. Tyto karty můžete uvolnit nebo uzamknout stejně jako okna nástrojů. Další informace naleznete v tématu [přizpůsobení rozložení oken v aplikaci Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Chcete-li skrýt všechna okna nástrojů a maximalizovat okno editoru kódu, stiskněte klávesu **Alt** + **SHIFT** + **ENTER** a přepněte *režim zobrazení na celé obrazovce*.

## <a name="set-c-coding-styles-and-formatting"></a>Nastavení C++ stylů a formátování kódu

Můžete určit mnoho možností formátování jednotlivých kódů, například odsazení a pozice složených závorek, a to tak, že přejdete na **nástroje**@no__t**Možnosti**-1  > **textový editor** > **C/C++**  > **formátování** (nebo typ **Stiskněte kombinaci kláves CTRL + Q** a vyhledejte "formátování"). Případně můžete zadat jeden ze stylů [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (nebo vlastní styl ClangFormat):

![ClangFormat možnosti](media/clang-format-ide.png)

Další informace o všech možnostech formátování naleznete v tématu [Možnosti, textový editor, CC++/, formátování](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Nastavení barevného motivu

Chcete-li nastavit světlé nebo tmavé pozadí, zadejte **CTRL + Q** a vyhledejte "barevný motiv". K dispozici můžete také prostřednictvím **nástrojů** >  @no__t**Možnosti**-3**prostředí** a zvolit **barevný motiv**:

![Barevné motivy](media/tools-options-color-theme.png)

Následující obrázek znázorňuje tmavý motiv:

![Tmavý motiv](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Přizpůsobení barevného zabarvení kódu

V aplikaci Visual Studio 2019 můžete vybrat ze tří předdefinovaných *schémat barev* , která určují, jak jsou v editoru barevně barvené prvky kódu. Chcete-li zvolit motiv, přejděte do **nástrojů** > **Možnosti**-1  > **textový editor** > **zobrazení** **C/C++**  >  a vyberte možnost **barevné schéma**:

![C++Barevná schémata](media/color-schemes.png)

Ve schématu barev sady **Visual Studio 2017** je většina prvků kódu jednoduše černá. V **rozšířeném** barevném schématu jsou zabarvení funkcí, místních proměnných, maker a dalších prvků. V **rozšířených (globálních vs. Members)** schématu jsou globální funkce a proměnné barevně zabarvované na rozdíl od členů třídy. Výchozí režim je **Vylepšený** a vypadá takto:

![Rozšířené barevné schéma](media/color-scheme-enhanced.png)

Bez ohledu na to, který motiv nebo barevné schéma je aktivní, můžete přizpůsobit písmo a barvy pro jednotlivé prvky kódu tím, že přejdete na **nástroje** > **možnosti**-1  > **prostředí** > **písma a barvy** (nebo typ  **CTRL + Q** a vyhledejte "fonts" (písma). Posuňte se dolů na seznam zobrazených položek, dokud C++ neuvidíte možnosti:

![C++možnosti písma a barvy](media/tools-options-cpp-colors.png)

Barvy, které nastavíte, přepíší hodnoty definované pro barevná schémata. Pokud jste změnili barvu, ale chcete použít výchozí barvy pro barevné schéma, je nutné nastavit barvu zpátky na **výchozí** .

## <a name="customize-the-toolbars"></a>Přizpůsobení panelů nástrojů

Panely nástrojů poskytují pohodlný způsob, jak vydávat příkazy jediným kliknutím myši, a ne pomocí nabídek nebo klávesových zkratek. Sada Visual Studio obsahuje standardní sadu panelů nástrojů. Pro standardní C++ vývoj jsou nejužitečnější panely nástrojů pravděpodobně standardní, textový editor, sestavení, ladění, Správa zdrojového kódu a případně porovnání souborů. Pro vývoj pro Windows je editor dialogových oken a editor obrázků vhodný pro rozložení dialogových oken a úprav ikon.

Najeďte myší na ikony na panelu nástrojů, abyste viděli, který příkaz představuje:

![QuickInfo panelu nástrojů](media/toolbar-mouse-hover.png)

Kliknutím na šipku dolů můžete přidat nebo odebrat příkazy nebo vytvořit vlastní panel nástrojů. Chcete-li přesunout panel nástrojů do nového umístění, přetáhněte ho na panel s tečkovanými tečkami vlevo:

![Přizpůsobení nebo přesunutí panelu nástrojů](media/toolbar-move-edit.png).

Další informace najdete v tématu [Postupy: přizpůsobení nabídek a panelů nástrojů v aplikaci Visual Studio](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio).

## <a name="show-or-hide-line-numbers"></a>Zobrazit nebo skrýt čísla řádků

Chcete-li určit, zda se mají čísla řádků zobrazit vlevo od oken editoru, přejděte na **číslo řádku**a zaškrtnout nebo zrušte jeho kontrolu:

![Čísla řádků](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Vytvoření klávesových zkratek

Všechny příkazy v aplikaci Visual Studio lze vytvořit pomocí klávesových zkratek s různými kombinacemi kláves CTRL, ALT a Shift. Můžete vytvořit vlastní zástupce, a to tak, že přejdete na **nástroje**@no__t**možnosti**-1 @no__t**prostředí**@no__t-**5 (** nebo zadáte **CTRL + Q** a vyhledáte "zkratky"). Další informace naleznete v tématu [identifikace a přizpůsobení klávesových zkratek v aplikaci Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
