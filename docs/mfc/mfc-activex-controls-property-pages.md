---
title: "Ovládací prvky MFC ActiveX: Stránky vlastností | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3dd62127d5fb09675d6c91963d85dd6ae7f44f35
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-property-pages"></a>MFC – ovládací prvky ActiveX: Stránky vlastností
Stránky vlastností umožnit uživateli ovládacího prvku ActiveX k zobrazení a změna vlastností ovládacího prvku ActiveX. Tyto vlastnosti jsou dostupné přes vyvolání řízení dialogové okno Vlastnosti, která obsahuje jeden nebo více stránek vlastností, které poskytují vlastní grafické rozhraní pro zobrazení a úprava vlastností ovládacího prvku.  
  
 Stránky vlastností ovládacího prvku ActiveX zobrazují dvěma způsoby:  
  
-   Při operaci vlastností ovládacího prvku (**OLEIVERB_PROPERTIES**) je vyvolána, ovládacího prvku otevře dialogové okno vlastností modální, který obsahuje stránky vlastností ovládacího prvku.  
  
-   Kontejner můžete zobrazit svůj vlastní nemodálního dialogu, který ukazuje na stránkách vlastností vybraný ovládací prvek.  
  
 Dialogové okno Vlastnosti (zobrazené na následujícím obrázku) se skládá z oblasti pro zobrazení aktuální stránky vlastností, karty pro přepínání mezi stránky vlastností a kolekce tlačítek, provádět běžné úkoly jako zavřením tohoto dialogového okna Vlastnosti stránky zrušení všechny změny, nebo okamžitě použití změn do ovládacího prvku ActiveX.  
  
 ![Dialogové okno Vlastnosti pro Circ3 –](../mfc/media/vc373i1.gif "vc373i1")  
Dialogové okno Vlastnosti  
  
 Tento článek se zabývá témata týkající se použití stránek vlastností v ovládacím prvku ActiveX. Mezi ně patří:  
  
