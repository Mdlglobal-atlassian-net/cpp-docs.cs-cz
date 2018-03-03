---
title: "_Cisqrt – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CIsqrt
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _CIsqrt
- CIsqrt
dev_langs:
- C++
helpviewer_keywords:
- CIsqrt intrinsic
- _CIsqrt intrinsic
ms.assetid: 663548ea-398c-48ee-8397-a787c6ebb937
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5662683c53323d103105f04e872e91e137dbfe26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cisqrt"></a>_CIsqrt
Vypočítá druhou odmocninu čísla nejvyšší hodnotu v zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __cdecl _CIsqrt();  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato verze `sqrt` funkce má specializované konvence volání, která funguje s technologií kompilátoru. Ji urychluje spuštění, protože kopie brání generován a pomáhá s přidělení registru.  
  
 Výsledná hodnota se posune do horní části zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** x86  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)