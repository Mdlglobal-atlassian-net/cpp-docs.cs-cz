---
title: RECT – Struktura1 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LPRECT
- RECT
dev_langs:
- C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa77af9dd97afc2e9b0cfb94c1fd4c69a50f309b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419591"
---
# <a name="rect-structure1"></a>RECT – Struktura1

`RECT` Struktury definuje souřadnice levého a pravého dolního rohu obdélníku.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagRECT {
    LONG left;
    LONG top;
    LONG right;
    LONG bottom;
} RECT;
```

## <a name="members"></a>Členové

`left`<br/>
Určuje souřadnice x levého horního rohu obdélníku.

`top`<br/>
Určuje souřadnici y levého horního rohu obdélníku.

`right`<br/>
Určuje souřadnici x v pravém dolním rohu obdélníku.

`bottom`<br/>
Určuje souřadnici y pravého dolního rohu obdélníku.

## <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** windef.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRect – třída](../../atl-mfc-shared/reference/crect-class.md)
