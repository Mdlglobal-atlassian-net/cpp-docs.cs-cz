---
title: _execvpe, _wexecvpe
ms.date: 11/04/2016
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
helpviewer_keywords:
- wexecvpe function
- execvpe function
- _wexecvpe function
- _execvpe function
ms.assetid: c0c3c986-d9c0-4814-a96c-10f0b3092766
ms.openlocfilehash: 064f8b94a9a97795015c09c11cd56e0370dcc60c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431691"
---
# <a name="execvpe-wexecvpe"></a>_execvpe, _wexecvpe

Načte a spustí nový podřízený proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Cesta k souboru pro spuštění.

*argv*<br/>
Pole ukazatelů na parametry.

*envp*<br/>
Pole ukazatelů do nastavení prostředí.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu se tato funkce nevrací do volajícího procesu. Návratová hodnota-1 označuje chybu, v takovém případě **errno** je nastavena globální proměnná.

|**errno** hodnota|Popis|
|-------------------|-----------------|
|**E2BIG**|Místa požadovaného pro argumenty a nastavení prostředí je větší než 32 KB.|
|**EACCES**|Zadaný soubor má narušení uzamčení nebo sdílení.|
|**EMFILE**|Je otevřeno příliš mnoho souborů. (Zadaný soubor musí být otevřen pro určení, zda je spustitelný soubor.)|
|**ENOENT**|Soubor nebo cesta nebyla nalezena.|
|**ENOEXEC**|Zadaný soubor není spustitelný soubor nebo má neplatný formát spustitelného souboru.|
|**ENOMEM**|Není k dispozici ke spuštění nového procesu; není dostatek paměti dostupná paměť byla poškozena; nebo existuje neplatný blok, což znamená, že volající proces nebyl správně přiděleny.|

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí načte a spustí nový proces a předá pole ukazatelů do argumentů příkazového řádku a pole ukazatelů do nastavení prostředí. Tyto funkce používají **cesta** proměnnou prostředí k vyhledání souboru pro spuštění.

**_Execvpe** funkce ověřují své parametry. Pokud *cmdname* je ukazatel s hodnotou null, nebo pokud *argv* je nulový ukazatel, ukazatel na prázdné pole nebo ukazatel na pole, které obsahuje prázdný řetězec jako první argument, tyto funkce vyvolají neplatné Obslužná rutina parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1. Není spuštěn žádný proces.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|--------------|---------------------|---------------------|
|**_execvpe**|\<Process.h >|\<errno.h>|
|**_wexecvpe**|\<Process.h > nebo \<wchar.h >|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [funkce _exec, _wexec](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
