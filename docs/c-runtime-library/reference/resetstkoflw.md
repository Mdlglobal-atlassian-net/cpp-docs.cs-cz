---
title: _resetstkoflw
ms.date: 4/2/2020
api_name:
- _resetstkoflw
- _o__resetstkoflw
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- resetstkoflw
- _resetstkoflw
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
ms.openlocfilehash: dfe0de4f48173a0e79bcdcfb24bfdf7a21f47a04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332821"
---
# <a name="_resetstkoflw"></a>_resetstkoflw

Obnoví se z přetečení zásobníku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _resetstkoflw( void );
```

## <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná, nula, pokud se nezdaří.

## <a name="remarks"></a>Poznámky

Funkce **_resetstkoflw** se obnoví z podmínky přetečení zásobníku, což umožňuje programu pokračovat namísto selhání s chybou závažné výjimky. Pokud **_resetstkoflw** funkce není volána, neexistují žádné stránky guard po předchozí výjimce. Při příštím přetečení zásobníku neexistují žádné výjimky vůbec a proces ukončí bez upozornění.

Pokud vlákno v aplikaci způsobí **výjimku EXCEPTION_STACK_OVERFLOW,** vlákno opustilo svůj zásobník v poškozeném stavu. To je na rozdíl od jiných výjimek, jako je **EXCEPTION_ACCESS_VIOLATION** nebo **EXCEPTION_INT_DIVIDE_BY_ZERO**, kde není poškozen zásobníku. Zásobník je nastaven na libovolně malou hodnotu při prvním načtení programu. Zásobník pak roste na vyžádání, aby vyhovovaly potřebám vlákna. To je implementováno umístěním stránky s přístupem PAGE_GUARD na konci aktuálního zásobníku. Další informace naleznete v [tématu Vytváření stránek stráží](/windows/win32/Memory/creating-guard-pages).

Když kód způsobí, že ukazatel zásobníku přejděte na adresu na této stránce, dojde k výjimce a systém provádí následující tři věci:

- Odebere PAGE_GUARD ochranu na stránce guard tak, aby vlákno můžete číst a zapisovat data do paměti.

- Přidělí novou stránku ochranného krytu, která se nachází jednu stránku pod poslední.

- Znovu spustí instrukce, která vyvolala výjimku.

Tímto způsobem systém může automaticky zvětšit velikost zásobníku pro vlákno. Každé vlákno v procesu má maximální velikost zásobníku. Velikost zásobníku je nastavena v době kompilace [/STACK (Stack Allocations)](../../build/reference/stack-stack-allocations.md)nebo [příkazem STACKSIZE](../../build/reference/stacksize.md) v souboru .def pro projekt.

Při překročení této maximální velikosti zásobníku systém provádí následující tři věci:

- Odebere ochranu PAGE_GUARD na stránce ochranného krytu, jak bylo popsáno výše.

- Pokusí se přidělit novou stránku strážpod poslední. To se však nezdaří, protože byla překročena maximální velikost zásobníku.

- Vyvolá výjimku tak, aby ji vlákno mohlo zpracovat v bloku výjimek.

Všimněte si, že v tomto okamžiku zásobníku již nemá ochrannou stránku. Při příštím, že program zvětší zásobník u konce, kde by měl být stráž stránku, program zapíše za konec zásobníku a způsobí narušení přístupu.

Volání **_resetstkoflw** obnovit ochrannou stránku vždy, když se provádí obnovení po výjimce přetečení zásobníku. Tato funkce může být volána zevnitř hlavního těla **__except** bloku nebo mimo **blok __except.** Existují však určitá omezení, kdy by měla být použita. **_resetstkoflw** by nikdy neměly být volány z:

- Výraz filtru.

- Funkce filtru.

- Funkce volaná z funkce filtru.

- Blok **úlovků.**

- **Blok __finally.**

V těchto bodech zásobníkještě není dostatečně odvinut.

Výjimky přetečení zásobníku jsou generovány jako strukturované výjimky, nikoli výjimky jazyka C++, takže **_resetstkoflw** není užitečné v běžném bloku **catch,** protože nezachytí výjimku přetečení zásobníku. Pokud se však [_set_se_translator](set-se-translator.md) používá k implementaci překladače strukturovaných výjimek, který vyvolá výjimky jazyka C++ (jako v druhém příkladu), výsledkem výjimky přetečení zásobníku je výjimka c++, kterou může zpracovat blok catch jazyka C++.

Není bezpečné volat **_resetstkoflw** v bloku catch jazyka C++, který je dosažen z výjimky vyvolané strukturovanou funkcí překladače výjimek. V tomto případě není uvolněno místo zásobníku a ukazatel zásobníku není resetován, dokud mimo blok catch, i když destruktory byly volány pro všechny zničitelné objekty před blok catch. Tato funkce by neměla být volána, dokud není uvolněno místo zásobníku a ukazatel zásobníku nebyl resetován. Proto by měla být volána pouze po ukončení catch bloku. Jako malý zásobníku co nejvíce by měl být použit v bloku catch, protože přetečení zásobníku, ke kterému dochází v bloku catch, který se sám pokouší zotavit z předchozího přetečení zásobníku, není obnovitelný a může způsobit, že program přestane reagovat, protože přetečení v bloku catch aktivuje výjimku, která je sama zpracována stejným blokem catch.

Existují situace, kdy **_resetstkoflw** může selhat i v případě, že je použit ve správném umístění, například v rámci **__except** bloku. Pokud i po odvíjení zásobníku stále není dostatek místa v zásobníku vlevo pro spuštění **_resetstkoflw** bez zápisu do poslední stránky zásobníku, **_resetstkoflw** se nezdaří obnovit poslední stránku zásobníku jako ochranná stránka a vrátí 0, což znamená selhání. Proto bezpečné použití této funkce by měla zahrnovat kontrolu vrácené hodnoty namísto za předpokladu, že zásobník je bezpečné použití.

Strukturované zpracování výjimek nezachytí **výjimku STATUS_STACK_OVERFLOW** při kompilaci aplikace s **/clr** (viz [/clr (Kompilace běžného jazykového běhu)](../../build/reference/clr-common-language-runtime-compilation.md)).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_resetstkoflw**|\<malloc.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovny:** Všechny verze [funkcí knihovny CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje doporučené použití **funkce _resetstkoflw.**

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

Program přestane reagovat bez provádění dalších iterací.

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

### <a name="code"></a>kód

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

## <a name="see-also"></a>Viz také

[_alloca](alloca.md)<br/>
