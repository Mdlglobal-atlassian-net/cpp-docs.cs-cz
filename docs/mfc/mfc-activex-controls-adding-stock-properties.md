---
title: 'Ovládací prvky MFC ActiveX: Přidání uložených vlastností | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c51a2efba3c89b4e216fec96459b14c3d0c637d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC – ovládací prvky ActiveX: Přidání uložených vlastností
Uložené vlastnosti liší od vlastní vlastnosti v tom, že už jsou implementované v třídě `COleControl`. `COleControl` obsahuje předdefinované členské funkce, které podporují společných vlastností pro ovládací prvek. Některé běžné vlastnosti zahrnují ovládacího prvku popisek a barvy popředí a na pozadí. Informace o dalších vlastností uložených v tématu [Stock vlastnosti nepodporuje Průvodce přidáním vlastnosti](#_core_stock_properties_supported_by_classwizard) dále v tomto článku. Odesílání položek mapy uložených vlastností vždy předchází **DISP_STOCKPROP**.  
  
 Tento článek popisuje postup přidání uložených vlastností (v tomto případě titulek) do ovládacího prvku ActiveX pomocí Průvodce přidáním vlastnosti a vysvětluje výsledné změny kódu. Témata zahrnují:  
  
-   [Pomocí Průvodce přidáním vlastnosti pro přidání uložených vlastností](#_core_using_classwizard_to_add_a_stock_property)  
  
-   [Přidat vlastnost průvodce změní pro uložené vlastnosti](#_core_classwizard_changes_for_stock_properties)  
  
-   [Uložené vlastnosti nepodporuje Průvodce přidáním vlastnosti](#_core_stock_properties_supported_by_classwizard)  
  
-   [Uložené vlastnosti a oznámení](#_core_stock_properties_and_notification)  
  
-   [Barva vlastnosti](#_core_color_properties)  
  
    > [!NOTE]
    >  Vlastní ovládací prvky jazyka Visual Basic obvykle mají vlastnosti, například horní, vlevo, šířky, výšky, Align, značka, název, pořadové číslo prvku, zarážek tabulátorů a nadřazené. ActiveX – kontejnery ovládacích prvků, ale jsou zodpovědní za implementaci těchto vlastností ovládacího prvku a proto by nemělo – ovládací prvky ActiveX podporuje tyto vlastnosti.  
  
##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> Pomocí Průvodce přidáním vlastnosti pro přidání uložených vlastností  
 Přidání uložených vlastností vyžaduje méně kódu než přidání vlastních vlastností, protože podpora automaticky zpracovává vlastnost `COleControl`. Následující postup ukazuje, přidání zásob Vlastnosti titulku Framework ovládací prvek ActiveX a můžete také použít k přidání dalších uložených vlastností. Nahraďte název vybrané uložených vlastností pro titulek.  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Chcete-li přidat vlastnost uložených titulek pomocí Průvodce přidáním vlastnosti  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.  
  
3.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek (druhého uzlu uzlu knihovny) a místní nabídce.  
  
4.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat vlastnost**.  
  
     Tím se otevře [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md).  
  
5.  V **název vlastnosti** pole, klikněte na tlačítko **popisek**.  
  
6.  Klikněte na tlačítko **Dokončit**.  
  
##  <a name="_core_classwizard_changes_for_stock_properties"></a> Přidat vlastnost průvodce změní pro uložené vlastnosti  
 Protože `COleControl` podporuje uložených vlastností, Průvodce přidáním vlastnosti nezmění deklaraci třídy žádným způsobem; přidá vlastnost expediční mapy. Průvodce přidáním vlastnosti přidá následující řádek do expediční mapy ovládacího prvku, který je umístěný v implementaci (. Soubor CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]  
  
 Následující řádek je přidán do ovládacího prvku rozhraní popis (. Soubor IDL):  
  
 [!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]  
  
 Tento řádek přiřadí vlastnosti titulku konkrétním ID. Všimněte si, že vlastnost je vazbu a bude požadovat oprávnění z databáze před změnou hodnoty.  
  
 To zpřístupňuje vlastnosti titulku uživatelům ovládacího prvku. Pokud chcete použít hodnotu uložených vlastností, přístupu k členské proměnné nebo funkce člena `COleControl` základní třídy. Další informace o těchto členské proměnné a členské funkce najdete v další části, Stock vlastnosti nepodporuje Průvodce přidáním vlastnosti.  
  
##  <a name="_core_stock_properties_supported_by_classwizard"></a> Stock vlastnostech podporovaných zprostředkovatelem Průvodce přidáním vlastnosti  
 `COleControl` Třída poskytuje devět uložených vlastností. Můžete přidat vlastnosti, které chcete pomocí Průvodce přidáním vlastnosti.  
  
|Vlastnost|Položku mapy odesílání|Jak získat přístup k hodnota|  
|--------------|------------------------|-------------------------|  
|**Vzhled**|**(DISP_STOCKPROP_APPEARANCE)**|Hodnota, které jsou dostupné jako **m_sAppearance**.|  
|`BackColor`|**(DISP_STOCKPROP_BACKCOLOR)**|Hodnota přístupný pro volání `GetBackColor`.|  
|`BorderStyle`|**(DISP_STOCKPROP_BORDERSTYLE)**|Hodnota, které jsou dostupné jako **m_sBorderStyle**.|  
|**Popisek**|**(DISP_STOCKPROP_CAPTION)**|Hodnota přístupný pro volání `InternalGetText`.|  
|**povoleno**|**(DISP_STOCKPROP_ENABLED)**|Hodnota, které jsou dostupné jako **m_bEnabled**.|  
|**Písma**|**(DISP_STOCKPROP_FONT)**|Najdete v článku [MFC – ovládací prvky ActiveX: použití písem](../mfc/mfc-activex-controls-using-fonts.md) pro použití.|  
|`ForeColor`|**(DISP_STOCKPROP_FORECOLOR)**|Hodnota přístupný pro volání `GetForeColor`.|  
|**hWnd**|**(DISP_STOCKPROP_HWND)**|Hodnota, které jsou dostupné jako `m_hWnd`.|  
|**Text**|**(DISP_STOCKPROP_TEXT)**|Hodnota přístupný pro volání `InternalGetText`. Tato vlastnost je stejný jako **popisek**, s výjimkou názvu vlastnosti.|  
|**ReadyState**|**DISP_STOCKPROP_READYSTATE()**|Hodnota, které jsou dostupné jako m_lReadyState nebo `GetReadyState`|  
  
##  <a name="_core_stock_properties_and_notification"></a> Uložené vlastnosti a oznámení  
 Většina uložených vlastností mít funkce oznámení, které je možné přepsat. Například, vždy, když `BackColor` vlastnost je změnit, `OnBackColorChanged` je volána funkce (členské funkce ovládacího prvku třídy). Výchozí implementace (v `COleControl`) volání `InvalidateControl`. Tato funkce přepsání, pokud chcete provést další akce v odpovědi na tuto situaci.  
  
##  <a name="_core_color_properties"></a> Barva vlastnosti  
 Můžete použít stock `ForeColor` a `BackColor` vlastnosti nebo vlastní vlastnosti vlastních barev, při vykreslování ovládacího prvku. Chcete-li použít vlastnost barva, zavolejte [COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) – členská funkce. Parametry této funkce se hodnota vlastnosti barvy a popisovač volitelné palety. Vrácená hodnota je **COLORREF** hodnotu, která se dá předat do GDI funguje, jako například `SetTextColor` a `CreateSolidBrush`.  
  
 Barva hodnoty stock `ForeColor` a `BackColor` přístup k vlastnostem voláním buď `GetForeColor` nebo `GetBackColor` fungovat, v uvedeném pořadí.  
  
 Následující příklad ukazuje, při vykreslování ovládacího prvku pomocí vlastnosti tyto dvě barvy. Se inicializuje dočasného **COLORREF** proměnné a `CBrush` objekt pomocí volání `TranslateColor`: jeden pomocí `ForeColor` vlastnost a dalších pomocí `BackColor` vlastnost. Dočasného `CBrush` objekt se pak použije k vyplnění obdélníku ovládacího prvku a barvu textu se nastavuje pomocí `ForeColor` vlastnost.  
  
 [!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [MFC – ovládací prvky ActiveX: vlastnosti](../mfc/mfc-activex-controls-properties.md)   
 [MFC – ovládací prvky ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [COleControl – třída](../mfc/reference/colecontrol-class.md)
