---
title: _swab
ms.date: 11/04/2016
api_name:
- _swab
- stdlib/_swab
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
ms.openlocfilehash: b0faba55c42023f4d66adae68de6be2c1ab009a0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946290"
---
# <a name="_swab"></a>_swab

Prohodí bajty.

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
Data, která se mají zkopírovat a zaměnit

*propojovací*<br/>
Umístění úložiště pro zaměněná data.

*n*<br/>
Počet bajtů, které mají být zkopírovány a prohozeny.

## <a name="return-value"></a>Návratová hodnota

Funkce **stěr** nevrací hodnotu. Funkce nastaví **errno** na **EINVAL** , pokud buď má ukazatel *Src* nebo *cíl* hodnotu null nebo *n* je menší než nula, a je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

Další informace o tomto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Pokud *n* je i, funkce **_swab** kopíruje *n* bajtů z *Src*, zahodí každou dvojici sousedících bajtů a výsledek uloží na *cíl*. Pokud *n* je lichá, **_swab** zkopíruje a zamění prvních *n*-1 bajtů *Src*a finální bajt není kopírován. Funkce **_swab** se obvykle používá k přípravě binárních dat pro přenos do počítače, který používá jiné pořadí bajtů.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_swab**|C: \<Stdlib. h > C++: \<cstdlib > nebo \<Stdlib. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
