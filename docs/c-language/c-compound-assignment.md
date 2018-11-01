---
title: Složené přiřazení jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
ms.openlocfilehash: 102f53378430074a59636eb18488a7ab51289731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445133"
---
# <a name="c-compound-assignment"></a>Složené přiřazení jazyka C

Operátory složeného přiřazení kombinují operátor jednoduchého přiřazení s jiným binárním operátorem. Operátory složeného přiřazení provádějí operace zadané dalším operátorem, následně přiřazují výsledek levému operandu. Například výraz složeného přiřazení jako

> *Expression1* **+=** *expression2*

lze chápat jako

> *Expression1* **=** *expression1* **+** *expression2*

Výraz složeného přiřazení však není ekvivalentní k rozšířené verzi, protože výraz složeného přiřazení vyhodnotí *expression1* pouze jednou, zatímco rozšířená verze vyhodnocuje  *Expression1* dvakrát: v operaci sčítání a v operaci přiřazení.

Operandy operátoru složeného přiřazení musí být integrálního typu nebo typu s plovoucí desetinnou čárkou. Každý operátor složeného přiřazení provádí převody prováděné odpovídajícím binárním operátorem a omezuje typy jeho operandů. Přiřazení sčítání (`+=`) a přiřazení odčítání (**-=**) operátory lze také mít levý operand typu ukazatel, ve kterém případě zpracovával pravý operand musí být celočíselného typu. Výsledek operace složeného přiřazení má hodnotu a typ levého operandu.

```C
#define MASK 0xff00

n &= MASK;
```

V tomto příkladu se provádí operace logického bitového AND na `n` a `MASK` a výsledek je přiřazen k `n`. Konstanta manifestu `MASK` je definována s [#define](../preprocessor/hash-define-directive-c-cpp.md) direktiva preprocesoru.

## <a name="see-also"></a>Viz také

[Operátory přiřazení v jazyce C](../c-language/c-assignment-operators.md)