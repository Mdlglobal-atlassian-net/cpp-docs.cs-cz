---
title: Chyba kompilátoru C2099
ms.date: 11/04/2016
f1_keywords:
- C2099
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
ms.openlocfilehash: 9c83b4a50cb9cf5c5b1992f0f64e2eeb013b48e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575757"
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