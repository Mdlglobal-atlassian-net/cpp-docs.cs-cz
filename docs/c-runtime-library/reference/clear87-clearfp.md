---
title: _clear87, _clearfp
ms.date: 04/05/2018
apiname:
- _clearfp
- _clear87
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clearfp
- _clearfp
- _clear87
- clear87
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
ms.openlocfilehash: 4148f85d82a4210033686455c73046081832e3c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477256"
---
# <a name="clear87-clearfp"></a>_clear87, _clearfp

Načte a vymaže slovo stav s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>Návratová hodnota

Bity v hodnotě vrácené označují stav s plovoucí desetinnou čárkou před voláním **_clear87 –** nebo **_clearfp –**. Kompletní definici bitů, vrácený **_clear87 –**, naleznete v Float.h. Mnoho matematických knihovních funkcí upravit 8087/80287 stavového slova, může mít nepředvídatelné výsledky. Návratové hodnoty z **_clear87 –** a **_status87 –** stát spolehlivější, jak se provádí méně operací s plovoucí desetinnou čárkou mezi známými stavy slovo stav s plovoucí desetinnou čárkou.

## <a name="remarks"></a>Poznámky

**_Clear87 –** funkce vymaže příznaky výjimky klíčové slovo stav s plovoucí desetinnou čárkou, nastaví zaneprázdněný bit na hodnotu 0 a vrátí stavového slova. S plovoucí desetinnou čárkou stavové slovo je kombinací 8087/80287 stavového slova a dalších podmínek zjištěných obslužnou rutinou výjimky 8087/80287, jako je například přetečení a podtečení zásobníku s plovoucí desetinnou čárkou.

**_clearfp –** je platformě nezávislá, přenosná verze **_clear87 –** rutiny. Je stejný jako **_clear87 –** na platformách Intel (x86) a je také podporována x64 a ARM platformy. Chcete-li zajistit, že váš kód s plovoucí desetinnou čárkou je přenosný na x64 a ARM, použijte **_clearfp –**. Pokud cílíte pouze x86 platformy, můžete použít buď **_clear87 –** nebo **_clearfp –**.

Tyto funkce jsou zastaralé při kompilaci s [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) protože modul CLR podporuje pouze základní přesnost s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_clear87**|\<float.h >|
|**_clearfp**|\<float.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_clear87.c
// compile with: /Od

// This program creates various floating-point
// problems, then uses _clear87 to report on these problems.
// Compile this program with Optimizations disabled (/Od).
// Otherwise the optimizer will remove the code associated with
// the unused floating-point values.
//

#include <stdio.h>
#include <float.h>

int main( void )
{
   double a = 1e-40, b;
   float x, y;

   printf( "Status: %.4x - clear\n", _clear87()  );

   // Store into y is inexact and underflows:
   y = a;
   printf( "Status: %.4x - inexact, underflow\n", _clear87() );

   // y is denormal:
   b = y;
   printf( "Status: %.4x - denormal\n", _clear87() );
}
```

```Output
Status: 0000 - clear
Status: 0003 - inexact, underflow
Status: 80000 - denormal
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_control87 – _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
