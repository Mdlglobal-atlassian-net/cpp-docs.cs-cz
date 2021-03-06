---
title: Složené přiřazení jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
ms.openlocfilehash: 39a9391e2a62a59c5e7fd7937c1f3d12509b76ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327896"
---
# <a name="c-compound-assignment"></a>Složené přiřazení jazyka C

Operátory složeného přiřazení kombinují operátor jednoduchého přiřazení s jiným binárním operátorem. Operátory složeného přiřazení provádějí operace zadané dalším operátorem, následně přiřazují výsledek levému operandu. Například výraz složeného přiřazení jako

> *Výraz1* **+=** *Výraz2*

lze chápat jako

> *Výraz1* **=** *expression1* Výraz1 **+** *Výraz2*

Výraz složeného přiřazení však není ekvivalentem rozšířené verze, protože výraz složeného přiřazení vyhodnocuje *Výraz1* pouze jednou, zatímco rozbalená verze vyhodnocuje *Výraz1* dvakrát: v operaci sčítání a v operaci přiřazení.

Operandy operátoru složeného přiřazení musí být integrálního typu nebo typu s plovoucí desetinnou čárkou. Každý operátor složeného přiřazení provádí převody prováděné odpovídajícím binárním operátorem a omezuje typy jeho operandů. Operátory sčítání a přiřazení (`+=`) a odečítání (**-=**) mohou mít také levý operand typu ukazatel. v takovém případě musí být operand pravého typu integrálního typu. Výsledek operace složeného přiřazení má hodnotu a typ levého operandu.

```C
#define MASK 0xff00

n &= MASK;
```

V tomto příkladu se provádí operace logického bitového AND na `n` a `MASK` a výsledek je přiřazen k `n`. Konstanta `MASK` manifestu je definována pomocí direktivy preprocesoru [#define](../preprocessor/hash-define-directive-c-cpp.md) .

## <a name="see-also"></a>Viz také

[Operátory přiřazení v jazyce C](../c-language/c-assignment-operators.md)
