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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b19b66279427aa4623cff037e67067096eb6bd42
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917788"
---
# <a name="_resetstkoflw"></a>_resetstkoflw

Obnoví z přetečení zásobníku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _resetstkoflw( void );
```

## <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná, nula, pokud selže.

## <a name="remarks"></a>Poznámky

Funkce **_resetstkoflw** se obnoví z podmínky přetečení zásobníku, což umožní programu pokračovat, aniž by došlo k selhání s závažnou chybou výjimky. Pokud není volána funkce **_resetstkoflw** , neexistují žádné Guard žádné stránky po předchozí výjimce. Při příštím přetečení zásobníku nejsou vůbec žádné výjimky a proces se ukončí bez upozornění.

Pokud vlákno v aplikaci způsobí výjimku **EXCEPTION_STACK_OVERFLOW** , vlákno opustí svůj zásobník v poškozeném stavu. To je na rozdíl od jiných výjimek, například **EXCEPTION_ACCESS_VIOLATION** nebo **EXCEPTION_INT_DIVIDE_BY_ZERO**, kde zásobník není poškozený. Zásobník je nastaven na libovolně malá hodnota při prvním načtení programu. Zásobník pak roste na vyžádání, aby splňoval potřeby vlákna. To je implementováno vložením stránky s PAGE_GUARDm přístupem na konci aktuálního zásobníku. Další informace najdete v tématu [vytváření ochranných stránek](/windows/win32/Memory/creating-guard-pages).

Když kód způsobí, že ukazatel zásobníku odkazuje na adresu na této stránce, dojde k výjimce a systém provede následující tři věci:

- Odstraní ochranu PAGE_GUARD na stránce Guard, aby vlákno mohlo číst a zapisovat data do paměti.

- Přidělí novou stránku Guard, která je umístěná na jedné stránce pod poslední.

- Znovu spustí instrukci, která vyvolala výjimku.

Tímto způsobem systém může zvětšit velikost zásobníku pro vlákno automaticky. Každé vlákno v procesu má maximální velikost zásobníku. Velikost zásobníku je nastavena v době kompilace [/Stack (přidělení zásobníku)](../../build/reference/stack-stack-allocations.md)nebo příkazem [STACKSIZE](../../build/reference/stacksize.md) v souboru. def pro projekt.

Při překročení této maximální velikosti zásobníku provede systém následující tři věci:

- Odstraní ochranu PAGE_GUARD na stránce Guard, jak je popsáno výše.

- Pokusí se o přidělení nové ochranné stránky pod poslední z nich. Tato chyba se ale nezdařila, protože byla překročena maximální velikost zásobníku.

- Vyvolá výjimku, aby ji vlákno mohl zpracovat v bloku výjimky.

Všimněte si, že v tomto okamžiku zásobník už nemá chráněnou stránku. Až program příště rozroste zásobník na konec, kde by měla být ochranná stránka, program zapíše za konec zásobníku a způsobí porušení přístupu.

Pokud se obnovení provádí po výjimce přetečení zásobníku, volejte **_resetstkoflw** k obnovení stránky Guard. Tuto funkci lze volat zevnitř hlavního těla **__except** bloku nebo mimo blok **__except** . Existují však určitá omezení, která by měla být použita. **_resetstkoflw** by nikdy neměly být volány z:

- Výraz filtru.

- Funkce filtru.

- Funkce volaná z funkce filtru.

- Blok **catch** .

- Blok **__finally** .

V těchto bodech zásobník ještě není dostatečně neoddělený.

Výjimky přetečení zásobníku jsou generovány jako strukturované výjimky, nikoli jako výjimka jazyka C++, takže **_resetstkoflw** nejsou užitečné v běžném bloku **catch** , protože nebudou zachytit výjimku přetečení zásobníku. Pokud je však [_set_se_translator](set-se-translator.md) použita k implementaci překladatele strukturované výjimky, který vyvolá výjimky jazyka c++ (jako v druhém příkladu), výsledkem výjimky přetečení zásobníku je výjimka jazyka c++, která může být zpracována blokem catch jazyka c++.

Není bezpečné volat **_resetstkoflw** v bloku catch jazyka C++, který je dosažitelný z výjimky vyvolané funkcí překladače strukturované výjimky. V tomto případě není prostor zásobníku uvolněn a ukazatel zásobníku není resetován do vně bloku catch, a to i v případě, že destruktory byly volány pro všechny objekty zničitelné před blokem catch. Tato funkce by neměla být volána, dokud není uvolněn prostor zásobníku a byl resetován ukazatel zásobníku. Proto by měla být volána pouze po ukončení bloku catch. V bloku catch by se měla použít co nejmenší velikost zásobníku, protože přetečení zásobníku, ke kterému dojde v bloku catch, který se sám pokouší obnovit z předchozího přetečení zásobníku, není obnovitelné a může způsobit, že program přestane reagovat, protože přetečení v bloku catch vyvolá výjimku, kterou sám zpracuje stejný blok catch.

Existují situace, kdy **_resetstkoflw** může selhat, i když se používá ve správném umístění, například v rámci bloku **__except** . Pokud i po uvolnění zásobníku stále není dostatek volného místa pro spuštění **_resetstkoflw** bez psaní do poslední stránky zásobníku, **_resetstkoflw** selže při resetování poslední stránky zásobníku jako ochranné stránky a vrátí hodnotu 0, což značí selhání. Proto by bezpečné použití této funkce mělo zahrnovat kontrolu návratové hodnoty namísto za předpokladu, že je zásobník bezpečně používán.

Strukturované zpracování výjimek nebude zachytit výjimku **STATUS_STACK_OVERFLOW** , je-li aplikace kompilována s možností **/CLR** (viz [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_resetstkoflw**|\<. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovny:** Všechny verze [funkcí knihovny CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje Doporučené použití funkce **_resetstkoflw** .

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

Následující příklad ukazuje Doporučené použití **_resetstkoflw** v programu, kde jsou strukturované výjimky převedeny na výjimky jazyka C++.

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
