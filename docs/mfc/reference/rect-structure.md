---
title: RECT – struktura
ms.date: 11/04/2016
f1_keywords:
- LPRECT
- RECT
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
ms.openlocfilehash: 1cb997fc0f1ec89eabf5e4d2c2c5ccb15e3bafec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549006"
---
# <a name="rect-structure"></a>RECT – struktura

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
