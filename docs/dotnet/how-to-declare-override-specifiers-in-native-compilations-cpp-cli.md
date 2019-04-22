---
title: 'Postupy: Deklarace specifikátorů Override (C++vyhodnocovací)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: db74ef226242ec8f4f70f2769fbc8ba102a808c8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777178"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Postupy: Deklarace specifikátorů Override v nativních kompilacích (C++vyhodnocovací)

[zapečetěné](../extensions/sealed-cpp-component-extensions.md), [abstraktní](../extensions/abstract-cpp-component-extensions.md), a [přepsat](../extensions/override-cpp-component-extensions.md) jsou k dispozici v kompilaci, které nepoužívají **/ZW** nebo [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
>  C ++ 11 jazyka podle standardu ISO má [přepsat](../cpp/override-specifier.md) identifikátor a [konečné](../cpp/final-specifier.md) identifikátor a obě jsou podporovány v aplikaci Visual Studio pomocí `final` místo `sealed` v kódu, který slouží k zkompilovat jako nativní.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje, že `sealed` je platný v nativních kompilacích.

### <a name="code"></a>Kód

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

Následující příklad ukazuje, že `override` je platný v nativních kompilacích.

### <a name="code"></a>Kód

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

Tento příklad ukazuje, že `abstract` je platný v nativních kompilacích.

### <a name="code"></a>Kód

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>Viz také:

[override – specifikátory](../extensions/override-specifiers-cpp-component-extensions.md)
