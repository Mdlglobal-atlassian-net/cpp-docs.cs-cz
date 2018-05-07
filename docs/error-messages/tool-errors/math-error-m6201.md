---
title: Chyba matematické operace M6201 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6201
dev_langs:
- C++
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6a15e841cfc8daf1abdafc9997698807e7356af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="math-error-m6201"></a>Chyba matematické operace M6201
'function': _domain – chyba  
  
 Argument pro danou funkci byla mimo doménu platné vstupní hodnoty pro tuto funkci.  
  
## <a name="example"></a>Příklad  
  
```  
result = sqrt(-1.0)   // C statement  
result = SQRT(-1.0)   !  FORTRAN statement  
```  
  
 Tato chyba volání `_matherr` funkce s názvem funkce, jeho argumenty a typ chyby. Je možné přepsat `_matherr` funkce přizpůsobit zpracování určitých spuštění s plovoucí desetinnou čárkou matematické chyby.