---
title: "Deleteitemstruct – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DELETEITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93be7b23ae713caea5fa64e437fe792c550589f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="deleteitemstruct-structure"></a>DELETEITEMSTRUCT – struktura
`DELETEITEMSTRUCT` Struktura popisuje odstraněné vykreslovaných vlastníkem pole se seznamem nebo pole se seznamem položku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagDELETEITEMSTRUCT { /* ditms */  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    HWND hwndItem;  
    UINT itemData;  
} DELETEITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CtlType`  
 Určuje **ODT_LISTBOX** (pole se seznamem vykreslovaných vlastníkem) nebo **ODT_COMBOBOX** (pole se seznamem vykreslované uživatelem).  
  
 `CtlID`  
 Určuje identifikátor pole se seznamem nebo pole se seznamem.  
  
 `itemID`  
 Určuje index položky v seznamu nebo pole se seznamem, který je právě odebírán.  
  
 `hwndItem`  
 Identifikuje ovládacího prvku.  
  
 `itemData`  
 Určuje definované aplikací data pro položku. Tato hodnota je předaná do ovládacího prvku **lParam** parametr zprávu, která přidá položku do pole se seznamem nebo pole se seznamem.  
  
## <a name="remarks"></a>Poznámky  
 Při odebrání položky ze seznamu nebo pole se seznamem nebo zničena pole se seznamem nebo pole se seznamem, systém Windows odešle `WM_DELETEITEM` zprávu, která se vlastníkem jednotlivých odstraněných položek. **LParam** parametr zprávy obsahuje ukazatel na tuto strukturu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)


