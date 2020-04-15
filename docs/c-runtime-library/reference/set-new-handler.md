---
title: _set_new_handler
ms.date: 4/2/2020
api_name:
- _set_new_handler
- _o__set_new_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_new_handler
- set_new_handler
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
ms.openlocfilehash: c3f1b9bd8bf2a4404e2239858e4c3c59b755bacd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332380"
---
# <a name="_set_new_handler"></a>_set_new_handler

Přenese řízení do mechanismu zpracování chyb, pokud **nový** operátor nepodaří přidělit paměť.

## <a name="syntax"></a>Syntaxe

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>Parametry

*pNewHandler*<br/>
Ukazatel na funkci zpracování paměti dodané aplikací. Argument 0 způsobí, že nové obslužné rutiny, které mají být odebrány.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na předchozí funkci zpracování výjimek registrovanou **_set_new_handler**, aby bylo možné předchozí funkci později obnovit. Pokud nebyla nastavena žádná předchozí funkce, vrácená hodnota může být použita k obnovení výchozího chování; tato hodnota může být **NULL**.

## <a name="remarks"></a>Poznámky

Funkce **_set_new_handler** C++ určuje funkci zpracování výjimek, která získá kontrolu, pokud **se novému** operátoru nepodaří přidělit paměť. Pokud **se nové** nezdaří, systém run-time automaticky zavolá funkci zpracování výjimek, která byla předána jako argument pro **_set_new_handler**. **_PNH**, definované v New.h, je ukazatel na funkci, která vrací typ **int** a trvá argument typu **size_t**. Pomocí **size_t** určete velikost místa, které má být přiděleno.

Neexistuje žádná výchozí obslužná rutina.

**_set_new_handler** je v podstatě schéma uvolňování paměti. Systém run-time opakuje přidělení pokaždé, když funkce vrátí nenulovou hodnotu a selže, pokud funkce vrátí 0.

Výskyt funkce **_set_new_handler** v programu zaregistruje funkci zpracování výjimek zadanou v seznamu argumentů se systémem run-time:

```cpp
// set_new_handler1.cpp
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <new.h>

int handle_program_memory_depletion( size_t )
{
   // Your code
}

int main( void )
{
   _set_new_handler( handle_program_memory_depletion );
   int *pi = new int[BIG_NUMBER];
}
```

Adresu funkce, která byla naposledy předána **funkci _set_new_handler,** můžete uložit a později ji obnovit:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

Funkce [_set_new_mode](set-new-mode.md) C++ nastaví nový režim obslužné rutiny pro [malloc](malloc.md). Nový režim obslužné rutiny označuje, zda při selhání **malloc** volá novou rutinu obslužné rutiny nastavenou **_set_new_handler**. Ve výchozím nastavení **malloc** nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Můžete přepsat toto výchozí chování tak, že když **malloc** selže přidělit paměť, **malloc** volá rutinu nové obslužné rutiny stejným způsobem, jako **nový** operátor, když se nezdaří ze stejného důvodu. Chcete-li přepsat výchozí, volejte:

```cpp
_set_new_mode(1);
```

brzy ve vašem programu nebo odkaz s Newmode.obj.

Pokud je k `operator new` dispozici definované uživatelem, nové funkce obslužné rutiny nejsou automaticky volány k selhání.

Další informace naleznete [v tématu new](../../cpp/new-operator-cpp.md) and [delete](../../cpp/delete-operator-cpp.md) in the *C++ Language Reference*.

Existuje jedna obslužná rutina **_set_new_handler** pro všechny dynamicky propojené knihovny DLL nebo spustitelné soubory. i v případě, že zavoláte **_set_new_handler** může být obslužná rutina nahrazena jinou nebo že nahrazujete obslužnou rutinu nastavenou jinou sadou DLL nebo spustitelnýsoubor.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

V tomto příkladu při selhání přidělení je ovládací prvek převeden na MyNewHandler. Argument předaný MyNewHandler je počet požadovaných bajtů. Hodnota vrácená z MyNewHandler je příznak označující, zda přidělení by měla být opakována: nenulová hodnota označuje, že přidělení by měla být opakována a nulová hodnota označuje, že přidělení se nezdařilo.

```cpp
// crt_set_new_handler.cpp
// compile with: /c
#include <stdio.h>
#include <new.h>
#define BIG_NUMBER 0x1fffffff

int coalesced = 0;

int CoalesceHeap()
{
   coalesced = 1;  // Flag RecurseAlloc to stop
   // do some work to free memory
   return 0;
}
// Define a function to be called if new fails to allocate memory.
int MyNewHandler( size_t size )
{
   printf("Allocation failed. Coalescing heap.\n");

   // Call a function to recover some heap space.
   return CoalesceHeap();
}

int RecurseAlloc() {
   int *pi = new int[BIG_NUMBER];
   if (!coalesced)
      RecurseAlloc();
   return 0;
}

int main()
{
   // Set the failure handler for new to be MyNewHandler.
   _set_new_handler( MyNewHandler );
   RecurseAlloc();
}
```

```Output
Allocation failed. Coalescing heap.

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Zdarma](free.md)<br/>
[realloc](realloc.md)<br/>
