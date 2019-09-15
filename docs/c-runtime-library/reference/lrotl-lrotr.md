---
title: _lrotl, _lrotr
ms.date: 04/04/2018
api_name:
- _lrotl
- _lrotr
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
- lrotr
- lrotl
- _lrotr
- _lrotl
helpviewer_keywords:
- lrotl function
- bits
- _lrotr function
- lrotr function
- rotating bits
- _lrotl function
- bits, rotating
ms.assetid: d42f295b-35f9-49d2-9ee4-c66896ffe68e
ms.openlocfilehash: ea78aeb8829a80abae345b4e9e6ac3a7bbaddf8b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953033"
---
# <a name="_lrotl-_lrotr"></a>_lrotl, _lrotr

Otočí bity doleva ( **_lrotl**) nebo Right ( **_lrotr**).

## <a name="syntax"></a>Syntaxe

```C
unsigned long _lrotl( unsigned long value, int shift );
unsigned long _lrotr( unsigned long value, int shift );
```

### <a name="parameters"></a>Parametry

*value*<br/>
Hodnota, která se má otočit

*posouvá*<br/>
Počet bitů na posunutí *hodnoty*.

## <a name="return-value"></a>Návratová hodnota

Obě funkce vrací otočenou hodnotu. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Funkce **_lrotl** a **_lrotr** otočí *hodnoty* pomocí *SHIFT* bitů. **_lrotl** otočí hodnotu vlevo a k většímu počtu významných bitů. **_lrotr** otočí hodnotu vpravo směrem k méně významným bitům. Obě funkce zabalí bity za jeden konec *hodnoty* na druhý koncový objekt.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lrotl**, **_lrotr**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_lrot.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   unsigned long val = 0x0fac35791;

   printf( "0x%8.8lx rotated left eight bits is 0x%8.8lx\n",
            val, _lrotl( val, 8 ) );
   printf( "0x%8.8lx rotated right four bits is 0x%8.8lx\n",
            val, _lrotr( val, 4 ) );
}
```

```Output
0xfac35791 rotated left eight bits is 0xc35791fa
0xfac35791 rotated right four bits is 0x1fac3579
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_rotl, _rotl64, _rotr, _rotr64](rotl-rotl64-rotr-rotr64.md)<br/>
