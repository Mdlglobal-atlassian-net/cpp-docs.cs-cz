---
title: _execlp, _wexeclp
ms.date: 11/04/2016
api_name:
- _wexeclp
- _execlp
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
- api-ms-win-crt-process-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 6ae1805dd00428aee0acca4bcb3ee221bce1d271
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937186"
---
# <a name="_execlp-_wexeclp"></a>_execlp, _wexeclp

Načte a spustí nové podřízené procesy.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Cesta k souboru, který má být spuštěn.

*arg0*, ... *argn*<br/>
Seznam ukazatelů na parametry.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu se tyto funkce nevrátí do volajícího procesu. Návratová hodnota-1 označuje chybu. v takovém případě je nastavena globální proměnná **errno** .

|hodnota **errno**|Popis|
|-------------------|-----------------|
|**E2BIG**|Požadované místo pro argumenty a nastavení prostředí překračuje 32 KB.|
|**EACCES**|U zadaného souboru došlo k narušení uzamčení nebo sdílení.|
|**EINVAL**|Neplatný parametr|
|**EMFILE**|Je otevřeno příliš mnoho souborů (zadaný soubor musí být otevřen, aby bylo možné zjistit, zda je spustitelný).|
|**ENOENT**|Soubor nebo cesta nenalezeny.|
|**ENOEXEC**|Zadaný soubor není spustitelný nebo má neplatný formát spustitelného souboru.|
|**ENOMEM**|K provedení nového procesu není k dispozici dostatek paměti. dostupná paměť je poškozená; nebo existuje neplatný blok, který označuje, že volající proces nebyl správně přidělen.|

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí načte a spustí nový proces, přičemž předá každý argument příkazového řádku jako samostatný parametr a pomocí proměnné prostředí **path** vyhledá soubor, který se má provést.

Funkce **_execlp** ověřují jejich parametry. Pokud je *cmdname* nebo *arg0* ukazatel s hodnotou null nebo prázdný řetězec, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí-1. Nespustí se žádný nový proces.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|--------------|---------------------|---------------------|
|**_execlp**|\<Process. h >|\<errno.h>|
|**_wexeclp**|\<Process. h > \<nebo WCHAR. h >|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_exec, _Wexec Functions](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
