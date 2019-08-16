---
title: Editor panelů nástrojůC++()
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
ms.openlocfilehash: 72c42a06da8276d118c6c204f838ed4b31d142b9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514689"
---
# <a name="toolbar-editor-c"></a>Editor panelů nástrojůC++()

**Editor panelu nástrojů** umožňuje vytvořit prostředky panelu nástrojů a převést rastrové obrázky na prostředky panelu nástrojů. **Editor panelu nástrojů** používá grafický displej k zobrazení panelu nástrojů a tlačítek, která se přesně podobají tomu, jak budou vypadat v dokončené aplikaci.

Okno **editoru panelu nástrojů** zobrazuje dvě zobrazení obrázku tlačítka, stejně jako okno **editoru obrázků** . Dělicí čára odděluje dvě podokna a přetažením rozděleného pruhu můžete změnit relativní velikosti podoken. Aktivní podokno zobrazuje ohraničení výběru a nad dvěma zobrazeními obrázku je panel nástrojů pro předmět.

![Toolbar Editor](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**Editor panelu nástrojů**

**Editor panelu nástrojů** je podobný **editoru obrázků** ve funkcích a položky nabídky, grafické nástroje a rastrové mřížky mezi těmito dvěma položkami jsou stejné. V nabídce **obrázku** je příkaz nabídky pro přepínání mezi **editorem nástrojů** a **editorem obrázků**. Další informace o použití panelu nástrojů **Grafika** , palety **barev** nebo nabídky **Obrázek** naleznete v tématu [Editor obrázků](../windows/image-editor-for-icons.md).

Můžete vytvořit nový panel nástrojů v C++ projektu převodem rastrového obrázku. Obrázek z rastrového obrázku se převede na obrázky tlačítek panelu nástrojů. Rastrový obrázek obsahuje několik obrázků tlačítek v jedné bitmapě s jedním obrázkem pro každé tlačítko. Obrázky mohou mít libovolnou velikost, protože výchozí hodnota je 16 pixelů a výška obrázku. Velikost obrázků tlačítek můžete zadat v dialogovém okně **nový prostředek panelu nástrojů** , když v **editoru obrázků**zvolíte **Editor panelu nástrojů** v nabídce **Obrázek** .

Dialogové okno **nový prostředek panelu nástrojů** umožňuje zadat šířku a výšku přidaných tlačítek do prostředku panelu nástrojů v C++ projektu. Výchozí hodnota je 16 × 15 pixelů.

Rastrový obrázek, který se používá k vytvoření panelu nástrojů, má maximální šířku 2048, takže pokud nastavíte **šířku tlačítka** na *512*, můžete mít jenom čtyři tlačítka. Pokud nastavíte možnost šířka na *513*, můžete mít pouze tři tlačítka.

Dialogové okno **nový prostředek panelu nástrojů** má následující vlastnosti:

|Vlastnost|Popis|
|---|---------------|
|**Šířka tlačítka**|Poskytuje prostor pro zadání šířky tlačítek panelu nástrojů, které převádíte z rastrového prostředku na prostředek panelu nástrojů.|
|**Výška tlačítka**|Poskytuje místo, kde můžete zadat výšku tlačítek panelu nástrojů, která převádíte z rastrového prostředku na prostředek panelu nástrojů.|

> [!NOTE]
> Obrázky jsou oříznuty na zadanou šířku a výšku a barvy jsou upraveny tak, aby používaly standardní barvy panelů nástrojů (16 barev).

Ve výchozím nastavení se na pravé straně panelu nástrojů zobrazí nové nebo prázdné tlačítko. Toto tlačítko můžete přesunout před úpravou. Když vytvoříte nové tlačítko, zobrazí se na pravé straně upravovaného tlačítka jiné prázdné tlačítko. Po uložení panelu nástrojů se prázdné tlačítko neuloží.

Tlačítko panelu nástrojů má následující vlastnosti:

|Vlastnost|Popis|
|--------------|-----------------|
|**ID**|Definuje ID pro tlačítko. V rozevíracím seznamu jsou uvedeny běžné názvy **ID** .|
|**Délk**|Nastaví šířku tlačítka. doporučuje se 16 pixelů.|
|**Výška**|Nastaví výšku tlačítka. Výška jednoho tlačítka změní výšku všech tlačítek na panelu nástrojů. doporučuje se 15 pixelů.|
|**Zeptat se**|Definuje zprávu zobrazenou na stavovém řádku. Přidáním *\n* a názvu přidáte k tomuto tlačítku na panelu nástrojů **Popis** . Další informace najdete v tématu [Vytvoření popisu tlačítka](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Šířka** a **Výška** se aplikují na všechna tlačítka. Rastrový obrázek, který se používá k vytvoření panelu nástrojů, má maximální šířku 2048, takže pokud nastavíte šířku tlačítka na *512*, můžete mít jenom čtyři tlačítka a pokud nastavíte šířku na *513*, můžete mít jenom tři tlačítka.

## <a name="how-to"></a>Postupy

**Editor panelu nástrojů** vám umožní:

### <a name="to-create-new-toolbars"></a>Vytvoření nových panelů nástrojů

1. V **prostředky**klikněte pravým tlačítkem na soubor *. RC* a vyberte **Přidat prostředek**. Máte-li v souboru *. RC* existující panel nástrojů, můžete kliknout pravým tlačítkem myši na složku **panelu nástrojů** a vybrat možnost **Vložit panel nástrojů**.

1. V dialogovém okně **Přidat prostředek** vyberte v seznamu **typ prostředku** položku **panel nástrojů** a klikněte na tlačítko **Nový**.

   Pokud se vedle typu prostředku **+** **panelu nástrojů** zobrazí znaménko plus (), znamená to, že jsou k dispozici šablony panelu nástrojů. Vyberte znaménko plus a rozbalte seznam šablon, vyberte šablonu a zvolte **Nový**.

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>Převod rastrových obrázků na prostředky panelu nástrojů

1. Otevřete existující rastrový prostředek v [editoru obrázků](../windows/image-editor-for-icons.md). Pokud bitmapa ještě není ve vašem souboru *. RC* , klikněte pravým tlačítkem myši na soubor *. RC* a zvolte **importovat**, potom přejděte k rastrovému obrázku, který chcete přidat do souboru *. RC* , a vyberte **otevřít**.

1. Přejít k**editoru panelu nástrojů** **Obrázek** > nabídky

   Zobrazí se dialogové okno **nový prostředek panelu nástrojů** . Šířku a výšku obrázků ikon můžete změnit tak, aby odpovídaly rastrovému obrázku. Obrázek panelu nástrojů se pak zobrazí v **editoru panelu nástrojů**.

1. Chcete-li dokončit převod, změňte **ID** příkazu tlačítka pomocí [okno Vlastnosti](/visualstudio/ide/reference/properties-window). Zadejte nové *ID* nebo v rozevíracím seznamu vyberte **ID** .

   > [!TIP]
   > Okno **vlastnosti** obsahuje v záhlaví tlačítko připínáček a tato možnost povoluje nebo zakazuje **automatické skrývání** okna. Chcete-li procházet všechny vlastnosti tlačítka panelu nástrojů bez nutnosti znovu otevřít jednotlivá okna vlastností, vypněte **automatické skrývání** , aby okno **vlastnosti** zůstalo nefunkční.

   Identifikátory příkazů pro tlačítka na novém panelu nástrojů můžete změnit také pomocí [okno Vlastnosti](/visualstudio/ide/reference/properties-window).

### <a name="to-manage-toolbar-buttons"></a>Správa tlačítek panelu nástrojů

#### <a name="to-create-a-new-toolbar-button"></a>Vytvoření nového tlačítka panelu nástrojů

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources) rozbalte složku prostředků (například *Project1. RC*).

1. Rozbalte složku **panel nástrojů** a vyberte panel nástrojů, který chcete upravit, a proveďte jednu z následujících akcí:

   - Přiřaďte ID k prázdnému tlačítku na pravé straně panelu nástrojů. Můžete to provést úpravou vlastnosti **ID** v [okně Vlastnosti](/visualstudio/ide/reference/properties-window). Například můžete chtít, aby tlačítko panelu nástrojů mělo stejné ID jako možnost nabídky. V takovém případě můžete pomocí rozevíracího seznamu vybrat **ID** možnosti nabídky.

   - V podokně **zobrazení panelu nástrojů** vyberte prázdné tlačítko na pravé straně panelu nástrojů a začněte kreslit. ID příkazu výchozího tlačítka je přiřazeno (ID_BUTTON\<n >).

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Přidání obrázku na panel nástrojů jako tlačítko

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)otevřete panel nástrojů tak, že na něj dvakrát kliknete.

