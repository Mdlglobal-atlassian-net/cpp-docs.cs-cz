---
title: Compareitemstruct – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COMPAREITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a94d39c6b6c256444cd2850f7e55a7e4b87f6d7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compareitemstruct-structure"></a>COMPAREITEMSTRUCT – struktura
`COMPAREITEMSTRUCT` Struktura poskytuje identifikátory a aplikace zadaná data pro dvě položky v seznamu seřazená, vykreslovaných vlastníkem nebo pole se seznamem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagCOMPAREITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    HWND hwndItem;  
    UINT itemID1;  
    DWORD itemData1;  
    UINT itemID2;  
    DWORD itemData2;  
} COMPAREITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CtlType`  
 **ODT_LISTBOX** (který určuje pole se seznamem vykreslování vlastníka) nebo **ODT_COMBOBOX** (který určuje pole se seznamem vykreslování vlastníka).  
  
 `CtlID`  
 ID ovládacího prvku pole se seznamem nebo pole se seznamem.  
  
 `hwndItem`  
 Popisovač okna ovládacího prvku.  
  
 *itemID1*  
 Index první položky v seznamu nebo porovnávané – pole se seznamem.  
  
 *itemData1*  
 Data zadaná aplikace pro první položka porovnávané. Tato hodnota byla předána volání, které přidá položku do pole se seznamem nebo seznamu.  
  
 *itemID2*  
 Index druhý položky v seznamu nebo porovnávané – pole se seznamem.  
  
 *itemData2*  
 Zadaná aplikace data pro druhou položku porovnávané. Tato hodnota byla předána volání, které přidá položku do pole se seznamem nebo seznamu.  
  
## <a name="remarks"></a>Poznámky  
 Vždy, když aplikace přidá novou položku do pole se seznamem vykreslovaných vlastníkem nebo pole se seznamem vytvořené pomocí **cbs_sort –** nebo **lbs_sort –** styl, systém Windows odešle vlastník `WM_COMPAREITEM` zprávy. `lParam` Parametr zprávy obsahuje dlouho ukazatel `COMPAREITEMSTRUCT` struktura. Po přijetí zprávy, vlastník porovná dvě položky a vrátí hodnotu, která určuje, která položka seřadí před dalších.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

