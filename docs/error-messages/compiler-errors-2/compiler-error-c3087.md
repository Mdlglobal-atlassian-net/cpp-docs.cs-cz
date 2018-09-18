---
title: Chyba kompilátoru C3087 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3087
dev_langs:
- C++
helpviewer_keywords:
- C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a95b14df3701d26a249e8e0d0e8ec4bafe5eb0d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041607"
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