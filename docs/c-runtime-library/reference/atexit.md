---
title: AtExit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: atexit
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
apitype: DLLExport
f1_keywords: atexit
dev_langs: C++
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8e812f39041287d17ee87766f6971d299654f0f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atexit"></a>atexit
Zpracuje zadané funkci na konec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int atexit(  
   void (__cdecl *func )( void )  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `func`  
 Funkce, která se má volat.  
  
## <a name="return-value"></a>Návratová hodnota  
 `atexit`Vrátí hodnotu 0, pokud bylo úspěšné, nebo obsahuje nenulovou hodnotu, pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 `atexit` Funkce je předán na adresu funkce (`func`) se volá, když se program ukončí normálně. Následná volání `atexit` vytvořit registrace funkcí, které jsou spouštěny v pořadí ven (LIFO) last-in. Funkce předaný `atexit` nepřijímají parametry. `atexit`a `_onexit` použít halda pro uložení registrace funkcí. Proto počet funkcí, které lze registrovat je omezena pouze halda paměti.  
  
 Kód `atexit` funkce nesmí obsahovat žádné závislost na všechny knihovny DLL, které by mohly mít již zrušeno při `atexit` funkce je volána.  
  
 Chcete-li vygenerovat ANSI kompatibilní aplikace, použijte standardu ANSI `atexit` – funkce (místo podobné `_onexit` funkce).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`atexit`|\<stdlib.h >|  
  
## <a name="example"></a>Příklad  
 Tento program nabízených oznámení čtyři funkce do zásobníku funkcí při spouštění `atexit` je volána. Při ukončení programu, tyto programy jsou spouštěny na poslední, nejprve se základ.  
  
```  
// crt_atexit.c  
#include <stdlib.h>  
#include <stdio.h>  
  
void fn1( void ), fn2( void ), fn3( void ), fn4( void );  
  
int main( void )  
{  
   atexit( fn1 );  
   atexit( fn2 );  
   atexit( fn3 );  
   atexit( fn4 );  
   printf( "This is executed first.\n" );  
}  
  
void fn1()  
{  
   printf( "next.\n" );  
}  
  
void fn2()  
{  
   printf( "executed " );  
}  
  
void fn3()  
{  
   printf( "is " );  
}  
  
void fn4()  
{  
   printf( "This " );  
}  
```  
  
```Output  
This is executed first.  
This is executed next.  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [ukončení, _exit –, _exit –](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)