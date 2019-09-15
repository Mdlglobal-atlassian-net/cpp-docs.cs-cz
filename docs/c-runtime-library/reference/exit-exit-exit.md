---
title: exit, _Exit, _exit
ms.date: 01/02/2018
api_name:
- _exit
- exit
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
ms.openlocfilehash: fd988ca6339c00b454d673d3bec6f137753ac83a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941660"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

Ukončí volající proces. Funkce **Exit** po vyčištění ji ukončí; **_exit** a **_exit** se okamžitě ukončí.

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

*status*<br/>
Stavový kód ukončení.

## <a name="remarks"></a>Poznámky

Funkce **Exit**, **_Exit** a **_Exit** ukončí volající proces. Funkce **Exit** volá destruktory pro objekty lokální z vlákna a pak volá – v pořadí posledních vstupů (LIFO) – funkce, které jsou zaregistrované pomocí **atexit** a **_onexit**, a pak vyprázdní všechny vyrovnávací paměti souborů před tím, než se ukončí. přihlášení. Funkce **_Exit** a **_Exit** ukončí proces bez zničení místních objektů vlákna nebo zpracování **atexit** nebo **_onexit** funkcí a bez vyprázdnění vyrovnávací paměti datového proudu.

I když volání **Exit**, **_Exit** a **_Exit** nevrací hodnotu, hodnota ve *stavu* je zpřístupněna hostitelskému prostředí nebo čeká na volajícím procesu, pokud existuje, po ukončení procesu. Obvykle volající nastaví hodnotu *stav* na 0, aby označovala normální ukončení, nebo na jinou hodnotu, která označuje chybu. *Stavová* hodnota je k dispozici pro příkaz dávkového příkazu **errorlevel** a je reprezentovaná jednou ze dvou konstant: **EXIT_SUCCESS**, která představuje hodnotu 0 nebo **EXIT_FAILURE**, která představuje hodnotu 1.

Funkce **Exit**, **_Exit**, **_Exit**, **quick_exit**, **_cexit**a **_c_exit** se chovají takto.

|Funkce|Popis|
|--------------|-----------------|
|**exit**|Provede kompletní postupy ukončení knihovny jazyka C, ukončí proces a poskytne dodaný stavový kód hostitelskému prostředí.|
|**_Exit**|Provede minimální postupy ukončení knihovny jazyka C, ukončí proces a poskytne dodaný stavový kód hostitelskému prostředí.|
|**_exit**|Provede minimální postupy ukončení knihovny jazyka C, ukončí proces a poskytne dodaný stavový kód hostitelskému prostředí.|
|**quick_exit**|Provádí rychlé postupy ukončení knihovny jazyka C, ukončí proces a poskytne poskytnutému kódu stavu hostitelskému prostředí.|
|**_cexit**|Provede kompletní postupy ukončení knihovny jazyka C a vrátí se volajícímu. Neukončí proces.|
|**_c_exit**|Provede minimální postupy ukončení knihovny jazyka C a vrátí se volajícímu. Neukončí proces.|

Při volání funkce **Exit**, **_Exit** nebo **_Exit** nejsou volány destruktory pro všechny dočasné nebo automatické objekty, které existují v době volání. Automatický objekt je nestatický lokální objekt definovaný ve funkci. Dočasný objekt je objekt, který je vytvořen kompilátorem, jako například hodnota vrácená voláním funkce. Chcete-li odstranit automatický objekt před voláním funkce **Exit**, **_Exit**nebo **_Exit**, explicitně zavolejte destruktor pro objekt, jak je znázorněno zde:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Nepoužívejte **DLL_PROCESS_ATTACH** k volání funkce **Exit** z **DllMain**. Chcete-li ukončit funkci **DllMain** , vraťte **hodnotu false** z **DLL_PROCESS_ATTACH**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**exit**, **_Exit**, **_exit**|\<Process. h > \<nebo Stdlib. h >|

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

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
