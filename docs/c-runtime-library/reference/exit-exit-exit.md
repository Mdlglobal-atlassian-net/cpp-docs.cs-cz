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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 5bdb5ff5c8309e03a49f9518f65a45d5757e9bfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347639"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

Ukončí proces volání. Funkce **ukončení** ukončí po vyčištění; **_exit** a **_Exit** okamžitě to ukončit.

> [!NOTE]
> Tuto metodu nepoužívejte k vypnutí aplikace univerzální platformy Windows (UPW), s výjimkou scénářů testování nebo ladění. Programové nebo způsoby, jak zavřít aplikaci store, nejsou povoleny v souladu se [zásadami Microsoft Storu](/legal/windows/agreements/store-policies). Další informace naleznete v [tématu Životní cyklus aplikace UPW](/windows/uwp/launch-resume/app-lifecycle). Další informace o aplikacích pro Windows 10 najdete v [tématu Návody k aplikacím pro Windows 10](https://developer.microsoft.com/windows/apps).

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

*Stav*<br/>
Ukončovací stavový kód.

## <a name="remarks"></a>Poznámky

Funkce **ukončení**, **_Exit** a **_exit** ukončí proces volání. Funkce **ukončení** volá destruktory pro místní objekty podprocesu, pak volání – v pořadí poslední in-first-out (LIFO) funkce, které jsou registrovány **atexit** a **_onexit**a potom vyprázdní všechny vyrovnávací paměti souborů před ukončením procesu. Funkce **_Exit** a **_exit** ukončit proces bez zničení objektů místní ho vlákna nebo zpracování **funkce atexit** nebo **_onexit** a bez vyprázdnění vyrovnávacípaměti datového proudu.

Přestože **volání ukončení**, **_Exit** a **_exit** nevrací hodnotu, hodnota *stavu* je k dispozici hostitelskému prostředí nebo čekající proces volání, pokud existuje, po ukončení procesu. Obvykle volající nastaví hodnotu *stavu* 0 označuje normální ukončení nebo na jinou hodnotu označující chybu. Hodnota *stavu* je k dispozici pro příkaz **ERRORLEVEL** dávky operačního systému a je reprezentována jednou ze dvou konstant: **EXIT_SUCCESS**, která představuje hodnotu 0 nebo **EXIT_FAILURE**, která představuje hodnotu 1.

Funkce **exit**, **_Exit**, **_exit**, **quick_exit**, **_cexit**a **_c_exit** se chovají následujícím způsobem.

|Funkce|Popis|
|--------------|-----------------|
|**Ukončit**|Provádí úplné procedury ukončení knihovny C, ukončí proces a poskytne zadaný stavový kód hostitelskému prostředí.|
|**_Exit**|Provádí minimální procedury ukončení knihovny C, ukončí proces a poskytne zadaný stavový kód hostitelskému prostředí.|
|**_exit**|Provádí minimální procedury ukončení knihovny C, ukončí proces a poskytne zadaný stavový kód hostitelskému prostředí.|
|**quick_exit**|Provádí rychlé procedury ukončení knihovny C, ukončí proces a poskytuje zadaný stavový kód hostitelskému prostředí.|
|**_cexit**|Provede úplné procedury ukončení knihovny C a vrátí volajícímu. Neukončí proces.|
|**_c_exit**|Provádí minimální procedury ukončení knihovny C a vrátí volajícímu. Neukončí proces.|

Při volání **exit**, **_Exit** nebo **_exit** funkce, nejsou volány destruktory pro všechny dočasné nebo automatické objekty, které existují v době volání. Automatický objekt je nestatický místní objekt definovaný ve funkci. Dočasný objekt je objekt, který je vytvořen kompilátorem, například hodnota vrácená voláním funkce. Chcete-li zničit automatický objekt před voláním **exit**, **_Exit**nebo **_exit**, explicitně volejte destruktor objektu, jak je znázorněno zde:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Nepoužívejte **DLL_PROCESS_ATTACH** k volání **ukončení** z **DllMain**. Chcete-li ukončit funkci **DLLMain,** vraťte funkci **FALSE** z **DLL_PROCESS_ATTACH**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_Exit** **_Exit**, **_exit**|\<process.h> \<nebo stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
[Přerušení](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, _wexec funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, _wspawn funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
