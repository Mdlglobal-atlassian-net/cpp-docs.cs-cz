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
ms.openlocfilehash: 5aadb00e6e010467ee9c70dc357916d3c4f81853
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211079"
---
# <a name="toolbar-editor-c"></a>Editor panelu nástrojů (C++)

**Panelu nástrojů editoru** umožňuje vytvářet prostředky panelu nástrojů a rastrové obrázky převést prostředky panelu nástrojů. **Panelu nástrojů editoru** využívá grafické zobrazení k zobrazení panelu nástrojů a tlačítka, která se velmi podobají, jak bude vypadat dokončené aplikace.

**Panelu nástrojů editoru** okno naleznete dvě zobrazení obrázku tlačítka, stejně jako **Editor obrázků** okna. Rozdělit pruh odděluje a můžete přetáhnout příčku ze strany na stranu, a změnit tak relativní velikosti podoken. Aktivní podokno zobrazuje hranici výběru a nad dvě zobrazení obrázku je panel nástrojů předmět.

![Toolbar Editor](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**Editor panelu nástrojů**

**Panelu nástrojů editoru** je podobný **Editor obrázků** funkcí a položek nabídky, grafické nástroje a rastrový obrázek mřížky mezi nimi jsou stejné. Je v příkazu nabídky **Image** nabídky přepínat mezi **panelu nástrojů editoru** a **Editor obrázků**. Další informace o používání **grafiky** nástrojů **barvy** palety, nebo **Image** nabídky, naleznete v tématu [Editor obrázků](../windows/image-editor-for-icons.md).

Můžete vytvořit nový panel nástrojů v projektu jazyka C++ převedením rastrový obrázek. Obrázek z rastrového obrázku se převede na obrázky tlačítek pro panel nástrojů. Obvykle rastrový obrázek obsahuje několik imagí tlačítko v jediné bitmapě pomocí jedné image pro každé tlačítko. Image může mít libovolnou velikost, protože výchozí hodnota je 16 pixelů na šířku a výšku obrázku. Můžete zadat velikost obrázky tlačítek v **nový prostředek panelu nástrojů** dialogové okno při výběru **panelu nástrojů editoru** z **Image** při v nabídce  **Editor obrázků**.

**Nový prostředek panelu nástrojů** dialogové okno umožňuje zadat šířka a výška ohraničení tlačítka, které přidáváte do nástrojů prostředku v projektu jazyka C++. Výchozí hodnota je 16 × 15 pixelů.

Rastrový obrázek, který se používá k vytvoření panelu nástrojů má maximální šířku 2048, tak pokud nastavíte **šířku tlačítka** k *512*, můžete mít jenom čtyři tlačítka. Pokud nastavíte šířku na *513*, můžete mít jenom tři tlačítka.

**Nový prostředek panelu nástrojů** dialogové okno má následující vlastnosti:

|Vlastnost|Popis|
|---|---------------|
|**Šířka tlačítka**|Poskytuje prostor pro zadání šířku pro tlačítka panelu nástrojů, které při převádění z prostředku rastrového obrázku na prostředek panelu nástrojů.|
|**Výška tlačítka**|Poskytuje prostor pro zadání výšku pro tlačítka panelu nástrojů, které při převádění z prostředku rastrového obrázku na prostředek panelu nástrojů.|

> [!NOTE]
> Image se ořízne na šířku a výšku zadán a barvy jsou upraveny pro použití standardních barev panelu nástrojů (16 barev).

Ve výchozím nastavení je na pravém konci panelu nástrojů zobrazí tlačítko Nový nebo prázdný. Toto tlačítko můžete přesunout začnete upravovat. Při vytváření nového tlačítka další prázdné tlačítko vpravo se zobrazí upravená tlačítka. Při ukládání panelu nástrojů tlačítko prázdné se neuloží.

Tlačítka panelu nástrojů má následující vlastnosti:

|Vlastnost|Popis|
|--------------|-----------------|
|**ID**|Definuje ID pro tlačítko. Rozevírací seznam obsahuje běžné **ID** názvy.|
|**Šířka**|Nastavuje šířku tlačítka. doporučuje se 16 pixelů.|
|**Výška**|Nastaví výšku tlačítka. Výška tlačítka změní výšku všechna tlačítka na panelu nástrojů. doporučuje se 15 pixelů.|
|**Zeptat se**|Definuje zprávy zobrazí ve stavovém řádku. Přidání *\n* a přidá název **popisek** na toto tlačítko panelu nástrojů. Další informace najdete v tématu [vytvoření popisu](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Šířka** a **výška** platí pro všechna tlačítka. Rastrový obrázek, který se používá k vytvoření panelu nástrojů má maximální šířku 2048, tak pokud nastavíte šířku tlačítka na *512*, můžete mít jenom čtyři tlačítka a nastavte šířku na *513*, můžete mít jenom tři tlačítka.

## <a name="how-to"></a>Postupy

**Panelu nástrojů editoru** vám umožní:

### <a name="to-create-new-toolbars"></a>K vytvoření nových panelů nástrojů

1. V **prostředků** zobrazení, klikněte pravým tlačítkem na soubor .rc a zvolte **přidat prostředek**. Pokud máte existující nástrojů v souboru .rc, kliknete pravým tlačítkem **nástrojů** a pak zvolte položku **vložit nástrojů**.

1. V **přidat prostředek** dialogu **nástrojů** v **typ prostředku** seznamu a pak zvolte **nový**.

   Pokud symbol plus (**+**) se zobrazí vedle **nástrojů** typ prostředku, znamená to, že šablony nástrojů jsou k dispozici. Vyberte znaménko plus rozbalit seznam šablon, vyberte šablonu a zvolte **nový**.

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>Převod bitmap na prostředky panelu nástrojů

1. Otevřete existující prostředek rastrového obrázku v [Editor obrázků](../windows/image-editor-for-icons.md). Pokud ještě rastrového obrázku není v souboru .rc, klikněte pravým tlačítkem na soubor .rc a zvolte **Import**, přejděte na rastrový obrázek, kterou chcete přidat do souboru .rc a vyberte **otevřít**.

1. Přejděte do nabídky **Image** > **panelu nástrojů editoru**.

   **Nový prostředek panelu nástrojů** zobrazí se dialogové okno. Můžete změnit šířku a výšku obrázky ikon tak, aby odpovídaly rastrového obrázku. Obrázek panelu nástrojů se následně zobrazí **panelu nástrojů editoru**.

1. K dokončení převodu, změňte příkaz **ID** pomocí tlačítka [okno vlastností](/visualstudio/ide/reference/properties-window). Zadejte nový *ID* nebo vyberte **ID** z rozevíracího seznamu.

   > [!TIP]
   > **Vlastnosti** okno obsahuje tlačítko připínáčku v záhlaví a tento výběr povolí nebo zakáže **automaticky skrýt** okna. K cyklování skrze všechny vlastnosti tlačítka panelu nástrojů, aniž byste museli znovu otevřít windows jednotlivých vlastností, zapněte **automaticky skrýt** vypnout proto **vlastnosti** okno zůstane bez pohybu.

   Identifikátory příkazů tlačítka na nový panel nástrojů můžete také změnit pomocí [okno vlastností](/visualstudio/ide/reference/properties-window).

### <a name="to-manage-toolbar-buttons"></a>Ke správě tlačítka na panelu nástrojů

Vytvoření nového tlačítka panelu nástrojů:

1. V [zobrazení prostředků](../windows/resource-view-window.md) rozbalte složku prostředků (například *Project1.rc*).

1. Rozbalte **nástrojů** a pak zvolte položku panelu nástrojů pro úpravy, udělejte jednu z následujících akcí:

   - Přiřaďte ID prázdné tlačítko na pravém konci panelu nástrojů. Můžete tak učinit pomocí úpravy **ID** vlastnost [okno vlastností](/visualstudio/ide/reference/properties-window). Můžete například poskytnout stejný Identifikátor jako možnost nabídky tlačítka panelu nástrojů. V takovém případě použijte pole rozevíracího seznamu vyberte **ID** položky nabídky.

   - Vyberte tlačítko prázdné na pravém konci panelu nástrojů (v **panel nástrojů zobrazení** podokno) a začněte kreslení. Je přiřazen výchozí Identifikátor příkazu tlačítka (ID_BUTTON\<n >).

Můžete také zkopírovat a vložit obrázek do nového tlačítka panelu nástrojů.

Chcete-li přidat bitovou kopii na panelu nástrojů jako tlačítko:

1. V [zobrazení prostředků](../windows/resource-view-window.md), otevřete poklepáním panelu nástrojů.

1. Dále otevřete image, kterou chcete přidat na panel nástrojů.

   > [!NOTE]
   > Pokud obrázek otevřít v sadě Visual Studio, se otevře v **Image** editoru. Image můžete otevřít také v jiných aplikacích grafiky.

1. Z **upravit** nabídce zvolte **kopírování**.

1. Přepnout na panel nástrojů tak, že vyberete jeho karty v horní části okna zdroje.

1. Z **upravit** nabídce zvolte **vložit**.

   Obrázek se zobrazí na panelu nástrojů jako nového tlačítka.

Přesunutí tlačítka panelu nástrojů:

V **panel nástrojů zobrazení** podokně přetáhněte tlačítko, které chcete přesunout do nového umístění na panelu nástrojů.

Kopírování tlačítek z panelu nástrojů, podržte klávesu **Ctrl** klíč a **panel nástrojů zobrazení** podokně přetáhněte tlačítko buď nové místo na panelu nástrojů nebo do umístění na jiný panel nástrojů.

Odstranění tlačítka panelu nástrojů vyberte tlačítko panelu nástrojů a přetáhněte ho z panelu nástrojů.

Vložit nebo odebrání mezer mezi tlačítky na panelu nástrojů, buď přetáhněte je ze nebo vůči navzájem na panelu nástrojů.

|Akce|Krok|
|------|------|
|Vložit mezeru před tlačítko, které není mezeru|Přetáhněte tlačítko na pravé straně nebo dolů, dokud se překrývá na tlačítko Další informace o uprostřed.|
|Vložit mezeru před tlačítko, které následuje mezera a zajistit koncové mezery|Přetáhněte toto tlačítko, dokud pravé nebo dolní okraj je právě klepnou na tlačítko Další nebo právě překrývá.|
|Vložit mezeru před tlačítko, které následuje mezera a zavřete tento následující místo|Přetáhněte tlačítko na pravé straně nebo dolů, dokud se překrývá na tlačítko Další informace o uprostřed.|
|Chcete-li odebrat mezery mezi tlačítka na panelu nástrojů|Přetáhněte tlačítko na jedné straně místa směrem k tlačítku na druhé straně prostor se překrývá na tlačítko Další informace o urazili polovinu cesty.|

> [!NOTE]
> Pokud není místa vedle tlačítka, které jste přetažením směrem od a více než polovinu životnosti minulé vedle tlačítka, přetáhněte tlačítko **panelu nástrojů editoru** vloží mezeru na opačnou stranu tlačítka, které jste přetažení.

Chcete-li změnit vlastnosti tlačítka panelu nástrojů:

1. V projektu jazyka C++ vyberte tlačítko panelu nástrojů.

1. Zadejte nové ID v **ID** vlastnost [okno vlastností](/visualstudio/ide/reference/properties-window), nebo pomocí rozevíracího seznamu vyberte novou **ID**.

Vytvoření popisku tlačítka pro tlačítko toolbar:

1. Vyberte tlačítko panelu nástrojů.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window)v **výzvy** pole, přidejte popis tlačítka na stavový řádek a po něm, přidejte `\n` a název nástroje tip.

Například viz popis tlačítka pro **tisk** tlačítko **WordPad**:

1. Otevřít **WordPad**.

1. Najeďte myší **tisk** tlačítka panelu nástrojů a Všimněte si, že slovo `Print` je nyní plovoucí pod ukazatele myši.

1. Podívejte se na stavovém řádku v dolní části **WordPad** okno a Všimněte si, že nyní zobrazuje text `Prints the active document`.

`Print` je název tip nástroje a `Prints the active document` je popis tlačítka na stavový řádek.

Pokud chcete tento efekt použití **panelu nástrojů editoru**, nastavte **výzvy** vlastnost `Prints the active document\nPrint`.

## <a name="requirements"></a>Požadavky

Knihovny MFC nebo ATL

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)
<!--
[Menus and Other Resources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Toolbar Button Properties](../windows/toolbar-button-properties.md)<br/>-->
