---
title: "_cexit –, _c_exit – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _c_exit
- _cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
dev_langs: C++
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 099114e2c05a1466b11e88c176d40a6ec70fe360
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cexit-cexit"></a>_cexit, _c_exit
Operace vyčištění provede a vrátí bez proces se ukončuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _cexit( void );  
void _c_exit( void );  
```  
  
## <a name="remarks"></a>Poznámky  
 `_cexit` Funkce volání v last-in, pořadí ven (LIFO), funkce registrovaných `atexit` a `_onexit`. Potom `_cexit` vyprázdnění všech vstupně-výstupní vyrovnávací paměti a zavře všechny otevřené datové proudy před vrácením. `_c_exit`je stejný jako `_exit` , ale vrací do procesu volání bez zpracování `atexit` nebo `_onexit` nebo abyste vyprázdnili vyrovnávací paměti datového proudu. Chování `exit`,`_exit`, `_cexit`, a `_c_exit` je uvedené v následující tabulce.  
  
|Funkce|Chování|  
|--------------|--------------|  
|`exit`|Provádí kompletní postupy ukončení knihovna jazyka C, ukončí proces a ukončí se zadaný stavovým kódem.|  
|`_exit`|Provede rychlé C knihovny ukončení postupy, ukončí proces a ukončí se zadaný stavovým kódem.|  
|`_cexit`|Provádí kompletní postupy ukončení knihovna jazyka C a vrátí volajícího, ale není ukončení procesu.|  
|`_c_exit`|Provede rychlé postupy ukončení knihovna jazyka C a vrátí volajícího, ale není ukončení procesu.|  
  
 Při volání `_cexit` nebo `_c_exit` funkce, nejsou názvem destruktory pro dočasné nebo automatické objekty, které existují v čase volání. Automatické objekt je objekt, který je definovaný ve funkci, kde není objekt deklarovaný statická. Dočasný objekt je objekt vytvořený kompilátoru. Zrušení automatického objekt před voláním `_cexit` nebo `_c_exit`, explicitní volání destruktoru objektu, následujícím způsobem:  
  
```  
myObject.myClass::~myClass( );  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_cexit`|\<Process.h >|  
|`_c_exit`|\<Process.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [AtExit](../../c-runtime-library/reference/atexit.md)   
 [_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)   
 [ukončení, _exit –, _exit –](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit –, _onexit_m –](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)