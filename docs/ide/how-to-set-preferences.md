---
title: Nastavení předvoleb kódování c++ v sadě Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: e3a665ead7a314b343ec3320e95b189f83a38a47
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365392"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Nastavení předvoleb kódování c++ v sadě Visual Studio

Přizpůsobením sady Visual Studio můžete usnadnit, zvýšit produktivitu a příjemnou možnosti kódování jazyka C++. Můžete:

- Přizpůsobte nabídky a panely nástrojů.
- Uspořádejte rozložení okna.
- Nastavte barevné motivy.
- Zadejte pravidla formátování jazyka C++, včetně několika stylů clangformatu.
- Vytvořte vlastní klávesové zkratky.

Předvolby můžete synchronizovat mezi více počítači a vytvářet a ukládat více sad předvoleb a sdílet je se spoluhráči. Můžete nainstalovat rozšíření z webu Visual Studio Marketplace, což vám další možnosti pro přizpůsobení chování. Další informace naleznete [v tématu Přizpůsobení prostředí IDE sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Uspořádání rozložení okna

V okně sady Visual Studio je prostor rozdělen do hlavní nabídky, panelu nástrojů, editoru kódu (nebo okna dokumentu) a oken nástrojů (například Průzkumník řešení a Seznam chyb). Některá okna se navzájem překrývají ve stejné poloze. Například Průzkumník řešení, zobrazení tříd, zobrazení prostředků a Průzkumník správy zdrojového kódu sdílejí stejnou výchozí pozici. Přepínáte mezi nimi výběrem karet v dolní části rámečku. Chcete-li, aby byla dvě nebo více těchto oken viditelná současně, přetáhněte jedno z nich za záhlaví na novou pozici. Můžete ukotvit proti jednomu z okrajů hlavního okna sady Visual Studio nebo jej můžete uvolnit.

Následující snímek obrazovky ukazuje okno **Průzkumníka týmu** přetahované z výchozí polohy na novou ukotvenou pozici na levé straně editoru kódu. Modrá stínovaná oblast ukazuje, kam bude okno umístěno při uvolnění tlačítka myši.

![Snímek obrazovky s oknem Průzkumníka týmu Visual Studia se zvýrazněnou změnou rozložení](media/window-layout-move-team-explorer.png)

V okně dokumentu je každý otevřený soubor obsažen v rámečku s kartami. Tyto karty můžete uvolnit nebo zamknout, stejně jako okna nástrojů. Další informace naleznete [v tématu Přizpůsobení rozložení oken v sadě Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Chcete-li skrýt všechna okna nástrojů a maximalizovat okno Editor kódu, přepněte *režim celé obrazovky*stisknutím **klávesy Alt** + **Shift** + **Enter** .

## <a name="set-c-coding-styles-and-formatting"></a>Nastavení stylů a formátování kódování jazyka C++

Můžete určit mnoho možností formátování jednotlivých kódů, například odsazení a pozice složených závorek. Chcete-li tak učinit, přejděte na**možnosti** >  **nástroje** > **textový editor** > **C/ C ++** > **formátování** (nebo zadejte Ctrl **+ Q** a vyhledejte "Formátování"). Případně můžete zadat jeden ze stylů [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (nebo vlastní styl ClangFormat).

![Snímek obrazovky s možnostmi ClangFormat](media/clang-format-ide.png)

Další informace o všech možnostech formátování naleznete v [tématech Možnosti, Textový editor, C/C++, Formátování](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Nastavení barevného motivu

Chcete-li nastavit světlé nebo tmavé pozadí, zadejte **Ctrl + Q** a vyhledejte "Barevný motiv". Můžete je také najít tak, že přejdete do**prostředí** > **Možnosti** >  **nástroje**a zvolíte **barevný motiv**.

![Snímek obrazovky s barevnými motivy](media/tools-options-color-theme.png)

Například zde je tmavý motiv:

![Snímek obrazovky s Visual Studio s tmavým barevným motivem](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Přizpůsobení vybarvení kódu

V Sadě Visual Studio 2019 si můžete vybrat ze tří *předdefinovaných barevných schémat*. Ty určují, jak jsou prvky kódu v editoru obarveny. Chcete-li vybrat motiv, přejděte do**Options** > **textového editoru textových editorů** > **c/c++** > **View** **a** > zvolte **Barevné schéma**:

![Snímek obrazovky s možnostmi barevného schématu jazyka C++ se zvýrazněným zvýrazněním](media/color-schemes.png)

V barevném schématu s názvem **Visual Studio 2017**je většina prvků kódu jednoduše černá. V **rozšířeném** barevném schématu jsou obarveny funkce, místní proměnné, makra a další prvky. V **rozšířeném (Globals vs. Members)** schéma globální funkce a proměnné jsou obarveny kontrastovat s členy třídy. Výchozí režim je **Rozšířený**a vypadá takto:

![Snímek obrazovky s rozšířeným barevným schématem](media/color-scheme-enhanced.png)

Bez ohledu na to, který motiv nebo barevné schéma je aktivní, můžete přizpůsobit písmo a barvy pro jednotlivé prvky kódu. Chcete-li to provést, přejděte na**možnosti** >  **nástrojů** > **prostředí** > **písma a barvy** (nebo zadejte Ctrl + **Q** a vyhledejte "Písma"). Posuňte se dolů v seznamu položek zobrazení, dokud se nezobrazí možnosti jazyka C++.

![Snímek obrazovky s možnostmi písma a barev jazyka C++](media/tools-options-cpp-colors.png)

Barvy, které zde nastavíte, přepíší hodnoty definované pro barevná schémata. Pokud se chcete vrátit k výchozím barvám barevného schématu, nastavte ji zpět na **výchozí**.

## <a name="customize-the-toolbars"></a>Přizpůsobení panelů nástrojů

Panely nástrojů poskytují pohodlný způsob vydávání příkazů jediným kliknutím, nikoli pomocí nabídek nebo klávesových zkratek. Visual Studio obsahuje standardní sadu panelů nástrojů. Pro standardní vývoj jazyka C++ jsou nejužitečnější panely nástrojů pravděpodobně Standardní, Textový editor, Sestavení, Ladění, Řízení zdrojového kódu a Porovnat soubory. Pro vývoj systému Windows jsou dialogový editor a Editor obrázků užitečné pro rozmisťování dialogových oken a úpravy ikon.

Najeďte na ikony na panelu nástrojů a podívejte se, který příkaz představuje:

![Snímek obrazovky s ikonami panelu nástrojů s příkladem informací o příkazech dostupných při najetí přes](media/toolbar-mouse-hover.png)

Výběrem šipky dolů můžete přidat nebo odebrat příkazy nebo vytvořit vlastní panel nástrojů. Chcete-li panel nástrojů přesunout do nového umístění, přetáhněte jej vedle tečkovaného pruhu vlevo.

![Snímek obrazovky panelu nástrojů se zvýrazněnou šipkou dolů a tečkovaným pruhem](media/toolbar-move-edit.png).

Další informace naleznete v [tématu Postup: Přizpůsobení nabídek a panelů nástrojů v sadě Visual Studio](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio).

## <a name="show-or-hide-line-numbers"></a>Zobrazení nebo skrytí čísel řádků

Můžete určit, zda se čísla řádků zobrazí na levé straně oken editoru. V **části Možnosti**vyberte v části **C/C++** položku **Obecné**. V části **Nastavení** vyberte nebo zrušte **zaškrtnutí políčka Čísla řádků**v závislosti na vašich preferencích.

![Snímek obrazovky s obecnými možnostmi se zvýrazněnými čísly řádků](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Vytváření klávesových zkratek

Mnoho příkazů v sadě Visual Studio obsahuje *klávesové zkratky*, kombinace kláves s klávesami Ctrl, Alt a Shift. Tyto klávesové zkratky můžete upravit nebo vytvořit nové vlastní v sadě Visual Studio. Přejděte na **klávesnici Tools** > **Options** > **Environment** > **Keyboard** (nebo zadejte Ctrl + **Q** a vyhledejte "zkratky"). Další informace naleznete v [tématu Identifikace a přizpůsobení klávesových zkratek v sadě Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
