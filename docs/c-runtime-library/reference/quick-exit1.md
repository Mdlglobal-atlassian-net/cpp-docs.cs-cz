---
title: quick_exit1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: quick_exit
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
- quick_exit
- process/quick_exit
- stdlib/quick_exit
dev_langs: C++
helpviewer_keywords: quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d2ae187d0132ca53b1ffba2b26ef18fa467b9072
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="quickexit"></a>quick_exit
Způsobí ukončení normální programu proběhnout.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec(noreturn) void quick_exit(  
    int status  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 stav  
 Kód stavu se vraťte do prostředí hostitele.  
  
## <a name="return-value"></a>Návratová hodnota  
 `quick_exit` Funkce nelze vrátit k jeho volajícího.  
  
## <a name="remarks"></a>Poznámky  
 `quick_exit` Funkce způsobí ukončení normální programu. Zavolá žádné funkce registrovaných `atexit`, `_onexit` nebo signál registrovaných obslužné rutiny `signal` funkce. Pokud není definován chování `quick_exit` nazývá více než jednou, nebo pokud `exit` je volána funkce.  
  
 `quick_exit` Funkce volání v last-in, pořadí ven (LIFO), funkce registrovaných `at_quick_exit`, s výjimkou pro tyto funkce už voláno, když byl zaregistrován funkce.  Pokud není definován chování [longjmp](../../c-runtime-library/reference/longjmp.md) přišla v průběhu hovoru registrovaná funkce, která by ukončit volání funkce.  
  
 Po zavolání registrovaná funkce `quick_exit` vyvolá `_Exit` pomocí `status` hodnota vrátit kontrolu hostitelské prostředí.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`quick_exit`|\<Process.h > nebo \<stdlib.h >|  
  
 Další informace o kompatibilitě najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [AtExit](../../c-runtime-library/reference/atexit.md)   
 [_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)   
 [ukončení, _exit –, _exit –](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit –, _onexit_m –](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)   
 [_wsystem – systém](../../c-runtime-library/reference/system-wsystem.md)