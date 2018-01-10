---
title: "_spawnvpe –, _wspawnvpe – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- _wspawnvpe function
- processes, creating
- _spawnvpe function
- processes, executing new
- wspawnvpe function
- process creation
- spawnvpe function
ms.assetid: 3db6394e-a955-4837-97a1-fab1db1e6092
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eda03fa80228a218e34c472df2400f7bfe1d8a3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="spawnvpe-wspawnvpe"></a>_spawnvpe, _wspawnvpe
Vytvoří a spustí nový proces.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `mode`  
 Režim spuštění pro volání procesu  
  
 `cmdname`  
 Cesta k souboru spouštění  
  
 `argv`  
 Pole ukazatele na argumenty. Argument `argv`[0] je obvykle ukazatel na cestu v reálném režimu nebo název programu v chráněném režimu, a `argv`[1] prostřednictvím `argv`[`n`] jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Argument `argv`[`n` + 1] musí být `NULL` ukazatel na konec seznamu argumentů.  
  
 `envp`  
 Pole ukazatele na nastavení prostředí  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota z synchronního `_spawnvpe` nebo `_wspawnvpe` (`_P_WAIT` zadaná pro `mode`) je stav ukončení nový proces. Vrácená hodnota z asynchronní `_spawnvpe` nebo `_wspawnvpe` (`_P_NOWAIT` nebo `_P_NOWAITO` zadaná pro `mode`) je proces popisovač. Stav ukončení je 0, pokud proces ukončen normálně. Můžete nastavit stav ukončení nenulovou hodnotu, pokud proces spuštěný konkrétně volá `exit` rutiny s argumentem nenulové hodnoty. Pokud nový proces explicitně nenastavili stav kladné ukončení, označuje stav kladné ukončení abnormální ukončení s přerušení nebo přerušení. Vrácená hodnota -1 označuje chybu (není spuštěn nový proces). V takovém případě `errno` nastaven na jednu z následujících hodnot:  
  
 `E2BIG`  
 Seznam argumentů překračuje 1024 bajtů  
  
 `EINVAL`  
 `mode`argument je neplatný.  
  
 `ENOENT`  
 Soubor nebo cesta nebyla nalezena.  
  
 `ENOEXEC`  
 Zadaný soubor není spustitelný soubor nebo má neplatný formát souboru spustitelný soubor  
  
 `ENOMEM`  
 Nedostatek paměti je k dispozici pro spuštění nový proces  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratové kódy.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí se vytvoří a spustí nový proces, předávání pole ukazatele argumenty příkazového řádku a pole ukazatele na nastavení prostředí. Použijte tyto funkce `PATH` proměnnou prostředí najít soubor provést.  
  
 Tyto funkce ověřit jejich parametrů. Pokud má jedna `cmdname` nebo `argv` je ukazatel s hodnotou null, nebo pokud `argv` odkazuje na ukazatele null, nebo `argv[0]` je řetězec prázdný obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL`a vrátí hodnotu -1. Žádný nový proces je vytvořený.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_spawnvpe`|\<stdio.h > nebo \<process.h >|  
|`_wspawnvpe`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad v [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [AtExit](../../c-runtime-library/reference/atexit.md)   
 [_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)   
 [ukončení, _exit –, _exit –](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall –](../../c-runtime-library/reference/flushall.md)   
 [_getmbcp –](../../c-runtime-library/reference/getmbcp.md)   
 [_onexit –, _onexit_m –](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_setmbcp –](../../c-runtime-library/reference/setmbcp.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)