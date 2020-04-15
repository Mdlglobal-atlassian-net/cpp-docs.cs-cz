---
title: 'MFC – ovládací prvky ActiveX: Stránky vlastností'
ms.date: 11/19/2018
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
ms.openlocfilehash: c31d13e03483f8632f17a526da75ebe8e21bccbf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364571"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC – ovládací prvky ActiveX: Stránky vlastností

Stránky vlastností umožňují uživateli ovládacího prvku ActiveX zobrazit a změnit vlastnosti ovládacího prvku ActiveX. K těmto vlastnostem se přistupuje vyvoláním dialogového okna vlastností ovládacího prvku, které obsahuje jednu nebo více stránek vlastností, které poskytují vlastní grafické rozhraní pro zobrazení a úpravu vlastností ovládacího prvku.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

Stránky vlastností ovládacího prvku ActiveX jsou zobrazeny dvěma způsoby:

- Když je vyvoláno sloveso Vlastnosti ovládacího prvku (**OLEIVERB_PROPERTIES**), ovládací prvek otevře dialogové okno modální vlastnosti, které obsahuje stránky vlastností ovládacího prvku.

- Kontejner může zobrazit vlastní nemodální dialogové okno, které zobrazuje stránky vlastností vybraného ovládacího prvku.

Dialogové okno vlastnosti (znázorněné na následujícím obrázku) se skládá z oblasti pro zobrazení aktuální stránky vlastností, karet pro přepínání mezi stránkami vlastností a kolekce tlačítek, která provádějí běžné úkoly, jako je zavření dialogového okna stránky vlastností, zrušení provedených změn nebo okamžité použití změn v ovládacím prvku ActiveX.

![Dialogové okno Vlastnosti pro Circ3](../mfc/media/vc373i1.gif "Dialogové okno Vlastnosti pro Circ3") <br/>
Dialogové okno Vlastnosti

Tento článek popisuje témata související s používáním stránek vlastností v ovládacím prvku ActiveX. Mezi ně patří:

