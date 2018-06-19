---
title: _get_dstbias – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_dstbias
- __dstbias
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
- __dstbias
- _get_dstbias
- get_dstbias
dev_langs:
- C++
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82e334c6fcb282bebb003992219f6cf215ab7437
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397763"
---
# <a name="getdstbias"></a>_get_dstbias

Načte posun na letní čas v sekundách.

## <a name="syntax"></a>Syntaxe

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>Parametry

*Sekund*<br/>
Posun v sekundách letní čas.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu nebo **errno** hodnotu, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

**_Get_dstbias –** funkce načte počtem sekund za letní čas jako celé číslo. Pokud platí letní čas, výchozí posun je 3 600 sekund, což je počet sekund za jednu hodinu (i když několik oblastí sledovat posun dvou hodin).

Pokud *sekund* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **einval –**.

Doporučujeme, abyste tuto funkci použít místo makro **_dstbias** nebo zastaralé funkce **__dstbias**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_dstbias**|\<Time.h >|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Správa času](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
