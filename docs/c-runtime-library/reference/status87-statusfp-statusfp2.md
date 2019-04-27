---
title: _status87, _statusfp, _statusfp2
ms.date: 04/05/2018
apiname:
- _statusfp2
- _statusfp
- _status87
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
ms.openlocfilehash: 271c28dd4e267e5b3b702858cc398689e3e35d6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62354428"
---
# <a name="status87-statusfp-statusfp2"></a>_status87, _statusfp, _statusfp2

Získá slovo stav s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
unsigned int _status87( void );
unsigned int _statusfp( void );
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)
```

### <a name="parameters"></a>Parametry

*px86*<br/>
Tato adresa je vyplněna stavovým slovem pro x87 jednotku s plovoucí desetinnou čárkou.

*pSSE2*<br/>
Tato adresa je vyplněna stavovým slovem pro jednotku s plovoucí desetinnou čárkou SSE2.

## <a name="return-value"></a>Návratová hodnota

Pro **_status87 –** a **_statusfp –**, bity ve vrácené hodnotě označují stav s plovoucí desetinnou čárkou. Podívejte se FLOAT. H zahrnout soubor pro definici bitů, které jsou vrácené **_statusfp –**. Mnoho matematických knihovních funkcí upravuje s plovoucí desetinnou čárkou stavového slova s nepředvídatelnými výsledky. Optimalizace můžete změnit pořadí, kombinovat a eliminovat operací s plovoucí desetinnou čárkou kolem volání **_status87 –**, **_statusfp –** a související funkce. Použití [/Od (zakázat (ladění))](../../build/reference/od-disable-debug.md) – možnost kompilátoru nebo [fenv_access](../../preprocessor/fenv-access.md) – Direktiva pragma zabránit optimalizace, které změnit pořadí operací s plovoucí desetinnou čárkou. Návratové hodnoty z **_clearfp –** a **_statusfp –** a také vrácené parametry **_statusfp2 –**, jsou spolehlivější, pokud se provádí méně operací s plovoucí desetinnou čárkou mezi známými stavy slovo stav s plovoucí desetinnou čárkou.

## <a name="remarks"></a>Poznámky

**_Statusfp –** funkce získá slovo stav s plovoucí desetinnou čárkou. Stavové slovo je kombinací stav procesoru s plovoucí desetinnou čárkou a dalších podmínek zjištěných obslužnou rutinou výjimky s plovoucí desetinnou čárkou, například s plovoucí desetinnou čárkou přetečení a podtečení zásobníku. Nemaskované výjimky jsou kontrolovány před vrácením obsahu stavového slova jsou vráceny. To znamená, že volající je informován o čekajících výjimkách. Na x86 platformy, **_statusfp –** vrací kombinaci x87 a stav s plovoucí desetinnou čárkou SSE2. Na x64 platformy, který je vrácen stav je založen na stavu MXCSR SSE. Na platformách ARM **_statusfp –** vrátí stav z registru fpscr.

**_statusfp –** je platformě nezávislá, přenosná verze **_status87 –**. Je stejný jako **_status87 –** na platformách Intel (x86) a je také podporována x64 a ARM platformy. Chcete-li zajistit, že váš kód s plovoucí desetinnou čárkou je přenosný na všechny architektury, použijte **_statusfp –**. Pokud cílíte pouze x86 platformy, můžete použít buď **_status87 –** nebo **_statusfp –**.

Doporučujeme **_statusfp2 –** pro čipy (například Pentium IV), které mají x87 a procesor s plovoucí desetinnou čárkou SSE2. Pro **_statusfp2 –**, jsou adresy vyplněny pomocí slovo stav s plovoucí desetinnou čárkou x87 nebo procesor s plovoucí desetinnou čárkou SSE2. Pro čip, který podporuje x87 a procesory s plovoucí desetinnou čárkou SSE2, je EM_AMBIGUOUS nastavena na 1, pokud **_statusfp –** nebo **_controlfp** se používá a akce byla nejednoznačná, protože by mohla odkazovat x87 nebo SSE2 slovo stav s plovoucí desetinnou čárkou. **_Statusfp2 –** funkce je podporována pouze na x86 platformy.

Tyto funkce nejsou vhodné pro [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) protože common language runtime (CLR) podporuje pouze základní přesnost s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_status87**, **_statusfp**, **_statusfp2**|\<float.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
