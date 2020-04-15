---
title: _cabs
ms.date: 4/2/2020
api_name:
- _cabs
- _o__cabs
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: e77e1811cb6f002c06e514b5f737b8a92ea84282
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333682"
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

*Z*<br/>
Komplexní číslo.

## <a name="return-value"></a>Návratová hodnota

**_cabs** vrátí absolutní hodnotu argumentu, pokud je úspěšná. Při přetečení **vrátí _cabs** **HUGE_VAL** a nastaví **errno** na **ERANGE**. Pomocí [_matherr](matherr.md)můžete změnit zpracování chyb .

## <a name="remarks"></a>Poznámky

Funkce **_cabs** vypočítá absolutní hodnotu komplexního čísla, které musí být strukturou typu [_complex](../../c-runtime-library/standard-types.md). Struktura *z* se skládá ze skutečné složky *x* a imaginární složky *y*. Volání **_cabs** vytvoří hodnotu ekvivalentní hodnotě `sqrt( z.x * z.x + z.y * z.y )`výrazu .

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cabs**|\<math.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)