1. Pak otevřete obrázek, který chcete přidat na panel nástrojů.

   > [!NOTE]
   > Otevřete-li obrázek v aplikaci Visual Studio, otevře se v **editoru obrázků**. Můžete také otevřít obrázek v jiných grafických programech.

1. Přejděte do nabídky **Upravit** > **kopii**.

1. Přepněte na panel nástrojů výběrem jeho karty v horní části okna zdroje.

1. Přejděte do nabídky **Upravit** > **vložení**.

   Obrázek se zobrazí na panelu nástrojů jako nové tlačítko.

#### <a name="to-move-a-toolbar-button"></a>Přesunutí tlačítka panelu nástrojů

V podokně **zobrazení panelu nástrojů** přetáhněte tlačítko, které chcete přesunout do nového umístění na panelu nástrojů.

- Chcete-li kopírovat tlačítka z panelu nástrojů, podržte stisknutou klávesu **CTRL** a v podokně **zobrazení panelu nástrojů** přetáhněte tlačítko na jeho nové umístění na panelu nástrojů nebo na jiné místo na jiném panelu nástrojů.

- Chcete-li odstranit tlačítko panelu nástrojů, vyberte tlačítko panelu nástrojů a přetáhněte jej mimo panel nástrojů.

- Chcete-li vložit nebo odebrat mezeru mezi tlačítky na panelu nástrojů, přetáhněte je od sebe na panelu nástrojů nebo směrem ven.

