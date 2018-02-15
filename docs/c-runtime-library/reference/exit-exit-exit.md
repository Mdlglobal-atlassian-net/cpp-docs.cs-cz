---
title: "ukončení, _exit –, _exit – | Microsoft Docs"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed4835662a53f3cb19b47818a9d6adfb3dfb2930
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="exit-exit-exit"></a>exit, _Exit, _exit

Ukončí proces volání. `exit` Funkce ukončí ho po vyčištění; `_exit` a `_Exit` okamžitě ho ukončit.

> [!NOTE]
> Vypnout aplikaci pomocí univerzální platformu Windows (UWP), s výjimkou testování nebo ladění scénáře nepoužívejte tuto metodu. Zavřete aplikaci ve Store způsoby programový nebo uživatelského rozhraní nejsou povolené podle požadavků [Microsoft Store zásady](/legal/windows/agreements/store-policies). Další informace najdete v tématu [životního cyklu aplikace pro UPW](/windows/uwp/launch-resume/app-lifecycle). Další informace o aplikacích pro Windows 10 najdete v tématu [postupy, příručky pro aplikace pro Windows 10](http://go.microsoft.com/fwlink/p/?linkid=619133).

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

_Stav_  
Ukončovací kód stavu.

## <a name="remarks"></a>Poznámky

`exit`, `_Exit` a `_exit` funkce ukončit proces volání. `exit` Funkce volá destruktory pro místní objekty, pak zavolá – v pořadí last-in-first-out (LIFO) – funkce, které jsou registrovány `atexit` a `_onexit`a pak vyprázdnění všech vyrovnávací paměti souboru předtím, než ho ukončí proces. `_Exit` a `_exit` funkce ukončit proces bez zničení objektů místní nebo zpracování `atexit` nebo `_onexit` funkce a bez vyprázdnění vyrovnávací paměti datového proudu.

I když `exit`, `_Exit` a `_exit` volání nevrátí hodnotu, hodnotu v _stav_ je k dispozici na hostitelském prostředí nebo volání proces čekání, pokud takové existuje, po ukončení procesu. Obvykle se nastaví volajícího _stav_ hodnotu na 0, budou znamenat normální ukončovací nebo na jinou hodnotu indikující chybu. _Stav_ hodnota je k dispozici pro operační systém dávkovém příkazu `ERRORLEVEL` a je reprezentované pomocí jedné z dvě konstanty: `EXIT_SUCCESS`, který představuje hodnotu 0, nebo `EXIT_FAILURE`, představuje hodnotu 1.

`exit`, `_Exit`, `_exit`, `quick_exit`, `_cexit`, A `_c_exit` funkce chovat následujícím způsobem.

|Funkce|Popis|
|--------------|-----------------|
|`exit`|Provede dokončení procedury ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód na hostitelském prostředí.|
|`_Exit`|Provede minimální postupy ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód na hostitelském prostředí.|
|`_exit`|Provede minimální postupy ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód na hostitelském prostředí.|
|`quick_exit`|Provede rychlé postupy ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód, který má hostitelské prostředí.|
|`_cexit`|Provádí kompletní C knihovny ukončení postupy a vrátí volajícímu. Nelze ukončit proces.|
|`_c_exit`|Provede minimální C knihovny ukončení postupy a vrátí volajícímu. Nelze ukončit proces.|

Při volání `exit`, `_Exit` nebo `_exit` nejsou volat funkci, destruktory pro dočasné nebo automatické objekty, které existují v čase volání. Automatické objekt je nestatické místní objekt definovaný ve funkci. Dočasný objekt je objekt, který byl vytvořený v kompilátoru, jako je například hodnotu vrácenou z volání funkce. Chcete-li odstranit Automatická objekt před voláním `exit`, `_Exit`, nebo `_exit`, explicitní volání destruktoru objektu, jak je vidět tady:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Pro volání funkce `DLL_PROCESS_ATTACH` z funkce `exit` nepoužívejte hodnotu `DllMain`. Chcete-li ukončit `DLLMain` fungovat, vrátí `FALSE` z `DLL_PROCESS_ATTACH`.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|`exit`, `_Exit`, `_exit`|\<Process.h > nebo \<stdlib.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)  
[abort](../../c-runtime-library/reference/abort.md)  
[atexit](../../c-runtime-library/reference/atexit.md)  
[_cexit, _c_exit](../../c-runtime-library/reference/cexit-c-exit.md)  
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)  
[_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)  
[quick_exit](../../c-runtime-library/reference/quick-exit1.md)  
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)  
[system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)  
