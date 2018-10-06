---
title: Konec, _Exit, _exit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _exit
- exit
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
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb5bd1ef619c899a6b0faab33104a579fdb9f1d0
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821271"
---
# <a name="exit-exit-exit"></a>ukončit, _Exit, _exit

Ukončí volající proces. **Ukončit** funkce skončí po vyčištění **_exit** a **_Exit** ukončit okamžitě.

> [!NOTE]
> Nepoužívejte tuto metodu k vypnutí aplikace univerzální platformy Windows (UPW), s výjimkou testování nebo ladění scénářů. Zavření aplikace pro Store způsoby programátorské nebo uživatelské rozhraní nejsou povoleny podle [zásady Microsoft Store](/legal/windows/agreements/store-policies). Další informace najdete v tématu [životního cyklu aplikace pro UPW](/windows/uwp/launch-resume/app-lifecycle). Další informace o aplikacích pro Windows 10 najdete v tématu [postupy příručky pro aplikace pro Windows 10](https://developer.microsoft.com/windows/apps).

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
Ukončovací kód stavu.

## <a name="remarks"></a>Poznámky

**Ukončit**, **_Exit** a **_exit** funkce ukončí volající proces. **Ukončit** volá funkci pro místní objekty, pak zavolá – v pořadí last-in-first-out (LIFO) – funkce, které jsou registrovány **atexit** a **_onexit**a potom vyprázdní všechny vyrovnávací paměti souborů než proces ukončí. **_Exit** a **_exit** funkce ukončit bez zničení objektů thread local nebo zpracování **atexit** nebo **_onexit**funkce a bez vyprazdňování vyrovnávací paměti datového proudu.

I když **ukončit**, **_Exit** a **_exit** volání nesmí vracet hodnotu, hodnota v *stav* je k dispozici do hostitelského prostředí nebo čeká volajícího procesu, pokud nějaký existuje – po ukončení procesu. Obvykle, nastaví volajícího *stav* hodnotu 0 udávající normální ukončení nebo na jinou hodnotu udávající chybu. *Stav* hodnota není k dispozici k příkazu batch operačního systému **ERRORLEVEL** a je reprezentována jednou ze dvou konstant: **EXIT_SUCCESS**, která představuje hodnotu 0 nebo **EXIT_FAILURE**, která představuje hodnotu 1.

**Ukončit**, **_Exit**, **_exit**, **quick_exit**, **_cexit –**, a **_c_exit –** funkce se chovají následovně.

|Funkce|Popis|
|--------------|-----------------|
|**ukončení**|Provádí kompletní postupy ukončení knihovny jazyka C, ukončí proces a poskytuje zadaným stavovým kódem do hostitelského prostředí.|
|**_Exit**|Provádí minimální postupy ukončení knihovny jazyka C, ukončí proces a poskytuje zadaným stavovým kódem do hostitelského prostředí.|
|**_exit**|Provádí minimální postupy ukončení knihovny jazyka C, ukončí proces a poskytuje zadaným stavovým kódem do hostitelského prostředí.|
|**quick_exit**|Provádí rychlé postupy ukončení knihovny jazyka C, ukončí proces a poskytuje zadaným stavovým kódem do hostitelského prostředí.|
|**_cexit**|Provádí kompletní postupy ukončení knihovny jazyka C a vrátí řízení volajícímu. Nelze ukončit proces.|
|**_c_exit**|Provádí minimální postupy ukončení knihovny jazyka C a vrátí řízení volajícímu. Nelze ukončit proces.|

Při volání **ukončit**, **_Exit** nebo **_exit** funkce, nejsou volány destruktory dočasných nebo automatických objektů, které existují v okamžiku volání. Automatický objekt je definován ve funkci nestatická místní objekt. Dočasný objekt je objekt, který je vytvořen kompilátorem, jako je například hodnota vrácená volání funkce. Chcete-li zničit automatický objekt před voláním **ukončit**, **_Exit**, nebo **_exit**, explicitně zavolejte destruktor objektu, jak je znázorněno zde:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Nepoužívejte **DLL_PROCESS_ATTACH** volat **ukončit** z **DllMain**. Pro ukončení **DLLMain** fungovat, vraťte **FALSE** z **DLL_PROCESS_ATTACH**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**Ukončete**, **_Exit**, **_exit**|\<Process.h > nebo \<stdlib.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
