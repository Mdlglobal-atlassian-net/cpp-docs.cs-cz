---
title: Chyba kompilátoru C3087
ms.date: 11/04/2016
f1_keywords:
- C3087
helpviewer_keywords:
- C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
ms.openlocfilehash: 43044e0708ce9c30099c7d25935a8ff9605f45ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489713"
---
# <a name="compiler-error-c3087"></a>Chyba kompilátoru C3087

'named_argument': volání 'attribute' už tento člen inicializuje

Pojmenovaný argument byl zadán ve stejném bloku atribut jako nepojmenovaným argumentem pro stejnou hodnotu. Zadejte pouze pojmenované nebo nepojmenovaný argument.

## <a name="example"></a>Příklad

Následující ukázka generuje C3087.

```
// C3087.cpp
// compile with: /c
[idl_quote("quote1", text="quote2")];   // C3087
[idl_quote(text="quote3")];   // OK
[idl_quote("quote4")];   // OK
```