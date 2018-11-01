---
title: ABC – struktura
ms.date: 11/04/2016
f1_keywords:
- ABC
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
ms.openlocfilehash: f899a84ddbe5ca3ec3abd4dff135a585aa61eaa9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549562"
---
# <a name="abc-structure"></a>ABC – struktura

`ABC` Struktura obsahuje Šířka znaku v písma TrueType.

## <a name="syntax"></a>Syntaxe

```
typedef struct _ABC { /* abc */
    int abcA;
    UINT abcB;
    int abcC;
} ABC;
```

#### <a name="parameters"></a>Parametry

*abcA*<br/>
Určuje mezery A znaku. Mezery A je vzdálenost k přidání do aktuální pozici před kreslením glyf znaku.

*abcB*<br/>
Určuje mezery B znaku. Mezery B je šířku části vykresleného glyf znaku.

*abcC*<br/>
Určuje mezery C znaku. Mezery C je vzdálenost k přidání do aktuální pozici, aby poskytují napravo od glyf znaku prázdný znak.

## <a name="remarks"></a>Poznámky

Celková šířka znaku je součtem mezery A, B a C. A nebo pole jazyka C může být záporná hodnota, při označení underhangs nebo přesahu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** wingdi.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

