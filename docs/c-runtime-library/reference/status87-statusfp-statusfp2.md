---
title: _status87, _statusfp, _statusfp2
ms.date: 04/05/2018
api_name:
- _statusfp2
- _statusfp
- _status87
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
- _statusfp2
- _statusfp
- statusfp2
- _status87
- status87
- statusfp
helpviewer_keywords:
- floating-point functions, getting status word
- floating-point numbers, status word
- status87 function
- status word, getting floating point
- statusfp function
- _statusfp function
- _statusfp2 function
- statusfp2 function
- _status87 function
- floating-point functions
- status word
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
ms.openlocfilehash: 54faf70296ef41f2682f88a8edaa82ee0d2071d4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958095"
---
# <a name="_status87-_statusfp-_statusfp2"></a>_status87, _statusfp, _statusfp2

Získá stavové slovo s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _status87( void );
unsigned int _statusfp( void );
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)
```

### <a name="parameters"></a>Parametry

*px86*<br/>
Tato adresa je vyplněna stavovým slovem pro jednotku s plovoucí desetinnou čárkou x87.

*pSSE2*<br/>
Tato adresa je vyplněna stavovým slovem pro jednotku s plovoucí desetinnou čárkou SSE2.

## <a name="return-value"></a>Návratová hodnota

V případě **_status87** a **_statusfp**počet bitů v hodnotě, která je vrácena, indikuje stav s plovoucí desetinnou čárkou. Viz FLOAT. Soubor vložených souborů H pro definici bitů vrácených funkcí **_statusfp**. Řada funkcí matematické knihovny upraví stavové slovo s plovoucí desetinnou čárkou, které má nepředvídatelné výsledky. Optimalizace může přeuspořádat, zkombinovat a eliminovat operace s plovoucí desetinnou čárkou kolem volání do **_status87**, **_statusfp**a souvisejících funkcí. Použijte možnost kompilátoru [/od (Disable (Ladit))](../../build/reference/od-disable-debug.md) nebo direktivu pragma [fenv_access](../../preprocessor/fenv-access.md) , abyste zabránili optimalizacím, které změní pořadí operací s plovoucí desetinnou čárkou. Návratové hodnoty z hodnot **_clearfp** a **_statusfp**a také návratové parametry **_statusfp2**jsou spolehlivější, pokud se mezi známými stavy v případě stavového slova s plovoucí desetinnou čárkou provádí méně operací s plovoucí desetinnou čárkou.

## <a name="remarks"></a>Poznámky

Funkce **_statusfp** získá stavové slovo s plovoucí desetinnou čárkou. Stavové slovo je kombinací stavu procesoru s plovoucí desetinnou čárkou a dalších podmínek zjištěných obslužnou rutinou výjimky s plovoucí desetinnou čárkou, například přetečení a podtečení zásobníku s plovoucí desetinnou čárkou. Nemaskované výjimky jsou kontrolovány před tím, než se vrátí obsah stavového slova. To znamená, že volající je informován o nevyřízených výjimkách. Na platformách x86 **_statusfp** vrátí kombinaci stavu s plovoucí desetinnou čárkou X87 a SSE2. Na platformách x64 je vrácený stav založený na stavu MXCSR SSE. Na platformách ARM vrátí **_statusfp** stav z registru FPSCR.

**_statusfp** je přenosná verze **_status87**, která je nezávislá na platformě. Je stejný jako **_status87** na platformách Intel (x86) a podporuje je i platformy x64 a ARM. Chcete-li zajistit, aby byl kód s plovoucí desetinnou čárkou přenosný pro všechny architektury, použijte **_statusfp**. Pokud cílíte jenom na platformy x86, můžete použít buď **_status87** nebo **_statusfp**.

Doporučujeme **_statusfp2** pro čipy (jako je procesor Pentium IV), které mají procesor X87 a SSE2 s plovoucí desetinnou čárkou. Pro **_statusfp2**se adresy vyplní pomocí stavového slova s plovoucí desetinnou čárkou pro procesor X87 nebo SSE2 s plovoucí desetinnou čárkou. U čipu, který podporuje procesory s plovoucí desetinnou čárkou x87 a SSE2, je EM_AMBIGUOUS nastaveno na hodnotu 1, pokud je použit **_statusfp** nebo **_controlfp** a tato akce byla dvojznačná, protože by mohla odkazovat na stavové slovo x87 nebo SSE2 s plovoucí desetinnou čárkou. Funkce **_statusfp2** je podporována pouze na platformách x86.

Tyto funkce nejsou užitečné pro [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) , protože modul CLR (Common Language Runtime) podporuje pouze výchozí přesnost s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_status87**, **_statusfp**, **_statusfp2**|\<float. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_statusfp.c
// Build by using: cl /W4 /Ox /nologo crt_statusfp.c
// This program creates various floating-point errors and
// then uses _statusfp to display messages that indicate these problems.

#include <stdio.h>
#include <float.h>
#pragma fenv_access(on)

double test( void )
{
   double a = 1e-40;
   float b;
   double c;

   printf("Status = 0x%.8x - clear\n", _statusfp());

   // Assignment into b is inexact & underflows:
   b = (float)(a + 1e-40);
   printf("Status = 0x%.8x - inexact, underflow\n", _statusfp());

   // c is denormal:
   c = b / 2.0;
   printf("Status = 0x%.8x - inexact, underflow, denormal\n",
            _statusfp());

   // Clear floating point status:
   _clearfp();
   return c;
}

int main(void)
{
   return (int)test();
}
```

```Output
Status = 0x00000000 - clear
Status = 0x00000003 - inexact, underflow
Status = 0x00080003 - inexact, underflow, denormal
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
