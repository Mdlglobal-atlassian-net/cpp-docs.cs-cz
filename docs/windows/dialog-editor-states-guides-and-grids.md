---
title: Stavy editoru dialogových oken (vodítka a mřížky) (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], guides and margins
- guides, clearing
- guides
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
- guides, disabling snapping
- controls [C++], snap to guides/grid
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
- grid spacing
- guides, settings
- layout grid in Dialog Editor
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
ms.assetid: dbacf9ef-e8b0-4125-a7ce-84911c482e98
ms.openlocfilehash: 52fc19d8a39680c16692177e2758fba78afc7d3a
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484991"
---
# <a name="dialog-editor-states-guides-and-grids-c"></a>Stavy editoru dialogových oken (vodítka a mřížky) (C++)

Můžete uspořádat ovládací prvky v dialogových oknech s **dialogové okno** editoru v jednom ze tří různých stavů:

- Pomocí vodítek a okrajů na (výchozí nastavení)

- Pomocí mřížky rozložení v

- Bez jakékoli funkce přichycení nebo zarovnání

[Nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) obsahuje tlačítka, která řídí stav. Chcete-li změnit stav, klikněte na příslušnou položku. Můžete také změnit stavy pomocí **nastavení vodítek** příkaz **formátu** nabídky.

**Nastavení vodítek** dialogové okno má následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Vodítka rozložení**|Zobrazuje nastavení vodítek rozložení.|
|**Žádné**|Skryje nástroje rozložení.|
|**Pravítka a vodítka**|Pokud povolená, přidá do nástroje rozložení; pravítka příručky je možné použít v pravítka. Výchozí příručky jsou okraje, které je možné přesunout přetažením. Vyberte pravítka umístit průvodce. Ovládací prvky "přichytávat" k Průvodci při přesunutí ovládacích prvků nad nebo vedle sebe. Ovládací prvky se také přesunout pomocí průvodce po jste k němu připojená. Když ovládací prvek je připojen k vodítko na každé straně a přesunout vodítko, změní velikost ovládacího prvku.|
|**Mřížka**|Vytvoří rozložení mřížky. Nové ovládací prvky budou automaticky zarovnat k mřížce.|
|**Rozteč mřížky**|Nastavení pro rozteč mřížky se zobrazí v poli jednotky dialogu (dlu).|
|**Width: Dlu**|Nastavuje šířku mřížky rozložení v dlu. Vodorovné DLU je průměrná délka pole písmo dialogového okna dělený čtyři.|
|**Height: Dlu**|Nastaví výšku mřížky rozložení v dlu. Svislé DLU je průměrná výška pole písmo dialogového okna dělený osmidílné série.|

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="create-and-set-guides-and-margins"></a>Vytvoření a nastavení vodítek a okrajů

Ať už přesouváte ovládací prvky, přidání ovládacích prvků nebo změna uspořádání aktuální rozložení, příručky pomáhají Zarovnat ovládací prvky přesně v rámci dialogového okna. Průvodce se zobrazí jako modré čáry s koncovými body v dialogovém okně zobrazí v editoru a odpovídající šipky v pravítka v horní části a sledovat levému okraji **dialogové okno** editoru.

Při vytváření dialogového okna, jsou k dispozici čtyři okraje. Okraje jsou upravené vodítka, povolí jako modré čáry s koncovými body.

### <a name="to-create-a-guide"></a>Chcete-li vytvořit vodítko

V rámci pravítku klikněte po vytvoření průvodce. (Jedním kliknutím vytvoří nový průvodce; spuštění dvojitým kliknutím **nastavení vodítek** dialogovému oknu, ve kterém můžete zadat nastavení vodítek.)

### <a name="to-set-a-guide"></a>Chcete-li nastavit vodítko

V dialogovém okně klikněte na tlačítko průvodce a přetáhněte ji na jiné místo. (Můžete také klikněte na šipku v pravítku, chcete-li přetáhněte průvodci přidružené.)

Souřadnice průvodce se zobrazí ve stavovém řádku v dolní části okna a pravítka. Přesunutí ukazatele myši na šipku v pravítku, chcete-li zobrazit přesné umístění v průvodci.

### <a name="to-delete-a-guide"></a>Chcete-li odstranit Průvodce

Přetáhněte z dialogových oken v průvodci.

\- nebo –

Přetáhněte šipku odpovídající vypnout pravítko.

### <a name="to-move-margins"></a>Chcete-li přesunout okraje

Přetáhněte na okraji na nové místo.

