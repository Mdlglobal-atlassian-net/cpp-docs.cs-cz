---
title: "_Crtdbgbreak – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtDbgBreak
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
- _CrtDbgBreak
- CrtDbgBreak
dev_langs: C++
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dafc1b743af2b11c83f7dc6d932844c6aa9da609
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crtdbgbreak"></a>_CrtDbgBreak
Nastaví přerušení na konkrétní řádek kódu. (Používá se v režimu ladění jenom.)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _CrtDbgBreak( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Není k dispozici žádnou návratovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `_CrtDbgBreak` Funkce nastaví ladicích zarážek na konkrétní řádek kódu, kde se funkce nachází. Tato funkce se používá v režimu ladění pouze a závisí na `_DEBUG` dříve definovaný.  
  
 Další informace o použití jiných podporující háku běhové funkce a psaní vlastního klienta definované funkce háku najdete v tématu [zápis vaše vlastní ladění funkce háku](/visualstudio/debugger/debug-hook-function-writing).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_CrtDbgBreak`|\<CRTDBG.h >|  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [__debugbreak](../../intrinsics/debugbreak.md)