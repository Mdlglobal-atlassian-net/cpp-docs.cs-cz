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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 78675ef91c2ab68e18f6111b4908886017ae1f79
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917151"
---
# <a name="_cexit-_c_exit"></a>_cexit, _c_exit

Provede operace vyčištění a vrátí se bez ukončení procesu.

## <a name="syntax"></a>Syntaxe

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Poznámky

Funkce **_cexit** volá v pořadí posledních v, First-out (LIFO) funkce zaregistrované v **atexit** a **_onexit**. Pak **_cexit** vyprázdní všechny vstupně-výstupní vyrovnávací paměti a před vrácením zavře všechny otevřené streamy. **_c_exit** je stejná jako **_exit** , ale vrátí se do volajícího procesu bez zpracování **atexit** nebo **_onexit** nebo vyprázdnění vyrovnávací paměti datového proudu. V následující tabulce je uvedeno chování funkce **Exit**, **_exit**, **_cexit**a **_c_exit** .

|Funkce|Chování|
|--------------|--------------|
|**akci**|Provede kompletní postupy ukončení knihovny jazyka C, ukončí proces a ukončí se zadaným kódem stavu.|
|**_exit**|Provádí rychlé postupy ukončení knihovny jazyka C, ukončí proces a ukončí se zadaným stavovým kódem.|
|**_cexit**|Provede kompletní postupy ukončení knihovny jazyka C a vrátí se volajícímu, ale neukončí proces.|
|**_c_exit**|Provede rychlé postupy ukončení knihovny jazyka C a vrátí se volajícímu, ale neukončí proces.|

Při volání funkce **_cexit** nebo **_c_exit** nejsou volány destruktory pro všechny dočasné nebo automatické objekty, které existují v době volání. Automatický objekt je objekt, který je definován ve funkci, kde objekt není deklarován jako static. Dočasný objekt je objekt vytvořený kompilátorem. Chcete-li odstranit automatický objekt před voláním **_cexit** nebo **_c_exit**, explicitně zavolejte destruktor pro objekt následujícím způsobem:

```cpp
myObject.myClass::~myClass( );
```

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cexit**|\<Process. h>|
|**_c_exit**|\<Process. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[přerušit](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn Funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
