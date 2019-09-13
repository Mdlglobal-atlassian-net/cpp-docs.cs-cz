---
title: _set_doserrno
ms.date: 11/04/2016
api_name:
- _set_doserrno
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_doserrno
- set_doserrno
helpviewer_keywords:
- _set_doserrno function
- doserrno global variable
- set_doserrno function
- _doserrno global variable
ms.assetid: 8686c159-3797-4705-a53e-7457869ca6f3
ms.openlocfilehash: e4060992477e5d30dfad0725948cbc719b4d0270
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948620"
---
# <a name="_set_doserrno"></a>_set_doserrno

Nastaví hodnotu globální proměnné [_doserrno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="syntax"></a>Syntaxe

```C
errno_t _set_doserrno( int error_value );
```

### <a name="parameters"></a>Parametry

*error_value*<br/>
Nová hodnota **_doserrno**

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu nula.

## <a name="remarks"></a>Poznámky

Možné hodnoty jsou definovány v errno. h.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_set_doserrno**|\<stdlib.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_get_doserrno](get-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
