---
title: _execlp, _wexeclp
ms.date: 11/04/2016
apiname:
- _wexeclp
- _execlp
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
- _wexeclp
- wexeclp
- _execlp
helpviewer_keywords:
- execlp function
- _execlp function
- _wexeclp function
- wexeclp function
ms.assetid: 7b179163-4bcd-4d6a-8baf-68f886791928
ms.openlocfilehash: db13263ca4574d59821d5783b9ae83f278fef14d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506636"
---
# <a name="execlp-wexeclp"></a>_execlp, _wexeclp

Načte a spustí nový podřízený proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _execlp(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL
);
intptr_t _wexeclp(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>Parametry

*cmdname*<br/>
Cesta k souboru pro spuštění.

*arg0*,... *argn*<br/>
Seznam ukazatelů na parametry.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu se tato funkce nevrací do volajícího procesu. Návratová hodnota-1 označuje chybu, v takovém případě **errno** je nastavena globální proměnná.

|**errno** hodnota|Popis|
|-------------------|-----------------|
|**E2BIG**|Místo požadované pro argumenty a nastavení prostředí je větší než 32 KB.|
|**EACCES**|Zadaný soubor má narušení uzamčení nebo sdílení.|
|**EINVAL**|Neplatný parametr.|
|**EMFILE**|Příliš mnoho souborů otevřete (zadaný soubor musí být otevřen pro určení, zda je spustitelný).|
|**ENOENT**|Soubor nebo cesta nebyla nalezena.|
|**ENOEXEC**|Zadaný soubor není spustitelný soubor nebo má neplatný formát spustitelného souboru.|
|**ENOMEM**|Není k dispozici ke spuštění nového procesu; není dostatek paměti dostupná paměť byla poškozena; nebo existuje neplatný blok, která udává, že volající proces nebyl správně přidělen.|

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí načte a spustí nový proces, přičemž předá každý argument příkazového řádku jako samostatný parametr a použije **cesta** proměnnou prostředí k vyhledání souboru pro spuštění.

**_Execlp –** funkce ověřují své parametry. Pokud *cmdname* nebo *arg0* je ukazatel s hodnotou null nebo prázdný řetězec, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1. Není spuštěn žádný nový proces.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|--------------|---------------------|---------------------|
|**_execlp**|\<Process.h >|\<errno.h>|
|**_wexeclp**|\<Process.h > nebo \<wchar.h >|\<errno.h>|

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
