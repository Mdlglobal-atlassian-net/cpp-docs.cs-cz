---
title: "_spawnle –, _wspawnle – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _spawnle
- _wspawnle
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
- spawnle
- _spawnle
- wspawnle
- _wspawnle
dev_langs: C++
helpviewer_keywords:
- spawnle function
- processes, creating
- _wspawnle function
- processes, executing new
- process creation
- wspawnle function
- _spawnle function
ms.assetid: 80308892-2815-49b1-8cca-53894c366f5a
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1db331aa1f424e96cc10f89a944abc1e4ac43d2f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="spawnle-wspawnle"></a>_spawnle, _wspawnle
Vytvoří a spustí nový proces.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
intptr_t _spawnle(  
   int mode,  
   const char *cmdname,  
   const char *arg0,  
   const char *arg1,  
   ... const char *argn,  
   NULL,  
   const char *const *envp   
);  
intptr_t _wspawnle(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   const wchar_t *arg1,  
   ... const wchar_t *argn,  
   NULL,  
   const wchar_t *const *envp   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mode`  
 Režim spuštění pro proces volání.  
  
 `cmdname`  
 Cesta k souboru, který má být proveden.  
  
 `arg0, arg1, ... argn`  
 Seznam ukazatele na argumenty. `arg0` Argument je obvykle ukazatel na `cmdname`. Argumenty `arg1` prostřednictvím `argn` jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Následující `argn`, musí existovat `NULL` ukazatel na konec seznamu argumentů.  
  
 `envp`  
 Pole ukazatele na nastavení prostředí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota z synchronního `_spawnle` nebo `_wspawnle` (`_P_WAIT` zadaná pro `mode`) je stav ukončení nový proces. Vrácená hodnota z asynchronní `_spawnle` nebo `_wspawnle` (`_P_NOWAIT` nebo `_P_NOWAITO` zadaná pro `mode`) je proces popisovač. Stav ukončení je 0, pokud proces ukončen normálně. Můžete nastavit stav ukončení nenulovou hodnotu, pokud proces spuštěný konkrétně volá `exit` rutiny s argumentem nenulové hodnoty. Pokud nový proces explicitně nenastavili stav kladné ukončení, označuje stav kladné ukončení abnormální ukončení s přerušení nebo přerušení. Vrácená hodnota -1 označuje chybu (není spuštěn nový proces). V takovém případě `errno` nastaven na jednu z následujících hodnot.  
  
 `E2BIG`  
 Seznam argumentů je větší než 1024 bajtů.  
  
 `EINVAL`  
 `mode`argument je neplatný.  
  
 `ENOENT`  
 Soubor nebo cesta nebyla nalezena.  
  
 `ENOEXEC`  
 Zadaný soubor není spustitelný soubor nebo má neplatný formát souboru spustitelný soubor.  
  
 `ENOMEM`  
 Nedostatek paměti je k dispozici pro spuštění nový proces.  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí se vytvoří a spustí nový proces předávání každý argument příkazového řádku jako samostatného parametru a také řadu ukazatele předávání do nastavení prostředí.  
  
 Tyto funkce ověřit jejich parametrů. Pokud má jedna `cmdname` nebo `arg0` je prázdný řetězec nebo nulového ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL`a vrátí hodnotu -1. Žádný nový proces je vytvořený.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_spawnle`|\<Process.h >|  
|`_wspawnle`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad v [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [AtExit](../../c-runtime-library/reference/atexit.md)   
 [_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)   
 [ukončení, _exit –, _exit –](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall –](../../c-runtime-library/reference/flushall.md)   
 [_getmbcp –](../../c-runtime-library/reference/getmbcp.md)   
 [_onexit –, _onexit_m –](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_setmbcp –](../../c-runtime-library/reference/setmbcp.md)   
 [_wsystem – systém](../../c-runtime-library/reference/system-wsystem.md)