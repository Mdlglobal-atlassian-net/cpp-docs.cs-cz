---
title: _set_new_handler
ms.date: 11/04/2016
apiname:
- _set_new_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_new_handler
- set_new_handler
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
ms.openlocfilehash: bc7718503f59c69868a75cac9383286a548fc307
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356495"
---
# <a name="setnewhandler"></a>_set_new_handler

Přenese ovládací prvek na váš mechanismus zpracování chyb, pokud **nové** operátor selže přidělování paměti.

## <a name="syntax"></a>Syntaxe

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>Parametry

*pNewHandler*<br/>
Ukazatel na zpracování funkce paměti poskytované aplikací. Argument 0 způsobí, že novou obslužnou rutinu, která se má odebrat.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na předchozí výjimku zpracování funkcí registrovaných **_set_new_handler**, takže lze později obnovit předchozí funkce. Pokud byla nastavena žádná předchozí funkce, vrácená hodnota je možné obnovit výchozí chování; Tato hodnota může být **NULL**.

## <a name="remarks"></a>Poznámky

C++ **_Set_new_handler** funkce určuje funkci zpracování výjimek, která získá kontrolu, pokud **nové** operátor selže přidělování paměti. Pokud **nové** selže, systém za běhu automaticky volá funkci zpracování výjimek, který byl předán jako argument **_set_new_handler**. **_Pnh –**, definované v New.h, je ukazatel na funkci, která vrací typ **int** a přebírá argument typu **size_t**. Použití **size_t** k určení množství místa, která bude přidělena.

Neexistuje žádný výchozí obslužnou rutinu.

**_set_new_handler** je v podstatě schéma uvolnění paměti. Za běhu systému zopakuje pokus o přidělení pokaždé, když vaše funkce vrátí nenulovou hodnotu a selže, pokud funkce vrátí hodnotu 0.

Výskyt **_set_new_handler** funkce v programu zaregistruje funkci zpracování výjimek zadaných v seznamu argumentů systému za běhu:

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

Adresa funkce, která byla naposledy předána můžete uložit **_set_new_handler** fungovat a později ji obnovit:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

C++ [_Set_new_mode](set-new-mode.md) funkce nastaví nový režim obslužné rutiny pro [malloc](malloc.md). Nový režim obslužné rutiny Určuje, zda je při selhání, **malloc** je volat nové rutiny obsluhy úmluvu **_set_new_handler**. Ve výchozím nastavení **malloc** nevolá nové rutiny obsluhy při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby, když **malloc** selže přidělování paměti, **malloc** volá nové rutiny obsluhy ve stejném způsobu, jakým **nové** operátor Když selže ze stejného důvodu. Pokud chcete přepsat výchozí nastavení, volání:

```cpp
_set_new_mode(1);
```

v rané fázi vašeho programu nebo propojení s Newmode.obj.

Pokud uživatelem definované `operator new` je k dispozici nové funkce obslužnou rutinu nejsou volány automaticky při selhání.

Další informace najdete v tématu [nové](../../cpp/new-operator-cpp.md) a [odstranit](../../cpp/delete-operator-cpp.md) v *referenční dokumentace jazyka C++*.

Existuje jeden **_set_new_handler** obslužné rutiny pro všechny dynamicky propojené knihovny DLL nebo spustitelné soubory, i v případě, že zavoláte **_set_new_handler** vaše obslužná rutina může být nahrazena jinou nebo nahrazujete Obslužná rutina nastavením jiného souboru DLL nebo spustitelného souboru.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

V tomto příkladu když selže přidělování je kontrola předána MyNewHandler. Argument předaný MyNewHandler je počet bajtů. Hodnota vrácená z MyNewHandler je příznak označující, zda je třeba opakovat přidělení: Nenulová hodnota označuje, že je třeba opakovat přidělení a nulová hodnota označuje, že se nepodařilo přidělit.

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
