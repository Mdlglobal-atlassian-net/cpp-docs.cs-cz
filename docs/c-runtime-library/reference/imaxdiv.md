---
title: imaxdiv
ms.date: 04/05/2018
api_name:
- imaxdiv
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
- imaxdiv
helpviewer_keywords:
- imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
ms.openlocfilehash: 72bbb1198b79d79bb81acc35ce6c2a836fdd5f1d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954637"
---
# <a name="imaxdiv"></a>imaxdiv

Vypočítá podíl a zbytek dvou celočíselných hodnot libovolné velikosti v rámci jedné operace.

## <a name="syntax"></a>Syntaxe

```C
imaxdiv_t imaxdiv(
   intmax_t numer,
   intmax_t denom
);
```

### <a name="parameters"></a>Parametry

*numer*<br/>
Čitatel.

*denom*<br/>
Jmenovatel.

## <a name="return-value"></a>Návratová hodnota

**imaxdiv** volaná s argumenty typu [intmax_t](../../c-runtime-library/standard-types.md) vrátí strukturu typu [imaxdiv_t](../../c-runtime-library/standard-types.md) , která zahrnuje podíl a zbytek.

## <a name="remarks"></a>Poznámky

Funkce **imaxdiv** rozdělí *numer* na *denom* , a tím vypočítá podíl a zbytek. Struktura **imaxdiv_t** obsahuje podíl, **intmax_t** **quot**a zbytek **intmax_t** **Zbýv**. Znaménko podílu je stejné jako u matematického podílu. Jeho absolutní hodnota je největší celé číslo, které je menší než absolutní hodnota matematického podílu. Pokud je jmenovatel 0, program se ukončí s chybovou zprávou.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**imaxdiv**|\<inttypes.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_imaxdiv.c
// Build using: cl /W3 /Tc crt_imaxdiv.c
// This example takes two integers as command-line
// arguments and calls imaxdiv to divide the first
// argument by the second, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x,y;
   imaxdiv_t div_result;

   x = atoll(argv[1]);
   y = atoll(argv[2]);

   printf("The call to imaxdiv(%lld, %lld)\n", x, y);
   div_result = imaxdiv(x, y);
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",
          div_result.quot, div_result.rem);
}
```

Při sestavování a následně volání s parametry příkazového řádku pro `9460730470000000 8766`kód generuje tento výstup:

```Output
The call to imaxdiv(9460730470000000, 8766)
results in a quotient of 1079252848505, and a remainder of 5170
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[div](div.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
