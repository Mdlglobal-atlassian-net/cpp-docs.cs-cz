---
title: _getmaxstdio
ms.date: 11/04/2016
apiname:
- _getmaxstdio
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getmaxstdio
- getmaxstdio
helpviewer_keywords:
- files [C++], number open
- _getmaxstdio function
- getmaxstdio function
- open files, getting number
ms.assetid: 700ca8ce-4a8c-4e00-9467-dfa9d6b831a0
ms.openlocfilehash: ea8e516b4c0806230376ea52e399c9fa1f9a858a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618335"
---
# <a name="getmaxstdio"></a>_getmaxstdio

Vrátí počet souběžně otevřených souborů je povolená úroveň vstupně-výstupních operací datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int _getmaxstdio( void );
```

## <a name="return-value"></a>Návratová hodnota

Vrací číslo představující počet souběžně otevřených souborů, které jsou aktuálně je povolená **stdio** úroveň.

## <a name="remarks"></a>Poznámky

Použití [_setmaxstdio –](setmaxstdio.md) nakonfigurovat počet souběžně otevřených souborů je povolená **stdio** úroveň.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getmaxstdio**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_setmaxstdio.c
// The program retrieves the maximum number
// of open files and prints the results
// to the console.

#include <stdio.h>

int main()
{
   printf( "%d\n", _getmaxstdio());

   _setmaxstdio(2048);

   printf( "%d\n", _getmaxstdio());
}
```

```Output
512
2048
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
