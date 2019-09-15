---
title: _get_timezone
ms.date: 11/04/2016
api_name:
- _get_timezone
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
ms.openlocfilehash: cf77ca21383bcae6919b6c1d00b99c082ef99919
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955638"
---
# <a name="_get_timezone"></a>_get_timezone

Načte rozdíl v sekundách mezi koordinovaným světovým časem (UTC) a místním časem.

## <a name="syntax"></a>Syntaxe

```C
error_t _get_timezone(
    long* seconds
);
```

### <a name="parameters"></a>Parametry

*Second*<br/>
Rozdíl v sekundách mezi časem UTC a místním časem.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu nebo **errno** hodnoty, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Funkce **_get_timezone** načítá rozdíl v sekundách mezi časem UTC a místním časem jako celé číslo. Výchozí hodnota je 28 800 sekund, pro Tichomoří (běžný čas) (osm hodin za časem UTC).

Pokud jsou sekundy **null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_timezone**|\<time.h>|

Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_tzname](get-tzname.md)<br/>
