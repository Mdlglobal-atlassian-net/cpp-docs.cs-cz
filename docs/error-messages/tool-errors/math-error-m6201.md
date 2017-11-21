---
title: "Chyba matematické operace M6201 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6201
dev_langs: C++
helpviewer_keywords: M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e8288770d74497e576a299d683b846214a187a1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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