---
title: __CxxFrameHandler | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __CxxFrameHandler
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __CxxFrameHandler
dev_langs:
- C++
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4741e0da471e9b82b4d4a2f436feaae482fbbae0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cxxframehandler"></a>__CxxFrameHandler
Vnitřní funkce CRT. Používá CRT pro zpracování strukturovaných výjimka rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
EXCEPTION_DISPOSITION __CxxFrameHandler(  
      EHExceptionRecord  *pExcept,  
      EHRegistrationNode *pRN,  
      void               *pContext,   
      DispatcherContext  *pDC  
   )  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExcept`  
 Výjimka záznam, který je předán možné `catch` příkazy.  
  
 `pRN`  
 Dynamické informace o rámce zásobníku, který slouží ke zpracování výjimky. Další informace najdete v tématu ehdata.h.  
  
 `pContext`  
 Kontext. (Nepoužívá se na procesory Intel.)  
  
 `pDC`  
 Další informace o funkce zásobníku a položka rámečku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden z *výrazu filtru* hodnoty používané [zkuste-except – příkaz](../cpp/try-except-statement.md).  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|__CxxFrameHandler|excpt.h, ehdata.h|