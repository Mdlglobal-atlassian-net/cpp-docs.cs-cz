---
title: _get_errno
ms.date: 11/04/2016
api_name:
- _get_errno
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
- _get_errno
helpviewer_keywords:
- get_errno function
- errno global variable
- _get_errno function
ms.assetid: b3fd5ebc-f41b-4314-a2f4-2f2d79d6e740
ms.openlocfilehash: 4d60f7ea7a36b4a8c4be678d26c0b0c59e5ec534
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955976"
---
# <a name="_get_errno"></a>_get_errno

Získá aktuální hodnotu globální proměnné errno.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_errno(
   int * pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Ukazatel na celé číslo, který má být vyplněn aktuální hodnotou proměnné **errno** .

## <a name="return-value"></a>Návratová hodnota

Vrátí nulu v případě úspěchu; chybový kód při selhání. Pokud má PValue **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Možné hodnoty **errno** jsou definované v errno. h. Podívejte se také na [errno konstanty](../../c-runtime-library/errno-constants.md).

## <a name="example"></a>Příklad

```C
// crt_get_errno.c
#include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <share.h>
#include <errno.h>

int main()
{
   errno_t err;
   int pfh;
   _sopen_s( &pfh, "nonexistent.file", _O_WRONLY, _SH_DENYNO, _S_IWRITE );
   _get_errno( &err );
   printf( "errno = %d\n", err );
   printf( "fyi, ENOENT = %d\n", ENOENT );
}
```

```Output
errno = 2
fyi, ENOENT = 2
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_get_errno**|\<stdlib.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_set_errno](set-errno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
