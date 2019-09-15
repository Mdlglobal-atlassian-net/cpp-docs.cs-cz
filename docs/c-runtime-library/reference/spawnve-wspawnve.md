---
title: _spawnve, _wspawnve
ms.date: 11/04/2016
api_name:
- _spawnve
- _wspawnve
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
- wspawnve
- _spawnve
- _wspawnve
- spawnve
helpviewer_keywords:
- _spawnve function
- spawnve function
- wspawnve function
- processes, creating
- _wspawnve function
- processes, executing new
- process creation
ms.assetid: 26d1713d-b551-4f21-a07b-e9891a2ae6cf
ms.openlocfilehash: 37ff1358e8639d49992b8cfafb76b2ddac079889
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947540"
---
# <a name="_spawnve-_wspawnve"></a>_spawnve, _wspawnve

Vytvoří a spustí nový proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Mode*<br/>
Režim spuštění pro volající proces.

*cmdname*<br/>
Cesta k souboru, který má být spuštěn.

*argv*<br/>
Pole ukazatelů na argumenty. Argument *argv*[0] je obvykle ukazatel na cestu v reálném režimu nebo v názvu programu v chráněném režimu. *argv*[1] až *argv*[**n**] jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Argument *argv*[**n** + 1] musí být ukazatel s **hodnotou null** k označení konce seznamu argumentů.

*envp*<br/>
Pole ukazatelů na nastavení prostředí

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota z synchronního **_spawnve** nebo **_wspawnve** ( **_P_WAIT** zadaná pro *režim*) je stav ukončení nového procesu. Vrácená hodnota z asynchronního **_spawnve** nebo **_wspawnve** ( **_P_NOWAIT** nebo **_P_NOWAITO** určená pro *režim*) je obslužná rutina procesu. Stav ukončení je 0, pokud byl proces ukončen normálně. Stav ukončení můžete nastavit na nenulovou hodnotu, pokud vytvořený proces konkrétně volá rutinu **ukončení** s nenulovým argumentem. Pokud nový proces neexplicitně nastavil kladný stav ukončení, pozitivní stav ukončení indikuje abnormální ukončení s přerušením nebo přerušením. Návratová hodnota-1 označuje chybu (nový proces není spuštěn). V tomto případě je **errno** nastaveno na jednu z následujících hodnot.

|||
|-|-|
| **E2BIG** | Seznam argumentů překračuje 1024 bajtů. |
| **EINVAL** | Argument *režimu* je neplatný. |
| **ENOENT** | Soubor nebo cesta nebyla nalezena. |
| **ENOEXEC** | Zadaný soubor není spustitelný nebo má neplatný formát spustitelného souboru. |
| **ENOMEM** | K provedení nového procesu není k dispozici dostatek paměti. |

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí vytvoří a spustí nový proces, předá pole ukazatelů na argumenty příkazového řádku a pole ukazatelů do nastavení prostředí.

Tyto funkce ověřují své parametry. Pokud je buď *cmdname* nebo *argv* ukazatel s hodnotou null, nebo pokud *argv* odkazuje na ukazatel s hodnotou null, nebo *argv*[0] je prázdný řetězec, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL**a vrátí-1. Nevytvoří se žádný nový proces.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_spawnve**|\<stdio. h > nebo \<Process. h >|
|**_wspawnve**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_spawn, _Wspawn Functions](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
