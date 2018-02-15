---
title: "_malloca – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _malloca
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
- malloca
- _malloca
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d61874320712e6cef7f783bb1c4fb03f53ac40e9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="malloca"></a>_malloca
Přidělí paměť v zásobníku. Toto je verze [_alloca –](../../c-runtime-library/reference/alloca.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_malloca(   
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `size`  
 Počet bajtů přidělování v zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_malloca` Rutiny vrátí `void` ukazatel na přidělené místa, což záruku, že se vhodně zarovnána pro ukládání jakéhokoli typu objektu. Pokud `size` 0, `_malloca` přiděluje položku s nulovou délkou a vrací neplatný ukazatel na danou položku.  
  
 Pokud nelze přidělit prostor, je vygenerována výjimce přetečení zásobníku. Výjimce přetečení zásobníku není C++ výjimka; je strukturovaného výjimek. Místo použití zpracovávání výjimek v jazyce C++, je nutné použít [strukturované zpracování výjimek](../../cpp/structured-exception-handling-c-cpp.md) (SEH).  
  
## <a name="remarks"></a>Poznámky  
 `_malloca` přiděluje `size` bajtů z zásobník program nebo haldě, pokud je tato žádost překračuje velikost v bajtech poskytují `_ALLOCA_S_THRESHOLD`. Rozdíl mezi `_malloca` a `_alloca` je, že `_alloca` vždy přiděluje v zásobníku, bez ohledu na velikost. Na rozdíl od `_alloca`, který nevyžaduje ani povolit volání `free` uvolnit paměť, takže přiděleno, `_malloca` vyžaduje použití [_freea –](../../c-runtime-library/reference/freea.md) na uvolnění paměti. V režimu ladění `_malloca` vždy přidělí paměť z haldě.  
  
 Existují omezení explicitně volání `_malloca` v obslužné rutiny výjimek (EH). EH rutiny, které běží na procesory x86 – třída fungovat ve vlastním rámečku paměti: jejich vykonávat úkoly v paměti, který není založen na aktuální umístění ukazatele zásobníku nadřazených funkce. Většina běžné implementace patří zpracování (SEH) systému Windows NT strukturovaná výjimek a výrazy klauzule catch C++. Proto explicitně volání `_malloca` v některém z následujících scénářů výsledků v programu selhání při návratu do volání rutiny EH:  
  
-   Výraz filtru výjimek SEH systému Windows NT: `__except` (`_malloca ()` )  
  
-   Obslužná rutina systému Windows NT SEH poslední výjimky: `__finally` {`_malloca ()` }  
  
-   Výraz klauzule catch C++ EH  
  
 Ale `_malloca` je možné volat přímo z v rutiny EH nebo z zadané aplikaci zpětné volání, které volán v jednom ze scénářů EH dříve uvedené.  
  
> [!IMPORTANT]
>  V systému Windows XP Pokud `_malloca` nazývá uvnitř bloku try/catch musí volat [_resetstkoflw –](../../c-runtime-library/reference/resetstkoflw.md) v bloku catch.  
  
 Kromě výše uvedené omezení, při použití [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) možnost `_malloca` nelze použít v `__except` bloky. Další informace najdete v tématu [/CLR – omezení](../../build/reference/clr-restrictions.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_malloca`|\<malloc.h>|  
  
## <a name="example"></a>Příklad  
  
```  
// crt_malloca_simple.c  
#include <stdio.h>  
#include <malloc.h>  
  
void Fn()  
{  
   char * buf = (char *)_malloca( 100 );  
   // do something with buf  
   _freea( buf );  
}  
  
int main()  
{  
   Fn();  
}  
```  
  
## <a name="example"></a>Příklad  
  
```  
// crt_malloca_exception.c  
// This program demonstrates the use of  
// _malloca and trapping any exceptions  
// that may occur.  
  
#include <windows.h>  
#include <stdio.h>  
#include <malloc.h>  
  
int main()  
{  
    int     size;  
    int     numberRead = 0;  
    int     errcode = 0;  
    void    *p = NULL;  
    void    *pMarker = NULL;  
  
    while (numberRead == 0)  
    {  
        printf_s("Enter the number of bytes to allocate "  
                 "using _malloca: ");  
        numberRead = scanf_s("%d", &size);  
    }  
  
    // Do not use try/catch for _malloca,  
    // use __try/__except, since _malloca throws  
    // Structured Exceptions, not C++ exceptions.  
  
    __try  
    {  
        if (size > 0)  
        {  
            p =  _malloca( size );  
        }  
        else  
        {  
            printf_s("Size must be a positive number.");  
        }  
        _freea( p );  
    }  
  
    // Catch any exceptions that may occur.  
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )  
    {  
        printf_s("_malloca failed!\n");  
  
        // If the stack overflows, use this function to restore.  
        errcode = _resetstkoflw();  
        if (errcode)  
        {  
            printf("Could not reset the stack!");  
            _exit(1);  
        }  
    };  
}  
```  
  
## <a name="input"></a>Vstup  
  
```  
1000  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
Enter the number of bytes to allocate using _malloca: 1000  
```  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [calloc –](../../c-runtime-library/reference/calloc.md)   
 [malloc –](../../c-runtime-library/reference/malloc.md)   
 [realloc –](../../c-runtime-library/reference/realloc.md)   
 [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)