---
title: Upozornění linkerů LNK4248
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: 4ba05ef067c539dc9c0aca6dc2a395748fd217a2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988096"
---
# <a name="linker-tools-warning-lnk4248"></a>Upozornění linkerů LNK4248

Nerozpoznaný token TypeRef (token) pro typ Image se možná nespustí.

Typ nemá v metadatech MSIL definici.

LINKERŮ LNK4248 může nastat, pokud je k dispozici pouze Dopředná deklarace pro typ v modulu MSIL (zkompilovaný s **/CLR**), kde je typ odkazován v modulu MSIL a kde je modul MSIL propojený s nativním modulem, který má definici pro daný typ.

V této situaci linker poskytne definici nativního typu v metadatech MSIL a to může být pro správné chování.

Pokud je však deklarace dopředné typu typu CLR, pak definice nativního typu linkeru nemusí být správná.

Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zadejte definici typu v modulu MSIL.

## <a name="example"></a>Příklad

Následující ukázka generuje LINKERŮ LNK4248. Definujte strukturu A, která se má vyřešit.

```cpp
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

Následující ukázka má dopřednou definici typu.

```cpp
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

Následující ukázka generuje LINKERŮ LNK4248.

```cpp
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
