---
title: Vytváření, přesunutí a úprava tlačítek panelu nástrojů (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
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
ms.assetid: d0f0c6c6-9d7e-42b5-a86a-7558127386e7
ms.openlocfilehash: 2a67123e444ad208eaae74a24b72288f2dbb3bdb
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742697"
---
# <a name="creating-moving-and-editing-toolbar-buttons-c"></a>Vytváření, přesunutí a úprava tlačítek panelu nástrojů (C++)

Můžete snadno vytvořit, přesunutí, kopírování a úprava tlačítek panelu nástrojů.

Ve výchozím nastavení je na pravém konci panelu nástrojů zobrazí tlačítko Nový nebo prázdný. Toto tlačítko můžete přesunout začnete upravovat. Při vytváření nového tlačítka další prázdné tlačítko vpravo se zobrazí upravená tlačítka. Při ukládání panelu nástrojů tlačítko prázdné se neuloží.

Vlastnosti tlačítka panelu nástrojů jsou:

|Vlastnost|Popis|
|--------------|-----------------|
|**ID**|Definuje ID pro tlačítko. Rozevírací seznam obsahuje běžné **ID** názvy.|
|**Šířka**|Nastavuje šířku tlačítka. doporučuje se 16 pixelů.|
|**Výška**|Nastaví výšku tlačítka. Výška tlačítka změní výšku všechna tlačítka na panelu nástrojů. doporučuje se 15 pixelů.|
|**Zeptat se**|Definuje zprávy zobrazí ve stavovém řádku. Přidání \n a název Přidá popis tlačítka na toto tlačítko panelu nástrojů. Další informace najdete v tématu [vytvoření popisu](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Šířka** a **výška** platí pro všechna tlačítka. Rastrový obrázek, který se používá k vytvoření panelu nástrojů má maximální šířku 2048. Takže pokud nastavíte šířku tlačítka na 512, můžete mít jenom čtyři tlačítka a nastavte šířku na 513 lze pouze máte tři tlačítka.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

Zobrazte následující akce:

## <a name="to-create-a-new-toolbar-button"></a>K vytvoření nového tlačítka panelu nástrojů

1. V [zobrazení prostředků](../windows/resource-view-window.md) rozbalte složku prostředků (například *Project1.rc*).

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. Rozbalte **nástrojů** a pak zvolte položku panelu nástrojů pro úpravy.

1. Přiřaďte ID prázdné tlačítko na pravém konci panelu nástrojů. Můžete tak učinit pomocí úpravy **ID** vlastnost [okno vlastností](/visualstudio/ide/reference/properties-window). Můžete například poskytnout stejný Identifikátor jako možnost nabídky tlačítka panelu nástrojů. V takovém případě použijte pole rozevíracího seznamu vyberte **ID** položky nabídky.

   -nebo-

   Vyberte tlačítko prázdné na pravém konci panelu nástrojů (v **panel nástrojů zobrazení** podokno) a začněte kreslení. Je přiřazen výchozí Identifikátor příkazu tlačítka (ID_BUTTON\<n >).

Můžete také zkopírovat a vložit obrázek do nového tlačítka panelu nástrojů.

## <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Chcete-li přidat bitovou kopii na panelu nástrojů jako tlačítko

1. V [zobrazení prostředků](../windows/resource-view-window.md), otevřete poklepáním panelu nástrojů.

1. Dále otevřete image, kterou chcete přidat na panel nástrojů.

   > [!NOTE]
   > Pokud obrázek otevřít v sadě Visual Studio, se otevře v **Image** editoru. Image můžete otevřít také v jiných aplikacích grafiky.

1. Z **upravit** nabídce zvolte **kopírování**.

1. Přepnout na panel nástrojů tak, že vyberete jeho karty v horní části okna zdroje.

1. Z **upravit** nabídce zvolte **vložit**.

   Obrázek se zobrazí na panelu nástrojů jako nového tlačítka.

## <a name="to-move-a-toolbar-button"></a>Přesunutí tlačítka panelu nástrojů

V **panel nástrojů zobrazení** podokně přetáhněte tlačítko, které chcete přesunout do nového umístění na panelu nástrojů.

## <a name="to-copy-buttons-from-a-toolbar"></a>Kopírování tlačítek z panelu nástrojů

1. Podržte stisknutou klávesu **Ctrl** klíč.

1. V **panel nástrojů zobrazení** podokně přetáhněte tlačítko buď nové místo na panelu nástrojů nebo do umístění na jiný panel nástrojů.

## <a name="to-delete-a-toolbar-button"></a>Odstranění tlačítka panelu nástrojů

Tlačítko panelu nástrojů vyberte a přetáhněte ho z panelu nástrojů.

## <a name="to-insert-or-remove-space-between-buttons-on-a-toolbar"></a>Vložit nebo odebrání mezer mezi tlačítky na panelu nástrojů

Obecně platí k vložení mezery mezi tlačítka, přetáhněte je od sebe na panelu nástrojů. Chcete-li odebrat místa, přetáhněte je směrem k sobě navzájem.

### <a name="to-insert-a-space-before-a-button-that-isnt-followed-by-a-space"></a>Vložit mezeru před tlačítko, které není mezeru

Přetáhněte tlačítko na pravé straně nebo dolů, dokud se překrývá na tlačítko Další informace o uprostřed.

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-to-keep-the-trailing-space"></a>Vložit mezeru před tlačítko, které následuje mezera a zajistit koncové mezery

Přetáhněte toto tlačítko, dokud pravé nebo dolní okraj je právě klepnou na tlačítko Další nebo právě překrývá.

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-close-up-that-following-space"></a>Vložit mezeru před tlačítko, které následuje mezera a zavřete tento následující místo

Přetáhněte tlačítko na pravé straně nebo dolů, dokud se překrývá na tlačítko Další informace o uprostřed.

### <a name="to-remove-a-space-between-buttons-on-a-toolbar"></a>Chcete-li odebrat mezery mezi tlačítka na panelu nástrojů

Přetáhněte tlačítko na jedné straně místa směrem k tlačítku na druhé straně prostor se překrývá na tlačítko Další informace o urazili polovinu cesty.

   Pokud není žádný prostor vedle tlačítka, které jste přetažením směrem od a více než polovinu životnosti minulé vedle tlačítka, přetáhněte tlačítko **nástrojů** editor také vloží mezeru na opačnou stranu tlačítka, které jste přetažení.

## <a name="to-change-the-properties-of-a-toolbar-button"></a>Chcete-li změnit vlastnosti tlačítka panelu nástrojů

1. V projektu jazyka C++ vyberte tlačítko panelu nástrojů.

1. Zadejte nové ID v **ID** vlastnost [okno vlastností](/visualstudio/ide/reference/properties-window), nebo pomocí rozevíracího seznamu vyberte novou **ID**.

## <a name="requirements"></a>Požadavky

Knihovny MFC nebo ATL

## <a name="see-also"></a>Viz také

[Editor panelu nástrojů](../windows/toolbar-editor.md)
