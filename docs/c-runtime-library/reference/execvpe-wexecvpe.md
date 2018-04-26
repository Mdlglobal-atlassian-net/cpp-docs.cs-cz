---
title: _execvpe –, _wexecvpe – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _execvpe
- _wexecvpe
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wexecvpe
- execvpe
- _wexecvpe
- _execvpe
dev_langs:
- C++
helpviewer_keywords:
- wexecvpe function
- execvpe function
- _wexecvpe function
- _execvpe function
ms.assetid: c0c3c986-d9c0-4814-a96c-10f0b3092766
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 808f991fdf3ef8c8739eb148120922e95ec8f35a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="execvpe-wexecvpe"></a>_execvpe, _wexecvpe

Načte a spustí novou podřízené procesy.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _execvpe(
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wexecvpe(
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parametry

*cmdname*<br/>
Cesta k souboru provést.

*argv –*<br/>
Pole ukazatele na parametry.

*envp –*<br/>
Pole ukazatele na nastavení prostředí.

## <a name="return-value"></a>Návratová hodnota

Pokud bylo úspěšné, nevrátí se tyto funkce pro proces volání. Vrácená hodnota -1 označuje chybu, v takovém případě **errno** globální proměnná je nastavená.

|**errno** hodnota|Popis|
|-------------------|-----------------|
|**E2BIG –**|Místo, které je nutné pro argumenty a nastavení prostředí větší než 32 KB.|
|**EACCES –**|Zadaný soubor došlo k narušení uzamčení nebo sdílení.|
|**EMFILE –**|Je otevřeno příliš mnoho souborů. (K určení, zda je spustitelný soubor musí otevřít zadaný soubor.)|
|**ENOENT –**|Soubor nebo cesta nebyla nalezena.|
|**ENOEXEC –**|Zadaný soubor není spustitelný soubor nebo má neplatný formát souboru spustitelný soubor.|
|**ENOMEM –**|Nedostatek paměti je k dispozici pro spuštění nový proces; dostupná paměť je poškozená; nebo neplatný bloku existuje, což naznačuje, že proces volání nebyla přidělena správně.|

Další informace o těchto a dalších návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí načte a spustí nový proces a předá pole ukazatele argumenty příkazového řádku a pole ukazatele na nastavení prostředí. Použijte tyto funkce **cesta** proměnnou prostředí najít soubor provést.

**_Execvpe –** funkcí ověření jejich parametrů. Pokud *cmdname* je ukazatel s hodnotou null, nebo pokud *argv –* ukazatele null, je ukazatel na prázdné pole nebo odkazy na pole, které obsahuje prázdný řetězec jako první argument, tyto funkce vyvolání neplatný Obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátí hodnotu -1. Žádný proces se spustí.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|--------------|---------------------|---------------------|
|**_execvpe**|\<Process.h >|\<errno.h>|
|**_wexecvpe**|\<Process.h > nebo \<wchar.h >|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
