---
title: FILETIME – struktura
ms.date: 11/04/2016
f1_keywords:
- FILETIME
helpviewer_keywords:
- FILETIME structure [MFC]
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
ms.openlocfilehash: f70792b83637018e707b6ee48d1b169f28d46d71
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514930"
---
# <a name="filetime-structure"></a>FILETIME – struktura

`FILETIME` Struktura je 64bitová hodnota reprezentující počet 100nanosekundových intervalů o délce od 1. ledna 1601.

## <a name="syntax"></a>Syntaxe

```
typedef struct _FILETIME {
    DWORD dwLowDateTime;   /* low 32 bits */
    DWORD dwHighDateTime;  /* high 32 bits */
} FILETIME, *PFILETIME, *LPFILETIME;
```

#### <a name="parameters"></a>Parametry

*dwLowDateTime*<br/>
Určuje nízkou 32 bity čas souboru.

*dwHighDateTime*<br/>
Určuje vysoké 32 bity čas souboru.

## <a name="requirements"></a>Požadavky

**Záhlaví:** windef.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

