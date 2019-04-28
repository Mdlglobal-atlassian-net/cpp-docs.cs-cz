---
title: _spawnlp, _wspawnlp
ms.date: 11/04/2016
apiname:
- _wspawnlp
- _spawnlp
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
- _wspawnlp
- wspawnlp
- _spawnlp
helpviewer_keywords:
- wspawnlp function
- _spawnlp function
- processes, creating
- processes, executing new
- _wspawnlp function
- process creation
- spawnlp function
ms.assetid: 74fc6e7a-4f24-4103-9387-7177875875e6
ms.openlocfilehash: 44137aefcec8f6658a90117288a47696f4d31903
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62355234"
---
# <a name="spawnlp-wspawnlp"></a>_spawnlp, _wspawnlp

Vytvoří a spustí nový proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _spawnlp(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL
);
intptr_t _wspawnlp(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>Parametry

*Režim*<br/>
Režim spuštění pro volající proces.

*cmdname*<br/>
Cesta k souboru, který má být proveden.

*arg0*, *arg1*, ... *argn*<br/>
Seznam ukazatelů na argumenty. *Arg0* argument je obvykle ukazatel na *cmdname*. Argumenty *arg1* prostřednictvím *argn* jsou ukazatele na znakové řetězce tvořící nový seznam argumentů. Následující *argn*, musí existovat **NULL** ukazatel k označení konce seznamu argumentů.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota ze synchronního **_spawnlp –** nebo **_wspawnlp –** (**_P_WAIT** zadaný pro *režimu*) je stav ukončení nového procesu . Hodnota vrácená z asynchronního **_spawnlp –** nebo **_wspawnlp –** (**_P_NOWAIT** nebo **_P_NOWAITO** zadaný pro  *režim*) je obslužná rutina procesu. Stav ukončení je 0, pokud proces skončil normálně. Můžete nastavit stav ukončení na nenulovou hodnotu, pokud spuštěný proces konkrétně zavolá **ukončit** rutiny s nenulovým argumentem. Pokud nový proces explicitně nenastavil pozitivní, označuje pozitivní abnormální ukončení zrušením nebo přerušením. Návratová hodnota-1 označuje chybu (není spuštěn nový proces). V takovém případě **errno** nastavena na jednu z následujících hodnot.

|||
|-|-|
| **E2BIG** | Seznam argumentů přesahuje 1024 bajtů. |
| **EINVAL** | *režim* argument je neplatný. |
| **ENOENT** | Soubor nebo cesta nebyla nalezena. |
| **ENOEXEC** | Zadaný soubor není spustitelný soubor nebo má neplatný formát spustitelného souboru. |
| **ENOMEM** | Nedostatek paměti je k dispozici ke spuštění nového procesu. |

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí vytvoří a spustí nový proces, přičemž předá každý argument příkazového řádku jako samostatný parametr a použije **cesta** proměnnou prostředí k vyhledání souboru pro spuštění.

Tyto funkce ověřují své parametry. Pokud *cmdname* nebo *arg0* je prázdný řetězec nebo ukazatel s hodnotou null, tyto funkce generují výjimku neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL**a vrátí hodnotu -1. Není vytvořen žádný nový proces.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_spawnlp**|\<process.h>|
|**_wspawnlp**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md).

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
