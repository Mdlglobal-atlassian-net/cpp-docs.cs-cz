---
title: div, ldiv –, lldiv – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- div
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
- div
dev_langs:
- C++
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3a0e28030b62f68d478cb976b1f89d91904655a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="div-ldiv-lldiv"></a>div, ldiv –, lldiv –

Vypočítá podílu a zbývající dva celočíselné hodnoty.

## <a name="syntax"></a>Syntaxe

```C
div_t div(
   int numer,
   int denom
);
ldiv_t ldiv(
   long numer,
   long denom
);
lldiv_t lldiv(
   long long numer,
   long long denom
);
```

```cpp
ldiv_t div(
   long numer,
   long denom
); /* C++ only */
lldiv_t div(
   long long numer,
   long long denom
); /* C++ only */
```

### <a name="parameters"></a>Parametry

*počet*<br/>
Čítači.

*denom*<br/>
Jmenovatel.

## <a name="return-value"></a>Návratová hodnota

**div** volat pomocí argumenty typu **int** vrací strukturu typu **div_t –**, což zahrnuje podílu a zbytek. Návratová hodnota s argumenty typu **dlouho** je **ldiv_t –**a návratovou hodnotu s argumenty typu **dlouho** **dlouho** je **lldiv_t**. **div_t –**, **ldiv_t –**, a **lldiv_t** jsou definovány v \<stdlib.h >.

## <a name="remarks"></a>Poznámky

**Div** funkce vydělí *kontrolních* podle *denom* a tím vypočítá podílu a zbytek. [Div_t –](../../c-runtime-library/standard-types.md) struktura obsahuje podílu, **potřebná**a zbývající, **rem**. Znaménko podílu je stejný jako u matematickém podílu. Jeho absolutní hodnota je největší číslo typu integer, která je menší než hodnota absolutní matematickém podílu. Pokud jmenovatel hodnotu 0, program se ukončí s chybovou zprávou.

Přetížení **div** které přebírají argumenty typu **dlouho** nebo **dlouho** **dlouho** jsou dostupné jenom pro C++ – kód. Návratové typy [ldiv_t –](../../c-runtime-library/standard-types.md) a [lldiv_t](../../c-runtime-library/standard-types.md) obsahuje členy **potřebná** a **rem**, které mají stejný význam jako členové **div_t –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**div**, **ldiv –**, **lldiv –**|\<stdlib.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_div.c
// arguments: 876 13

// This example takes two integers as command-line
// arguments and displays the results of the integer
// division. This program accepts two arguments on the
// command line following the program name, then calls
// div to divide the first argument by the second.
// Finally, it prints the structure members quot and rem.
//

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main( int argc, char *argv[] )
{
   int x,y;
   div_t div_result;

   x = atoi( argv[1] );
   y = atoi( argv[2] );

   printf( "x is %d, y is %d\n", x, y );
   div_result = div( x, y );
   printf( "The quotient is %d, and the remainder is %d\n",
           div_result.quot, div_result.rem );
}
```

```Output
x is 876, y is 13
The quotient is 67, and the remainder is 5
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
