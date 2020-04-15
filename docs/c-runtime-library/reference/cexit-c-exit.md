---
title: _cexit, _c_exit
ms.date: 4/2/2020
api_name:
- _c_exit
- _cexit
- _o__cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
ms.openlocfilehash: 9eb856efca054423465aa7d30092edaf83a65eeb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333535"
---
# <a name="_cexit-_c_exit"></a>_cexit, _c_exit

Provádí operace vyčištění a vrátí bez ukončení procesu.

## <a name="syntax"></a>Syntaxe

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Poznámky

Funkce **_cexit** volání v pořadí last-in, first-out (LIFO), funkce registrované **atexit** a **_onexit**. Potom **_cexit** vyprázdní všechny vstupně-v vyrovnávací paměti a zavře všechny otevřené datové proudy před návratem. **_c_exit** je stejný jako **_exit** ale vrátí se do volajícího procesu bez zpracování **atexit** nebo **_onexit** nebo vyprázdnění datové ho dpuštěné. Chování **ukončovací**, **_exit**, **_cexit**a **_c_exit** je uvedeno v následující tabulce.

|Funkce|Chování|
|--------------|--------------|
|**Ukončit**|Provádí úplné procedury ukončení knihovny C, ukončí proces a ukončí zadaný stavový kód.|
|**_exit**|Provádí rychlé postupy ukončení knihovny C, ukončí proces a ukončí s zadaným stavovým kódem.|
|**_cexit**|Provádí úplné procedury ukončení knihovny C a vrátí volajícímu, ale neukončí proces.|
|**_c_exit**|Provádí rychlé postupy ukončení knihovny C a vrátí volajícímu, ale neukončí proces.|

Při volání **_cexit** nebo **_c_exit** funkce, nejsou volány destruktory pro všechny dočasné nebo automatické objekty, které existují v době volání. Automatický objekt je objekt, který je definován ve funkci, kde objekt není deklarován jako statický. Dočasný objekt je objekt vytvořený kompilátorem. Chcete-li zničit automatický objekt před voláním **_cexit** nebo **_c_exit**, explicitně volání destruktoru pro objekt, a to následovně:

```cpp
myObject.myClass::~myClass( );
```

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[Přerušení](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
