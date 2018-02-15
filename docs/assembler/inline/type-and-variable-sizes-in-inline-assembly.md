---
title: "Typ a velikost proměnných ve vloženém sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- length
- Type
dev_langs:
- C++
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38cbbd292ea662a725a8356b53fd0c1686e698e1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>Typ a velikost proměnných ve vloženém sestavení
**Microsoft Specific**  
  
 **Délka**, **velikost**, a **typ** operátory mají omezenou význam ve vloženém sestavení. Nelze je použít na všech s `DUP` – operátor (protože nelze definovat data pomocí direktivy MASM nebo operátory). Ale můžete je použít k vyhledání velikost jazyka C nebo C++ proměnné nebo typy:  
  
-   **Délka** operátor může vrátit počet elementů v matici. Vrátí hodnotu 1 pro proměnné jiné pole.  
  
-   **Velikost** operátor může vrátit velikost proměnné jazyka C nebo C++. Proměnnou velikost je produkt jeho **délka** a **typu**.  
  
-   **Typ** operátor může vrátit velikost jazyka C nebo C++ typu nebo proměnné. Pokud je proměnná pole, **typ** vrátí velikost jednoho prvku pole.  
  
 Například, pokud má 8 element program `int` pole,  
  
```  
int arr[8];  
```  
  
 Následující výrazy jazyka C a sestavení yield velikost `arr` a jejích elementů.  
  
|__asm|C|Velikost|  
|-------------|-------|----------|  
|**Délka** směrování žádostí na aplikace|`sizeof`(arr)/`sizeof`(arr[0])|8|  
|**VELIKOST** směrování žádostí na aplikace|`sizeof`(arr)|32|  
|**TYP** směrování žádostí na aplikace|`sizeof`(arr[0])|4|  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)