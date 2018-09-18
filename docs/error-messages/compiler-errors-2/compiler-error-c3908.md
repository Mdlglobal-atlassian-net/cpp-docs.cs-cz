---
title: Chyba kompilátoru C3908 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3908
dev_langs:
- C++
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7591b8ab5f8495b6af866e23e7a169b0f9cd29a6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047314"
---
# <a name="compiler-error-c3908"></a>Chyba kompilátoru C3908

úroveň přístupu méně omezující než 'konstrukce.

Přístupové metody vlastností (get nebo set) nemůže mít méně omezující přístupová oprávnění, než přístup k zadané v samotné vlastnosti.  Stejně tak v případě metody přistupujícího objektu události.

Další informace najdete v tématu [vlastnost](../../windows/property-cpp-component-extensions.md) a [události](../../windows/event-cpp-component-extensions.md).

Následující ukázka generuje C3908:

```
// C3908.cpp
// compile with: /clr
ref class X {
protected:
   property int i {
   public:   // C3908 property i is protected
      int get();
   private:
      void set(int);   // OK more restrictive
   };
};
```