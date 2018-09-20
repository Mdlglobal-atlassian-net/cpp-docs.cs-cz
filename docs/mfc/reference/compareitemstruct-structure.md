---
title: Compareitemstruct – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: 450e6fa4694c35929196cc5df3bf2fd6b4e843c4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406819"
---
# <a name="compareitemstruct-structure"></a>COMPAREITEMSTRUCT – struktura

`COMPAREITEMSTRUCT` Struktury poskytuje identifikátory a poskytované aplikací dat pro dvě položky v seznamu seřazené, vykreslování nebo pole se seznamem.

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

*CtlType*<br/>
ODT_LISTBOX (který určuje pole se seznamem vykreslené vlastníkem.) nebo ODT_COMBOBOX (který určuje, do pole se seznamem vykreslené vlastníkem.).

*CtlID*<br/>
ID ovládacího prvku pro pole se seznamem nebo pole se seznamem.

*hwndItem*<br/>
Popisovač okna ovládacího prvku.

*itemID1*<br/>
Index první položky v seznamu nebo pole se seznamem, který se porovnává.

*itemData1*<br/>
Poskytované aplikací dat, pro který se porovnává první položky. Tato hodnota byla předána volání, které přidá položku do pole se seznamem nebo seznamu.

*itemID2*<br/>
Index druhé položky v seznamu nebo pole se seznamem, který se porovnává.

*itemData2*<br/>
Data poskytované aplikací pro druhou položku, který se porovnává. Tato hodnota byla předána volání, které přidá položku do pole se seznamem nebo seznamu.

## <a name="remarks"></a>Poznámky

Pokaždé, když aplikace přidá nová položka pole se seznamem vykreslovaných vlastníkem nebo vytvořili stylem CBS_SORT nebo LBS_SORT – pole se seznamem, Windows odešle zprávu WM_COMPAREITEM vlastníka. *LParam* parametr zprávy obsahuje dlouhým ukazatelem na `COMPAREITEMSTRUCT` struktury. Po přijetí zprávy, vlastník porovná dvě položky a vrátí hodnotu určující, která položka řadí před druhé.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winuser

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

