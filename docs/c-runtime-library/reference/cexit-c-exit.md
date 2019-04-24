---
title: _cexit, _c_exit
ms.date: 11/04/2016
apiname:
- _c_exit
- _cexit
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
ms.openlocfilehash: a075e8a8e965a195765b86ffa21fed0915dbf5ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335487"
---
# <a name="cexit-cexit"></a>_cexit, _c_exit

Provádí operace vyčištění a vrátí bez ukončení procesu.

## <a name="syntax"></a>Syntaxe

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Poznámky

**_Cexit –** volání v poslední dovnitř, první (ven LIFO) objednávky, funkce registrované pomocí funkcí **atexit** a **_onexit**. Potom **_cexit –** vyprázdní všechny vyrovnávací paměti vstupně-výstupní operace a zavře všechny otevřené datové proudy před vrácením. **_c_exit –** je stejný jako **_exit** , ale vrací do volajícího procesu bez zpracování **atexit** nebo **_onexit** nebo vyprazdňování vyrovnávací paměti datového proudu. Chování **ukončit**, **_exit**, **_cexit –**, a **_c_exit –** je uveden v následující tabulce.

|Funkce|Chování|
|--------------|--------------|
|**exit**|Provádí kompletní postupy ukončení knihovny jazyka C, ukončí proces a se zadaným stavovým kódem se ukončí.|
|**_exit**|Provádí rychlé postupy ukončení knihovny jazyka C, ukončí proces a se zadaným stavovým kódem se ukončí.|
|**_cexit**|Provádí kompletní postupy ukončení knihovny jazyka C a vrátí volajícímu, ale neukončí proces.|
|**_c_exit**|Provádí rychlé postupy ukončení knihovny jazyka C a vrátí volajícímu, ale neukončí proces.|

Při volání **_cexit –** nebo **_c_exit –** funkcí, nejsou volány destruktory dočasných nebo automatických objektů, které existují v okamžiku volání. Automatický objekt je objekt, který je definován ve funkci, kde tento objekt není deklarován jako statický. Dočasný objekt je objekt vytvořený kompilátorem. Chcete-li zničit automatický objekt před voláním **_cexit –** nebo **_c_exit –**, explicitně zavolejte destruktor objektu následovně:

```cpp
myObject.myClass::~myClass( );
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
