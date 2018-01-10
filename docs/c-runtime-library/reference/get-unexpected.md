---
title: "_get_unexpected – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_unexpected
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
- __get_unexpected
- _get_unexpected
- get_unexpected
dev_langs: C++
helpviewer_keywords:
- __get_unexpected function
- get_unexpected function
- _get_unexpected function
ms.assetid: a5f7a7a0-18e0-485e-953d-db291068a1e8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d40eab2cb632f7a29d88f0718388ea0582b147d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="getunexpected"></a>_get_unexpected
Vrátí rutina ukončení má být volána `unexpected`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unexpected_function _get_unexpected( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na funkci registrovaných [set_unexpected –](../../c-runtime-library/reference/set-unexpected-crt.md). Pokud byla nastavena žádná funkce, návratovou hodnotu může použít k obnovení výchozího chování; Tato hodnota může mít hodnotu NULL.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_get_unexpected`|\<EH.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [set_terminate –](../../c-runtime-library/reference/set-terminate-crt.md)   
 [ukončení](../../c-runtime-library/reference/terminate-crt.md)   
 [neočekávané](../../c-runtime-library/reference/unexpected-crt.md)