---
title: "Measureitemstruct – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MEASUREITEMSTRUCT
dev_langs: C++
helpviewer_keywords: MEASUREITEMSTRUCT structure [MFC]
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ce5221943ba1591a01ddebe2c261e4197fa18501
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="measureitemstruct-structure"></a>MEASUREITEMSTRUCT – struktura
`MEASUREITEMSTRUCT` Struktura informuje Windows dimenzí, nebo nabídky ovládací prvek položky vykreslované uživatelem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagMEASUREITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    UINT itemWidth;  
    UINT itemHeight;  
    DWORD itemData  
} MEASUREITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CtlType`  
 Obsahuje typ ovládacího prvku. Typy ovládacích prvků hodnoty jsou následující:  
  
- **ODT_COMBOBOX** vykreslování vlastníka – pole se seznamem  
  
- **ODT_LISTBOX** pole se seznamem kreslení vlastníka  
  
- **ODT_MENU** nabídky kreslení vlastníka  
  
 `CtlID`  
 Obsahuje ID ovládacího prvku pole se seznamem, pole se seznamem nebo tlačítko. Tento člen není použit nabídky.  
  
 `itemID`  
 Obsahuje ID položky nabídky nabídky nebo ID položky seznamu pole proměnné výšky pole se seznamem nebo pole se seznamem. Tento člen není použit pro pole se seznamem-height nebo pole se seznamem, nebo pro tlačítko.  
  
 *itemWidth*  
 Určuje šířku položky nabídky. Vlastník položky nabídky vykreslování vlastníka musí vyplnit tento člen, než vrátí zprávu.  
  
 *itemHeight*  
 Určuje výšku jednotlivé položky v seznamu nebo nabídky. Předtím, než vrátí zprávu, vlastník pole se seznamem vykreslování vlastníka jsou seznam nebo položka nabídky musíte vyplnit tento člen. Maximální výška položku v seznamu je 255.  
  
 `itemData`  
 Pole se seznamem nebo pole se seznamem tento člen obsahuje hodnotu, která byla předána do pole se seznamem pomocí jedné z následujících akcí:  
  
- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)  
  
- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)  
  
- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)  
  
- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)  
  
 Tento člen nabídky, obsahuje hodnotu, která byla předána do nabídky pomocí jedné z následujících akcí:  
  
- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)  
  
- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)  
  
- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)  
  
 To umožňuje systému Windows správně zpracovat interakce uživatele pomocí ovládacího prvku. Selhání k vyplnění správné členů `MEASUREITEMSTRUCT` struktura může způsobit nesprávnou operaci ovládacího prvku.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)

