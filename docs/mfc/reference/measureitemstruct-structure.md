---
title: Measureitemstruct – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MEASUREITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- MEASUREITEMSTRUCT structure [MFC]
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff015fdaf9e37d919459cadc8e4c35c4b795b3f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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

