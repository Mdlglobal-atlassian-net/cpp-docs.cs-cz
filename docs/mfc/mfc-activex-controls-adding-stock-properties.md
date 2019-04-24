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
ms.openlocfilehash: 940f61c9ce6ccb57843333582455e61c1f7ac73b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225340"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC – ovládací prvky ActiveX: Přidání uložených vlastností

Uložené vlastnosti liší od vlastních vlastností, že je již implementováno třídou `COleControl`. `COleControl` obsahuje předdefinované členské funkce, které podporují společné vlastnosti ovládacího prvku. Některé běžné vlastnosti zahrnout záhlaví ovládacího prvku a barvy popředí a pozadí. Informace o dalších uložených vlastností naleznete v tématu [akcie vlastnosti nepodporuje Průvodce přidáním vlastnosti](#_core_stock_properties_supported_by_classwizard) dále v tomto článku. Položky mapy odbavení populace, které vlastnosti jsou vždy předchází DISP_STOCKPROP.

Tento článek popisuje postup přidání uložených vlastností (v tomto případě titulků) do ovládacího prvku ActiveX pomocí Průvodce přidáním vlastnosti a vysvětluje výsledné změny kódu. Mezi témata patří:

- [Pomocí Průvodce přidáním vlastnosti pro přidání uložených vlastností](#_core_using_classwizard_to_add_a_stock_property)

- [Přidat Průvodce vlastností změny provedené u uložených vlastností](#_core_classwizard_changes_for_stock_properties)

- [Uložené vlastnosti, které jsou podporované pomocí Průvodce přidáním vlastnosti](#_core_stock_properties_supported_by_classwizard)

- [Uložené vlastnosti a oznámení](#_core_stock_properties_and_notification)

- [Vlastnosti barvy](#_core_color_properties)

    > [!NOTE]
    >  Vlastní ovládací prvky jazyka Visual Basic mají obvykle vlastnosti, například horní, vlevo, šířka, výška, zarovnání, značky, název, TabIndex, TabStop a nadřazené. ActiveX – kontejnery ovládacích prvků, ale zodpovídají za implementaci těchto vlastností ovládacího prvku, a proto by neměl tyto vlastnosti podporují ovládací prvky ActiveX.

##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> Použití Průvodce přidáním vlastnosti pro přidání uložených vlastností

Přidání uložených vlastností vyžaduje méně kódu než přidání vlastních vlastností, protože podporují pro vlastnost je automaticky zpracována `COleControl`. Následující postup ukazuje přidání akcie Vlastnosti titulku rozšiřovatelnou platformu pro ovládací prvek ActiveX a je také možné přidat další základní vlastnosti. Nahraďte názvem vybrané uložených vlastností pro popisek.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Přidání uložených vlastností titulek, pomocí Průvodce přidáním vlastnosti

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klikněte pravým tlačítkem na uzel rozhraní pro ovládací prvek (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat vlastnost**.

   Tím se otevře [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md).

1. V **název vlastnosti** klikněte **titulek**.

1. Klikněte na tlačítko **Dokončit**.

##  <a name="_core_classwizard_changes_for_stock_properties"></a> Přidat Průvodce změny vlastností pro uložené vlastnosti

Protože `COleControl` podporuje uložené vlastnosti, Průvodce přidáním vlastnosti deklarace třídy nijak nemění; vlastnost přidá do mapy odeslání. Průvodce přidáním vlastnosti přidá následující řádek do mapy odbavení ovládacího prvku, který je umístěn v implementaci (. Soubor CPP):

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

Následující řádek je přidán do rozhraní popis ovládacího prvku (. Soubor IDL):

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Tento řádek přiřadí vlastnosti titulku konkrétní ID. Všimněte si, že vlastnost je umožňujících vazbu a bude požadovat oprávnění z databáze před změnou hodnoty.

To zpřístupňuje vlastnost Caption uživatelům ovládacího prvku. Pokud chcete použít hodnotu uložených vlastností, přístup k členské proměnné nebo členská funkce `COleControl` základní třídy. Další informace o těchto členské proměnné a členské funkce najdete v další části, Stock vlastnosti nepodporuje Průvodce přidáním vlastnosti.

##  <a name="_core_stock_properties_supported_by_classwizard"></a> Uložené podporovaných vlastností Průvodce přidáním vlastnosti

`COleControl` Třída poskytuje devět uložených vlastností. Můžete přidat vlastnosti, které chcete pomocí Průvodce přidáním vlastnosti.

|Vlastnost|Zápis do mapy odbavení|Jak získat přístup k hodnotě|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE( )|Hodnota, které jsou dostupné jako `m_sAppearance`.|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR( )|Hodnota přístupná pomocí volání `GetBackColor`.|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE( )|Hodnota, které jsou dostupné jako `m_sBorderStyle`.|
|`Caption`|DISP_STOCKPROP_CAPTION( )|Hodnota přístupná pomocí volání `InternalGetText`.|
|`Enabled`|DISP_STOCKPROP_ENABLED( )|Hodnota, které jsou dostupné jako `m_bEnabled`.|
|`Font`|DISP_STOCKPROP_FONT( )|Přečtěte si článek [knihovny MFC – ovládací prvky ActiveX: Použití písem](../mfc/mfc-activex-controls-using-fonts.md) za využití.|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR( )|Hodnota přístupná pomocí volání `GetForeColor`.|
|`hWnd`|DISP_STOCKPROP_HWND( )|Hodnota, které jsou dostupné jako `m_hWnd`.|
|`Text`|DISP_STOCKPROP_TEXT( )|Hodnota přístupná pomocí volání `InternalGetText`. Tato vlastnost je stejný jako `Caption`, s výjimkou názvu vlastnosti.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|Hodnota, které jsou dostupné jako `m_lReadyState` nebo `GetReadyState`|

##  <a name="_core_stock_properties_and_notification"></a> Uložené vlastnosti a oznámení

Většina uložených vlastností má funkce oznámení, které mohou být přepsána nastaveními. Například, vždy, když `BackColor` změněna vlastnost `OnBackColorChanged` je volána funkce (členské funkce třídy ovládacího prvku). Výchozí implementace (v `COleControl`) volání `InvalidateControl`. Tato funkce přepište, pokud chcete provést další akce v reakci na této situaci.

##  <a name="_core_color_properties"></a> Vlastnosti barvy

Můžete použít stock `ForeColor` a `BackColor` vlastnosti nebo vlastní vlastnosti vlastních barev, při vykreslování ovládacího prvku. Chcete-li použít vlastnost color, zavolejte [COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) členskou funkci. Parametry této funkce se hodnota vlastnosti barvy a popisovač volitelné palety. Vrácená hodnota je **COLORREF** hodnotu, která může být předán GDI funkcí, jako například `SetTextColor` a `CreateSolidBrush`.

Barevných stock `ForeColor` a `BackColor` vlastnosti jsou přístupná pomocí volání buď `GetForeColor` nebo `GetBackColor` fungovat v uvedeném pořadí.

Následující příklad ukazuje použití těchto vlastností barev dvou při vykreslování ovládacího prvku. Inicializuje dočasný **COLORREF** proměnné a `CBrush` objektu s voláními `TranslateColor`: jednu `ForeColor` vlastností a jiných použití `BackColor` vlastnost. Dočasný `CBrush` objekt se pak použije k vykreslení ovládacího prvku obdélníku a barvu textu se nastavuje pomocí `ForeColor` vlastnost.

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Vlastnosti](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl – třída](../mfc/reference/colecontrol-class.md)
