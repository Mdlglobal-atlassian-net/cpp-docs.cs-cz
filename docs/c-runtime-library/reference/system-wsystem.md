---
title: system, _wsystem
ms.date: 11/04/2016
api_name:
- system
- _wsystem
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
ms.openlocfilehash: 82b39f012bebb41772cdc7350eb08dba48678fdd
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957681"
---
# <a name="system-_wsystem"></a>system, _wsystem

Provede příkaz.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*systému*<br/>
Příkaz, který má být spuštěn.

## <a name="return-value"></a>Návratová hodnota

Pokud je příkaz **null** a je nalezen překladač příkazů, vrátí nenulovou hodnotu. Pokud není nalezen překladač příkazů, vrátí hodnotu 0 a nastaví **errno** na **ENOENT**. Pokud *příkaz* není **null**, **systém** vrátí hodnotu, která je vrácena překladačem příkazu. Vrátí hodnotu 0 pouze v případě, že překladač příkazů vrátí hodnotu 0. Návratová hodnota-1 označuje chybu a **errno** je nastavena na jednu z následujících hodnot:

|||
|-|-|
| **E2BIG** | Seznam argumentů (který je závislý na systému) je příliš velký. |
| **ENOENT** | Překladač příkazů nebyl nalezen. |
| **ENOEXEC** | Soubor příkazového interpretu nelze provést, protože formát není platný. |
| **ENOMEM** | K provedení příkazu není k dispozici dostatek paměti. nebo je dostupná paměť poškozená; nebo existuje neplatný blok, který indikuje, že proces, který volá volání, nebyl správně přidělen. |

Další informace o těchto návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

**Systémová** funkce předá *příkaz* překladači příkazů, který spustí řetězec jako příkaz operačního systému. **systém** používá proměnné prostředí **ComSpec** a **path** k vyhledání souboru. exe příkazového interpretu. Pokud je příkaz **null**, funkce pouze kontroluje, zda existuje překladač příkazů.

Musíte explicitně vyprázdnit, pomocí [fflush](fflush.md) nebo [_flushall](flushall.md), nebo zavřít libovolný datový proud před voláním **System**.

**_wsystem** je verze **systému**s velkým znakem. Argument *příkazu* pro **_wsystem** je řetězec s velkým znakem. Tyto funkce se chovají identicky jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**souborů**|**souborů**|**_wsystem**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**souborů**|\<Process. h > \<nebo Stdlib. h >|
|**_wsystem**|\<Process. h > \<nebo Stdlib. h > \<nebo WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

V tomto příkladu se k zadání textového souboru používá **systém** .

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crt_systemtxt"></a>Vstup: crt_system. txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
