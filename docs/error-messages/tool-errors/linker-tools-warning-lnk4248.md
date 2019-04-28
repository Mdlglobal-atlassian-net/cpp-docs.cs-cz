---
title: Upozornění linkerů LNK4248
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: db9432c505b7348c9bef5ed34aac1cb4edecb17b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352515"
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