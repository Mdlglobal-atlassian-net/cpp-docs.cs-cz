---
title: _get_daylight
ms.date: 11/04/2016
api_name:
- __daylight
- _get_daylight
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
- get_daylight
- _get_daylight
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
ms.openlocfilehash: 9f63d3baa1e9411039d1482b4cbfbf4bce4e9872
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956049"
---
# <a name="_get_daylight"></a>_get_daylight

Načte časový posun letního času v hodinách.

## <a name="syntax"></a>Syntaxe

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>Parametry

*hodin*<br/>
Posun v hodinách letního času uložení.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu nebo **errno** hodnoty, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Funkce **_get_daylight** načítá počet hodin v letním čase jako celé číslo. Pokud je aktivní letní čas, je výchozím posunem jedna hodina (i když pár oblastí sleduje posun o dvě hodiny).

Pokud je *počet hodin* **null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

Doporučujeme použít tuto funkci namísto makra **_daylight** nebo zastaralé funkce **__daylight**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_daylight**|\<time.h>|

Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