- [Implementace výchozí stránky vlastností ovládacího prvku ActiveX](#_core_implementing_the_default_property_page)

- [Přidání ovládacích prvků na stránku vlastností](#_core_adding_controls_to_a_property_page)

- [Přizpůsobení funkce DoDataExchange](#_core_customizing_the_dodataexchange_function)

Další informace o použití stránek vlastností v ovládacím prvku ActiveX naleznete v následujících článcích:

- [MFC – ovládací prvky ActiveX: Přidání další stránky přizpůsobených vlastností](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md)

Informace o použití seznamů vlastností v jiné aplikaci knihovny MFC než ovládací prvek ActiveX naleznete v [tématu Property Sheets](../mfc/property-sheets-mfc.md).

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>Implementace stránky výchozích vlastností

Pokud k vytvoření řídicího projektu použijete Průvodce ovládacím prvkem ActiveX, průvodce ovládacím prvkem ActiveX poskytne výchozí třídu stránky vlastností pro ovládací prvek odvozený z [třídy COlePropertyPage](../mfc/reference/colepropertypage-class.md). Zpočátku je tato stránka vlastností prázdná, ale můžete do ní přidat libovolný ovládací prvek dialogového okna nebo sadu ovládacích prvků. Vzhledem k tomu, že Průvodce ovládacím prvkem ActiveX vytvoří ve `COlePropertyPage`výchozím nastavení pouze jednu třídu stránky vlastností, musí být pomocí zobrazení tříd vytvořeny další třídy stránek vlastností (také odvozené z nich). Další informace o tomto postupu naleznete v tématu [Ovládací prvky ActiveX knihovny MFC: Přidání další stránky vlastních vlastností](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).

Implementace stránky vlastností (v tomto případě výchozí) je proces ve třech krocích:

#### <a name="to-implement-a-property-page"></a>Implementace stránky vlastností

1. Přidejte `COlePropertyPage`odvozenou třídu do řídicího projektu. Pokud byl projekt vytvořen pomocí Průvodce ovládacím prvkem ActiveX (jako v tomto případě), výchozí třída stránky vlastností již existuje.

1. Pomocí editoru dialogů přidejte do šablony stránky vlastností všechny ovládací prvky.

1. Přizpůsobte `DoDataExchange` funkci `COlePropertyPage`odvozené třídy pro výměnu hodnot mezi ovládacím prvkem stránky vlastností a ovládacím prvkem ActiveX.

Pro například následující postupy používají jednoduchý ovládací prvek (s názvem "Ukázka"). Ukázka byla vytvořena pomocí Průvodce ovládacím prvkem ActiveX a obsahuje pouze vlastnost Titulek na skladě.

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>Přidání ovládacích prvků na stránku vlastností

#### <a name="to-add-controls-to-a-property-page"></a>Přidání ovládacích prvků na stránku vlastností

1. S otevřeným řídicím projektem otevřete zobrazení zdrojů.

1. Poklepejte na ikonu **adresáře Dialog.**

1. Otevřete dialogové okno IDD_PROPPAGE_SAMPLE.

   Průvodce ovládacím prvkem ActiveX připojí název projektu na konec ID dialogového okna, v tomto případě ukázka.

1. Přetáhněte vybraný ovládací prvek z panelu nástrojů do oblasti dialogového okna.

1. V tomto příkladu stačí ovládací prvek popisek textu "Titulek :" a ovládací prvek pole pro úpravy s identifikátorem IDC_CAPTION.

1. Kliknutím na **Uložit** na panelu nástrojů uložte změny.

Nyní, když bylo uživatelské rozhraní změněno, je třeba propojit textové pole s vlastností Caption. To se provádí v následující části `CSamplePropPage::DoDataExchange` úpravou funkce.

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>Přizpůsobení funkce DoDataExchange

Vaše stránka vlastností [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) funkce umožňuje propojit hodnoty stránky vlastností se skutečnými hodnotami vlastností v ovládacím prvku. Chcete-li vytvořit odkazy, je nutné namapovat příslušná pole stránky vlastností na jejich příslušné vlastnosti ovládacího prvku.

Tato mapování jsou implementována pomocí stránky vlastností **DDP_** funkce. Funkce **DDP_** fungují stejně jako **DDX_** funkce používané ve standardních dialogových oknech knihovny MFC s jednou výjimkou. Kromě odkazu na proměnnou člena **DDP_** funkce převzít název vlastnosti ovládacího prvku. Následuje typická položka ve `DoDataExchange` funkci stránky vlastností.

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Tato funkce přidruží *m_caption* členskou proměnnou stránky `DDP_TEXT` vlastností pomocí funkce.

Po vložení ovládacího prvku stránky vlastností je třeba vytvořit propojení mezi ovládacím prvkem stránky vlastností, `DDP_Text` IDC_CAPTION a vlastností skutečného ovládacího prvku Caption, pomocí funkce popsané výše.

[Stránky vlastností](../mfc/reference/property-pages-mfc.md) jsou k dispozici pro další typy ovládacích prvku dialogového okna, jako jsou zaškrtávací políčka, přepínací tlačítka a seznamy. V následující tabulce je uvedena celá sada stránek vlastností **DDP_** funkce a jejich účely:

### <a name="property-page-functions"></a>Funkce stránky vlastností

|Název funkce|Pomocí této funkce můžete propojit|
|-------------------|-------------------------------|
|`DDP_CBIndex`|Index vybraného řetězce v poli se seznamem s vlastností ovládacího prvku.|
|`DDP_CBString`|Vybraný řetězec v poli se seznamem s vlastností ovládacího prvku. Vybraný řetězec může začínat stejnými písmeny jako hodnota vlastnosti, ale nemusí se plně shodovat.|
|`DDP_CBStringExact`|Vybraný řetězec v poli se seznamem s vlastností ovládacího prvku. Vybraný řetězec a hodnota řetězce vlastnosti se musí přesně shodovat.|
|`DDP_Check`|Zaškrtávací políčko s vlastností ovládacího prvku.|
|`DDP_LBIndex`|Index vybraného řetězce v seznamu s vlastností ovládacího prvku.|
|`DDP_LBString`|Vybraný řetězec v seznamu s vlastností ovládacího prvku. Vybraný řetězec může začínat stejnými písmeny jako hodnota vlastnosti, ale nemusí se plně shodovat.|
|`DDP_LBStringExact`|Vybraný řetězec v seznamu s vlastností ovládacího prvku. Vybraný řetězec a hodnota řetězce vlastnosti se musí přesně shodovat.|
|`DDP_Radio`|Přepínací tlačítko s vlastností ovládacího prvku.|
|`DDP_Text`|Text s vlastností ovládacího prvku.|

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[COlePropertyPage – třída](../mfc/reference/colepropertypage-class.md)
