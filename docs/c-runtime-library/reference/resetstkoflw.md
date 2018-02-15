---
title: "_resetstkoflw – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _resetstkoflw
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
- resetstkoflw
- _resetstkoflw
dev_langs:
- C++
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89a62ddd07f21a89e8b34cb62f1a5e5147d92b06
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="resetstkoflw"></a>_resetstkoflw
Obnoví z přetečení zásobníku.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int _resetstkoflw ( void );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci úspěšné, nula. Pokud se nezdaří.  
  
## <a name="remarks"></a>Poznámky  
 `_resetstkoflw` Funkce obnoví z podmínku přetečení zásobníku, povolení programu pokračovat místo selhání s chybou závažné výjimce. Pokud `_resetstkoflw` funkce není volána, neobsahuje žádné stránky ochrana po předchozí výjimku. Přetečení při příštím se zásobníku, nejsou vůbec žádné výjimky a proces ukončí bez upozornění.  
  
 Pokud způsobí, že vlákno v aplikaci **EXCEPTION_STACK_OVERFLOW** výjimky, vlákno opustil jeho zásobníku v poškozeného stavu. Tím se liší od dalších výjimkách, jako **EXCEPTION_ACCESS_VIOLATION** nebo **EXCEPTION_INT_DIVIDE_BY_ZERO**, kde není poškozený zásobníku. V zásobníku nastavena na hodnotu nahodile malé při prvním načtení programu. V zásobníku se pak zvětšování na vyžádání, aby vyhovovaly vlákno. Tato možnost je implementovaná umístěním stránky s přístupem PAGE_GUARD na konci aktuální zásobníku. Další informace najdete v tématu [vytváření stránek ochrana](http://msdn.microsoft.com/library/windows/desktop/aa366549).  
  
 Když kód způsobí ukazatel zásobníku tak, aby odkazoval na adresu na této stránce, dojde k výjimce a systému provádí následující tři věci:  
  
-   Odebere PAGE_GUARD ochranu na stránce ochrana tak, aby vlákno může číst a zapisovat data do paměti.  
  
-   Přiděluje nový ochranu stránky, který je umístěn jednu stránku níže poslední.  
  
-   Opakovaně pokyn, vyvolá výjimku.  
  
 Tímto způsobem můžete systém zvětšete velikost zásobníku pro vlákno automaticky. Každé vlákno v procesu má zásobník maximální velikost. Velikost zásobníku nastavena v době kompilace pomocí [/STACK (přidělení zásobníku)](../../build/reference/stack-stack-allocations.md), nebo [velikost zásobníku](../../build/reference/stacksize.md) – příkaz souboru .def pro projekt.  
  
 Při překročení této maximální velikost zásobníku systému provádí následující tři věci:  
  
-   Odebere PAGE_GUARD ochranu na stránce ochrana, jak se popisuje výš.  
  
-   Pokusí se přidělit novou stránku ochrana pod poslední. Ale to nezdaří, protože byla překročena maximální velikost zásobníku.  
  
-   Vyvolá výjimku, tak, aby vlákno může zpracovat v bloku výjimky.  
  
 Všimněte si, že v tomto bodě zásobníku už má ochranu stránku. Při příštím, program zvětšování zásobníku úplně za účelem, kde by měla být na stránce ochrana, program zapíše přesahuje za konec zásobníku a způsobí, že porušení přístupu.  
  
 Volání `_resetstkoflw` obnovit ochranná stránka vždy, když obnovení probíhá po výjimce přetečení zásobníku. Tuto funkci lze volat z hlavní část `__except` bloku nebo mimo **__except** bloku. Nicméně existují určitá omezení na Pokud se má použít. `_resetstkoflw` by měla být volána nikdy z:  
  
-   Výraz filtru.  
  
-   Funkce filtru.  
  
-   Funkci nazvanou z funkce filtru.  
  
-   A **catch** bloku.  
  
-   A `__finally` bloku.  
  
 V těchto bodech v zásobníku ještě není dostatečně oddělen.  
  
 Výjimky přetečení zásobníku se generují jako strukturovaný výjimky, není výjimky jazyka C++, takže `_resetstkoflw` není užitečné v běžný **catch** blokovat, protože nezachytí výjimce přetečení zásobníku. Ale pokud [_set_se_translator –](../../c-runtime-library/reference/set-se-translator.md) slouží k implementaci překladač strukturovaného výjimek, který vyvolá výjimky jazyka C++ (jako v druhém příkladu), catch výsledků výjimce přetečení zásobníku v C++ výjimka, která může být zpracována podle jazyka C++ blok.  
  
 Není bezpečné volat **_resetstkoflw –** v bloku catch C++, který je dostupný z výjimka vyvolaná objektem funkce překladač strukturovaného výjimek. V takovém případě není uvolněno místo zásobníku a ukazatel zásobníku není resetovat, dokud mimo blok catch, i když destruktory mít byla volána pro všechny objekty zničitelné před blok catch. Tuto funkci nelze volat, dokud uvolněn zásobníku a ukazatel zásobníku byl obnoven. Proto by měla být volána pouze po ukončení blok catch. V bloku catch třeba použít jako málo místa zásobníku nejdříve, protože k přetečení zásobníku, který se nachází v bloku catch, který je sám Probíhá pokus o obnovení z předchozí přetečení zásobníku není použitelná pro obnovení a může způsobit, že program přestal reagovat, jako přetečení v aktivační události bloku catch výjimku samotné používá stejnou catch – blok.  
  
 Existují situace, kdy **_resetstkoflw –** může selhat, i když použijete na správné místo, například v rámci **__except** bloku. Pokud i po unwinding zásobníku, není pořád dostatek místa zbývající ke spuštění **_resetstkoflw –** bez psaní na poslední stránku v zásobníku **_resetstkoflw –** nepodaří obnovit na poslední stránku Zásobník jako ochranná stránka a vrátí hodnotu 0, udávající neúspěch. Proto bezpečné používání této funkce by měly obsahovat kontrola návratovou hodnotu místo za předpokladu, že je bezpečné použití zásobníku.  
  
 Strukturované zpracování výjimek nezachytí `STATUS_STACK_OVERFLOW` výjimky, když je aplikace kompilovat s `/clr` (najdete v části [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_resetstkoflw`|\<malloc.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
 **Knihovny:** všechny verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití doporučené `_resetstkoflw` funkce.  
  
```  
// crt_resetstkoflw.c  
// Launch program with and without arguments to observe  
// the difference made by calling _resetstkoflw.  
  
#include <malloc.h>  
#include <stdio.h>  
#include <windows.h>  
  
void recursive(int recurse)  
{  
   _alloca(2000);  
   if (recurse)  
      recursive(recurse);  
}  
  
// Filter for the stack overflow exception.  
// This function traps the stack overflow exception, but passes  
// all other exceptions through.   
int stack_overflow_exception_filter(int exception_code)  
{  
   if (exception_code == EXCEPTION_STACK_OVERFLOW)  
   {  
       // Do not call _resetstkoflw here, because  
       // at this point, the stack is not yet unwound.  
       // Instead, signal that the handler (the __except block)  
       // is to be executed.  
       return EXCEPTION_EXECUTE_HANDLER;  
   }  
   else  
       return EXCEPTION_CONTINUE_SEARCH;  
}  
  
int main(int ac)  
{  
   int i = 0;  
   int recurse = 1, result = 0;  
  
   for (i = 0 ; i < 10 ; i++)  
   {  
      printf("loop #%d\n", i + 1);  
      __try  
      {  
         recursive(recurse);  
  
      }  
  
      __except(stack_overflow_exception_filter(GetExceptionCode()))  
      {  
         // Here, it is safe to reset the stack.  
  
         if (ac >= 2)  
         {  
            puts("resetting stack overflow");  
            result = _resetstkoflw();  
         }  
      }  
  
      // Terminate if _resetstkoflw failed (returned 0)  
      if (!result)  
         return 3;  
   }  
  
   return 0;  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
 Bez argumentů program:  
  
```  
loop #1  
```  
  
 Aplikace přestane reagovat bez provedení další iterací.  
  
 Pomocí programu argumenty:  
  
```  
loop #1  
resetting stack overflow  
loop #2  
resetting stack overflow  
loop #3  
resetting stack overflow  
loop #4  
resetting stack overflow  
loop #5  
resetting stack overflow  
loop #6  
resetting stack overflow  
loop #7  
resetting stack overflow  
loop #8  
resetting stack overflow  
loop #9  
resetting stack overflow  
loop #10  
resetting stack overflow  
```  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje použití doporučené `_resetstkoflw` v programu kde strukturovaných výjimky jsou převedeny na výjimky jazyka C++.  
  
### <a name="code"></a>Kód  
  
```  
// crt_resetstkoflw2.cpp  
// compile with: /EHa  
// _set_se_translator requires the use of /EHa  
#include <malloc.h>  
#include <stdio.h>  
#include <windows.h>  
#include <eh.h>  
  
class Exception { };  
  
class StackOverflowException : Exception { };  
  
// Because the overflow is deliberate, disable the warning that  
// this function will cause a stack overflow.  
#pragma warning (disable: 4717)  
void CauseStackOverflow (int i)  
{  
        // Overflow the stack by allocating a large stack-based array  
        // in a recursive function.  
        int a[10000];  
        printf("%d ", i);  
        CauseStackOverflow (i + 1);  
}  
  
void __cdecl SEHTranslator (unsigned int code, _EXCEPTION_POINTERS*)  
{  
   // For stack overflow exceptions, throw our own C++   
   // exception object.  
   // For all other exceptions, throw a generic exception object.  
   // Use minimal stack space in this function.  
   // Do not call _resetstkoflw in this function.  
  
   if (code == EXCEPTION_STACK_OVERFLOW)  
      throw StackOverflowException ( );  
   else  
      throw Exception( );  
}  
  
int main ( )  
{  
        bool stack_reset = false;  
        bool result = false;  
  
        // Set up a function to handle all structured exceptions,  
        // including stack overflow exceptions.  
        _set_se_translator (SEHTranslator);  
  
        try  
        {  
            CauseStackOverflow (0);  
        }  
        catch (StackOverflowException except)  
        {  
                // Use minimal stack space here.  
                // Do not call _resetstkoflw here.  
                printf("\nStack overflow!\n");  
                stack_reset = true;  
        }  
        catch (Exception except)  
        {  
                // Do not call _resetstkoflw here.  
                printf("\nUnknown Exception!\n");  
        }  
        if (stack_reset)  
        {  
          result = _resetstkoflw();  
          // If stack reset failed, terminate the application.  
          if (result == 0)  
             exit(1);  
        }  
  
        void* pv = _alloca(100000);  
        printf("Recovered from stack overflow and allocated 100,000 bytes"  
               " using _alloca.");  
  
   return 0;  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24  
Stack overflow!  
Recovered from stack overflow and allocated 100,000 bytes using _alloca.  
```  
  
## <a name="see-also"></a>Viz také  
 [_alloca](../../c-runtime-library/reference/alloca.md)