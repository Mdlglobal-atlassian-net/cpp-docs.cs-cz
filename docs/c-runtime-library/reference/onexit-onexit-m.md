---
title: "_onexit –, _onexit_m – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _onexit
- _onexit_m
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
f1_keywords:
- _onexit
- onexit_m
- onexit
- _onexit_m
dev_langs: C++
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9b376efd87c6ab38f87acea71082fd5bf6bd38b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="onexit-onexitm"></a>_onexit, _onexit_m
Zaregistruje rutinu, která má být volána v době ukončení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_onexit_t _onexit(  
   _onexit_t function  
);  
_onexit_t_m _onexit_m(  
   _onexit_t_m function  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `function`  
 Ukazatel na funkci, která se má volat při ukončení.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_onexit`vrací ukazatel na funkci, pokud bylo úspěšné nebo `NULL` Pokud není místa k uložení ukazatel na funkci.  
  
## <a name="remarks"></a>Poznámky  
 `_onexit` Funkce je předán na adresu funkce (`function`) se volá, když se program ukončí normálně. Následná volání `_onexit` vytvořit registrace funkcí, které jsou spouštěny v pořadí LIFO (last-in-first-out). Funkce předaný `_onexit` nepřijímají parametry.  
  
 V případě, že když `_onexit` je volána v rámci knihovny DLL, rutiny zaregistrována `_onexit` spustit na knihovny DLL je uvolnění po `DllMain` je volán s DLL_PROCESS_DETACH.  
  
 `_onexit`představuje rozšíření Microsoft. Přenositelnost ANSI použít [atexit](../../c-runtime-library/reference/atexit.md). `_onexit_m` Verze funkce je pro použití ve smíšeném režimu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_onexit`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_onexit.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
/* Prototypes */  
int fn1(void), fn2(void), fn3(void), fn4 (void);  
  
int main( void )  
{  
   _onexit( fn1 );  
   _onexit( fn2 );  
   _onexit( fn3 );  
   _onexit( fn4 );  
   printf( "This is executed first.\n" );  
}  
  
int fn1()  
{  
   printf( "next.\n" );  
   return 0;  
}  
  
int fn2()  
{  
   printf( "executed " );  
   return 0;  
}  
  
int fn3()  
{  
   printf( "is " );  
   return 0;  
}  
  
int fn4()  
{  
   printf( "This " );  
   return 0;  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
This is executed first.  
This is executed next.  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [AtExit](../../c-runtime-library/reference/atexit.md)   
 [ukončení, _exit –, _exit –](../../c-runtime-library/reference/exit-exit-exit.md)   
 [__dllonexit](../../c-runtime-library/dllonexit.md)