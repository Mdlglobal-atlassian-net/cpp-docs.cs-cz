---
title: MINMAXINFO – struktura
ms.date: 11/04/2016
f1_keywords:
- MINMAXINFO
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
ms.openlocfilehash: 11f55b1756623626769e21c006543b6993607b08
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517842"
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

