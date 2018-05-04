---
title: _execvp –, _wexecvp – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _execvp
- _wexecvp
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
- _execvp
- wexecvp
- _wexecvp
dev_langs:
- C++
helpviewer_keywords:
- _execvp function
- _wexecvp function
- wexecvp function
- execvp function
ms.assetid: a4db15df-b204-4987-be7c-de84c3414380
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c47154bd999b421c2170118236a899dcc4e2860
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="execvp-wexecvp"></a>_execvp, _wexecvp

Načte a spustí novou podřízené procesy.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _execvp(
   const char *cmdname,
   const char *const *argv
);
intptr_t _wexecvp(
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>Parametry

*cmdname*<br/>
Cesta k souboru provést.

*argv –*<br/>
Pole ukazatele na parametry.

## <a name="return-value"></a>Návratová hodnota

Pokud bylo úspěšné, nevrátí se tyto funkce pro proces volání. Vrácená hodnota -1 označuje chybu, v takovém případě **errno** globální proměnná je nastavená.

|**errno** hodnota|Popis|
|-------------------|-----------------|
|**E2BIG –**|Místo požadované pro argumenty a nastavení prostředí je větší než 32 KB.|
|**EACCES –**|Zadaný soubor došlo k narušení uzamčení nebo sdílení.|
|**EINVAL –**|Neplatný parametr.|
|**EMFILE –**|Příliš mnoho souborů otevřete (zadaný soubor musí být otevřené pro určení, zda je spustitelný soubor).|
|**ENOENT –**|Soubor nebo cesta nebyla nalezena.|
|**ENOEXEC –**|Zadaný soubor není spustitelný soubor nebo má neplatný formát souboru spustitelný soubor.|
|**ENOMEM –**|Nedostatek paměti je k dispozici pro spuštění nový proces; dostupná paměť je poškozená; nebo bloku neplatný existuje, která určuje, že proces volání nebyla přidělena správně.|

Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí načte a spustí nový proces, pole ukazatele předání argumentů příkazového řádku a pomocí **cesta** proměnnou prostředí najít soubor provést.

**_Execvp –** funkcí ověření jejich parametrů. Pokud *cmdname* je ukazatel s hodnotou null, nebo *argv –* je ukazatel s hodnotou null, ukazatel na prázdné pole, nebo pokud pole obsahuje prázdný řetězec jako první argument, tyto funkce vyvolat obslužnou rutinu neplatný parametr jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátí hodnotu -1. Žádný proces se spustí.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|--------------|---------------------|---------------------|
|**_execvp**|\<Process.h >|\<errno.h>|
|**_wexecvp**|\<Process.h > nebo \<wchar.h >|\<errno.h>|

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
