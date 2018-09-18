---
title: Upozornění Linkerů LNK4248 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4248
dev_langs:
- C++
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ff2c3edd942eb0d38d16a6986044f90358c4e9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062160"
---
# <a name="linker-tools-warning-lnk4248"></a>Upozornění linkerů LNK4248

Nerozpoznaný token typeref (token) pro 'type'; bitové kopie se možná nespustí.

Typ nemá definici v metadatech jazyka MSIL.

LNK4248 může dojít, když je Dopředná deklarace pro typ v modulu jazyka MSIL (zkompilovaná **/CLR**), kde se v modulu jazyka MSIL odkazuje typ a modul MSIL je propojena s nativní modul, který obsahuje definici pro typ.

V takovém případě linkeru poskytne definici nativního typu v metadatech jazyk MSIL a to může poskytnout pro správné fungování.

Nicméně pokud deklarace dopředu typu je typ CLR, pak propojovacího programu nativní typ definice nemusí být správný

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zadejte definici typu v modulu jazyka MSIL.

## <a name="example"></a>Příklad

Následující ukázka generuje LNK4248. Definujte strukturu A vyřešit.

```
// LNK4248.cpp
// compile with: /clr /W1
// LNK4248 expected
struct A;
void Test(A*){}

int main() {
   Test(0);
}
```

## <a name="example"></a>Příklad

Následující příklad obsahuje dopředné definici typu.

```
// LNK4248_2.cpp
// compile with: /clr /c
class A;   // provide a definition for A here to resolve
A * newA();
int valueA(A * a);

int main() {
   A * a = newA();
   return valueA(a);
}
```

## <a name="example"></a>Příklad

Následující ukázka generuje LNK4248.

```
// LNK4248_3.cpp
// compile with: /c
// post-build command: link LNK4248_2.obj LNK4248_3.obj
class A {
public:
   int b;
};

A* newA() {
   return new A;
}

int valueA(A * a) {
   return (int)a;
}
```