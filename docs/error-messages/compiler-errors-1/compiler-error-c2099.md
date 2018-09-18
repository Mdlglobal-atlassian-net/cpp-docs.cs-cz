---
title: Chyba kompilátoru C2099 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2099
dev_langs:
- C++
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fcbefa4d8fb9d5503f28cf3bf39cafc6b05a225
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116825"
---
# <a name="compiler-error-c2099"></a>Chyba kompilátoru C2099

Inicializátor není konstantní

Tato chyba vydává pouze kompilátor jazyka C a dochází pouze bez automatické proměnné.  Kompilátor inicializuje bez automatické proměnné na začátku programu a musí být konstantní hodnoty, které jsou inicializovány pomocí.

## <a name="example"></a>Příklad

Následující ukázka generuje C2099.

```
// C2099.c
int j;
int *p;
j = *p;   // C2099 *p is not a constant
```

## <a name="example"></a>Příklad

C2099 může také dojít, protože kompilátor nedokáže provést konstantní skládání na výrazu v rámci **/FP: strict** vzhledem k tomu, že nastavení prostředí přesnost s plovoucí desetinnou čárkou (viz [_controlfp_s –](../../c-runtime-library/reference/controlfp-s.md) pro Další informace) se můžou lišit od kompilace čas spuštění.

Když je konstantní skládání selže, kompilátor vyvolá dynamická inicializace, což není povoleno v jazyce C.

Chcete-li vyřešit tuto chybu, kompilace modulu jako souboru s příponou .cpp nebo zjednodušit.

Další informace najdete v tématu [/fp (určení chování plovoucí desetinné čárky)](../../build/reference/fp-specify-floating-point-behavior.md).

Následující ukázka generuje C2099.

```
// C2099_2.c
// compile with: /fp:strict /c
float X = 2.0 - 1.0;   // C2099
float X2 = 1.0;   // OK
```