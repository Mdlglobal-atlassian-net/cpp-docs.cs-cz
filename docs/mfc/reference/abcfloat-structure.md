---
title: ABCFLOAT – struktura
ms.date: 11/04/2016
f1_keywords:
- ABCFLOAT
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
ms.openlocfilehash: b9e3923e8c70e38fe5efe959db8da43118cc6445
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443654"
---
# <a name="abcfloat-structure"></a>ABCFLOAT – struktura

`ABCFLOAT` Struktura obsahuje A, B a C šířku písma znak.

## <a name="syntax"></a>Syntaxe

```
typedef struct _ABCFLOAT { /* abcf */
    FLOAT abcfA;
    FLOAT abcfB;
    FLOAT abcfC;
} ABCFLOAT;
```

#### <a name="parameters"></a>Parametry

*abcfA*<br/>
Určuje mezery A znaku. Mezery A je vzdálenost k přidání do aktuální pozici před kreslením glyf znaku.

*abcfB*<br/>
Určuje mezery B znaku. Mezery B je šířku části vykresleného glyf znaku.

*abcfC*<br/>
Určuje mezery C znaku. Mezery C je vzdálenost k přidání do aktuální pozici, aby poskytují napravo od glyf znaku prázdný znak.

## <a name="remarks"></a>Poznámky

Šířku A, B a C se měří podél řádku base písma. Přírůstek znak (celková šířka) znak je součtem mezery A, B a C. A nebo pole jazyka C může být záporná hodnota, při označení underhangs nebo přesahu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** wingdi.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

