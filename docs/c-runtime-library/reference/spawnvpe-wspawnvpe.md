---
title: _spawnvpe –, _wspawnvpe – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _wspawnvpe function
- processes, creating
- _spawnvpe function
- processes, executing new
- wspawnvpe function
- process creation
- spawnvpe function
ms.assetid: 3db6394e-a955-4837-97a1-fab1db1e6092
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b1498b5772386edb986d3bbd87c63b7c856a3c3
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="spawnvpe-wspawnvpe"></a>_spawnvpe, _wspawnvpe

Vytvoří a spustí nový proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Režim spuštění pro volání procesu

*cmdname*<br/>
Cesta k souboru spouštění

*argv –*<br/>
Pole ukazatele na argumenty. Argument *argv –*[0] je obvykle ukazatel na cestu v reálném režimu nebo název programu v chráněném režimu, a *argv –*[1] prostřednictvím *argv –*[**n**] jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Argument *argv –*[**n** + 1] musí být **NULL** ukazatel na konec seznamu argumentů.

*envp –*<br/>
Pole ukazatele na nastavení prostředí

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota z synchronního **_spawnvpe –** nebo **_wspawnvpe –** (**_p_wait –** zadaná pro *režimu*) je nový stav ukončení proces. Vrácená hodnota z asynchronní **_spawnvpe –** nebo **_wspawnvpe –** (**_p_nowait –** nebo **_p_nowaito –** zadaná pro  *režim*) je proces popisovač. Stav ukončení je 0, pokud proces ukončen normálně. Můžete nastavit stav ukončení nenulovou hodnotu, pokud proces spuštěný konkrétně volá **ukončete** rutiny s argumentem nenulové hodnoty. Pokud nový proces explicitně nenastavili stav kladné ukončení, označuje stav kladné ukončení abnormální ukončení s přerušení nebo přerušení. Vrácená hodnota -1 označuje chybu (není spuštěn nový proces). V takovém případě **errno** nastaven na jednu z následujících hodnot:

|||
|-|-|
**E2BIG –**|Seznam argumentů je větší než 1024 bajtů.
**EINVAL –**|*režim* argument je neplatný.
**ENOENT –**|Soubor nebo cesta nebyla nalezena.
**ENOEXEC –**|Zadaný soubor není spustitelný soubor nebo má neplatný formát souboru spustitelný soubor.
**ENOMEM –**|Nedostatek paměti je k dispozici pro spuštění nový proces.

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratové kódy.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí se vytvoří a spustí nový proces, předávání pole ukazatele argumenty příkazového řádku a pole ukazatele na nastavení prostředí. Použijte tyto funkce **cesta** proměnnou prostředí najít soubor provést.

Tyto funkce ověřit jejich parametrů. Pokud má jedna *cmdname* nebo *argv –* je ukazatel s hodnotou null, nebo pokud *argv –* odkazuje na ukazatele null, nebo *argv –*[0] je řetězec prázdný, neplatný Obslužná rutina parametru je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –**a vrátí hodnotu -1. Žádný nový proces je vytvořený.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_spawnvpe**|\<stdio.h > nebo \<process.h >|
|**_wspawnvpe**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Viz také

[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
