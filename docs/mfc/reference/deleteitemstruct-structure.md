---
title: Deleteitemstruct – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: 9061205bdf3697e492b846d160a5b4dd2d154bb9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065015"
---
# <a name="deleteitemstruct-structure"></a>DELETEITEMSTRUCT – struktura

`DELETEITEMSTRUCT` Struktura popisuje odstraněnou vykreslovaných vlastníkem pole se seznamem nebo pole se seznamem položku.

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

*CtlType*<br/>
Určuje ODT_LISTBOX (vlastníkem vykreslený seznam pole) nebo ODT_COMBOBOX (do pole se seznamem vykreslované uživatelem).

*CtlID*<br/>
Určuje identifikátor používaného seznamu nebo pole se seznamem.

*ID položky*<br/>
Určuje index položky v seznamu nebo pole se seznamem odebírá.

*hwndItem*<br/>
Určuje ovládací prvek.

*itemData*<br/>
Určuje aplikace definované datové položky. Tato hodnota je předán do ovládacího prvku *lParam* parametr zprávy, která přidá položku do seznamu nebo pole se seznamem.

## <a name="remarks"></a>Poznámky

Když je položka odebrána ze seznamu nebo pole se seznamem nebo seznamu nebo pole se seznamem je zničen, Windows odešle zprávu WM_DELETEITEM vlastníka pro každou odstraněnou položku. *LParam* parametr zprávy obsahuje ukazatel na tuto strukturu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)

