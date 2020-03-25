---
title: _cabs
ms.date: 11/04/2016
api_name:
- _cabs
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cabs
helpviewer_keywords:
- cabs function
- absolute values
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: 2c2bd6b3f097095514e47b757306b4d83a990e45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170338"
---
# <a name="_cabs"></a>_cabs

Vypočítá absolutní hodnotu komplexního čísla.

## <a name="syntax"></a>Syntaxe

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>Parametry

*od*<br/>
Komplexní číslo.

## <a name="return-value"></a>Návratová hodnota

**_cabs** vrátí absolutní hodnotu svého argumentu, pokud je úspěšná. Při přetečení **_cabs** vrátí **HUGE_VAL** a nastaví **errno** na **ERANGE**. Můžete změnit zpracování chyb pomocí [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Funkce **_cabs** vypočítá absolutní hodnotu komplexního čísla, které musí být strukturou typu [_complex](../../c-runtime-library/standard-types.md). Struktura *z* se skládá z reálné komponenty *x* a imaginární komponenty *y*. Volání **_cabs** vytvoří hodnotu ekvivalentní `sqrt( z.x * z.x + z.y * z.y )`výrazu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cabs**|\<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)
