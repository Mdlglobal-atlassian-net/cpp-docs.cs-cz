---
title: Nastavení předvoleb C++ kódování v sadě Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: f1d222dc38720ea897cfbf2fb9fa0dd2727e7720
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816562"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Nastavení předvoleb C++ kódování v sadě Visual Studio

Přizpůsobením sady C++ Visual Studio můžete usnadnit práci s kódováním, produktivitu a pleasurable. Můžete:

- Přizpůsobení nabídek a panelů nástrojů.
- Uspořádat rozložení okna
- Nastavte barevné motivy.
- Zadejte C++ pravidla formátování, včetně několika stylů ClangFormat.
- Vytvořte vlastní klávesové zkratky.

Můžete synchronizovat předvolby napříč několika počítači a vytvořit a uložit několik sad předvoleb a sdílet je s ostatními týmu. Rozšíření můžete nainstalovat z Visual Studio Marketplace, což vám poskytne další možnosti pro přizpůsobení chování. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Uspořádat rozložení okna

V okně sady Visual Studio je místo rozděleno do hlavní nabídky, panelu nástrojů, editoru kódu (nebo okna dokumentu) a oken nástrojů (například Průzkumník řešení a Seznam chyb). Některá okna se vzájemně překrývají na stejné pozici. Například Průzkumník řešení, Zobrazení tříd, Prostředky a Průzkumník správy zdrojových souborů všechny sdílet stejné výchozí umístění. Můžete mezi nimi přepínat výběrem karet v dolní části rámečku. Chcete-li zobrazit dvě nebo více těchto oken současně, přetáhněte jednu z nich podle jejího záhlaví na novou pozici. Můžete ho ukotvit proti jednomu z ohraničení hlavního okna sady Visual Studio nebo ho můžete uvolnit.

Následující snímek obrazovky ukazuje **Team Explorer** okno přetažené z výchozí pozice na novou, ukotvenou pozici na levé straně editoru kódu. Modře šedivá oblast zobrazuje, kde bude okno umístěno po uvolnění tlačítka myši.

![Snímek obrazovky s oknem Team Explorer sady Visual Studio se zvýrazněnou změnou rozložení](media/window-layout-move-team-explorer.png)

