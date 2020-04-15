---
title: 'MFC – ovládací prvky ActiveX: Přidání uložených vlastností'
ms.date: 11/04/2016
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
ms.openlocfilehash: 16bdfddf0c028bc6a312767844b38c58c942d56e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364664"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC – ovládací prvky ActiveX: Přidání uložených vlastností

Vlastnosti zásob se liší od vlastních vlastností v tom, že jsou již implementovány třídou `COleControl`. `COleControl`obsahuje předdefinované členské funkce, které podporují společné vlastnosti ovládacího prvku. Některé běžné vlastnosti zahrnují titulek ovládacího prvku a barvy popředí a pozadí. Informace o dalších vlastnostech zásob naleznete v [tématu Vlastnosti skladu podporované Průvodcem přidáním vlastností](#_core_stock_properties_supported_by_classwizard) dále v tomto článku. Položky mapy odeslání pro vlastnosti zásob jsou vždy předponou DISP_STOCKPROP.

Tento článek popisuje, jak přidat vlastnost stock (v tomto případě Titulek) do ovládacího prvku ActiveX pomocí Průvodce přidáním vlastností a vysvětluje výsledné změny kódu. Témata:

- [Přidání vlastnosti akcie pomocí Průvodce přidáním vlastností](#_core_using_classwizard_to_add_a_stock_property)

- [Přidat změny Průvodce vlastnostmi pro vlastnosti zásob](#_core_classwizard_changes_for_stock_properties)

- [Vlastnosti zásob podporované Průvodcem přidáním vlastností](#_core_stock_properties_supported_by_classwizard)

- [Skladové nemovitosti a oznámení](#_core_stock_properties_and_notification)

- [Vlastnosti barev](#_core_color_properties)

    > [!NOTE]
    >  Vlastní ovládací prvky jazyka Visual Basic mají obvykle vlastnosti jako Horní, Vlevo, Šířka, Výška, Zarovnat, Tag, Název, TabIndex, TabStop a Parent. Kontejnery ovládacího prvku ActiveX jsou však zodpovědné za implementaci těchto vlastností ovládacího prvku, a proto ovládací prvky ActiveX by tyto vlastnosti neměly podporovat.

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a>Přidání vlastnosti pomocí Průvodce přidáním vlastností

Přidání vlastností zásob vyžaduje méně kódu než přidání vlastních `COleControl`vlastností, protože podpora vlastnosti je zpracována automaticky . Následující postup ukazuje přidání vlastnosti Caption na skladě do řídicího rámce ActiveX a lze ji také použít k přidání dalších vlastností zásob. Nahraďte název vybrané vlastnosti akcií titulek.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Přidání vlastnosti Titulek na skladě pomocí Průvodce přidáním vlastností

1. Načtěte projekt ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klepnutím pravým tlačítkem myši na uzel rozhraní ovládacího prvku (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat vlastnost**.

   Otevře se [Průvodce přidáním vlastností](../ide/names-add-property-wizard.md).

1. V poli **Název vlastnosti** klikněte na **Titulek**.

1. Klikněte na **Finish** (Dokončit).

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a>Přidat změny Průvodce vlastnostmi pro vlastnosti na skladě

Protože `COleControl` podporuje vlastnosti zásob, Průvodce přidáním vlastnosti žádným způsobem nezmění deklaraci třídy. přidá vlastnost do mapy odeslání. Průvodce přidáním vlastnosti přidá následující řádek do mapy odeslání ovládacího prvku, který se nachází v implementaci (. CPP) soubor:

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

Následující řádek je přidán do popisu rozhraní ovládacího prvku (. IDL) soubor:

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Tento řádek přiřadí vlastnosti Caption určité ID. Všimněte si, že vlastnost je vatou a bude požadovat oprávnění z databáze před úpravou hodnoty.

Tím zpřístupníte vlastnost Caption uživatelům ovládacího prvku. Chcete-li použít hodnotu vlastnosti stock, získejte `COleControl` přístup k členské proměnné nebo členské funkci základní třídy. Další informace o těchto členských proměnných a členských funkcích naleznete v další části Vlastnosti na skladě podporované Průvodcem přidáním vlastností.

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a>Vlastnosti akcií podporované Průvodcem přidáním vlastností

Třída `COleControl` poskytuje devět vlastností zásob. Požadované vlastnosti můžete přidat pomocí Průvodce přidáním vlastností.

|Vlastnost|Položka mapy odeslání|Jak získat přístup k hodnotě|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE( )|Hodnota přístupná jako `m_sAppearance`.|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR( )|Hodnota přístupná `GetBackColor`voláním .|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE( )|Hodnota přístupná jako `m_sBorderStyle`.|
|`Caption`|DISP_STOCKPROP_CAPTION( )|Hodnota přístupná `InternalGetText`voláním .|
|`Enabled`|DISP_STOCKPROP_ENABLED( )|Hodnota přístupná jako `m_bEnabled`.|
|`Font`|DISP_STOCKPROP_FONT( )|Viz článek [Ovládací prvky ActiveX knihovny MFC: Použití písem](../mfc/mfc-activex-controls-using-fonts.md) pro použití.|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR( )|Hodnota přístupná `GetForeColor`voláním .|
|`hWnd`|DISP_STOCKPROP_HWND( )|Hodnota přístupná jako `m_hWnd`.|
|`Text`|DISP_STOCKPROP_TEXT( )|Hodnota přístupná `InternalGetText`voláním . Tato vlastnost je `Caption`stejná jako , s výjimkou názvu vlastnosti.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|Hodnota přístupná jako `m_lReadyState` nebo`GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a>Vlastnosti a oznámení o zásobách

Většina vlastností zásob má funkce oznámení, které lze přepsat. Například při `BackColor` každé změně vlastnosti je volána `OnBackColorChanged` funkce (členská funkce třídy ovládacího prvku). Výchozí implementace (v `COleControl` `InvalidateControl`) volání . Přepsat tuto funkci, pokud chcete provést další akce v reakci na tuto situaci.

## <a name="color-properties"></a><a name="_core_color_properties"></a>Vlastnosti barev

Při malování ovládacího `BackColor` prvku můžete použít skladové a `ForeColor` vlastnosti nebo vlastní vlastnosti barev. Chcete-li použít vlastnost color, zavolejte členskou funkci [COleControl::TranslateColor.](../mfc/reference/colecontrol-class.md#translatecolor) Parametry této funkce jsou hodnota vlastnosti color a volitelného popisovače palety. Vrácená hodnota je hodnota **COLORREF,** která může být předána funkcím GDI, například `SetTextColor` a `CreateSolidBrush`.

Hodnoty barev pro `ForeColor` základní `BackColor` a vlastnosti jsou `GetForeColor` přístupné `GetBackColor` voláním funkce nebo funkce.

Následující příklad ukazuje použití těchto dvou vlastností barev při malování ovládacího prvku. Inicializuje dočasnou proměnnou **COLORREF** a `CBrush` `TranslateColor`objekt s `ForeColor` voláním : jeden `BackColor` pomocí vlastnosti a druhý pomocí vlastnosti. Dočasný `CBrush` objekt se pak používá k malování obdélníku ovládacího prvku `ForeColor` a barva textu je nastavena pomocí vlastnosti.

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Vlastnosti](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Třída COleControl](../mfc/reference/colecontrol-class.md)
