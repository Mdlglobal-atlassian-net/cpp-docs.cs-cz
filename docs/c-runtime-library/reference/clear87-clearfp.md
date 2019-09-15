---
title: _clear87, _clearfp
ms.date: 04/05/2018
api_name:
- _clearfp
- _clear87
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 4ca49895b881d9e307c1116681bc36f86b167c25
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942959"
---
# <a name="_clear87-_clearfp"></a>_clear87, _clearfp

Získá a smaže stavové slovo s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>Návratová hodnota

Bity v vrácené hodnotě označují stav s plovoucí desetinnou čárkou před voláním **_clear87** nebo **_clearfp**. Úplnou definici bitů vrácených funkcí **_clear87**naleznete v float. h. Mnohé z funkcí matematické knihovny upravují stavové slovo 8087/80287, které má nepředvídatelné výsledky. Návratové hodnoty z **_clear87** a **_status87** se stanou spolehlivější, protože mezi známými stavy pro stavové slovo s plovoucí desetinnou čárkou se provádí méně operací s plovoucí desetinnou čárkou.

## <a name="remarks"></a>Poznámky

Funkce **_clear87** vymaže příznaky výjimky ve stavovém slově s plovoucí desetinnou čárkou, nastaví bit Busy na 0 a vrátí stavové slovo. Stavové slovo s plovoucí desetinnou čárkou je kombinace stavového slova 8087/80287 a další podmínky zjištěné obslužnou rutinou výjimky 8087/80287, jako je přetečení a podtečení zásobníku s plovoucí desetinnou čárkou.

**_clearfp** je přenosná verze rutiny **_clear87** , která je nezávislá na platformě. Je stejný jako **_clear87** na platformách Intel (x86) a podporuje je i platformy x64 a ARM. Chcete-li zajistit, aby byl kód s plovoucí desetinnou čárkou přenosný do x64 a ARM, použijte **_clearfp**. Pokud cílíte jenom na platformy x86, můžete použít buď **_clear87** nebo **_clearfp**.

Tyto funkce jsou při kompilaci s možností [/CLR (modul CLR (Common Language Runtime Compilation) zastaralé)](../../build/reference/clr-common-language-runtime-compilation.md) , protože modul CLR (Common Language Runtime) podporuje pouze výchozí přesnost s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_clear87**|\<float. h >|
|**_clearfp**|\<float. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
