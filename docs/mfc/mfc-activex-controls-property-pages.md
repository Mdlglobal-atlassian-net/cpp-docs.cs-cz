---
title: 'MFC – ovládací prvky ActiveX: Stránky vlastností | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 053a6dcf009fa65bbba9c864803db78866037196
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204415"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC – ovládací prvky ActiveX: Stránky vlastností

Stránky vlastností umožnit uživateli ovládacího prvku ActiveX k zobrazení a změna vlastností ovládacího prvku ActiveX. Tyto vlastnosti jsou přístupné prostřednictvím volání ovládacího prvku dialogové okno Vlastnosti, která obsahuje jeden nebo více stránek vlastností, které poskytují vlastní grafické rozhraní pro zobrazení a úprava vlastností ovládacího prvku.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Stránky vlastností ovládacího prvku ActiveX jsou zobrazeny dvěma způsoby:

- Při operaci Properties ovládacího prvku (**OLEIVERB_PROPERTIES**) je vyvolána, ovládací prvek se otevře dialogové okno Vlastnosti modální okno, které obsahuje stránky vlastností ovládacího prvku.

- Kontejner můžete zobrazit vlastní nemodální dialogové okno, které se zobrazí na stránkách vlastností vybraného ovládacího prvku.

Dialogové okno Vlastnosti (znázorněný na následujícím obrázku) se skládá z oblasti pro zobrazení aktuální stránka vlastností karty pro přepínání mezi sadu tlačítek, provádět běžné úkoly, jako je například zavření dialogové okno stránky vlastností a stránek vlastností ruší se všechny změny provedené nebo okamžitě použití změn do ovládacího prvku ActiveX.

![Dialogové okno Vlastnosti pro Circ3 –](../mfc/media/vc373i1.gif "vc373i1") dialogové okno Vlastnosti

Tento článek obsahuje témata týkající se použití stránek vlastností v ovládacím prvku ActiveX. Zde jsou některé z nich:

