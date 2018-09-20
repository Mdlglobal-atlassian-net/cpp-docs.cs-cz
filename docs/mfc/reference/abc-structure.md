---
title: ABC – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABC
dev_langs:
- C++
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a977e3f0efd763ee416348f11e3c6b016c0d42e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373709"
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


