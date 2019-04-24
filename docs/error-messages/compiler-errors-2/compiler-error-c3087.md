---
title: Chyba kompilátoru C3087
ms.date: 11/04/2016
f1_keywords:
- C3087
helpviewer_keywords:
- C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
ms.openlocfilehash: 43044e0708ce9c30099c7d25935a8ff9605f45ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243255"
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