---
title: POINT – struktura
ms.date: 10/12/2018
f1_keywords:
- POINT
- LPPOINT
helpviewer_keywords:
- LPPOINT structure [MFC]
- POINT structure [MFC]
ms.assetid: 965736d8-4e53-41b6-9b8b-6961992dd21f
ms.openlocfilehash: c53f250b714c66e74a12432b879cbc4bcc1fd88d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646898"
---
# <a name="point-structure"></a>POINT – struktura

`POINT` Struktury definuje x*-* a souřadnice y bodu.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagPOINT {
    LONG x;
    LONG y;
} POINT;
```

#### <a name="parameters"></a>Parametry

*x*<br/>
Určuje souřadnici x bodu.

*y*<br/>
Určuje souřadnici y bodu.

## <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#37](../../mfc/codesnippet/cpp/point-structure1_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** windef.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPoint – třída](../../atl-mfc-shared/reference/cpoint-class.md)