V okně dokumentu je každý otevřený soubor obsažený v rámečku s kartami. Tyto karty můžete uvolnit nebo uzamknout, stejně jako okna nástrojů. Další informace naleznete v tématu [přizpůsobení rozložení oken v aplikaci Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Chcete-li skrýt všechna okna nástrojů a maximalizovat okno editoru kódu, stiskněte klávesu **Alt** + **SHIFT** + **ENTER** a přepněte *režim zobrazení na celé obrazovce*.

## <a name="set-c-coding-styles-and-formatting"></a>Nastavení C++ stylů a formátování kódu

Můžete určit mnoho možností formátování jednotlivých kódů, jako je například odsazení a pozice složených závorek. Provedete to tak, že přejdete do části **nástroje** > **Možnosti** > **textový editor** > **C/C++**  > **formátování** (nebo zadáte **CTRL + Q** a vyhledáte "formátování"). Případně můžete určit jeden ze stylů [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (nebo vlastní styl ClangFormat).

![Snímek obrazovky s možnostmi ClangFormat](media/clang-format-ide.png)

Další informace o všech možnostech formátování naleznete v tématu [Možnosti, textový editor, CC++/, formátování](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Nastavení barevného motivu

Chcete-li nastavit světlé nebo tmavé pozadí, zadejte **CTRL + Q** a vyhledejte "barevný motiv". Můžete je také najít tak, že v**prostředí** **nástroje** > **Možnosti** >  a zvolíte **barevný motiv**.

![Snímek obrazovky s barevnými motivy](media/tools-options-color-theme.png)

Tady je například tmavý motiv:

![Snímek obrazovky sady Visual Studio s tmavým barevným motivem](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Přizpůsobení barevného zabarvení kódu

V aplikaci Visual Studio 2019 můžete vybrat ze tří předdefinovaných *schémat barev*. Ty určují, jak jsou v editoru barevně barvené prvky kódu. Chcete-li zvolit motiv, použijte možnost **nástroje** > **Možnosti**-1  > **textový editor** > **zobrazení** **C/C++**  >  a vyberte možnost **barevné schéma**:

![Snímek obrazovky C++ s možnostmi barevného schématu se zvýrazněnou možností Enhanced](media/color-schemes.png)

V barevném schématu nazývaném **Visual Studio 2017**je většina prvků kódu jednoduše černá. V **rozšířeném** barevném schématu jsou zabarvení funkcí, místních proměnných, maker a dalších prvků. V **rozšířených (globálních vs. Members)** schématu jsou globální funkce a proměnné barevně zabarvované na rozdíl od členů třídy. Výchozí režim je **vylepšen**a vypadá takto:

![Snímek obrazovky s vylepšeným barevným schématem](media/color-scheme-enhanced.png)

Bez ohledu na to, který motiv nebo barevné schéma je aktivní, můžete přizpůsobit písmo a barvy pro jednotlivé prvky kódu. Provedete to tak, že přejdete do části **nástroje** > **Možnosti** > **prostředí** > **písma a barvy** (nebo zadáte **CTRL + Q** a vyhledáte "fonty"). Posuňte se dolů na seznam zobrazených položek, dokud C++ neuvidíte možnosti.

![Snímek obrazovky C++ s možnostmi písma a barvy](media/tools-options-cpp-colors.png)

Barvy, které nastavíte, přepíší hodnoty definované pro barevná schémata. Pokud se chcete vrátit k výchozím barvám pro barevné schéma, nastavte barvu zpátky na **výchozí**.

## <a name="customize-the-toolbars"></a>Přizpůsobení panelů nástrojů

Panely nástrojů poskytují pohodlný způsob, jak vydávat příkazy jediným kliknutím, a ne pomocí nabídek nebo klávesových zkratek. Sada Visual Studio obsahuje standardní sadu panelů nástrojů. Pro standardní C++ vývoj jsou nejužitečnější panely nástrojů pravděpodobně standardní, textový editor, sestavení, ladění, Správa zdrojového kódu a porovnání souborů. Pro vývoj pro Windows je editor dialogových oken a editor obrázků vhodný pro rozložení dialogových oken a úprav ikon.

Najeďte myší na ikony na panelu nástrojů, abyste viděli, který příkaz představuje:

![Snímek obrazovky s ikonami panelu nástrojů, kde jsou k dispozici například informace o příkazu při najetí myší](media/toolbar-mouse-hover.png)

Můžete přidat nebo odebrat příkazy nebo vytvořit vlastní panel nástrojů, a to tak, že vyberete šipku dolů. Chcete-li přesunout panel nástrojů do nového umístění, přetáhněte ho na panel s tečkovanými tečkami vlevo.

![Snímek obrazovky panelu nástrojů se zvýrazněnou šipkou dolů a tečkovaným pruhem](media/toolbar-move-edit.png).

Další informace najdete v tématu [Postupy: přizpůsobení nabídek a panelů nástrojů v aplikaci Visual Studio](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio).

## <a name="show-or-hide-line-numbers"></a>Zobrazit nebo skrýt čísla řádků

Můžete určit, zda se čísla řádků zobrazí na levé straně okna editoru. V nabídce **Možnosti**v části **CC++/** vyberte **Obecné**. V části **Nastavení** vyberte nebo vymažte **čísla řádků**v závislosti na vaší předvolbách.

![Snímek obrazovky s obecnými možnostmi s zvýrazněnými čísly řádků](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Vytvoření klávesových zkratek

Mnohé příkazy v aplikaci Visual Studio obsahují *klávesové zkratky*, kombinace kláves s klávesami CTRL, ALT a Shift. V aplikaci Visual Studio můžete tyto klávesové zkratky upravovat nebo vytvářet nové. V **nabídce nástroje**@no__t**možnosti**-1  > **prostředí**@no__t **-5 (** nebo zadejte **CTRL + Q** a vyhledejte "zkratky"). Další informace naleznete v tématu [identifikace a přizpůsobení klávesových zkratek v aplikaci Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
