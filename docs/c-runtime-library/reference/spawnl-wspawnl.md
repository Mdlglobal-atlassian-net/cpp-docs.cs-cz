---
title: _spawnl –, _wspawnl – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wspawnl
- _spawnl
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
- spawnl
- wspawnl
- _wspawnl
- _spawnl
dev_langs:
- C++
helpviewer_keywords:
- spawnl function
- processes, creating
- _spawnl function
- processes, executing new
- _wspawnl function
- wspawnl function
- process creation
ms.assetid: dd4584c9-7173-4fc5-b93a-6e7d3c2316d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcd276e59edd78942f14211845c615d7e4f7eb6d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410717"
---
# <a name="spawnl-wspawnl"></a>_spawnl, _wspawnl

Vytvoří a spustí nový proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _spawnl(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL
);
intptr_t _wspawnl(
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
Režim spuštění pro proces volání.

*cmdname*<br/>
Cesta k souboru, který má být proveden.

*arg0*, *arg1*,... *argn*<br/>
Seznam ukazatele na argumenty. *Arg0* argument je obvykle ukazatel na *cmdname*. Argumenty *arg1* prostřednictvím *argn* jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Následující *argn*, musí existovat **NULL** ukazatel na konec seznamu argumentů.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota z synchronního **_spawnl –** nebo **_wspawnl –** (**_p_wait –** zadaná pro *režimu*) je stav ukončení nový proces. Vrácená hodnota z asynchronní **_spawnl –** nebo **_wspawnl –** (**_p_nowait –** nebo **_p_nowaito –** zadaná pro *režimu* ) je proces popisovač. Stav ukončení je 0, pokud proces ukončen normálně. Můžete nastavit stav ukončení nenulovou hodnotu, pokud proces spuštěný konkrétně volá **ukončete** rutiny s argumentem nenulové hodnoty. Pokud nový proces explicitně nenastavili stav kladné ukončení, označuje stav kladné ukončení abnormální ukončení s přerušení nebo přerušení. Vrácená hodnota -1 označuje chybu (není spuštěn nový proces). V takovém případě **errno** nastaven na jednu z následujících hodnot.

|||
|-|-|
**E2BIG –**|Seznam argumentů je větší než 1024 bajtů.
**EINVAL –**|*režim* argument je neplatný.
**ENOENT –**|Soubor nebo cesta nebyla nalezena.
**ENOEXEC –**|Zadaný soubor není spustitelný soubor nebo má neplatný formát souboru spustitelný soubor.
**ENOMEM –**|Nedostatek paměti je k dispozici pro spuštění nový proces.

Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Tyto funkce ověřit jejich parametrů. Pokud má jedna *cmdname* nebo *arg0* je prázdný řetězec nebo nulového ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátí hodnotu -1. Žádný nový proces je vytvořený.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí se vytvoří a spustí nový proces, předávání každý argument příkazového řádku jako samostatného parametru.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_spawnl**|\<Process.h >|
|**_wspawnl**|\<stdio.h > nebo \<wchar.h >|

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
