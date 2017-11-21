---
title: "_Cipow – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIpow
apilocation:
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- CIpow
- _CIpow
dev_langs: C++
helpviewer_keywords:
- CIpow intrinsic
- _CIpow intrinsic
ms.assetid: 477aaf0c-ac58-4252-89dd-9f3e35d47536
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f5e2e9d621f2913b93d12288ce62c479907c4ba0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cipow"></a>_CIpow
Vypočítá *x* umocněné *y* power podle nejvyšších hodnot v zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __cdecl _CIpow();  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato verze `pow` funkce má specializované konvence volání, která funguje s technologií kompilátoru. Ji urychluje spuštění, protože kopie brání generován a pomáhá s přidělení registru.  
  
 Výsledná hodnota se posune do horní části zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** x86  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [Pow – powf – powl –](../c-runtime-library/reference/pow-powf-powl.md)