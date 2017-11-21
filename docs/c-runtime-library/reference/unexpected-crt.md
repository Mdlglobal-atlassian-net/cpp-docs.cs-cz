---
title: "neočekávané (CRT) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: unexpected
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
f1_keywords: unexpected
dev_langs: C++
helpviewer_keywords: unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 39cc7164a22b95f2c269c7bb1bd558374f56fa3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="unexpected-crt"></a>neočekávané (CRT)
Volání `terminate` nebo funkce, které zadáte pomocí `set_unexpected`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void unexpected( void );  
```  
  
## <a name="remarks"></a>Poznámky  
 `unexpected` Rutiny se nepoužívá s aktuální implementace zpracování výjimek jazyka C++. `unexpected`volání `terminate` ve výchozím nastavení. Psaní vlastních ukončení funkce a volání metody můžete změnit toto výchozí chování `set_unexpected` s názvem funkce jako její argument. `unexpected`volá funkci naposledy zadaný jako argument pro `set_unexpected`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`unexpected`|\<EH.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [_set_se_translator –](../../c-runtime-library/reference/set-se-translator.md)   
 [set_terminate –](../../c-runtime-library/reference/set-terminate-crt.md)   
 [set_unexpected –](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [ukončení](../../c-runtime-library/reference/terminate-crt.md)