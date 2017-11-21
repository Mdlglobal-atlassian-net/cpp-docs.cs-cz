---
title: "ukončení, _exit –, _exit – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _exit
- exit
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
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
dev_langs: C++
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
ms.assetid: b1501fa6-27c2-478c-9e93-cc4fd802a01f
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f68ef6938c1f42ccde300838915292c5abe36af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="exit-exit-exit"></a>ukončení, _exit –, _exit –
Ukončí proces volání. `exit` Funkce ukončí ho po vyčištění; `_exit` a `_Exit` okamžitě ho ukončit.  
  
> [!NOTE]
>  Nepoužívejte tuto metodu pro vypnutí aplikace univerzální platformu Windows (UWP) nebo [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace, kromě testování nebo ladění scénáře. Zavřete způsoby programový nebo uživatelského rozhraní [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace nejsou povoleny. Další informace o aplikacích pro Windows 8 a 8.1 najdete v tématu [životní cyklus aplikace](http://go.microsoft.com/fwlink/?LinkId=262853). Další informace o aplikacích pro Windows 10 najdete v tématu [postupy, příručky pro aplikace pro Windows 10](http://go.microsoft.com/fwlink/p/?linkid=619133).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void exit(   
   int const status   
);  
void _Exit(   
   int const status   
);  
void _exit(   
   int const status   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `status`  
 Ukončovací kód stavu.  
  
## <a name="remarks"></a>Poznámky  
 `exit`, `_Exit` a `_exit` funkce ukončit proces volání. `exit` Funkce volá destruktory pro místní objekty, pak zavolá – v pořadí last-in-first-out (LIFO) – funkce, které jsou registrovány `atexit` a `_onexit`a pak vyprázdnění všech vyrovnávací paměti souboru předtím, než ho ukončí proces. `_Exit` a `_exit` funkce ukončit proces bez zničení objektů místní nebo zpracování `atexit` nebo `_onexit` funkce a bez vyprázdnění vyrovnávací paměti datového proudu.  
  
 I když `exit`, `_Exit` a `_exit` volání nevrátí hodnotu, hodnotu v `status` je k dispozici na hostitelském prostředí nebo volání proces čekání, pokud takové existuje, po ukončení procesu. Obvykle se nastaví volajícího `status` hodnotu na 0, budou znamenat normální ukončovací nebo na jinou hodnotu indikující chybu. Hodnota parametru `status` je k dispozici dávkovému příkazu `ERRORLEVEL` operačního systému a je reprezentována jednou ze dvou konstant: `EXIT_SUCCESS`, která představuje hodnotu 0, nebo `EXIT_FAILURE`, která představuje hodnotu 1.  
  
 `exit`, `_Exit`, `_exit`, `quick_exit`, `_cexit`, A `_c_exit` funkce chovat následujícím způsobem.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`exit`|Provede dokončení procedury ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód na hostitelském prostředí.|  
|`_Exit`|Provede minimální postupy ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód na hostitelském prostředí.|  
|`_exit`|Provede minimální postupy ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód na hostitelském prostředí.|  
|`quick_exit`|Provede rychlé postupy ukončení knihovna jazyka C, ukončí proces a poskytuje zadaný stavový kód, který má hostitelské prostředí.|  
|`_cexit`|Provádí kompletní C knihovny ukončení postupy a vrátí volajícímu. Nelze ukončit proces.|  
|`_c_exit`|Provede minimální C knihovny ukončení postupy a vrátí volajícímu. Nelze ukončit proces.|  
  
Při volání `exit`, `_Exit` nebo `_exit` nejsou volat funkci, destruktory pro dočasné nebo automatické objekty, které existují v čase volání. Automatické objekt je nestatické místní objekt definovaný ve funkci. Dočasný objekt je objekt, který byl vytvořený v kompilátoru, jako je například hodnotu vrácenou z volání funkce. Chcete-li odstranit Automatická objekt před voláním `exit`, `_Exit`, nebo `_exit`, explicitní volání destruktoru objektu, jak je vidět tady:  
  
```cpp 
void last_fn() {} 
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);  
}
```  
  
Pro volání funkce `DLL_PROCESS_ATTACH` z funkce `exit` nepoužívejte hodnotu `DllMain`. Chcete-li ukončit `DLLMain` fungovat, vrátí `FALSE` z `DLL_PROCESS_ATTACH`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`exit`, `_Exit`, `_exit`|\<Process.h > nebo \<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_exit.c  
// This program returns an exit code of 1. The  
// error code could be tested in a batch file.  
  
#include <stdlib.h>  
  
int main( void )  
{  
   exit( 1 );  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [AtExit](../../c-runtime-library/reference/atexit.md)   
 [_cexit –, _c_exit –](../../c-runtime-library/reference/cexit-c-exit.md)   
 [_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)   
 [_onexit –, _onexit_m –](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [quick_exit](../../c-runtime-library/reference/quick-exit1.md)   
 [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)   
 [_wsystem – systém](../../c-runtime-library/reference/system-wsystem.md)