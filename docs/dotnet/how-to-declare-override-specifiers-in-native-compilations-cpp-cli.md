---
title: 'Postupy: deklarace specifikátorů Override (C + +/ CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8119ab62ee37320074df401c3986b56f3ea6cbfa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130396"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Postupy: Deklarace specifikátorů override v nativní kompilaci (C++/CLI)
[zapečetěné](../windows/sealed-cpp-component-extensions.md), [abstraktní](../windows/abstract-cpp-component-extensions.md), a [přepsat](../windows/override-cpp-component-extensions.md) jsou k dispozici v kompilaci, které nepoužívají **/ZW** nebo [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
> [!NOTE]
>  ISO C ++ 11 standardní jazyk má [přepsat](../cpp/override-specifier.md) identifikátor a [konečné](../cpp/final-specifier.md) identifikátor a obě jsou podporovány v aplikaci Visual Studio pak použijte `final` místo `sealed` v kódu, který je určen jako zkompilovat pouze nativní.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje, že `sealed` je platný v nativní kompilaci.  
  
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
 Další příklad ukazuje, že `override` je platný v nativní kompilaci.  
  
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
 Tento příklad ukazuje, že `abstract` je platný v nativní kompilaci.  
  
### <a name="code"></a>Kód  
  
```cpp  
// abstract_native_keyword.cpp  
class X abstract {};  
  
int main() {  
   X * MyX = new X;   // C3622 cannot instantiate abstract class  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Override – specifikátory](../windows/override-specifiers-cpp-component-extensions.md)