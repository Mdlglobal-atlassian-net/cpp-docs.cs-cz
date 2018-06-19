---
title: C3551 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3551
dev_langs:
- C++
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f9f69adcf071415d3c1760294bdaaaec7b71f8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257857"
---
# <a name="compiler-error-c3551"></a>C3551 chyby kompilátoru
"očekává, že že pozdní zadán návratový typ"  
  
 Pokud použijete `auto` – klíčové slovo jako zástupný symbol pro návratový typ funkce, je nutné zadat návratový typ pozdní zadaný. V následujícím příkladu pozdní určených pro návratový typ funkce `myFunction` ukazatel na pole čtyři elementy typu `int`.  
  
```  
auto myFunction()->int(*)[4];   
```  
  
## <a name="see-also"></a>Viz také  
 [auto](../../cpp/auto-cpp.md)