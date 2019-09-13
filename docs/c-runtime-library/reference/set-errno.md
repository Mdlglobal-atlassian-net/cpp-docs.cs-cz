---
title: _set_errno
ms.date: 11/04/2016
api_name:
- _set_errno
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
- set_errno
- _set_errno
helpviewer_keywords:
- errno global variable
- set_errno function
- _set_errno function
ms.assetid: d338914a-1894-4cf3-ae45-f2c4eb26590b
ms.openlocfilehash: 09800276886ecf1c2fdd2ffee63ddcb8cc57f61e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948595"
---
# <a name="_set_errno"></a>_set_errno

Nastavte hodnotu globální proměnné **errno** .

## <a name="syntax"></a>Syntaxe

```C
errno_t _set_errno( int error_value );
```

### <a name="parameters"></a>Parametry

*error_value*<br/>
Nová hodnota **errno**

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu nula.

## <a name="remarks"></a>Poznámky

Možné hodnoty jsou definovány v errno. h. Podívejte se také na [errno konstanty](../../c-runtime-library/errno-constants.md).

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

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_get_errno](get-errno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