Chcete-li okraj zmizí, přesune na okraji nulové pozice. Převést zpět na okraji, umístěte ukazatel myši na okraj nulové pozice a přesuňte do umístění na okraj.

## <a name="align-controls-on-a-guide"></a>Zarovnání ovládacích prvků podle vodítka

Úchyty pro změnu velikosti ovládacích prvků Přichytit k vodítkům při přesunutí ovládacích prvků a příručky Přichytit k ovládací prvky, pokud neexistují žádná opatření dříve přichycená k průvodci. Když průvodce se přesune, ovládací prvky, které jsou přichycená k němu také přesunout. Ovládací prvky přichycená k více než jeden Průvodce se mění velikost, pokud jeden z příručky přesunuta.

Značky v pravítka, která určují mezery v průvodci a ovládací prvky jsou definovány jednotky dialogu (dlu). DLU vychází z velikosti pole písmo dialogového okna, obvykle 8 bodu MS Shell Dlg. Vodorovné DLU je průměrná délka pole písmo dialogového okna dělený čtyři. Svislé DLU je průměrná výška písmo dělený osmidílné série.

### <a name="to-size-a-group-of-controls-with-guides"></a>Chcete-li velikost skupiny ovládacích prvků podle vodítka

1. Přichytit k vodítko straně ovládacího prvku (nebo ovládací prvky).

1. Přetáhněte vodítko na druhé straně ovládacího prvku (nebo ovládací prvky).

   V případě potřeby s více ovládacích prvků, velikost každého se přichytil k druhé průvodce.

1. Přesuňte buď Průvodce pro nastavení velikosti ovládacího prvku (nebo ovládací prvky).

### <a name="to-change-the-intervals-of-the-tick-marks"></a>Chcete-li změnit intervalech osové značky

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

1. V **nastavení vodítek** v dialogu **rozteč mřížky** v dlu zadejte novou šířku a výšku.

## <a name="disable-guides"></a>Zakázání vodítek

Speciální klávesy ve spojení s myši můžete zakázat přichycení efekt vodítka. Použití **Alt** klíč zakáže přichycení efekty v průvodci vybrali. Přesunutí průvodce s **Shift** klíč zabraňuje přesunutí s příručkou Přichycený ovládací prvek.

### <a name="to-disable-the-snapping-effect-of-the-guides"></a>Chcete-li zakázat přichycení efekt vodítka

Přetáhněte ovládací prvek při podržení **Alt** klíč.

### <a name="to-move-guides-without-moving-the-snapped-controls"></a>Chcete-li přesunout vodítka bez přesouvání Přichycený ovládací prvky

Přetáhněte vodítko při podržení **Shift** klíč.

### <a name="to-turn-off-the-guides"></a>Chcete-li vypnout vodítka

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

1. V **nastavení vodítek** dialogovém okně **vodítka rozložení**vyberte **žádný**.

   > [!NOTE]
   > Můžete také dvakrát kliknout na panelu pravítko pro přístup k **nastavení vodítek** dialogové okno.

\- nebo –

Na **formátu** nabídce vyberte možnost **průvodce přepínací tlačítko**.

## <a name="modify-the-layout-grid"></a>Změna mřížky rozložení

Při uvádění nebo uspořádání ovládacích prvků v dialogovém okně, můžete pro přesnější umístění rozložení mřížky. Po zapnutí mřížky "se přichytil k" tečkované čáry mřížky jakoby zmagnetizovat zobrazí ovládací prvky. Můžete zapnout a vypnout tuto funkci "přichycení k mřížce" a změnit velikost buňky mřížky rozložení.

### <a name="to-turn-the-layout-grid-on-or-off"></a>K zapnutí nebo vypnutí mřížky rozložení

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

1. V **nastavení vodítek** dialogové okno, zaškrtněte nebo zrušte **mřížky** tlačítko.

   Můžete řídit mřížky v jednotlivých **dialogové okno** oken editoru pomocí **Přepnout mřížku** tlačítko [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

### <a name="to-change-the-size-of-the-layout-grid"></a>Chcete-li změnit velikost rozložení mřížky

1. Z **formátu** nabídce zvolte **nastavení vodítek**.

1. V **nastavení vodítek** dialogového okna zadejte výšku a šířku v dlu buňky v mřížce. Minimální výšku nebo šířku je 4 dlu. Další informace o dlu najdete v tématu [uspořádání ovládacích prvků v dialogových oknech](../windows/arrangement-of-controls-on-dialog-boxes.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky (MFC)](../mfc/controls-mfc.md)<br/>
