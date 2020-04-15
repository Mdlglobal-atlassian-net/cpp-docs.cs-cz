---
title: system, _wsystem
ms.date: 4/2/2020
api_name:
- system
- _wsystem
- _o__wsystem
- _o_system
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tsystem
- _wsystem
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
ms.openlocfilehash: 21ce04d30da80a40a1162dce06ff378150008766
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362793"
---
# <a name="system-_wsystem"></a>system, _wsystem

Provede příkaz.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int system(
   const char *command
);
int _wsystem(
   const wchar_t *command
);
```

### <a name="parameters"></a>Parametry

*Příkaz*<br/>
Příkaz, který má být proveden.

## <a name="return-value"></a>Návratová hodnota

Pokud je *příkaz* **NULL** a je nalezen překladač příkazů, vrátí nenulovou hodnotu. Pokud není nalezen překladač příkazů, vrátí hodnotu 0 a nastaví **errno** na **ENOENT**. Pokud *příkaz* není **NULL**, **vrátí systém** hodnotu vrácenou překladačem příkazů. Vrátí hodnotu 0 pouze v případě, že překladač příkazů vrátí hodnotu 0. Vrácená hodnota - 1 označuje chybu a **errno** je nastavena na jednu z následujících hodnot:

|||
|-|-|
| **E2BIG** | Seznam argumentů (který je závislý na systému) je příliš velký. |
| **ENOENT** | Překladač příkazů nebyl nalezen. |
| **ENOEXEC** | Soubor překladače příkazů nelze spustit, protože formát není platný. |
| **ENOMEM** | Není k dispozici dostatek paměti pro spuštění příkazu; nebo byla poškozena dostupná paměť. nebo existuje neplatný blok, což znamená, že proces, který provádí volání nebyl přidělen správně. |

Další informace o těchto návratových kódech naleznete [v _doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

**Systémová** funkce předá *příkaz* překladaci příkazů, který provede řetězec jako příkaz operačního systému. **systém** používá proměnné prostředí **COMSPEC** a **PATH** k vyhledání souboru cmd.exe příkazu a interpretu. Pokud je *příkaz* **NULL**, funkce pouze zkontroluje, zda existuje interpret příkazu.

Před voláním **systému**je nutné explicitně vyprázdnit pomocí [fflush](fflush.md) nebo [_flushall](flushall.md)nebo zavřít jakýkoli datový proud .

**_wsystem** je širokoznaková verze **systému**; příkaz *command* argument **_wsystem** je řetězec široký znak. Tyto funkce se chovají stejně jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**systém**|**systém**|**_wsystem**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**systém**|\<process.h> \<nebo stdlib.h>|
|**_wsystem**|\<process.h> \<nebo stdlib.h> nebo \<wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento příklad používá **systém** k zadání textového souboru.

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crt_systemtxt"></a>Vstup: crt_system.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, _wspawn funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
