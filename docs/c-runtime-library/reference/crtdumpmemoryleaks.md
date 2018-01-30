---
title: "_Crtdumpmemoryleaks – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtDumpMemoryLeaks
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
apitype: DLLExport
f1_keywords:
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
dev_langs:
- C++
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 859f1918afc69054b13cab161f2d7b4801bcbd78
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks
Výpisy veškerou paměť bloků v haldě ladění při nevrácené paměti došlo k chybě (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int _CrtDumpMemoryLeaks( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 `_CrtDumpMemoryLeaks`Vrátí hodnotu PRAVDA, pokud je nalezen nevrácenou pamětí. Funkce, jinak vrátí hodnotu FALSE.  
  
## <a name="remarks"></a>Poznámky  
 `_CrtDumpMemoryLeaks` Funkce určuje, zda nevrácenou pamětí došlo od spuštění tohoto programu. Když se najde nevrácenou, informace o ladění záhlaví pro všechny objekty v haldě vypsána ve formě uživatelem čitelný. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtDumpMemoryLeaks` jsou odebrány při předběžném zpracování.  
  
 `_CrtDumpMemoryLeaks`se často nazývá na konci spuštění programu pro ověření, že bylo uvolněno všechny paměti přidělené aplikace. Funkci nelze volat automaticky v ukončení programu zapnutím `_CRTDBG_LEAK_CHECK_DF` bit pole [_crtdbgflag –](../../c-runtime-library/crtdbgflag.md) příznak pomocí [_crtsetdbgflag –](../../c-runtime-library/reference/crtsetdbgflag.md) funkce.  
  
 `_CrtDumpMemoryLeaks`volání [_crtmemcheckpoint –](../../c-runtime-library/reference/crtmemcheckpoint.md) se získat aktuální stav haldy a pak kontroluje stav bloků, které nebyly bylo uvolněno. Když je zjištěna neuvolněných bloku, `_CrtDumpMemoryLeaks` volání [_crtmemdumpallobjectssince –](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) k výpisu informace pro všechny objekty přidělené v haldě od začátku spuštění programu.  
  
 Ve výchozím nastavení, interní bloky C Runtime (`_CRT_BLOCK`) nejsou zahrnuty do operace výpisu paměti. [_Crtsetdbgflag –](../../c-runtime-library/reference/crtsetdbgflag.md) funkce slouží k zapnutí `_CRTDBG_CHECK_CRT_DF` bit z `_crtDbgFlag` zahrnout tyto bloky v procesu zjišťování úniku.  
  
 Další informace o stavu funkce hald a `_CrtMemState` struktury najdete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_CrtDumpMemoryLeaks`|\<crtdbg.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
 Příklad, jak pomocí `_CrtDumpMemoryLeaks`, najdete v části [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)