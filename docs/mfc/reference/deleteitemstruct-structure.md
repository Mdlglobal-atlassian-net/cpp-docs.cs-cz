---
title: Deleteitemstruct – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DELETEITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f56a09742276c7fcb1bd66ff1a36b1d17cdf882
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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


