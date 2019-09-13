---
title: _cexit, _c_exit
ms.date: 11/04/2016
api_name:
- _c_exit
- _cexit
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
ms.openlocfilehash: aa25d73bef1d85adfed77ba926e2d381e02e45e8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939258"
---
# <a name="_cexit-_c_exit"></a>_cexit, _c_exit

Provede operace vyčištění a vrátí se bez ukončení procesu.

## <a name="syntax"></a>Syntaxe

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Poznámky

Funkce **_cexit** volá v pořadí posledních v, First-out (LIFO) funkce zaregistrované v **atexit** a **_onexit**. **_Cexit** vyprázdní všechny vstupně-výstupní vyrovnávací paměti a před vrácením zavře všechny otevřené streamy. **_c_exit** je stejná jako **_exit** , ale vrátí se do volajícího procesu bez zpracování **atexit** nebo **_onexit** nebo vyprázdnění vyrovnávací paměti datového proudu. V následující tabulce je uvedeno chování funkce **Exit**, **_exit**, **_cexit**a **_c_exit** .

|Funkce|Chování|
|--------------|--------------|
|**exit**|Provede kompletní postupy ukončení knihovny jazyka C, ukončí proces a ukončí se zadaným kódem stavu.|
|**_exit**|Provádí rychlé postupy ukončení knihovny jazyka C, ukončí proces a ukončí se zadaným stavovým kódem.|
|**_cexit**|Provede kompletní postupy ukončení knihovny jazyka C a vrátí se volajícímu, ale neukončí proces.|
|**_c_exit**|Provede rychlé postupy ukončení knihovny jazyka C a vrátí se volajícímu, ale neukončí proces.|

Při volání funkce **_cexit** nebo **_c_exit** nejsou volány destruktory pro všechny dočasné nebo automatické objekty, které existují v době volání. Automatický objekt je objekt, který je definován ve funkci, kde objekt není deklarován jako static. Dočasný objekt je objekt vytvořený kompilátorem. Chcete-li odstranit automatický objekt před voláním **_cexit** nebo **_c_exit**, explicitně zavolejte destruktor pro objekt následujícím způsobem:

```cpp
myObject.myClass::~myClass( );
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cexit**|\<Process. h >|
|**_c_exit**|\<Process. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
