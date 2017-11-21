---
title: "_status87 – _statusfp –, _statusfp2 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5ea17630a79d91dcc0d6f9ce7fa3bd797159f528
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="status87-statusfp-statusfp2"></a>_status87, _statusfp, _statusfp2
Získá s plovoucí desetinnou čárkou stavového slova.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned int _status87( void );  
unsigned int _statusfp( void );  
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)  
```  
  
#### <a name="parameters"></a>Parametry  
 `px86`  
 Tato adresa je vyplněn stavového slova pro x87 jednotku s plovoucí desetinnou čárkou.  
  
 `pSSE2`  
 Tato adresa je vyplněn stavového slova pro jednotku SSE2 s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pro `_status87` a `_statusfp`, bity v hodnotě, která je vrácena označují stav s plovoucí desetinnou čárkou. Najdete v článku FLOAT. H zahrnují v souboru definice služby bits, které se vrátí pomocí `_statusfp`. Mnoho funkcí knihovny math upravit s plovoucí desetinnou čárkou stavového slova, s vést k neočekávaným výsledkům. Optimalizace můžete změnit pořadí, kombinace a eliminovat s plovoucí desetinnou čárkou operations kolem volání `_status87`, `_statusfp`a související funkce. Použití [/Od (zakázat (ladění))](../../build/reference/od-disable-debug.md) – možnost kompilátoru nebo [fenv_access –](../../preprocessor/fenv-access.md) – Direktiva pragma aby optimalizace, které změní pořadí operací s plovoucí desetinnou čárkou. Návratové hodnoty z `_clearfp` a `_statusfp`a také návratových parametrů `_statusfp2`, jsou spolehlivější Pokud méně s plovoucí desetinnou čárkou operací mezi známé stavy s plovoucí desetinnou čárkou stavového slova.  
  
## <a name="remarks"></a>Poznámky  
 `_statusfp` Funkce získá s plovoucí desetinnou čárkou stavového slova. Stavové slovo je kombinací stav s plovoucí desetinnou čárkou procesoru a další podmínky zjištěný obslužné rutiny výjimek plovoucí desetinné čárky – například přetečení zásobníku s plovoucí desetinnou čárkou a podtečení. Odmaskovaná výjimky jsou zaškrtnutá políčka pro dřív, než se vrátí obsah stavového slova. To znamená, že je volající informováni o čekající na vyřízení výjimky. Na x86 platforem, `_statusfp` vrátí kombinaci x87 a stav SSE2 s plovoucí desetinnou čárkou. Na x64 platforem, stav, který je vrácen je na základě SSE MXCSR stavu. Na platformách ARM `_statusfp` vrátí stav z registru FPSCR.  
  
 `_statusfp`je nezávislé na platformě, přenosné verze `_status87`. Je stejný jako `_status87` na platformách Intel (x86) a také podporuje x64 a ARM platformy. K zajištění, že váš kód s plovoucí desetinnou čárkou je přenosný na všechny architektury, použijte `_statusfp`. Pokud cílíte pouze x86 platformy, můžete použít buď `_status87` nebo `_statusfp`.  
  
 Doporučujeme, abyste `_statusfp2` pro čipy (například Pentium IV), kteří mají x87 a procesor SSE2 s plovoucí desetinnou čárkou. Pro `_statusfp2`, adresy jsou vyplněny v aplikaci word s plovoucí desetinnou čárkou stav x87 nebo SSE2 procesor s plovoucí desetinnou čárkou. Čip TPM podporující x87 a SSE2 s plovoucí desetinnou čárkou procesory, EM_AMBIGUOUS je nastavena na 1 v případě `_statusfp` nebo `_controlfp` se používá a akce se nejednoznačné, protože může odkazovat x87 nebo SSE2 s plovoucí desetinnou čárkou stavového slova. `_statusfp2` Funkce je podporována pouze na x86 platformy.  
  
 Tyto funkce nejsou vhodné pro [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) protože modul CLR (CLR) podporuje pouze výchozí přesnost s plovoucí desetinnou čárkou.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_status87`, `_statusfp`, `_statusfp2`|\<float.h – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [_clear87 –, _clearfp –](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)