---
title: _get_timezone – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_timezone
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
- _get_timezone
- get_timezone
dev_langs:
- C++
helpviewer_keywords:
- time zones
- get_timezone function
- _get_timezone function
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 111cbff00d1f6119fbd806cc5fc3d14c28a7d7c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398273"
---
# <a name="gettimezone"></a>_get_timezone

Načte rozdíl v sekundách mezi místním a koordinovaný světový čas (UTC).

## <a name="syntax"></a>Syntaxe

```C
error_t _get_timezone(
    long* seconds
);
```

### <a name="parameters"></a>Parametry

*Sekund*<br/>
Rozdíl v sekundách mezi místním ČASEM a.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu nebo **errno** hodnotu, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

**_Get_timezone –** funkce načte rozdíl v sekundách mezi místním ČASEM a jako celé číslo. Výchozí hodnota je 28 800 sekund pro Tichomořský běžný čas (8 hodin za čas UTC).

Pokud *sekund* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **einval –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_timezone**|\<Time.h >|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Správa času](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_tzname](get-tzname.md)<br/>
