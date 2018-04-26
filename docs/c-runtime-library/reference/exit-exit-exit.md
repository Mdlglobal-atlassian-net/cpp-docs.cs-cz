---
title: ukončení, _exit –, _exit – | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: e682d10fe15b611ff9ceb363d7d8593e41f386d6
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="exit-exit-exit"></a>ukončení, _exit –, _exit –

Ukončí proces volání. **Ukončete** funkce ukončí ho po vyčištění; **_exit –** a **_exit –** okamžitě ho ukončit.

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

*Stav* ukončovací kód stavu.

## <a name="remarks"></a>Poznámky

**Ukončete**, **_exit –** a **_exit –** funkce ukončit proces volání. **Ukončete** funkce volá destruktory pro místní objekty, pak zavolá – v pořadí last-in-first-out (LIFO) – funkce, které jsou registrovány **atexit** a **_onexit –**a pak vyprázdnění všech vyrovnávací paměti souboru předtím, než ho ukončí proces. **_Exit –** a **_exit –** funkce ukončit proces bez zničení objektů místní nebo zpracování **atexit** nebo **_onexit –**funkce a bez vyprázdnění vyrovnávací paměti datového proudu.

I když **ukončete**, **_exit –** a **_exit –** volání nevrátí hodnotu, hodnotu v *stav* je k dispozici pro hostitelské prostředí nebo čeká se na volání procesu, pokud takové existuje, po ukončení procesu. Obvykle se nastaví volajícího *stav* hodnotu na 0, budou znamenat normální ukončovací nebo na jinou hodnotu indikující chybu. *Stav* hodnota je k dispozici pro operační systém dávkovém příkazu **ERRORLEVEL** a je reprezentované pomocí jedné z dvě konstanty: **exit_success –**, která reprezentuje hodnotu 0 nebo **exit_failure –**, která představuje hodnotu 1.

**Ukončete**, **_exit –**, **_exit –**, **quick_exit**, **_cexit –**, a **_c_exit –** funkce chovat následujícím způsobem.

|Funkce|Popis|
|--------------|-----------------|
|**Ukončení**|Provede dokončení procedury ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód na hostitelském prostředí.|
|**_Exit**|Provede minimální postupy ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód na hostitelském prostředí.|
|**_exit**|Provede minimální postupy ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód na hostitelském prostředí.|
|**quick_exit**|Provede rychlé postupy ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód, který má hostitelské prostředí.|
|**_cexit**|Provádí kompletní C knihovny ukončení postupy a vrátí volajícímu. Nelze ukončit proces.|
|**_c_exit**|Provede minimální C knihovny ukončení postupy a vrátí volajícímu. Nelze ukončit proces.|

Při volání **ukončete**, **_exit –** nebo **_exit –** funkce, nejsou volána destruktory pro dočasné nebo automatické objekty, které existují v čase volání. Automatické objekt je nestatické místní objekt definovaný ve funkci. Dočasný objekt je objekt, který byl vytvořený v kompilátoru, jako je například hodnotu vrácenou z volání funkce. Zrušení automatického objekt před voláním **ukončete**, **_exit –**, nebo **_exit –**, explicitní volání destruktoru objektu, jak je vidět tady:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

Nepoužívejte **DLL_PROCESS_ATTACH** volat **ukončete** z **DllMain**. Chcete-li ukončit **DLLMain** fungovat, vrátí **FALSE** z **DLL_PROCESS_ATTACH**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**Ukončete**, **_exit –**, **_exit –**|\<Process.h > nebo \<stdlib.h >|

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

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
