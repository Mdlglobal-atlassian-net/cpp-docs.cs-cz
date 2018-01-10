---
title: "Typy celého čísla | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e324976d0054cd1b32188b6ebe0f10ab4e1bdd69
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="integer-types"></a>Typy celého čísla
Každé celočíselné konstantě je předán typ na základě její hodnoty a způsobu, jakým je vyjádřena. Můžete vynutit žádné celočíselná konstanta na typ **dlouho** připojením písmeno **l** nebo **L** na konec konstanta; můžete vynutit mohla být typu `unsigned` připojením **u** nebo **U** na hodnotu. Malé písmeno **l** může být zaměňovat s 1 číslice a je nutno. Některé formy **dlouho** podle celočíselné konstanty:  
  
```  
/* Long decimal constants */  
10L  
79L  
  
/* Long octal constants */  
012L  
0115L  
  
/* Long hexadecimal constants */  
0xaL or 0xAL  
0X4fL or 0x4FL  
  
/* Unsigned long decimal constant */  
776745UL  
778866LU  
```  
  
 Typ přiřazený konstantě závisí na hodnotě, kterou konstanta představuje. Hodnota konstanty musí být v rozsahu reprezentovatelných hodnot jejího typu. Typ konstanta Určuje, které převody jsou prováděny, když konstanta se používá ve výrazu nebo když znaménka minus (**-**) se použije. Tento seznam shrnuje pravidla převodu celočíselných konstant.  
  
-   Typ decimal konstanta bez příponu je buď `int`, **dlouho int**, nebo **nepodepsané dlouho int**. První z těchto tří typů, ve kterých lze hodnotu konstanty reprezentovat, je typ přiřazený konstantě.  
  
-   Typ přiřazené osmičkových a šestnáctkových konstanty bez přípony je `int`, `unsigned int`, **dlouho int**, nebo **nepodepsané dlouho int** v závislosti na velikosti konstanty.  
  
-   Typ přiřazené konstanty s **u** nebo **U** přípona je **nepodepsané int** nebo **nepodepsané dlouho int** v závislosti na jejich velikost.  
  
-   Typ přiřazené konstanty s **l** nebo **L** přípona je **dlouho int** nebo **nepodepsané dlouho int** v závislosti na jejich velikost.  
  
-   Typ přiřazené konstanty s **u** nebo **U** a **l** nebo **L** přípona je **nepodepsané dlouho int**.  
  
## <a name="see-also"></a>Viz také  
 [Konstanty typu Integer jazyka C](../c-language/c-integer-constants.md)