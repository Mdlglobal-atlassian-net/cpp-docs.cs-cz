---
title: _swab
ms.date: 11/04/2016
apiname:
- _swab
- stdlib/_swab
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: 64753383bcb94947e6b413b5f55ac6e2d9c7dbca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245502"
---
# <a name="swab"></a>_swab

Záměna bajtů.

## <a name="syntax"></a>Syntaxe

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>Parametry

*src*<br/>
Zkopírovat a dat prohodit.

*dest*<br/>
Umístění úložiště pro byl prohozen. data.

*n*<br/>
Počet bajtů, které mají být zkopírovány a prohodit.

## <a name="return-value"></a>Návratová hodnota

**Swab –** funkce nevrací hodnotu. Funkce sady **errno** k **EINVAL** Pokud buď *src* nebo *dest* ukazatele má hodnotu null nebo *n* menší než nula a neplatný parametr je vyvolána obslužná rutina, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o tomto a dalších návratových kódech.

## <a name="remarks"></a>Poznámky

Pokud *n* je sudé, **_swab –** funkce kopie *n* bajtů z *src*zaměňuje každý pár sousední bajtů a uloží výsledek v *dest*. Pokud *n* je liché, **_swab –** zkopíruje a zamění první *n*-1 bajtů *src*, a poslední bajt není zkopírován. **_Swab –** funkce se obvykle používá k připravte binární data pro přenos na počítač, který se používá pořadím různých bajtů.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_swab**|C: \<stdlib.h > C++: \<cstdlib – > nebo \<stdlib.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_swab.c

#include <stdlib.h>
#include <stdio.h>

char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";
char to[] =   "...........................";

int main()
{
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);
    _swab(from, to, sizeof(from));
    printf("After:  %s\n        %s\n\n", from, to);
}
```

```Output
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes
        ...........................

After:  BADCFEHGJILKNMPORQTSVUXWZY
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.
```

## <a name="see-also"></a>Viz také:

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
