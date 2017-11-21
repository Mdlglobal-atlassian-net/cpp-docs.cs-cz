---
title: "Složené přiřazení jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8771aba4328cef785347712f037ea21c5a46cfad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Operátory přiřazení jazyka C](../c-language/c-assignment-operators.md)