---
title: system, _wsystem
ms.date: 11/04/2016
apiname:
- system
- _wsystem
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 46c4949fcc8cfbe4a3477e66b57d8fc6fc97ed73
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328653"
---
# <a name="system-wsystem"></a>system, _wsystem

Spustí příkaz.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Příkaz, který se spustí.

## <a name="return-value"></a>Návratová hodnota

Pokud *příkaz* je **NULL** a překladač příkazů nenajde, vrátí nenulovou hodnotu. Pokud překladač příkazů nenajde, vrátí hodnotu 0 a nastaví **errno** k **ENOENT**. Pokud *příkaz* není **NULL**, **systému** vrací hodnotu, která je vrácena překladač příkazů. Vrátí hodnotu 0 pouze v případě, že překladač příkazu vrátí hodnotu 0. Návratová hodnota – 1 označuje chybu a **errno** nastavena na jednu z následujících hodnot:

|||
|-|-|
| **E2BIG** | Seznam argumentů (což je závislé na systému) je moc velká. |
| **ENOENT** | Překladač příkazů nelze nalézt. |
| **ENOEXEC** | Soubor překladač příkazů nelze provést, protože formát není platný. |
| **ENOMEM** | Není k dispozici ke spuštění příkazu; není dostatek paměti nebo dostupná paměť byla poškozena; nebo není platný blok existuje, což znamená, že proces, který provádí volání nepřidělil se správně. |

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pro další informace o těchto návratové kódy.

## <a name="remarks"></a>Poznámky

**Systému** funkce předává *příkaz* překladači příkazu, která spustí řetězec příkazu operačního systému. **systém** používá **COMSPEC** a **cesta** proměnné prostředí pro vyhledání překladač příkazů souboru CMD.exe. Pokud *příkaz* je **NULL**, funkce právě kontroluje, zda existuje překladač příkazů.

Je nutné provést explicitní vyprázdnění, s použitím [fflush –](fflush.md) nebo [_flushall –](flushall.md), nebo všechny proudy zavřít před voláním **systému**.

**_wsystem –** je verze širokého znaku **systému**; *příkaz* argument **_wsystem –** je širokoznaký řetězec. Tyto funkce chovají identicky jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem –**|**Systém**|**Systém**|**_wsystem**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Systém**|\<Process.h > nebo \<stdlib.h >|
|**_wsystem**|\<Process.h > nebo \<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento příklad používá **systému** zadejte do textového souboru.

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crtsystemtxt"></a>Vstup: crt_system.txt

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
