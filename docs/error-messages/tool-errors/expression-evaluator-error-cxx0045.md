---
title: "CXX0045 Chyba vyhodnocování výrazu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0045
dev_langs: C++
helpviewer_keywords:
- CXX0045
- CAN0045
ms.assetid: 32181bc8-e79c-4ad7-a82f-47c62ec06d7d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 97aabf5601680a9f7e94806619a2cc6c0e616e95
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0045"></a>Chyba při vyhodnocování výrazu CXX0045
není funkcí  
  
 Seznam argumentů byl zadán pro symbol v programu, který není název funkce.  
  
## <a name="example"></a>Příklad  
  
```  
queue( alpha, beta )  
```  
  
 Když `queue` není funkce.  
  
 Tato chyba je stejný jako CAN0045.