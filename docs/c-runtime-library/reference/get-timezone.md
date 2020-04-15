---
title: _get_timezone
ms.date: 4/2/2020
api_name:
- _get_timezone
- _o__get_timezone
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_timezone
- get_timezone
helpviewer_keywords:
- time zones
- get_timezone function
- _get_timezone function
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
ms.openlocfilehash: 94dfae1aaaddf9c545af4309d3ddc62a0bcb33f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344909"
---
# <a name="_get_timezone"></a>_get_timezone

Načte rozdíl v sekundách mezi koordinovaným univerzálním časem (UTC) a místním časem.

## <a name="syntax"></a>Syntaxe

```C
error_t _get_timezone(
    long* seconds
);
```

### <a name="parameters"></a>Parametry

*Sekund*<br/>
Rozdíl v sekundách mezi UTC a místním časem.

## <a name="return-value"></a>Návratová hodnota

Nula, pokud je úspěšná, nebo hodnota **errno,** pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Funkce **_get_timezone** načte rozdíl v sekundách mezi časem UTC a místním časem jako celé číslo. Výchozí hodnota je 28 800 sekund pro tichomořský standardní čas (osm hodin za časem UTC).

Pokud je *hodnota 000 000* **000**000 , je vyvolána neplatná obslužná rutina parametru, jak je popsáno v části [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **Funkce EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_timezone**|\<time.h>|

Další informace naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_tzname](get-tzname.md)<br/>
