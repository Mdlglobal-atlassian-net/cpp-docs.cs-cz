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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 75b5c0ebe47c8f82ab8ad328dd21505c458a6ac8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347806"
---
# <a name="_execvp-_wexecvp"></a>_execvp, _wexecvp

Načte a provede nové podřízené procesy.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Cesta k provedení souboru.

*argv*<br/>
Pole ukazatelů na parametry.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, tyto funkce se nevrátí do volajícího procesu. Vrácená hodnota -1 označuje chybu, v takovém případě je nastavena globální proměnná **errno.**

|**hodnota errno**|Popis|
|-------------------|-----------------|
|**E2BIG**|Prostor potřebný pro argumenty a nastavení prostředí přesahuje 32 KB.|
|**ACCACCES**|Zadaný soubor má zamykání nebo sdílení porušení.|
|**EINVAL**|Neplatný parametr.|
|**SOUBOR EM**|Otevře se příliš mnoho souborů (zadaný soubor musí být otevřen, aby bylo možné určit, zda je spustitelný).|
|**ENOENT**|Soubor nebo cesta nebyla nalezena.|
|**ENOEXEC**|Zadaný soubor není spustitelný nebo má neplatný formát spustitelného souboru.|
|**ENOMEM**|K provedení nového procesu není k dispozici dostatek paměti. dostupná paměť byla poškozena. nebo existuje neplatný blok, což znamená, že volající proces nebyl přidělen správně.|

Další informace o těchto a dalších návratových kódech naleznete [v tématech _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí načte a spustí nový proces, předávání pole ukazatelů argumenty příkazového řádku a pomocí proměnné prostředí **PATH** najít soubor spustit.

Funkce **_execvp** ověřují jejich parametry. Pokud *je název cmdname* ukazatelem null nebo *argv* je ukazatel null, ukazatel na prázdné pole nebo pokud pole obsahuje prázdný řetězec jako první argument, tyto funkce vyvolávají neplatnou obslužnou rutinu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce nastavit **errno** **eINVAL** a vrátit -1. Není spuštěn žádný proces.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelná hlavička|
|--------------|---------------------|---------------------|
|**_execvp**|\<process.h>|\<errno.h>|
|**_wexecvp**|\<process.h> \<nebo wchar.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad v [_exec, _wexec funkce](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[Přerušení](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
