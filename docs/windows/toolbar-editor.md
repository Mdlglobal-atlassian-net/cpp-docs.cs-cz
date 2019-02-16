---
title: Editor panelu nástrojů (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.toolbar.F1
- vc.editors.toolbar
- vc.editors.newtoolbarresource
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
- tool tips [C++], adding to toolbar buttons
- "\n in tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
ms.openlocfilehash: 7ef08551960c9308a84b9838249a3d9ff4950d98
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320611"
---
# <a name="toolbar-editor-c"></a>Editor panelu nástrojů (C++)

**Nástrojů** editor umožňuje vytvářet prostředky nástrojů jazyka C++ a rastrové obrázky převést prostředky panelu nástrojů. **Nástrojů** editor používá grafické zobrazení zobrazíte panel nástrojů a tlačítka, která se velmi podobají, jak bude vypadat dokončené aplikace.

**Nástrojů** okno editoru naleznete dvě zobrazení obrázku tlačítka, stejně jako okno editoru obrázků. Rozdělit pruh odděluje. Můžete přetáhnout příčku ze strany na stranu, a změnit tak relativní velikosti podoken. Aktivní podokno zobrazuje hranici výběru. Nad dvě zobrazení obrázku je panel nástrojů předmět.

![Toolbar Editor](../mfc/media/vctoolbareditor.gif "vcToolbarEditor") Toolbar Editor

**Nástrojů** editoru je podobný **Image** editor ve funkcích. Položky nabídky, grafické nástroje a rastrový obrázek mřížky jsou stejná jako v **Image** editoru. Příkaz nabídky **Image** nabídky, aby bylo možné přepínat mezi **nástrojů** editoru a **Image** editoru. Další informace o používání **grafiky** nástrojů **barvy** palety, nebo **Image** nabídky, naleznete v tématu [Editor obrázků](../windows/image-editor-for-icons.md).

Můžete vytvořit nový panel nástrojů v projektu jazyka C++ převedením rastrový obrázek. Obrázek z rastrového obrázku se převede na obrázky tlačítek pro panel nástrojů. Obvykle rastrový obrázek obsahuje několik imagí tlačítko v jediné bitmapě pomocí jedné image pro každé tlačítko. Image může mít libovolnou velikost, protože výchozí hodnota je 16 pixelů na šířku a výšku obrázku. Můžete zadat velikost Image tlačítko **nový prostředek panelu nástrojů** dialogové okno při výběru **panelu nástrojů editoru** z **Image** nabídky v editoru obrázků.

**Nový prostředek panelu nástrojů** dialogové okno umožňuje zadat šířka a výška ohraničení tlačítka, které přidáváte do nástrojů prostředku v projektu jazyka C++. Výchozí hodnota je 16 × 15 pixelů.

Rastrový obrázek, který se používá k vytvoření panelu nástrojů má maximální šířku 2048. Pokud jste nastavili **šířku tlačítka** až 512, můžete mít jenom čtyři tlačítka. Pokud nastavíte šířku na 513, může mít pouze tři tlačítka.

Dialogové okno má následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Šířka tlačítka**|Poskytuje prostor pro zadání šířku pro tlačítka panelu nástrojů, které při převádění z prostředku rastrového obrázku na prostředek panelu nástrojů. Image se ořízne na šířku a výšku zadán a barvy jsou upraveny pro použití standardních barev panelu nástrojů (16 barev).|
|**Výška tlačítka**|Poskytuje prostor pro zadání výšku pro tlačítka panelu nástrojů, které při převádění z prostředku rastrového obrázku na prostředek panelu nástrojů. Image se ořízne na šířku a výšku zadán a barvy jsou upraveny pro použití standardních barev panelu nástrojů (16 barev).|

Ve výchozím nastavení je na pravém konci panelu nástrojů zobrazí tlačítko Nový nebo prázdný. Toto tlačítko můžete přesunout začnete upravovat. Při vytváření nového tlačítka další prázdné tlačítko vpravo se zobrazí upravená tlačítka. Při ukládání panelu nástrojů tlačítko prázdné se neuloží.

Vlastnosti tlačítka panelu nástrojů jsou:

|Vlastnost|Popis|
|--------------|-----------------|
|**ID**|Definuje ID pro tlačítko. Rozevírací seznam obsahuje běžné **ID** názvy.|
|**Šířka**|Nastavuje šířku tlačítka. doporučuje se 16 pixelů.|
|**Výška**|Nastaví výšku tlačítka. Výška tlačítka změní výšku všechna tlačítka na panelu nástrojů. doporučuje se 15 pixelů.|
|**Zeptat se**|Definuje zprávy zobrazí ve stavovém řádku. Přidání \n a název Přidá popis tlačítka na toto tlačítko panelu nástrojů. Další informace najdete v tématu [vytvoření popisu](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Šířka** a **výška** platí pro všechna tlačítka. Rastrový obrázek, který se používá k vytvoření panelu nástrojů má maximální šířku 2048. Takže pokud nastavíte šířku tlačítka na 512, můžete mít jenom čtyři tlačítka a nastavte šířku na 513 lze pouze máte tři tlačítka.

## <a name="how-to"></a>Postupy

**Nástrojů** editor umožňuje:

### <a name="to-create-new-toolbars"></a>K vytvoření nových panelů nástrojů

1. V **prostředků** zobrazení, klikněte pravým tlačítkem na soubor .rc a pak zvolte **přidat prostředek** z místní nabídky. (Pokud máte existující nástrojů v souboru .rc, je můžete jednoduše kliknout pravým tlačítkem **nástrojů** a pak zvolte položku **vložit nástrojů** z místní nabídky.)

1. V **přidat prostředek** dialogu **nástrojů** v **typ prostředku** seznamu a pak zvolte **nový**.

   Pokud symbol plus (**+**) se zobrazí vedle **nástrojů** typ prostředku, znamená to, že šablony nástrojů jsou k dispozici. Vyberte znaménko plus rozbalit seznam šablon, vyberte šablonu a zvolte **nový**.

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>Převod bitmap na prostředky panelu nástrojů

1. Otevřete existující prostředek rastrového obrázku v [editor obrázků](../windows/image-editor-for-icons.md). (Pokud ještě rastrového obrázku není v souboru .rc, klikněte pravým tlačítkem na soubor .rc, zvolte **Import** z místní nabídky, přejděte na rastrový obrázek, které chcete přidat do souboru .rc a pak vyberte **otevřít**.)

1. Z **Image** nabídce zvolte **panelu nástrojů editoru**.

   **Nový prostředek panelu nástrojů** zobrazí se dialogové okno. Můžete změnit šířku a výšku obrázky ikon tak, aby odpovídaly rastrového obrázku. Obrázek panelu nástrojů se následně zobrazí v editoru panelu nástrojů.

1. K dokončení převodu, změňte příkaz **ID** pomocí tlačítka [okno vlastností](/visualstudio/ide/reference/properties-window). Zadejte nový **ID** nebo vyberte **ID** z rozevíracího seznamu.

   > [!TIP]
   > **Vlastnosti** okno obsahuje tlačítko připínáčku v záhlaví programu. Výběrem tohoto tlačítka povolí nebo zakáže **automaticky skrýt** okna. Rychle procházet všechny vlastnosti tlačítka panelu nástrojů bez nutnosti znovu otevřít windows jednotlivých vlastností, zapněte **automaticky skrýt** vypnout proto **vlastnosti** okno zůstane bez pohybu.

Identifikátory příkazů tlačítka na nový panel nástrojů můžete také změnit pomocí [okno vlastností](/visualstudio/ide/reference/properties-window).

### <a name="to-create-move-and-edit-toolbar-buttons"></a>K vytváření, přesunutí a úprava tlačítek panelu nástrojů

Můžete snadno vytvořit, přesunutí, kopírování a úprava tlačítek panelu nástrojů:

#### <a name="to-create-a-new-toolbar-button"></a>K vytvoření nového tlačítka panelu nástrojů

1. V [zobrazení prostředků](../windows/resource-view-window.md) rozbalte složku prostředků (například *Project1.rc*).

1. Rozbalte **nástrojů** a pak zvolte položku panelu nástrojů pro úpravy.

1. Přiřaďte ID prázdné tlačítko na pravém konci panelu nástrojů. Můžete tak učinit pomocí úpravy **ID** vlastnost [okno vlastností](/visualstudio/ide/reference/properties-window). Můžete například poskytnout stejný Identifikátor jako možnost nabídky tlačítka panelu nástrojů. V takovém případě použijte pole rozevíracího seznamu vyberte **ID** položky nabídky.

   -nebo-

   Vyberte tlačítko prázdné na pravém konci panelu nástrojů (v **panel nástrojů zobrazení** podokno) a začněte kreslení. Je přiřazen výchozí Identifikátor příkazu tlačítka (ID_BUTTON\<n >).

Můžete také zkopírovat a vložit obrázek do nového tlačítka panelu nástrojů.

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Chcete-li přidat bitovou kopii na panelu nástrojů jako tlačítko

1. V [zobrazení prostředků](../windows/resource-view-window.md), otevřete poklepáním panelu nástrojů.

1. Dále otevřete image, kterou chcete přidat na panel nástrojů.

   > [!NOTE]
   > Pokud obrázek otevřít v sadě Visual Studio, se otevře v **Image** editoru. Image můžete otevřít také v jiných aplikacích grafiky.

1. Z **upravit** nabídce zvolte **kopírování**.

1. Přepnout na panel nástrojů tak, že vyberete jeho karty v horní části okna zdroje.

1. Z **upravit** nabídce zvolte **vložit**.

   Obrázek se zobrazí na panelu nástrojů jako nového tlačítka.

#### <a name="to-move-a-toolbar-button"></a>Přesunutí tlačítka panelu nástrojů

V **panel nástrojů zobrazení** podokně přetáhněte tlačítko, které chcete přesunout do nového umístění na panelu nástrojů.

#### <a name="to-copy-buttons-from-a-toolbar"></a>Kopírování tlačítek z panelu nástrojů

1. Podržte stisknutou klávesu **Ctrl** klíč.

1. V **panel nástrojů zobrazení** podokně přetáhněte tlačítko buď nové místo na panelu nástrojů nebo do umístění na jiný panel nástrojů.

#### <a name="to-delete-a-toolbar-button"></a>Odstranění tlačítka panelu nástrojů

Tlačítko panelu nástrojů vyberte a přetáhněte ho z panelu nástrojů.

#### <a name="to-insert-or-remove-space-between-buttons-on-a-toolbar"></a>Vložit nebo odebrání mezer mezi tlačítky na panelu nástrojů

Obecně platí k vložení mezery mezi tlačítka, přetáhněte je od sebe na panelu nástrojů. Chcete-li odebrat místa, přetáhněte je směrem k sobě navzájem.

|Akce|Krok|
|------|------|
|Vložit mezeru před tlačítko, které není mezeru|Přetáhněte tlačítko na pravé straně nebo dolů, dokud se překrývá na tlačítko Další informace o uprostřed.|
|Vložit mezeru před tlačítko, které následuje mezera a zajistit koncové mezery|Přetáhněte toto tlačítko, dokud pravé nebo dolní okraj je právě klepnou na tlačítko Další nebo právě překrývá.|
|Vložit mezeru před tlačítko, které následuje mezera a zavřete tento následující místo|Přetáhněte tlačítko na pravé straně nebo dolů, dokud se překrývá na tlačítko Další informace o uprostřed.|
|Chcete-li odebrat mezery mezi tlačítka na panelu nástrojů|Přetáhněte tlačítko na jedné straně místa směrem k tlačítku na druhé straně prostor se překrývá na tlačítko Další informace o urazili polovinu cesty.|

> [!NOTE]
> Pokud není žádný prostor vedle tlačítka, které jste přetažením směrem od a více než polovinu životnosti minulé vedle tlačítka, přetáhněte tlačítko **nástrojů** editor také vloží mezeru na opačnou stranu tlačítka, které jste přetažení.

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>Chcete-li změnit vlastnosti tlačítka panelu nástrojů

1. V projektu jazyka C++ vyberte tlačítko panelu nástrojů.

1. Zadejte nové ID v **ID** vlastnost [okno vlastností](/visualstudio/ide/reference/properties-window), nebo pomocí rozevíracího seznamu vyberte novou **ID**.

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>Vytvoření popisku tlačítka pro tlačítko toolbar

1. Vyberte tlačítko panelu nástrojů.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window)v **výzvy** vlastnost pole, přidejte popis tlačítka pro stavový řádek; po něm, přidejte `\n` a název nástroje tip.

Je běžným příkladem popisku tlačítka **tisk** tlačítko **WordPad**:

1. Otevřít **WordPad**.

1. Najeďte myší **tisk** tlačítka panelu nástrojů.

1. Všimněte si, že slovo `Print` je nyní plovoucí pod ukazatele myši.

1. Podívejte se na stavovém řádku (dole **WordPad** okno) – Všimněte si, že nyní zobrazuje text `Prints the active document`.

`Print` v **kroku 3** je "nástroj tip name," a `Prints the active document` z **kroku 4** je "Popis tlačítka na stavový řádek."

Pokud chcete tento efekt použití **nástrojů** editor, můžete nastavit **výzvy** vlastnost `Prints the active document\nPrint`.

> [!NOTE]
> Můžete upravit pomocí text výzvy [okno vlastností](/visualstudio/ide/reference/properties-window).

## <a name="requirements"></a>Požadavky

Knihovny MFC nebo ATL

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)<br/>
[Nabídky a ostatní prostředky](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Vlastnosti tlačítka panelu nástrojů](../windows/toolbar-button-properties.md)<br/>
