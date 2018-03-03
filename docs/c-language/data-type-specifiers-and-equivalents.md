---
title: "Datový typ specifikátory a ekvivalenty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 596e3fcf4dab3f88abc17cac4bc32471e63b4bbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="data-type-specifiers-and-equivalents"></a>Specifikátory a ekvivalenty datového typu
Tato kniha obecně namísto dlouhých tvarů používá tvary specifikátorů typů uvedené v následující tabulce a předpokládá, že typ `char` je ve výchozím nastavení se znaménkem. Proto v této příručce `char` je ekvivalentní **podepsané char**.  
  
### <a name="type-specifiers-and-equivalents"></a>Specifikátory a ekvivalenty typu  
  
|Specifikátor typu|Ekvivalenty|  
|--------------------|---------------------|  
|**podepsané char**1|**char**|  
|**podepsaný int**|**podepsané**, **int**|  
|**krátká celočíselná podepsané**|**krátký**, **prostě podepsané**|  
|**podepsané dlouho int**|**dlouhé**, **podepsané dlouho**|  
|**unsigned char**|—|  
|**int bez znaménka**|**bez znaménka**|  
|**krátká celočíselná bez znaménka**|**short bez znaménka**|  
|**nepodepsané dlouho int**|**dlouho bez znaménka**|  
|**float**|—|  
|**long double**2|—|  
  
 1 Pokud provedete **char** typu bez znaménka ve výchozím nastavení (tak, že zadáte /J – možnost kompilátoru), nelze zkrátit **podepsané char** jako **char**.  
  
 2 mapuje v 32bitové a 64bitové verze operačních systémů Microsoft C kompilátoru **long double** na typ **dvojité**.  
  
 **Konkrétní Microsoft**  
  
 Zadávat lze změnit výchozí možnost kompilátoru /J **char** typu z podepsané na nepodepsané. Pokud tato možnost je ve skutečnosti **char** stejný význam jako **nepodepsané char**, a je nutné použít **podepsané** – klíčové slovo deklarovat hodnota podepsaný znaku. Pokud **char** hodnota je deklarován explicitně podepsaný držitelem, parametrem / neovlivňuje a hodnota je s rozšířeným při rozšířit do **int** typu. **Char** typ je rozšířené při rozšířit na nule **int** typu.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Specifikátory typu jazyka C](../c-language/c-type-specifiers.md)