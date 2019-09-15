---
title: _set_new_handler
ms.date: 11/04/2016
api_name:
- _set_new_handler
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
ms.openlocfilehash: a1f340887efd657dd9ff9bf219534d77fdd90aa3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948475"
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

Vrátí ukazatel na předchozí funkci zpracování výjimky zaregistrovanou funkcí **_set_new_handler**, aby bylo možné předchozí funkci obnovit později. Pokud není nastavená žádná předchozí funkce, můžete k obnovení výchozího chování použít návratovou hodnotu. Tato hodnota může být **null**.

## <a name="remarks"></a>Poznámky

C++ Funkce **_set_new_handler** Určuje funkci zpracování výjimek, která získá řízení, pokud operátor **New** nedokáže přidělit paměť. V případě **neúspěchu dojde v** systému za běhu k automatickému volání funkce zpracování výjimek, která byla předána jako argument pro **_set_new_handler**. **_PNH**definovaná v New. h je ukazatel na funkci, která vrací typ **int** a přebírá argument typu **size_t**. Pomocí **size_t** Určete množství místa, které se má přidělit.

Neexistuje žádná výchozí obslužná rutina.

**_set_new_handler** je v podstatě schéma uvolňování paměti. Systém za běhu pokusy o přidělení pokaždé, když funkce vrátí nenulovou hodnotu a v případě, že funkce vrátí hodnotu 0, dojde k chybě.

Výskyt funkce **_set_new_handler** v programu registruje funkci zpracování výjimek určenou v seznamu argumentů za běhu systému:

```cpp
// set_new_handler1.cpp
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

Adresu funkce, která byla naposledy předána funkci **_set_new_handler** , můžete uložit a později ji obnovit:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

C++ Funkce [_set_new_mode](set-new-mode.md) nastaví nový režim obslužné rutiny pro [stav](malloc.md)". Nový režim obslužné rutiny **označuje, zda je při** selhání zavolána nová rutina obslužné rutiny nastavenou na **_set_new_handler**. Ve výchozím nastavení nevolá hodnota \ nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby se při neúspěšném přidělení paměti nezdařila **volání nové** rutiny obslužné rutiny stejným způsobem jako operátor **New** , když dojde **k chybě ze** stejného důvodu. Chcete-li přepsat výchozí hodnotu, zavolejte:

```cpp
_set_new_mode(1);
```

nejdříve v programu nebo se připojte pomocí NewMode. obj.

Pokud je k dispozici `operator new` uživatelsky definované, nové funkce obslužné rutiny nejsou při selhání automaticky volány.

Další informace najdete v tématu [nové](../../cpp/new-operator-cpp.md) a [Odstranit](../../cpp/delete-operator-cpp.md) v  *C++ referenční příručce jazyka*.

Pro všechny dynamicky propojené knihovny DLL nebo spustitelné soubory je k dispozici jedna obslužná rutina **_set_new_handler** ; i když zavoláte **_set_new_handler** , může být obslužná rutina nahrazena jinou nebo, kterou nahrazujete obslužnou rutinu nastavenou jinou knihovnou DLL nebo spustitelným souborem.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_new_handler**|\<New. h >|

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

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
