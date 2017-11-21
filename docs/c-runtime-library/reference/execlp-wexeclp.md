---
title: "_execlp –, _wexeclp – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wexeclp
- _execlp
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
- _wexeclp
- wexeclp
- _execlp
dev_langs: C++
helpviewer_keywords:
- execlp function
- _execlp function
- _wexeclp function
- wexeclp function
ms.assetid: 7b179163-4bcd-4d6a-8baf-68f886791928
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f02bff312ec718333aa46184830397976b0df240
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="execlp-wexeclp"></a>_execlp, _wexeclp
Načte a spustí novou podřízené procesy.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
intptr_t _execlp(   
   const char *cmdname,  
   const char *arg0,  
   ... const char *argn,  
   NULL   
);  
intptr_t _wexeclp(   
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   ... const wchar_t *argn,  
   NULL   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cmdname`  
 Cesta k souboru provést.  
  
 `arg0, ... argn`  
 Seznam ukazatele na parametry.  
  
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
 Každá z těchto funkcí načte a spustí nový proces předávání každý argument příkazového řádku jako samostatného parametru a pomocí `PATH` proměnnou prostředí najít soubor provést.  
  
 `_execlp` Funkcí ověření jejich parametrů. Pokud `cmdname` nebo `arg0` ukazatele null nebo prázdný řetězec, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí hodnotu -1. Žádný nový proces se spustí.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|--------------|---------------------|---------------------|  
|`_execlp`|\<Process.h >|\<errno.h >|  
|`_wexeclp`|\<Process.h > nebo \<wchar.h >|\<errno.h >|  
  
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