---
title: CXX0064 Chyba vyhodnocování výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0064
dev_langs:
- C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7964eac628fa89695d1757cff8b7b329fd7fe713
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302133"
---
# <a name="expression-evaluator-error-cxx0064"></a>Chyba při vyhodnocování výrazu CXX0064
Nelze nastavit bod přerušení na člena vázané virtuální funkce  
  
 Zarážku byl nastaven na člena virtuální funkce prostřednictvím ukazatele na objekt, jako například:  
  
```  
pClass->vfunc( int );  
```  
  
 Zarážky můžete nastavit na virtuální funkci zadáním třídy, jako například:  
  
```  
Class::vfunc( int );  
```  
  
 Tato chyba je stejný jako CAN0064.