---
title: "_spawnlp –, _wspawnlp – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wspawnlp function
- _spawnlp function
- processes, creating
- processes, executing new
- _wspawnlp function
- process creation
- spawnlp function
ms.assetid: 74fc6e7a-4f24-4103-9387-7177875875e6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7fc388df8f1705c88b5510471b230c278665e70d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="spawnlp-wspawnlp"></a>_spawnlp, _wspawnlp
Vytvoří a spustí nový proces.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `mode`  
 Režim spuštění pro proces volání.  
  
 `cmdname`  
 Cesta k souboru, který má být proveden.  
  
 `arg0, arg1, ... argn`  
 Seznam ukazatele na argumenty. `arg0` Argument je obvykle ukazatel na `cmdname`. Argumenty `arg1` prostřednictvím `argn` jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Následující `argn`, musí existovat `NULL` ukazatel na konec seznamu argumentů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota z synchronního `_spawnlp` nebo `_wspawnlp` (`_P_WAIT` zadaná pro `mode`) je stav ukončení nový proces. Vrácená hodnota z asynchronní `_spawnlp` nebo `_wspawnlp` (`_P_NOWAIT` nebo `_P_NOWAITO` zadaná pro `mode`) je proces popisovač. Stav ukončení je 0, pokud proces ukončen normálně. Můžete nastavit stav ukončení nenulovou hodnotu, pokud proces spuštěný konkrétně volá `exit` rutiny s argumentem nenulové hodnoty. Pokud nový proces explicitně nenastavili stav kladné ukončení, označuje stav kladné ukončení abnormální ukončení s přerušení nebo přerušení. Vrácená hodnota -1 označuje chybu (není spuštěn nový proces). V takovém případě `errno` nastaven na jednu z následujících hodnot.  
  
 `E2BIG`  
 Seznam argumentů je větší než 1024 bajtů.  
  
 `EINVAL`  
 `mode` argument je neplatný.  
  
 `ENOENT`  
 Soubor nebo cesta nebyla nalezena.  
  
 `ENOEXEC`  
 Zadaný soubor není spustitelný soubor nebo má neplatný formát souboru spustitelný soubor.  
  
 `ENOMEM`  
 Nedostatek paměti je k dispozici pro spuštění nový proces.  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí vytvoří a spustí nový proces předávání každý argument příkazového řádku jako samostatného parametru a pomocí `PATH` proměnnou prostředí najít soubor provést.  
  
 Tyto funkce ověřit jejich parametrů. Pokud má jedna `cmdname` nebo `arg0` je prázdný řetězec nebo nulového ukazatele tyto funkce vygeneruje výjimka neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL`a vrátí hodnotu -1. Žádný nový proces je vytvořený.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_spawnlp`|\<process.h>|  
|`_wspawnlp`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad v [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [AtExit](../../c-runtime-library/reference/atexit.md)   
 [_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall –](../../c-runtime-library/reference/flushall.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)