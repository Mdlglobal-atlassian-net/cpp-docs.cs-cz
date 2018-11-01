---
title: _set_errno
ms.date: 11/04/2016
apiname:
- _set_errno
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_errno
- _set_errno
helpviewer_keywords:
- errno global variable
- set_errno function
- _set_errno function
ms.assetid: d338914a-1894-4cf3-ae45-f2c4eb26590b
ms.openlocfilehash: 42a60875d4ab701c05b8bc12f8d4afb77852e3a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452143"
---
# <a name="seterrno"></a>_set_errno

Nastavte hodnotu **errno** globální proměnné.

## <a name="syntax"></a>Syntaxe

```C
errno_t _set_errno( int error_value );
```

### <a name="parameters"></a>Parametry

*error_value*<br/>
Nová hodnota **errno**.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu vrátí hodnotu.

## <a name="remarks"></a>Poznámky

Možné hodnoty jsou definovány v Errno.h. Viz také [errno – konstanty](../../c-runtime-library/errno-constants.md).

## <a name="example"></a>Příklad

```C
// crt_set_errno.c
#include <stdio.h>
#include <errno.h>

int main()
{
   _set_errno( EILSEQ );
   perror( "Oops" );
}
```

```Output
Oops: Illegal byte sequence
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_set_errno**|\<stdlib.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_get_errno](get-errno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
