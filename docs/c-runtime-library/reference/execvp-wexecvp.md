---
title: _execvp, _wexecvp
ms.date: 4/2/2020
api_name:
- _execvp
- _wexecvp
- _o__execvp
- _o__wexecvp
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _execvp
- wexecvp
- _wexecvp
helpviewer_keywords:
- _execvp function
- _wexecvp function
- wexecvp function
- execvp function
ms.assetid: a4db15df-b204-4987-be7c-de84c3414380
ms.openlocfilehash: 224649abffd836667641f3c83e5f777f8752d7bd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915922"
---
# <a name="_execvp-_wexecvp"></a>_execvp, _wexecvp

Načte a spustí nové podřízené procesy.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Cesta k souboru, který má být spuštěn.

*argv*<br/>
Pole ukazatelů na parametry.

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

Každá z těchto funkcí načte a spustí nový proces, předá pole ukazatelů na argumenty příkazového řádku a pomocí proměnné prostředí **path** vyhledá soubor, který se má provést.

Funkce **_execvp** ověřují jejich parametry. Pokud je *cmdname* ukazatel s hodnotou null, nebo je *argv* ukazatel s hodnotou null, ukazatel na prázdné pole, nebo pokud pole obsahuje prázdný řetězec jako první argument, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí-1. Nespustí se žádný proces.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|--------------|---------------------|---------------------|
|**_execvp**|\<Process. h>|\<errno. h>|
|**_wexecvp**|\<Process. h> \<nebo WCHAR. h>|\<errno. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_exec _Wexec Functions](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[přerušit](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn Funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
