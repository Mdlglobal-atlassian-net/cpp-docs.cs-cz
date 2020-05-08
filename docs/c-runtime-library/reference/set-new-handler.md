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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 06da25fb38d18691f78973f4e63a8b7b48d98ce1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913957"
---
# <a name="_set_new_handler"></a>_set_new_handler

Přenáší řízení do mechanismu zpracování chyb, pokud operátor **New** nedokáže přidělit paměť.

## <a name="syntax"></a>Syntaxe

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>Parametry

*pNewHandler*<br/>
Ukazatel na funkci zpracování paměti dodanou aplikací. Argument 0 způsobí odebrání nové obslužné rutiny.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na předchozí funkci zpracování výjimky zaregistrovanou **_set_new_handler**, aby bylo možné předchozí funkci obnovit později. Pokud není nastavená žádná předchozí funkce, můžete k obnovení výchozího chování použít návratovou hodnotu. Tato hodnota může být **null**.

## <a name="remarks"></a>Poznámky

Funkce **_Set_new_handler** jazyka C++ určuje funkci zpracování výjimek, která získá řízení, pokud operátor **New** nedokáže přidělit paměť. V **případě neúspěchu dojde v** systému za běhu k automatickému volání funkce zpracování výjimek, která byla předána jako argument pro **_set_new_handler**. **_PNH**definovaná v New. h je ukazatel na funkci, která vrací typ **int** a přebírá argument typu **size_t**. Použijte **size_t** k určení množství místa, které se má přidělit.

Neexistuje žádná výchozí obslužná rutina.

**_set_new_handler** je v podstatě schéma uvolňování paměti. Systém za běhu pokusy o přidělení pokaždé, když funkce vrátí nenulovou hodnotu a v případě, že funkce vrátí hodnotu 0, dojde k chybě.

Výskyt funkce **_set_new_handler** v programu registruje funkci zpracování výjimek určenou v seznamu argumentů za běhu systému:

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

Můžete uložit adresu funkce, která byla naposledy předána do funkce **_set_new_handler** a později ji obnovit:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

Funkce [_Set_new_mode](set-new-mode.md) jazyka C++ nastaví nový režim obslužné rutiny pro stav [".](malloc.md) Nový režim obslužné rutiny **označuje, zda je při** selhání zavolána nová rutina obslužné rutiny, jak je nastavena **_set_new_handler**. Ve výchozím nastavení **malloc** nevolá hodnota \ nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby se při neúspěšném přidělení paměti nezdařila **volání nové** rutiny obslužné rutiny stejným způsobem jako operátor **New** , když dojde **k chybě ze** stejného důvodu. Chcete-li přepsat výchozí hodnotu, zavolejte:

```cpp
_set_new_mode(1);
```

nejdříve v programu nebo se připojte pomocí NewMode. obj.

Pokud je k dispozici `operator new` uživatelsky definované, nové funkce obslužné rutiny nejsou při selhání automaticky volány.

Další informace najdete v tématu [nové](../../cpp/new-operator-cpp.md) a [Odstranit](../../cpp/delete-operator-cpp.md) v *Referenční příručce jazyka C++*.

Existuje jedna obslužná rutina **_set_new_handler** pro všechny dynamicky propojené knihovny DLL nebo spustitelné soubory; i v případě, že zavoláte **_set_new_handler** obslužná rutina může být nahrazena jinou nebo, kterou nahrazujete obslužnou rutinu nastavenou jinou knihovnou DLL nebo spustitelným souborem.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_new_handler**|\<New. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

V tomto příkladu, pokud se přidělení nepovede, se ovládací prvek přenese do MyNewHandler. Argument předaný metodě MyNewHandler je počet požadovaných bajtů. Hodnota vrácená z MyNewHandler je příznak označující, zda se má pokus o přidělení zopakovat: nenulová hodnota znamená, že přidělení by se mělo opakovat, a nulová hodnota indikuje, že přidělení selhalo.

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
[dost](free.md)<br/>
[realloc](realloc.md)<br/>
