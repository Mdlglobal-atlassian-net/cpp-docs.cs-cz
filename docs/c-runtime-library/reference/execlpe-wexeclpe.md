---
title: "_execlpe –, _wexeclpe – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _execlpe
- _wexeclpe
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
- _wexeclpe
- execlpe
- wexeclpe
- _execlpe
dev_langs: C++
helpviewer_keywords:
- wexeclpe function
- _wexeclpe function
- _execlpe function
- execlpe function
ms.assetid: 07b861da-3e7e-4f1d-bb80-ad69b55e5162
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 488db0ebbc44265c2be35dcdcb6995c05d7b8a10
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="execlpe-wexeclpe"></a>_execlpe, _wexeclpe
Načte a spustí novou podřízené procesy.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
intptr_t _execlpe(   
   const char *cmdname,  
   const char *arg0,  
   ... const char *argn,  
   NULL,  
   const char *const *envp   
);  
intptr_t _wexeclpe(   
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   ... const wchar_t *argn,  
   NULL,  
   const wchar_t *const *envp   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cmdname`  
 Cesta k souboru provést.  
  
 `arg0, ... argn`  
 Seznam ukazatele na parametry.  
  
 `envp`  
 Pole ukazatele na nastavení prostředí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud bylo úspěšné, nevrátí se tyto funkce pro proces volání. Vrácená hodnota -1 označuje chybu, v takovém případě `errno` globální proměnná je nastavená.  
  
|`errno`Hodnota|Popis|  
|-------------------|-----------------|  
|`E2BIG`|Místo požadované pro argumenty a nastavení prostředí je větší než 32 KB.|  
|`EACCES`|Zadaný soubor došlo k narušení uzamčení nebo sdílení.|  
|`EINVAL`|Neplatný parametr.|  
|`EMFILE`|Příliš mnoho souborů otevřete (zadaný soubor musí být otevřené pro určení, zda je spustitelný soubor).|  
|`ENOENT`|Soubor nebo cesta nebyla nalezena.|  
|`ENOEXEC`|Zadaný soubor není spustitelný soubor nebo má neplatný formát souboru spustitelný soubor.|  
|`ENOMEM`|Nedostatek paměti je k dispozici pro spuštění nový proces; dostupná paměť je poškozená; nebo bloku neplatný existuje, která určuje, že proces volání nebyla přidělena správně.|  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí načte a spustí nový proces předávání každý argument příkazového řádku jako samostatného parametru a také řadu ukazatele předávání do nastavení prostředí. Použijte tyto funkce `PATH` proměnnou prostředí najít soubor provést.  
  
 `_execlpe` Funkcí ověření jejich parametrů. Pokud má jedna `cmdname` nebo `arg0` je null ukazatele nebo prázdný řetězec, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí hodnotu -1. Žádný nový proces se spustí.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|--------------|---------------------|---------------------|  
|`_execlpe`|\<Process.h >|\<errno.h >|  
|`_wexeclpe`|\<Process.h > nebo \<wchar.h >|\<errno.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad v [_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [AtExit](../../c-runtime-library/reference/atexit.md)   
 [ukončení, _exit –, _exit –](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit –, _onexit_m –](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)   
 [_wsystem – systém](../../c-runtime-library/reference/system-wsystem.md)