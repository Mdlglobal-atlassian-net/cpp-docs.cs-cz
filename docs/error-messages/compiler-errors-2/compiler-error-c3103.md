---
title: C3103 Chyba kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3103
dev_langs:
- C++
helpviewer_keywords:
- C3103
ms.assetid: 7984bd3e-d51d-43e4-b6f4-08c1e9fb9704
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abdfbdae575b400dd44ba16bd453dc82eb03c721
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050150"
---
# <a name="compiler-error-c3103"></a>C3103 chyby kompilátoru

"argument": opakovaný pojmenovaný argument

Atribut se nemůže opakovat. pojmenované argumenty.

Další informace najdete v tématu [uživatelem definované atributy](../../windows/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3103.

```
// C3103.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref class Attr : public Attribute {
public:
   int m_t;
};

[Attr(m_t = 10, m_t = 1)]   // C3103
// try the following line instead
// [Attr(m_t = 10)]
ref class A {};
```