---
title: _spawnlpe, _wspawnlpe
ms.date: 11/04/2016
api_name:
- _spawnlpe
- _wspawnlpe
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
- spawnlpe
- _wspawnlpe
- _spawnlpe
- wspawnlpe
helpviewer_keywords:
- _wspawnlpe function
- wspawnlpe function
- processes, creating
- spawnlpe function
- _spawnlpe function
- processes, executing new
- process creation
ms.assetid: e171ebfa-70e7-4c44-8331-2a291fc17bd6
ms.openlocfilehash: fe82d52418683d414ffbdd0f4fb0efd9bfd709cb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947651"
---
# <a name="_spawnlpe-_wspawnlpe"></a>_spawnlpe, _wspawnlpe

Vytvoří a spustí nový proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _spawnlpe(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wspawnlpe(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parametry

*Mode*<br/>
Režim spuštění pro volající proces.

*cmdname*<br/>
Cesta k souboru, který má být spuštěn.

*arg0*, *arg1*, ... *argn*<br/>
Seznam ukazatelů na argumenty. Argument *arg0* je obvykle ukazatel na *cmdname*. Argumenty *arg1* až *argn* jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Následující *argn*musí mít ukazatel s **hodnotou null** k označení konce seznamu argumentů.

*envp*<br/>
Pole ukazatelů na nastavení prostředí

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota z synchronního **_spawnlpe** nebo **_wspawnlpe** ( **_P_WAIT** zadaná pro *režim*) je stav ukončení nového procesu. Vrácená hodnota z asynchronního **_spawnlpe** nebo **_wspawnlpe** ( **_P_NOWAIT** nebo **_P_NOWAITO** určená pro *režim*) je obslužná rutina procesu. Stav ukončení je 0, pokud byl proces ukončen normálně. Můžete nastavit stav ukončení na nenulovou hodnotu, pokud vytvořený proces konkrétně používá nenulový argument pro volání **ukončovací** rutiny. Pokud nový proces neexplicitně nastavil kladný stav ukončení, pozitivní stav ukončení indikuje abnormální ukončení způsobený přerušením nebo přerušením. Návratová hodnota-1 označuje chybu (nový proces není spuštěn). V tomto případě je **errno** nastaveno na jednu z následujících hodnot.

|||
|-|-|
| **E2BIG** | Seznam argumentů překračuje 1024 bajtů. |
| **EINVAL** | Argument *režimu* je neplatný. |
| **ENOENT** | Soubor nebo cesta nebyla nalezena. |
| **ENOEXEC** | Zadaný soubor není spustitelný nebo má neplatný formát spustitelného souboru. |
| **ENOMEM** | K provedení nového procesu není k dispozici dostatek paměti. |

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí vytvoří a spustí nový proces, předá každý argument příkazového řádku jako samostatný parametr a předá pole ukazatelů do nastavení prostředí. Tyto funkce používají proměnnou prostředí **path** k vyhledání souboru, který má být spuštěn.

Tyto funkce ověřují své parametry. Pokud je buď *cmdname* nebo *arg0* prázdný řetězec nebo ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL**a vrátí-1. Nevytvoří se žádný nový proces.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_spawnlpe**|\<Process. h >|
|**_wspawnlpe**|\<stdio. h > nebo \<WCHAR. h >|

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
