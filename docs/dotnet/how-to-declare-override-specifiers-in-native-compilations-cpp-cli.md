---
title: 'Postup: Deklarovat deklarátory přepsání (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: 9f3f6855f257d0af250b9bbdd2c0360b308ce775
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374454"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Postupy: Deklarace specifikátorů override v nativní kompilaci (C++/CLI)

[zapečetěné](../extensions/sealed-cpp-component-extensions.md), [abstraktní](../extensions/abstract-cpp-component-extensions.md)a [přepsat](../extensions/override-cpp-component-extensions.md) jsou k dispozici v kompilacích, které nepoužívají **/ZW** nebo [/clr](../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
> Standardní jazyk ISO C++11 má identifikátor [přepsání](../cpp/override-specifier.md) a [konečný](../cpp/final-specifier.md) identifikátor a `final` oba `sealed` jsou podporovány v sadě Visual Studio Použití namísto v kódu, který je určen k kompilaci jako nativní pouze.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje, že `sealed` je platný v nativní kompilace.

### <a name="code"></a>kód

```cpp
// sealed_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
   virtual void g();
};

class X : public I1 {
public:
   virtual void g() sealed {}
};

class Y : public X {
public:

   // the following override generates a compiler error
   virtual void g() {}   // C3248 X::g is sealed!
};
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje, že `override` je platný v nativní kompilace.

### <a name="code"></a>kód

```cpp
// override_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
};

class X : public I1 {
public:
   virtual void f() override {}   // OK
   virtual void g() override {}   // C3668 I1::g does not exist
};
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tento příklad `abstract` ukazuje, že je platný v nativní kompilace.

### <a name="code"></a>kód

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>Viz také

[override – specifikátory](../extensions/override-specifiers-cpp-component-extensions.md)
