---
title: _execvpe, _wexecvpe
ms.date: 4/2/2020
api_name:
- _execvpe
- _wexecvpe
- _o__execvpe
- _o__wexecvpe
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
- wexecvpe
- _wexecvpe
- _execvpe
helpviewer_keywords:
- wexecvpe function
- execvpe function
- _wexecvpe function
- _execvpe function
ms.assetid: c0c3c986-d9c0-4814-a96c-10f0b3092766
ms.openlocfilehash: dd2e4c91affe211cc58a2f1c147646172f3f34c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347647"
---
# <a name="_execvpe-_wexecvpe"></a>_execvpe, _wexecvpe

Načte a spustí nové podřízené procesy.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Cesta k provedení souboru.

*argv*<br/>
Pole ukazatelů na parametry.

*envp*<br/>
Pole ukazatelů na nastavení prostředí.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, tyto funkce se nevrátí do volajícího procesu. Vrácená hodnota -1 označuje chybu, v takovém případě je nastavena globální proměnná **errno.**

|**hodnota errno**|Popis|
|-------------------|-----------------|
|**E2BIG**|Prostor, který je vyžadován pro argumenty a nastavení prostředí přesahuje 32 KB.|
|**ACCACCES**|Zadaný soubor má zamykání nebo sdílení porušení.|
|**SOUBOR EM**|Je otevřeno příliš mnoho souborů. (Zadaný soubor musí být otevřen, aby bylo možné určit, zda je spustitelný.)|
|**ENOENT**|Soubor nebo cesta nebyla nalezena.|
|**ENOEXEC**|Zadaný soubor není spustitelný nebo má neplatný formát spustitelného souboru.|
|**ENOMEM**|K provedení nového procesu není k dispozici dostatek paměti. dostupná paměť byla poškozena. nebo existuje neplatný blok, což znamená, že volající proces nebyl přidělen správně.|

Další informace o těchto a dalších návratových kódech naleznete [v tématech errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí načte a spustí nový proces a předá pole ukazatelů argumentům příkazového řádku a pole ukazatelů na nastavení prostředí. Tyto funkce používají proměnnou prostředí **PATH** k vyhledání souboru ke spuštění.

Funkce **_execvpe** ověřují jejich parametry. Pokud *cmdname* je ukazatel null, nebo pokud *argv* je ukazatel null, ukazatel na prázdné pole nebo ukazatel na pole, které obsahuje prázdný řetězec jako první argument, tyto funkce vyvolat neplatný parametr obslužné rutiny, jak je popsáno v [Parametr Validation](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce nastavit **errno** **eINVAL** a vrátit -1. Není spuštěn žádný proces.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelná hlavička|
|--------------|---------------------|---------------------|
|**_execvpe**|\<process.h>|\<errno.h>|
|**_wexecvpe**|\<process.h> \<nebo wchar.h>|\<errno.h>|

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
