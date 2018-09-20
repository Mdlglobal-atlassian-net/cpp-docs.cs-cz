---
title: Abcfloat – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABCFLOAT
dev_langs:
- C++
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a9bbece0773c14a4a8b545bc56209bf682e22c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375408"
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

