---
title: Minmaxinfo – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MINMAXINFO
dev_langs:
- C++
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b63589edbe47aa09b8a6be92b5b7eb7e29077c96
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402288"
---
# <a name="minmaxinfo-structure"></a>MINMAXINFO – struktura

`MINMAXINFO` Struktura obsahuje informace o maximální velikosti okna a pozice a jeho sledování minimální a maximální velikost.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagMINMAXINFO {
    POINT ptReserved;
    POINT ptMaxSize;
    POINT ptMaxPosition;
    POINT ptMinTrackSize;
    POINT ptMaxTrackSize;
} MINMAXINFO;
```

#### <a name="parameters"></a>Parametry

*ptReserved*<br/>
Vyhrazeno pro interní použití.

*ptMaxSize*<br/>
Určuje maximální šířku (point.x) a maximální výšku okna (point.y).

*ptMaxPosition*<br/>
Určuje pozici levé straně maximalizované okno (point.x) a pozice horní části okna maximalizované (point.y).

*ptMinTrackSize*<br/>
Určuje minimální šířku (point.x) pro sledování a minimální výšku (point.y) okna pro sledování.

*ptMaxTrackSize*<br/>
Určuje maximální šířku (point.x) pro sledování a maximální výška (point.y) v okně pro sledování.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winuser

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

