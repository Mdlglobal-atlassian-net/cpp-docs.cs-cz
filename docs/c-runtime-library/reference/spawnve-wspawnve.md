---
title: _spawnve, _wspawnve
ms.date: 4/2/2020
api_name:
- _spawnve
- _wspawnve
- _o__spawnve
- _o__wspawnve
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
- wspawnve
- _spawnve
- _wspawnve
helpviewer_keywords:
- _spawnve function
- spawnve function
- wspawnve function
- processes, creating
- _wspawnve function
- processes, executing new
- process creation
ms.assetid: 26d1713d-b551-4f21-a07b-e9891a2ae6cf
ms.openlocfilehash: 0f546185039bb1503af40d5f690fd8d8c172a679
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355861"
---
# <a name="_spawnve-_wspawnve"></a>_spawnve, _wspawnve

Vytvoří a spustí nový proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _spawnve(
   int mode,
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wspawnve(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parametry

*Režimu*<br/>
Režim spuštění volajícího procesu.

*cmdname*<br/>
Cesta k souboru, který má být proveden.

*argv*<br/>
Pole ukazatelů na argumenty. Argument *argv*[0] je obvykle ukazatel na cestu v reálném režimu nebo na název programu v chráněném režimu a *argv*[1] přes *argv*[**n**] jsou ukazatele na řetězce znaků tvořící nový seznam argumentů. Argument *argv*[**n** +1] musí být ukazatelem **NULL,** který označuje konec seznamu argumentů.

*envp*<br/>
Pole ukazatelů na nastavení prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota ze **synchronní_spawnve** nebo **_wspawnve** **(_P_WAIT** určené pro *režim)* je stav ukončení nového procesu. Vrácená hodnota z asynchronní **_spawnve** nebo **_wspawnve** **(_P_NOWAIT** nebo **_P_NOWAITO** určené pro *režim)* je popisovač procesu. Stav ukončení je 0, pokud proces normálně ukončen. Stav ukončení můžete nastavit na nenulovou hodnotu, pokud proces tření konkrétně volá **rutinu ukončení** s nenulovým argumentem. Pokud nový proces explicitně nenastavil kladný stav ukončení, kladný stav ukončení označuje abnormální ukončení s přerušením nebo přerušením. Vrácená hodnota -1 označuje chybu (nový proces není spuštěn). V tomto případě je **chybné** číslo nastaveno na jednu z následujících hodnot.

|||
|-|-|
| **E2BIG** | Seznam argumentů přesahuje 1024 bajtů. |
| **EINVAL** | argument *mode* je neplatný. |
| **ENOENT** | Soubor nebo cesta nebyla nalezena. |
| **ENOEXEC** | Zadaný soubor není spustitelný nebo má neplatný formát spustitelného souboru. |
| **ENOMEM** | K provedení nového procesu není k dispozici dostatek paměti. |

Další informace o těchto a dalších návratových kódech naleznete [v tématech _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí vytvoří a spustí nový proces, předávání pole ukazatelů na argumenty příkazového řádku a pole ukazatelů na nastavení prostředí.

Tyto funkce ověřují jejich parametry. Pokud *buď cmdname* nebo *argv* je ukazatel null, nebo pokud *argv* odkazuje na ukazatel null nebo *argv*[0] je prázdný řetězec, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce nastavit **errno** **eINVAL**a vrátit -1. Žádný nový proces je plodil.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_spawnve**|\<stdio.h> \<nebo process.h>|
|**_wspawnve**|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad v [_spawn, _wspawn funkce](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[Přerušení](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
