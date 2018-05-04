---
title: _spawnlpe –, _wspawnlpe – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _spawnlpe
- _wspawnlpe
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
- spawnlpe
- _wspawnlpe
- _spawnlpe
- wspawnlpe
dev_langs:
- C++
helpviewer_keywords:
- _wspawnlpe function
- wspawnlpe function
- processes, creating
- spawnlpe function
- _spawnlpe function
- processes, executing new
- process creation
ms.assetid: e171ebfa-70e7-4c44-8331-2a291fc17bd6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be8e86ddb6405c39f877bd9065a931b66238c2b6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="spawnlpe-wspawnlpe"></a>_spawnlpe, _wspawnlpe

Vytvoří a spustí nový proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Režim*<br/>
Režim spuštění pro proces volání.

*cmdname*<br/>
Cesta k souboru, který má být proveden.

*arg0*, *arg1*,... *argn*<br/>
Seznam ukazatele na argumenty. *Arg0* argument je obvykle ukazatel na *cmdname*. Argumenty *arg1* prostřednictvím *argn* jsou ukazatele na řetězce znaků, které vytvářejí nové seznam argumentů. Následující *argn*, musí existovat **NULL** ukazatel na konec seznamu argumentů.

*envp –*<br/>
Pole ukazatele na nastavení prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota z synchronního **_spawnlpe –** nebo **_wspawnlpe –** (**_p_wait –** zadaná pro *režimu*) je nový stav ukončení proces. Vrácená hodnota z asynchronní **_spawnlpe –** nebo **_wspawnlpe –** (**_p_nowait –** nebo **_p_nowaito –** zadaná pro  *režim*) je proces popisovač. Stav ukončení je 0, pokud proces ukončen normálně. Můžete nastavit stav ukončení nenulovou hodnotu, pokud proces spuštěný konkrétně používá nenulové hodnoty argumentu k volání **ukončete** rutiny. Pokud nový proces explicitně nenastavili stav kladné ukončení, označuje stav kladné ukončení neobvyklé východ způsobené přerušení nebo přerušení. Vrácená hodnota -1 označuje chybu (není spuštěn nový proces). V takovém případě **errno** nastaven na jednu z následujících hodnot.

|||
|-|-|
**E2BIG –**|Seznam argumentů je větší než 1024 bajtů.
**EINVAL –**|*režim* argument je neplatný.
**ENOENT –**|Soubor nebo cesta nebyla nalezena.
**ENOEXEC –**|Zadaný soubor není spustitelný soubor nebo má neplatný formát souboru spustitelný soubor.
**ENOMEM –**|Nedostatek paměti je k dispozici pro spuštění nový proces.

Další informace o těchto a dalších návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí vytvoří a spustí nový proces, předá každý argument příkazového řádku jako samostatného parametru a předá pole ukazatele nastavení prostředí. Použijte tyto funkce **cesta** proměnnou prostředí najít soubor provést.

Tyto funkce ověřit jejich parametrů. Pokud má jedna *cmdname* nebo *arg0* je prázdný řetězec nebo nulového ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –**a vrátí hodnotu -1. Žádný nový proces je vytvořený.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_spawnlpe**|\<Process.h >|
|**_wspawnlpe**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Viz také

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
