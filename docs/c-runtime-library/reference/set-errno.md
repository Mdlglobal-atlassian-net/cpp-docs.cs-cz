---
title: _set_errno
ms.date: 4/2/2020
api_name:
- _set_errno
- _o__set_errno
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: e889f8e2dabfffbcc69ff796fb21570b66b57fb0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913047"
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

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

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
|**_set_errno**|\<Stdlib. h>|\<errno. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_get_errno](get-errno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