-   [Implementace výchozí stránku vlastností pro ovládací prvek ActiveX](#_core_implementing_the_default_property_page)  
  
-   [Přidání ovládacích prvků na stránce vlastností](#_core_adding_controls_to_a_property_page)  
  
-   [Přizpůsobení DoDataExchange – funkce](#_core_customizing_the_dodataexchange_function)  
  
 Další informace o použití stránek vlastností v ovládacím prvku ActiveX najdete v následujících článcích:  
  
-   [Ovládací prvky MFC ActiveX: Přidání další stránky přizpůsobených vlastností](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [Ovládací prvky MFC ActiveX: Použití stránek uložených vlastností](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 Informace o používání vlastností v aplikaci MFC než ovládacího prvku ActiveX najdete v tématu [vlastností](../mfc/property-sheets-mfc.md).  
  
##  <a name="_core_implementing_the_default_property_page"></a>Implementace výchozí stránky vlastností  
 Pokud používáte Průvodce ovládacím prvkem ActiveX k vytvoření projektu ovládacího prvku, Průvodce ovládacím prvkem ActiveX poskytuje třídu výchozí vlastnosti stránky pro ovládací prvek odvozen od [COlePropertyPage třída](../mfc/reference/colepropertypage-class.md). Na začátku této stránky vlastností je prázdný, ale do něj může přidat žádné dialogové okno Ovládací prvek nebo sadu ovládacích prvků. Protože Průvodce ovládacím prvkem ActiveX vytvoří pouze jednu vlastnost třídy stránky ve výchozím nastavení, další vlastnosti třídy stránky (také odvozené z `COlePropertyPage`) musí být vytvořen pomocí zobrazení tříd. Další informace o tomto postupu najdete v tématu [MFC – ovládací prvky ActiveX: Přidání jinou vlastní vlastnost stránku](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).  
  
 Implementace vlastností stránky (v tomto případě výchozí hodnota) je proces třech krocích:  
  
#### <a name="to-implement-a-property-page"></a>K implementaci stránky vlastností  
  
1.  Přidat `COlePropertyPage`-odvozené třídy do projektu správy. Pokud projekt byl vytvořen pomocí Průvodce ovládacím prvkem ActiveX (jako v tomto případě), výchozí třídy stránky vlastností již existuje.  
  
2.  Použití editoru dialogových oken pro přidání všech ovládacích prvků do šablony stránky vlastností.  
  
3.  Přizpůsobení `DoDataExchange` funkce `COlePropertyPage`-odvozené třídy pro výměnu hodnoty mezi ovládacího prvku vlastnost stránky a ovládací prvek ActiveX.  
  
 Například pro účely, následující postupy použijte jednoduchý ovládací prvek (s názvem "Ukázkový"). Ukázka byla vytvořena pomocí Průvodce ovládacím prvkem ActiveX a obsahuje pouze uložených vlastností titulek.  
  
##  <a name="_core_adding_controls_to_a_property_page"></a>Přidání ovládacích prvků na stránce vlastností  
  
#### <a name="to-add-controls-to-a-property-page"></a>Přidání ovládacích prvků do stránky vlastností  
  
1.  Pomocí řízení projektu otevřít otevřete zobrazení prostředků.  
  
2.  Dvakrát klikněte **dialogové okno** directory ikonu.  
  
3.  Otevřete **IDD_PROPPAGE_SAMPLE** dialogové okno.  
  
     Průvodce ovládacím prvkem ActiveX přidá na konec dialogu ID, v takovém případě Ukázkový název projektu.  
  
4.  Přetáhnout myší vybraný ovládací prvek z panelu nástrojů na oblast dialogového okna.  
  
5.  V tomto příkladu textový popisek ovládacího prvku "Caption:" a prvek upravit s **IDC_CAPTION** postačí identifikátor.  
  
6.  Klikněte na tlačítko **Uložit** na panelu nástrojů a uložit provedené změny.  
  
 Teď, když byla změněna uživatelské rozhraní, budete muset propojit textové pole s vlastnosti titulku. To se provádí v následující části úpravou `CSamplePropPage::DoDataExchange` funkce.  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a>Přizpůsobení DoDataExchange – funkce  
 Stránky vlastností [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) funkce umožňuje propojit hodnoty vlastností stránky a skutečné hodnoty vlastností v ovládacím prvku. Když Pokud chcete stanovit odkazy, je nutné mapovat do jejich vlastnosti příslušných ovládacích prvků pole stránky odpovídající vlastnost.  
  
 Tato mapování jsou implementované pomocí stránky vlastností **ddp_ –** funkce. **Ddp_ –** funkce fungovat jako **DDX_** funkcí používaných v standardní dialogová okna MFC, s jednou výjimkou. Kromě odkaz na proměnnou člen **ddp_ –** funkce přebírat název vlastnosti ovládacího prvku. Následuje typický položku v `DoDataExchange` funkce pro danou stránku vlastností.  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]  
  
 Tato funkce přidruží stránka vlastností `m_caption` členské proměnné s popiskem, pomocí `DDP_TEXT` funkce.  
  
 Až budete mít vložit ovládací prvek vlastnost stránku, budete muset vytvořit propojení mezi ovládací prvek vlastnost stránku `IDC_CAPTION`, a vlastnost skutečný ovládací prvek popisek, pomocí **ddp_text –** fungovat, jak je popsáno výše.  
  
 [Stránky vlastností](../mfc/reference/property-pages-mfc.md) jsou k dispozici pro jiné typy ovládacích prvků dialogové okno, jako je například zaškrtávací políčka, přepínače a seznamy. Následující tabulka obsahuje celou sadu vlastností stránky **ddp_ –** funkce a jejich účely:  
  
### <a name="property-page-functions"></a>Funkce stránky vlastností  
  
|Název funkce|Tato funkce slouží k propojení|  
|-------------------|-------------------------------|  
|`DDP_CBIndex`|Vybraný řetězec index v poli se seznamem s vlastností ovládacího prvku.|  
|`DDP_CBString`|Vybraný řetězec v poli se seznamem s vlastností ovládacího prvku. Vybraný řetězec můžete začít s stejná písmena jako hodnotu vlastnosti, ale nemusí odpovídat plně.|  
|`DDP_CBStringExact`|Vybraný řetězec v poli se seznamem s vlastností ovládacího prvku. Vybraný řetězec a hodnotu vlastnosti řetězce musí přesně shodovat.|  
|`DDP_Check`|Zaškrtávací políčko s vlastností ovládacího prvku.|  
|`DDP_LBIndex`|Vybraný řetězec index v poli seznamu s vlastností ovládacího prvku.|  
|`DDP_LBString`|Vybraný řetězec v seznamu s vlastností ovládacího prvku. Vybraný řetězec můžete začít s stejná písmena jako hodnotu vlastnosti, ale nemusí odpovídat plně.|  
|`DDP_LBStringExact`|Vybraný řetězec v seznamu s vlastností ovládacího prvku. Vybraný řetězec a hodnotu vlastnosti řetězce musí přesně shodovat.|  
|`DDP_Radio`|Přepínače s vlastností ovládacího prvku.|  
|**Ddp_text –**|Text s vlastností ovládacího prvku.|  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [COlePropertyPage – třída](../mfc/reference/colepropertypage-class.md)
