---
title: "_Crtmemdifference – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
dev_langs: C++
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ba4dc873fbb0e77f3b2f939c9d62533849dab76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crtmemdifference"></a>_CrtMemDifference
Porovná dva paměti stavy a vrátí rozdíly mezi nimi (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _CrtMemDifference(   
   _CrtMemState *stateDiff,  
   const _CrtMemState *oldState,  
   const _CrtMemState *newState   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stateDiff`  
 Ukazatel na `_CrtMemState` struktura, která se používá k ukládání rozdíly mezi stavy dvě paměti (nevrátil).  
  
 `oldState`  
 Ukazatel předchozího stavu paměti (`_CrtMemState` struktura).  
  
 `newState`  
 Ukazatel na novější stav paměti (`_CrtMemState` struktura).  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud stavy paměť se výrazně liší, `_CrtMemDifference` vrátí hodnotu TRUE. Funkce, jinak vrátí hodnotu FALSE.  
  
## <a name="remarks"></a>Poznámky  
 `_CrtMemDifference` Funkce porovná `oldState` a `newState` a ukládá jejich rozdíly v `stateDiff`, který pak lze aplikací ke zjišťování nevracení paměti a jiných problémů paměti. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtMemDifference` jsou odebrány při předběžném zpracování.  
  
 `newState`a `oldState` musí být platný ukazatel `_CrtMemState` struktuře, definované v Crtdbg.h, který má byla vyplněna objektem [_crtmemcheckpoint –](../../c-runtime-library/reference/crtmemcheckpoint.md) před voláním `_CrtMemDifference`. `stateDiff`musí být ukazatel na dříve přidělené instanci `_CrtMemState` struktura. Pokud `stateDiff`, `newState`, nebo `oldState` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je nastaven na `EINVAL` , funkce vrátí hodnotu FALSE.  
  
 `_CrtMemDifference`Porovná `_CrtMemState` pole hodnoty bloků v `oldState` na hodnoty v `newState` a ukládá výsledky v `stateDiff`. Počet přidělené bloku typů nebo mezi dvěma paměti stavy liší celkový počet přidělených bloků pro každý typ, jsou stavy označeny jako výrazně lišit. Rozdíl mezi největší velikost někdy přidělené najednou dva stavy a rozdíl mezi celkový přidělení pro dva stavy jsou také uloženy v `stateDiff`.  
  
 Ve výchozím nastavení, interní bloky C Runtime (`_CRT_BLOCK`) nejsou zahrnuty v operacích stavu paměti. [_Crtsetdbgflag –](../../c-runtime-library/reference/crtsetdbgflag.md) funkce slouží k zapnutí `_CRTDBG_CHECK_CRT_DF` bit z `_crtDbgFlag` zjištění paměti a dalších operací stavu paměti zahrnout tyto bloky. Vydání bloky paměti (`_FREE_BLOCK`) nezpůsobí `_CrtMemDifference` vrátí hodnotu TRUE.  
  
 Další informace o stavu funkce hald a `_CrtMemState` struktury najdete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_CrtMemDifference`|\<crtdbg.h >|\<errno.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
 **Knihovny:** ladicí verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)