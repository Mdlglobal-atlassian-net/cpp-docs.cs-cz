---
title: Složené přiřazení jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ef882deb6a96117ec572aa675fe80158d192ce7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382039"
---
# <a name="c-compound-assignment"></a>Složené přiřazení jazyka C
Operátory složeného přiřazení kombinují operátor jednoduchého přiřazení s jiným binárním operátorem. Operátory složeného přiřazení provádějí operace zadané dalším operátorem, následně přiřazují výsledek levému operandu. Například výraz složeného přiřazení jako  
  
```  
  
expression1  
+=  
expression2  
  
```  
  
 lze chápat jako  
  
```  
  
expression1  
=  
expression1  
+  
expression2  
  
```  
  
 Složené přiřazení výraz však není ekvivalentní rozšířené verze, protože výsledkem výrazu složené přiřazení *expression1* pouze jednou, zatímco rozšířené verze vyhodnotí  *Expression1* dvakrát: v operaci sčítání a přiřazení operaci.  
  
 Operandy operátoru složeného přiřazení musí být integrálního typu nebo typu s plovoucí desetinnou čárkou. Každý operátor složeného přiřazení provádí převody prováděné odpovídajícím binárním operátorem a omezuje typy jeho operandů. Přiřazení sčítání (`+=`) a přiřazení odčítání (**-=**) operátory může mít levý operand typu ukazatele, ve kterém musí být případ pravém operand integrální typu. Výsledek operace složeného přiřazení má hodnotu a typ levého operandu.  
  
```  
#define MASK 0xff00  
  
n &= MASK;  
```  
  
 V tomto příkladu se provádí operace logického bitového AND na `n` a `MASK` a výsledek je přiřazen k `n`. Manifestu konstanta `MASK` je definovaná pomocí [#define](../preprocessor/hash-define-directive-c-cpp.md) direktivy preprocesoru.  
  
## <a name="see-also"></a>Viz také  
 [Operátory přiřazení v jazyce C](../c-language/c-assignment-operators.md)