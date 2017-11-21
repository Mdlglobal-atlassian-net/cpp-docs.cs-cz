---
title: "_Ciatan2 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIatan2
apilocation:
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- CIatan2
- _CIatan2
dev_langs: C++
helpviewer_keywords:
- _CIatan2 intrinsic
- CIatan2 intrinsic
ms.assetid: 31f8cc78-b79f-4576-b73b-8add18e08680
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6afa8ac8561b8ba2dcc7b8f7c2253ae29ecf6844
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ciatan2"></a>_CIatan2
Vypočítá Arkus tangens *x* / *y* kde *x* a *y* jsou hodnoty v horní části zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __cdecl _CIatan2();  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato verze `atan2` funkce má specializované konvence volání, která funguje s technologií kompilátoru. Ji urychluje spuštění, protože kopie brání generován a pomáhá s přidělení registru.  
  
 Výsledná hodnota se posune do horní části zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** x86  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [Atan, atanf –, atanl –, atan2, atan2f –, atan2l –](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)