---
title: exit, _Exit, _exit
ms.date: 4/2/2020
api_name:
- _exit
- exit
- _o__exit
- _o_exit
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
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
ms.openlocfilehash: a1c0eeaa6d66e91b913ce7940d37409fc4f6ac29
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909672"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

Ukončí volající proces. Funkce **Exit** po vyčištění ji ukončí; **_exit** a **_Exit** okamžitě ukončit.

> [!NOTE]
> Tuto metodu nepoužívejte k ukončení aplikace Univerzální platforma Windows (UWP), s výjimkou scénářů testování nebo ladění. Programové a uživatelské možnosti pro zavření aplikace ze Storu nejsou povolené podle [zásad Microsoft Store](/legal/windows/agreements/store-policies). Další informace najdete v tématu [životní cyklus aplikace UWP](/windows/uwp/launch-resume/app-lifecycle). Další informace o aplikacích pro Windows 10 najdete v tématu [návody pro aplikace pro Windows 10](https://developer.microsoft.com/windows/apps).

## <a name="syntax"></a>Syntaxe

```C
void exit(
   int const status
);
void _Exit(
   int const status
);
void _exit(
   int const status
);
```

### <a name="parameters"></a>Parametry

*stav*<br/>
Stavový kód ukončení.

## <a name="remarks"></a>Poznámky

Funkce **Exit**, **_Exit** a **_exit** ukončí volající proces. Funkce **Exit** volá destruktory pro objekty lokální z vlákna a pak volá – v pořadí posledního navýšení prvního objektu (LIFO) – funkce registrované **atexit** a **_onexit**a poté vyprázdní všechny vyrovnávací paměti souborů předtím, než proces ukončí. Funkce **_Exit** a **_exit** ukončí proces bez zničení místních objektů vlákna nebo zpracování funkcí **atexit** nebo **_onexit** a bez vyprázdnění vyrovnávací paměti datového proudu.

I když volání **Exit**, **_Exit** a **_exit** nevrací hodnotu, hodnota ve *stavu* je zpřístupněna hostitelskému prostředí nebo čeká na volajícím procesu, pokud existuje, po ukončení procesu. Obvykle volající nastaví hodnotu *stav* na 0, aby označovala normální ukončení, nebo na jinou hodnotu, která označuje chybu. *Stavová* hodnota je k dispozici pro příkaz dávkového příkazu **errorlevel** pro operační systém a je reprezentovaná jednou ze dvou konstant: **EXIT_SUCCESS**, která představuje hodnotu 0 nebo **EXIT_FAILURE**, která představuje hodnotu 1.

Funkce **Exit**, **_Exit**, **_exit**, **quick_exit**, **_cexit**a **_c_exit** se chovají následujícím způsobem.

|Funkce|Popis|
|--------------|-----------------|
|**akci**|Provede kompletní postupy ukončení knihovny jazyka C, ukončí proces a poskytne dodaný stavový kód hostitelskému prostředí.|
|**_Exit**|Provede minimální postupy ukončení knihovny jazyka C, ukončí proces a poskytne dodaný stavový kód hostitelskému prostředí.|
|**_exit**|Provede minimální postupy ukončení knihovny jazyka C, ukončí proces a poskytne dodaný stavový kód hostitelskému prostředí.|
|**quick_exit**|Provádí rychlé postupy ukončení knihovny jazyka C, ukončí proces a poskytne poskytnutému kódu stavu hostitelskému prostředí.|
|**_cexit**|Provede kompletní postupy ukončení knihovny jazyka C a vrátí se volajícímu. Neukončí proces.|
|**_c_exit**|Provede minimální postupy ukončení knihovny jazyka C a vrátí se volajícímu. Neukončí proces.|

Při volání funkce **Exit**, **_Exit** nebo **_exit** nejsou volány destruktory pro všechny dočasné nebo automatické objekty, které existují v době volání. Automatický objekt je nestatický lokální objekt definovaný ve funkci. Dočasný objekt je objekt, který je vytvořen kompilátorem, jako například hodnota vrácená voláním funkce. Chcete-li odstranit automatický objekt před voláním funkce **Exit**, **_Exit**nebo **_exit**, explicitně zavolejte destruktor pro objekt, jak je znázorněno zde:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Nepoužívejte **DLL_PROCESS_ATTACH** k volání funkce **Exit** z **DllMain**. Chcete-li ukončit funkci **DllMain** , vraťte **hodnotu false** z **DLL_PROCESS_ATTACH**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**Exit**, **_Exit** **_exit**|\<Process. h> \<nebo Stdlib. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_exit.c
// This program returns an exit code of 1. The
// error code could be tested in a batch file.

#include <stdlib.h>

int main( void )
{
   exit( 1 );
}
```

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[přerušit](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, _wexec funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, _wspawn Funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