|Akce|Krok|
|------|------|
|Vložení mezery před tlačítko, které není následováno mezerou|Přetáhněte tlačítko doprava nebo dolů, dokud se nepřekryje s tlačítkem Další v polovině.|
|Vložení mezery před tlačítko, na které následuje mezera a kde má být zachováno koncové místo|Přetáhněte tlačítko, dokud není pravé nebo dolní hrana pouze dotekem tlačítka Další nebo pouze překrytí.|
|Vložit mezeru před tlačítko, které následuje mezera, a zavřít následující místo|Přetáhněte tlačítko doprava nebo dolů, dokud se nepřekryje s tlačítkem Další v polovině.|
|Odebrání mezery mezi tlačítky na panelu nástrojů|Přetáhněte tlačítko na jednu stranu prostoru směrem k tlačítku na druhé straně prostoru, aby se překrývalo tlačítko Další o polovině.|

> [!NOTE]
> Pokud není žádné místo na straně tlačítka, na které přetahujete, a přetáhnete tlačítko více než uprostřed po sousedním tlačítku, **Editor panelu nástrojů** vloží mezeru na opačné straně tlačítka, které přetahujete.

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>Změna vlastností tlačítka panelu nástrojů

1. V C++ projektu vyberte tlačítko panelu nástrojů.

1. Zadejte nové ID do vlastnosti **ID** v [okně Vlastnosti](/visualstudio/ide/reference/properties-window)nebo použijte rozevírací seznam a vyberte nové **ID**.

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>Vytvoření tipu nástroje pro tlačítko panelu nástrojů

1. Vyberte tlačítko panelu nástrojů.

1. V [okně Vlastnosti](/visualstudio/ide/reference/properties-window)zadejte do pole **příkazového řádku** popis tlačítka pro stavový řádek a za zprávu přidejte a zadejte `\n` název popisu nástroje.

Například, chcete-li zobrazit popis tlačítka pro tlačítko **Tisk** v **programu WordPad**:

1. Otevřete **WordPad**.

1. Najeďte ukazatelem myši na tlačítko tiskového panelu nástrojů a Všimněte `Print` si, že je nyní plovoucí v rámci ukazatele myši.

1. Podívejte se na stavový řádek v dolní části okna **programu WordPad** a Všimněte si, že nyní zobrazuje text `Prints the active document`.

`Print`je název tipu nástroje a `Prints the active document` je popisem tlačítka pro stavový řádek.

Chcete-li tento efekt použít v **editoru panelu nástrojů**, nastavte vlastnost **prompt** na `Prints the active document\nPrint`hodnotu.

## <a name="requirements"></a>Požadavky

MFC nebo ATL

## <a name="see-also"></a>Viz také:

[](../windows/resource-editors.md)
Nabídky editorů prostředků[a další prostředky](/windows/win32/menurc/resources)<br/>
[Vlastnosti tlačítka panelu nástrojů](../windows/toolbar-button-properties.md)<br/>
