---
title: _execle –, _wexecle – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _execle
- _wexecle
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
- wexecle
- _execle
- _wexecle
dev_langs:
- C++
helpviewer_keywords:
- wexecle function
- execle function
- _wexecle function
- _execle function
ms.assetid: 75efa9c5-96b7-4e23-acab-06258901f63a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 519cdb78132c50513ae3197985de7faaceff7c91
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400639"
---
# <a name="execle-wexecle"></a>_execle, _wexecle

Načte a spustí novou podřízené procesy.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _execle(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wexecle(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL,
   const char *const *envp
);
```

### <a name="parameters"></a>Parametry

*cmdname*<br/>
Cesta k souboru provést.

*arg0*,... *argn*<br/>
Seznam ukazatele na parametry.

*envp –*<br/>
Pole ukazatele na nastavení prostředí.

## <a name="return-value"></a>Návratová hodnota

Pokud bylo úspěšné, nevrátí se tyto funkce pro proces volání. Vrácená hodnota -1 označuje chybu, v takovém případě **errno** globální proměnná je nastavená.

|**errno** hodnota|Popis|
|-------------------|-----------------|
|**E2BIG –**|Místo, které je nutné pro argumenty a nastavení prostředí větší než 32 KB.|
|**EACCES –**|Zadaný soubor došlo k narušení uzamčení nebo sdílení.|
|**EINVAL –**|Neplatný parametr.|
|**EMFILE –**|Je otevřeno příliš mnoho souborů. (K určení, zda je spustitelný soubor musí otevřít zadaný soubor.)|
|**ENOENT –**|Soubor nebo cesta nebyla nalezena.|
|**ENOEXEC –**|Zadaný soubor není spustitelný soubor nebo má neplatný formát souboru spustitelný soubor.|
|**ENOMEM –**|Nedostatek paměti je k dispozici pro spuštění nový proces; dostupná paměť je poškozená; nebo neplatný bloku existuje, což naznačuje, že proces volání nebyla přidělena správně.|

Další informace o těchto návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí načte a spustí nový proces a předá každý argument příkazového řádku jako samostatného parametru a předá pole ukazatele nastavení prostředí.

**_Execle –** funkcí ověření jejich parametrů. Pokud *cmdname* nebo *arg0* ukazatele null nebo prázdný řetězec, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátí hodnotu -1. Žádný nový proces se spustí.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|--------------|---------------------|---------------------|
|**_execle**|\<Process.h >|\<errno.h>|
|**_wexecle**|\<Process.h > nebo \<wchar.h >|\<errno.h>|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
