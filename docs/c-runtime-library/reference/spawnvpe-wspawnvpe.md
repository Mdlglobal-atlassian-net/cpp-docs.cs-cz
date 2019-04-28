---
title: _spawnvpe, _wspawnvpe
ms.date: 11/04/2016
apiname:
- _spawnvpe
- _wspawnvpe
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
- _spawnvpe
- wspawnvpe
- spawnvpe
- _wspawnvpe
helpviewer_keywords:
- _wspawnvpe function
- processes, creating
- _spawnvpe function
- processes, executing new
- wspawnvpe function
- process creation
- spawnvpe function
ms.assetid: 3db6394e-a955-4837-97a1-fab1db1e6092
ms.openlocfilehash: a98cc3c441261a92876b94e1231e66bb71e9d3d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62355078"
---
# <a name="spawnvpe-wspawnvpe"></a>_spawnvpe, _wspawnvpe

Vytvoří a spustí nový proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _spawnvpe(
   int mode,
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wspawnvpe(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parametry

*Režim*<br/>
Režim spuštění pro volající proces.

*cmdname*<br/>
Cesta k souboru, který se spustí

*argv*<br/>
Pole ukazatelů na argumenty. Argument *argv*[0] je obvykle ukazatel na cestu v reálném režimu nebo na název programu v chráněném režimu, a *argv*[1] až *argv*[**n**] jsou ukazatele na znakové řetězce tvořící nový seznam argumentů. Argument *argv*[**n** + 1] musí být **NULL** ukazatel k označení konce seznamu argumentů.

*envp*<br/>
Pole ukazatelů do nastavení prostředí

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota ze synchronního **_spawnvpe** nebo **_wspawnvpe –** (**_P_WAIT** zadaný pro *režimu*) je stav ukončení nového proces. Hodnota vrácená z asynchronního **_spawnvpe** nebo **_wspawnvpe –** (**_P_NOWAIT** nebo **_P_NOWAITO** zadaný pro  *režim*) je obslužná rutina procesu. Stav ukončení je 0, pokud proces skončil normálně. Můžete nastavit stav ukončení na nenulovou hodnotu, pokud spuštěný proces konkrétně zavolá **ukončit** rutiny s nenulovým argumentem. Pokud nový proces explicitně nenastavil pozitivní, označuje pozitivní abnormální ukončení zrušením nebo přerušením. Návratová hodnota-1 označuje chybu (není spuštěn nový proces). V takovém případě **errno** nastavena na jednu z následujících hodnot:

|||
|-|-|
| **E2BIG** | Seznam argumentů přesahuje 1024 bajtů. |
| **EINVAL** | *režim* argument je neplatný. |
| **ENOENT** | Soubor nebo cesta nebyla nalezena. |
| **ENOEXEC** | Zadaný soubor není spustitelný soubor nebo má neplatný formát spustitelného souboru. |
| **ENOMEM** | Nedostatek paměti je k dispozici ke spuštění nového procesu. |

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratových kódů.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí vytvoří a spustí nový proces, předá pole ukazatelů do argumentů příkazového řádku a pole ukazatelů do nastavení prostředí. Tyto funkce používají **cesta** proměnnou prostředí k vyhledání souboru pro spuštění.

Tyto funkce ověřují své parametry. Pokud *cmdname* nebo *argv* je ukazatel s hodnotou null, nebo pokud *argv* odkazuje na ukazatel s hodnotou null, nebo *argv*[0] je prázdný řetězec, neplatný je vyvolána obslužná rutina parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL**a vrátí hodnotu -1. Není vytvořen žádný nový proces.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_spawnvpe**|\<stdio.h > nebo \<process.h >|
|**_wspawnvpe**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Viz také:

[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
