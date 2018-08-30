---
title: _resetstkoflw | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31d3f647d2d72cf96c9b935c33376aae698464c8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207573"
---
# <a name="resetstkoflw"></a>_resetstkoflw

Zotavuje z přetečení zásobníku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _resetstkoflw( void );
```

## <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná, nula, pokud se nezdaří.

## <a name="remarks"></a>Poznámky

**_Resetstkoflw** funkce obnoví ze stavu přetečení zásobníku, což programu pokračovat místo selhání se závažnou chybou výjimky. Pokud **_resetstkoflw** funkce není volána, nejsou žádné ochranné stránky po předchozí výjimce. Příště, že je stack overflow, nejsou vůbec žádné výjimky a proces skončí bez varování.

Pokud vlákno v aplikaci způsobí, že **EXCEPTION_STACK_OVERFLOW** výjimky, vlákno opustí svůj zásobník v poškozeném stavu. To se liší od jiných výjimek, jako **EXCEPTION_ACCESS_VIOLATION** nebo **EXCEPTION_INT_DIVIDE_BY_ZERO**, kde zásobník není poškozen. Zásobník je nastaven na libovolně malou hodnotu při prvním načtení programu. Zásobník pak roste na požádání, aby vyhověl potřebám vlákna. Toto je implementováno umístěním stránky s přístupem PAGE_GUARD na konec aktuálního zásobníku. Další informace najdete v tématu [vytváření ochranné stránky](/windows/desktop/Memory/creating-guard-pages).

Pokud kód způsobí, že ukazatel zásobníku tak, aby odkazoval na adresu na této stránce, dojde k výjimce a systém provede následující tři věci:

- Odebere ochranu PAGE_GUARD na ochranné stránce tak, aby vlákno může číst a zapisovat data do paměti.

- Přidělí novou ochrannou stránku, která je umístěna jednu stránku za poslední stránkou.

- Znovu spustí operaci, která způsobila výjimku.

Tímto způsobem může systém zvětšit velikost zásobníku pro vlákno automaticky. Každé vlákno v procesu má maximální velikost zásobníku. Velikost zásobníku je nastavena v době kompilace [/Stack (přidělení zásobníku)](../../build/reference/stack-stack-allocations.md), nebo [STACKSIZE](../../build/reference/stacksize.md) – příkaz souboru .def projektu.

Při překročení maximální velikosti zásobníku systém provede následující tři věci:

- Odebere ochranu PAGE_GUARD na ochranné stránce, jak je uvedeno výše.

- Pokusí se o přidělení nové stránky guard pod poslední z nich. Ale to se nezdaří, protože byla překročena maximální velikost zásobníku.

- Vyvolá výjimku, takže ji vlákno může zpracovat v bloku výjimky.

Všimněte si, že v tomto okamžiku zásobník již nemá ochrannou stránku. Při příštím, že program roste zásobník až na konec, kde by měla být ochranná stránka, program zapíše za konec zásobníku a způsobí narušení přístupu.

Volání **_resetstkoflw** k obnovení ochranné stránky při každém provedení obnovení po výjimce přetečení zásobníku. Tuto funkci lze volat z hlavní **__except** bloku nebo mimo ně **__except** bloku. Existují však některá omezení, kdy by mělo být používáno. **_resetstkoflw** by měl být nikdy volán z::

- Výraz filtru.

- Funkce filtru.

- Funkce volána z funkce filtru.

- A **catch** bloku.

- A **__finally** bloku.

V těchto bodech zásobník ještě není dostatečně oddělen.

Výjimky přetečení zásobníku jsou generovány jako strukturované výjimky, ne výjimky jazyka C++, takže **_resetstkoflw** není k ničemu v běžném **catch** blokovat, protože nezachytí výjimku přetečení zásobníku. Nicméně pokud [_set_se_translator](set-se-translator.md) slouží k implementaci překladače strukturovaných výjimek, který vyvolá výjimky jazyka C++ (viz druhý příklad), catch výsledků výjimky přetečení zásobníku v výjimky jazyka C++, které mohou být zpracovány C++ blok.

Není bezpečné volat **_resetstkoflw** v bloku catch jazyka C++, který je dosažen z výjimky vyvolané funkcí překladače strukturované výjimky. V takovém případě není uvolněn prostor v zásobníku a ukazatel na zásobník není vynulován, dokud mimo blok catch, přestože destruktory byly volány pro zničitelné objekty před blokem catch. Tato funkce by neměl volána, dokud není uvolněno místo v zásobníku a ukazatel zásobníku se resetovalo. Proto by měla být volána jedině po ukončení bloku catch. Jako málo místa zásobníku, co možná byste měli použít ve blok catch, protože přetečení zásobníku, ke které dochází v bloku catch, který je sám pokouší o obnovení z předchozí přetečení zásobníku se nedá vrátit zpátky a může způsobit, že program přestane reagovat jako přetečení v aktivační události blok catch výjimky, že samotné je zpracována stejným blok catch.

Existují situace, kdy **_resetstkoflw** může selhat, i když se používá na správném místě, například v rámci **__except** bloku. Pokud ani po uvolnění zásobníku, není stále dostatek místa k provedení **_resetstkoflw** bez zápisu do poslední stránky zásobníku, **_resetstkoflw** nezdaří obnovit poslední stránku zásobníku jako ochrannou stránku a vrátí hodnotu 0 označující selhání. Proto bezpečné používání této funkce by měly zahrnovat kontrolu návratové hodnoty místo za předpokladu, že zásobník je bezpečné používat.

Strukturované zpracování výjimek nezachytí **STATUS_STACK_OVERFLOW** výjimka při kompilaci aplikace s **/CLR** (viz  [ /CLR (Common Language Runtime kompilace)](../../build/reference/clr-common-language-runtime-compilation.md)).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_resetstkoflw**|\<malloc.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** všechny verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje doporučené použití **_resetstkoflw** funkce.

```C
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

Ukázkový výstup bez argumentů programu:

```Output
loop #1
```

Program přestane reagovat bez provedení dalších iterací.

S argumenty programu:

```Output
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

Následující příklad ukazuje doporučené použití **_resetstkoflw** v programu, kde jsou strukturované výjimky převedeny na výjimky jazyka C++.

### <a name="code"></a>Kód

```cpp
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

```Output
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
Stack overflow!
Recovered from stack overflow and allocated 100,000 bytes using _alloca.
```

## <a name="see-also"></a>Viz také:

[_alloca](alloca.md)<br/>
