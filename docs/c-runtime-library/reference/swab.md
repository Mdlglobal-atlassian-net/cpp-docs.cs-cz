---
title: _swab
ms.date: 4/2/2020
api_name:
- _swab
- stdlib/_swab
- _o__swab
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: f7fe23cd9c1b2eab52ebe50904d0bb18fe16cea6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362955"
---
# <a name="_swab"></a>_swab

Swapy bajtů.

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
Data, která mají být zkopírována a vyměněna.

*Dest*<br/>
Úložiště pro zaměněná data.

*N*<br/>
Počet bajtů, které mají být zkopírovány a proměněny.

## <a name="return-value"></a>Návratová hodnota

Funkce **tamponu** nevrátí hodnotu. Funkce nastaví **errno** na **EINVAL,** pokud je ukazatel *src* nebo *dest* null nebo *n* je menší než nula a je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md).

Další informace o tomto a dalších návratových kódech naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

Pokud *n* je sudý, **_swab** funkce zkopíruje *n* bajtů z *src*, zamění každý pár sousedních bajtů a uloží výsledek na *dest*. Pokud *n* je lichý, **_swab** zkopíruje a zamění první *n*-1 bajty *src*a konečný bajt není zkopírován. Funkce **_swab** se obvykle používá k přípravě binárních dat pro přenos do počítače, který používá jiné pořadí bajtů.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_swab**|C: \<stdlib.h> C++: \<cstdlib> nebo \<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Manipulace s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
