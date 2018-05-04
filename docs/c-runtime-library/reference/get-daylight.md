---
title: _get_daylight – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __daylight
- _get_daylight
apilocation:
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
apitype: DLLExport
f1_keywords:
- get_daylight
- _get_daylight
dev_langs:
- C++
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0fbe7e36db2e5ca5365f43dc23281d9b5e79077d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="getdaylight"></a>_get_daylight

Načte posun na letní čas v hodinách.

## <a name="syntax"></a>Syntaxe

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>Parametry

*Hodiny*<br/>
Posun v hodinách letní čas.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu nebo **errno** hodnotu, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

**_Get_daylight –** funkce načte počtem hodin za letní čas jako celé číslo. Pokud platí letní čas, výchozí posun je jedna hodina (i když několik oblastí sledovat posun dvou hodin).

Pokud *hodin* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **einval –**.

Doporučujeme, abyste tuto funkci použít místo makro **_daylight** nebo zastaralé funkce **__daylight**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_daylight**|\<Time.h >|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Správa času](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