- [Implementace výchozí stránky vlastností pro ovládací prvek ActiveX](#_core_implementing_the_default_property_page)

- [Přidání ovládacích prvků na stránce vlastností](#_core_adding_controls_to_a_property_page)

- [Přizpůsobení DoDataExchange – funkce](#_core_customizing_the_dodataexchange_function)

Další informace o použití stránek vlastností v ovládacím prvku ActiveX najdete v následujících článcích:

- [MFC – ovládací prvky ActiveX: Přidání další stránky přizpůsobených vlastností](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC – ovládací prvky ActiveX: Použití stránek uložených vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md)

Informace o použití seznamů vlastností v aplikaci MFC než ovládací prvek ActiveX naleznete v tématu [vlastností](../mfc/property-sheets-mfc.md).

##  <a name="_core_implementing_the_default_property_page"></a> Implementace výchozí stránky vlastností

Pokud používáte Průvodce ovládacím prvkem ActiveX k vytvoření projektu ovládacího prvku, Průvodce ovládacím prvkem ActiveX poskytuje třídy stránky vlastností výchozí pro ovládací prvek odvozen od [COlePropertyPage – třída](../mfc/reference/colepropertypage-class.md). Na začátku této stránky vlastností je prázdná, ale k němu můžete přidat libovolný ovládací prvek dialogového okna nebo sadu ovládacích prvků. Vzhledem k tomu, že ve výchozím nastavení, další vlastnosti třídy stránky Průvodce ovládacím prvkem ActiveX vytvoří pouze jednu vlastnost třídy stránky (také odvozený z `COlePropertyPage`) musí být vytvořen pomocí zobrazení tříd. Další informace o tomto postupu najdete v tématu [knihovny MFC – ovládací prvky ActiveX: přidání další stránka vlastností vlastního](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).

Implementace vlastnosti stránky (v tomto případě výchozí hodnota) je třech krocích:

#### <a name="to-implement-a-property-page"></a>Implementace stránky vlastností

1. Přidat `COlePropertyPage`-odvozené třídy do projektu ovládacího prvku. Pokud projekt byl vytvořen pomocí Průvodce ovládacím prvkem ActiveX (stejně jako v tomto případě), výchozí třídy stránky vlastností již existuje.

1. Použití editoru dialogového okna pro přidání všech ovládacích prvků do šablony stránky vlastností.

1. Přizpůsobit `DoDataExchange` funkce `COlePropertyPage`-odvozené třídy k výměně hodnot mezi ovládací prvek stránky vlastností a ovládacího prvku ActiveX.

Například účely, následující postupy použijte jednoduché ovládací prvek (s názvem "Ukázkový"). Vzorek byl vytvořen pomocí Průvodce ovládacím prvkem ActiveX a obsahuje pouze uložených vlastností titulek.

##  <a name="_core_adding_controls_to_a_property_page"></a> Přidání ovládacích prvků na stránce vlastností

#### <a name="to-add-controls-to-a-property-page"></a>Chcete-li přidat ovládací prvky stránky vlastností

1. Pomocí ovládacího prvku projektu otevřený otevřete zobrazení prostředků.

1. Dvakrát klikněte **dialogové okno** ikonu adresáře.

1. Otevřete dialogové okno IDD_PROPPAGE_SAMPLE.

   Průvodce ovládacím prvkem ActiveX připojí na konec ID dialogu, v tomto případě ukázka název projektu.

1. Přetáhnout myší vybraný ovládací prvek z panelu nástrojů na oblast dialogového okna.

1. V tomto příkladu textový popisek ovládacího prvku "Caption:" a pole ovládacího prvku pro úpravy s identifikátorem IDC_CAPTION jsou dostačující.

1. Klikněte na tlačítko **Uložit** na panelu nástrojů uložte provedené změny.

Teď, když byla změněna uživatelského rozhraní, budete potřebovat odkázat textové pole s vlastností titulek. To se provádí v následující části tak, že upravíte `CSamplePropPage::DoDataExchange` funkce.

##  <a name="_core_customizing_the_dodataexchange_function"></a> Přizpůsobení DoDataExchange – funkce

Stránky vlastností [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) funkce umožňuje propojit hodnoty vlastností stránky pomocí skutečné hodnoty vlastností v ovládacím prvku. K vytvoření odkazů, je nutné mapovat pole stránky příslušné vlastnosti na jejich odpovídající ovládací prvek vlastnosti.

Tato mapování jsou implementovány pomocí stránky vlastností **ddp_ –** funkce. **Ddp_ –** funkce fungují jako **DDX_** funkcí používaných v standardní dialogová okna knihovny MFC, s jednou výjimkou. Kromě odkaz na proměnnou člena **ddp_ –** funkce vezme název vlastnosti ovládacího prvku. Následuje Typická položku v `DoDataExchange` funkce pro stránky vlastností.

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Tato funkce přidruží na stránce vlastností *m_caption* členskou proměnnou s titulkem, pomocí `DDP_TEXT` funkce.

Jakmile budete mít ovládacích prvků stránky vlastností, vložit, budete muset vytvořit propojení mezi vlastnost skutečný ovládací prvek, ovládací prvek stránky vlastností a IDC_CAPTION popisovat, pomocí `DDP_Text` fungovat tak, jak je popsáno výše.

[Stránky vlastností](../mfc/reference/property-pages-mfc.md) jsou k dispozici pro jiné typy ovládacích prvků dialogového okna, jako je například zaškrtávací políčka, přepínače a polích se seznamem. Následující tabulka uvádí celou sadu vlastností **ddp_ –** funkce a jejich účely:

### <a name="property-page-functions"></a>Funkce stránky vlastností

|Název funkce|Tato funkce slouží k propojení|
|-------------------|-------------------------------|
|`DDP_CBIndex`|Index vybrané řetězce v poli se seznamem s vlastností ovládacího prvku.|
|`DDP_CBString`|Vybraný řetězec v poli se seznamem s vlastností ovládacího prvku. Vybrané řetězce mohou začínat stejná písmena jako hodnotu vlastnosti, ale nemusejí odpovídat plně.|
|`DDP_CBStringExact`|Vybraný řetězec v poli se seznamem s vlastností ovládacího prvku. Vybraný řetězec a hodnotu vlastnosti řetězce musí přesně shodovat.|
|`DDP_Check`|Zaškrtněte políčko s vlastností ovládacího prvku.|
|`DDP_LBIndex`|Index vybrané řetězců v seznamu s vlastností ovládacího prvku.|
|`DDP_LBString`|Vybraný řetězec v seznamu s vlastností ovládacího prvku. Vybrané řetězce mohou začínat stejná písmena jako hodnotu vlastnosti, ale nemusejí odpovídat plně.|
|`DDP_LBStringExact`|Vybraný řetězec v seznamu s vlastností ovládacího prvku. Vybraný řetězec a hodnotu vlastnosti řetězce musí přesně shodovat.|
|`DDP_Radio`|Přepínací tlačítko s vlastností ovládacího prvku.|
|`DDP_Text`|Text s vlastností ovládacího prvku.|

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[COlePropertyPage – třída](../mfc/reference/colepropertypage-class.md)
