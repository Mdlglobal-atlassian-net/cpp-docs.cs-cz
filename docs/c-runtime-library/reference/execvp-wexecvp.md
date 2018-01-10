---
title: "_execvp –, _wexecvp – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _execvp
- _wexecvp
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
- _execvp
- wexecvp
- _wexecvp
dev_langs: C++
helpviewer_keywords:
- _execvp function
- _wexecvp function
- wexecvp function
- execvp function
ms.assetid: a4db15df-b204-4987-be7c-de84c3414380
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38ab921dc120fc82e05845c62dcc355167ad09c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="execvp-wexecvp"></a>_execvp, _wexecvp
Načte a spustí novou podřízené procesy.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
intptr_t _execvp(   
   const char *cmdname,  
   const char *const *argv   
);  
intptr_t _wexecvp(   
   const wchar_t *cmdname,  
   const wchar_t *const *argv   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cmdname`  
 Cesta k souboru provést.  
  
 `argv`  
 Pole ukazatele na parametry.  
  
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
 Každá z těchto funkcí načte a spustí nový proces, pole ukazatele předání argumentů příkazového řádku a pomocí `PATH` proměnnou prostředí najít soubor provést.  
  
 `_execvp` Funkcí ověření jejich parametrů. Pokud `cmdname` je ukazatel s hodnotou null, nebo `argv` je ukazatel s hodnotou null, ukazatel na prázdné pole, nebo pokud pole obsahuje prázdný řetězec jako první argument, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí hodnotu -1. Žádný proces se spustí.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|--------------|---------------------|---------------------|  
|`_execvp`|\<Process.h >|\<errno.h >|  
|`_wexecvp`|\<Process.h > nebo \<wchar.h >|\<errno.h >|  
  
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
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)