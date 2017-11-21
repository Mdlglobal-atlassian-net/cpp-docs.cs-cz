---
title: "_alloca – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _alloca
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
- _alloca
- alloca
dev_langs: C++
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6068e1b3e6765b2a409fbc33d1a97b228c82abcd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="alloca"></a>_alloca
Přidělí paměť v zásobníku. Tato funkce je zastaralý, protože bezpečnější verze je k dispozici. v tématu [_malloca –](../../c-runtime-library/reference/malloca.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_alloca(   
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`size`  
 Počet bajtů přidělování v zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_alloca` Rutiny vrátí `void` ukazatel na přidělené místa, což záruku, že se vhodně zarovnána pro ukládání jakéhokoli typu objektu. Pokud `size` 0, `_alloca` přiděluje položku s nulovou délkou a vrací neplatný ukazatel na danou položku.  
  
 Pokud nelze přidělit prostor, je vygenerována výjimce přetečení zásobníku. Výjimce přetečení zásobníku není C++ výjimka; je strukturovaného výjimek. Místo použití zpracovávání výjimek v jazyce C++, je nutné použít [strukturované zpracování výjimek](../../cpp/structured-exception-handling-c-cpp.md) (SEH).  
  
## <a name="remarks"></a>Poznámky  
 `_alloca`přiděluje `size` bajtů z programu zásobníku. Přidělené místo automaticky uvolněno při ukončení volání funkce (není při přidělení předá jenom mimo rozsah). Proto nepředávejte ukazatel hodnoty vrácené `_alloca` jako argument pro [volné](../../c-runtime-library/reference/free.md).  
  
 Existují omezení explicitně volání `_alloca` v obslužné rutiny výjimek (EH). EH rutiny, které běží na procesory x86 – třída fungovat ve vlastním rámečku paměti: jejich vykonávat úkoly v paměti, který není založen na aktuální umístění ukazatele zásobníku nadřazených funkce. Většina běžné implementace patří zpracování (SEH) systému Windows NT strukturovaná výjimek a výrazy klauzule catch C++. Proto explicitně volání `_alloca` v některém z následujících scénářů výsledků v programu selhání při návratu do volání rutiny EH:  
  
-   Výraz filtru výjimek SEH systému Windows NT: `__except` (`_alloca ()` )  
  
-   Obslužná rutina systému Windows NT SEH poslední výjimky: `__finally` {`_alloca ()` }  
  
-   Výraz klauzule catch C++ EH  
  
 Ale `_alloca` je možné volat přímo z v rutiny EH nebo z zadané aplikaci zpětné volání, které volán v jednom ze scénářů EH dříve uvedené.  
  
> [!IMPORTANT]
>  V systému Windows XP Pokud `_alloca` nazývá uvnitř bloku try/catch musí volat [_resetstkoflw –](../../c-runtime-library/reference/resetstkoflw.md) v bloku catch.  
  
 Kromě výše uvedené omezení, při použití[/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) možnost `_alloca` nelze použít v `__except` bloky. Další informace najdete v tématu [/CLR – omezení](../../build/reference/clr-restrictions.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_alloca`|\<malloc.h >|  
  
## <a name="example"></a>Příklad  
  
```  
// crt_alloca.c  
// This program demonstrates the use of  
// _alloca and trapping any exceptions  
// that may occur.  
  
#include <windows.h>  
#include <stdio.h>  
#include <malloc.h>  
  
int main()  
{  
    int     size = 1000;  
    int     errcode = 0;  
    void    *pData = NULL;  
  
    // Note: Do not use try/catch for _alloca,  
    // use __try/__except, since _alloca throws  
    // Structured Exceptions, not C++ exceptions.  
  
    __try {  
        // An unbounded _alloca can easily result in a   
        // stack overflow.  
        // Checking for a size < 1024 bytes is recommended.  
        if (size > 0 && size < 1024)  
        {  
            pData = _alloca( size );  
            printf_s( "Allocated %d bytes of stack at 0x%p",  
                      size, pData);  
        }  
        else  
        {  
            printf_s("Tried to allocate too many bytes.\n");  
        }  
    }  
  
    // If an exception occured with the _alloca function  
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )  
    {  
        printf_s("_alloca failed!\n");  
  
        // If the stack overflows, use this function to restore.  
        errcode = _resetstkoflw();  
        if (errcode)  
        {  
            printf_s("Could not reset the stack!\n");  
            _exit(1);  
        }  
    };  
}  
```  
  
```Output  
Allocated 1000 bytes of stack at 0x0012FB50  
```  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [calloc –](../../c-runtime-library/reference/calloc.md)   
 [malloc –](../../c-runtime-library/reference/malloc.md)   
 [realloc –](../../c-runtime-library/reference/realloc.md)   
 [_resetstkoflw –](../../c-runtime-library/reference/resetstkoflw.md)   
 [_malloca –](../../c-runtime-library/reference/malloca.md)