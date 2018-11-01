---
title: SYSTEMTIME – struktura
ms.date: 11/04/2016
f1_keywords:
- SYSTEMTIME
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
ms.openlocfilehash: b46482a9f4eb0165b72d74cb7d69e96e2a15e953
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559044"
---
# <a name="systemtime-structure"></a>SYSTEMTIME – struktura

`SYSTEMTIME` Struktura představuje datum a čas pomocí jednotlivých členů pro měsíc, den, rok, den v týdnu, hodinu, minutu, sekundu a milisekundu.

## <a name="syntax"></a>Syntaxe

```
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME;
```

#### <a name="parameters"></a>Parametry

*wYear*<br/>
Do aktuálního roku.

*Přechodu*<br/>
Aktuální měsíc. 1 je leden.

*wDayOfWeek*<br/>
Aktuální den v týdnu; 0 je neděle, pondělí je 1 a tak dále.

*wDay*<br/>
Aktuální den v měsíci.

*wHour*<br/>
Aktuální hodinu.

*wMinute*<br/>
Do aktuální minuty.

*wSecond*<br/>
Aktuální sekunda.

*wMilliseconds*<br/>
Aktuální milisekunda.

## <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** winbase.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

