---
title: systém, _wsystem – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9043b5bb76c438ee640f298eeed3f41b84a7ca30
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="system-wsystem"></a>system, _wsystem

Spustí příkaz.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*příkaz*<br/>
Příkaz, který má být proveden.

## <a name="return-value"></a>Návratová hodnota

Pokud *příkaz* je **NULL** a překladač příkazů je najít, vrátí nenulovou hodnotu. Pokud překladač příkazů není nalezeno, vrátí hodnotu 0 a nastaví **errno** k **enoent –**. Pokud *příkaz* není **NULL**, **systému** vrátí hodnotu, která vrátí překladač příkazů. Vrátí hodnotu 0 pouze v případě, že překladač příkazů vrátí hodnotu 0. Návratová hodnota - 1 znamená chybu, a **errno** nastaven na jednu z následujících hodnot:

|||
|-|-|
**E2BIG –**|Seznam argumentů (což je závislé na systém) je příliš dlouhý.
**ENOENT –**|Překladač příkazů nebyl nalezen.
**ENOEXEC –**|Překladač příkazů soubor nelze provést, protože formát není platný.
**ENOMEM –**|Je k dispozici ke spuštění příkazu; není dostatek paměti nebo dostupné paměti je poškozená; nebo neplatné blok neexistuje, což naznačuje, že proces, který je uskutečněním hovoru nebyla přidělena správně.

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pro další informace o těchto návratové kódy.

## <a name="remarks"></a>Poznámky

**Systému** funkce předává *příkaz* k překladač příkazů, které provede řetězec jako příkaz operačního systému. **systém** používá **COMSPEC** a **cesta** proměnné prostředí najít překladač příkazů soubor CMD.exe. Pokud *příkaz* je **NULL**, funkce právě ověří, zda existuje překladač příkazů.

Musíte explicitně vyprázdnit, pomocí [fflush –](fflush.md) nebo [_flushall –](flushall.md), nebo zavřete jakýkoli proud před voláním **systému**.

**_wsystem –** je verze široká charakterová **systému**; *příkaz* argument **_wsystem –** je široká charakterová řetězec. Tyto funkce chovají stejně jako jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem –**|**Systém**|**Systém**|**_wsystem**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Systém**|\<Process.h > nebo \<stdlib.h >|
|**_wsystem**|\<Process.h > nebo \<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
