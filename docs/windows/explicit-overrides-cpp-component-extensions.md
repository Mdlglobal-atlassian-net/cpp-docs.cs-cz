---
title: "Explicitní přepsání (C++ Component Extensions) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 346dd73952934d514b2741c41d5a27816b7152ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="explicit-overrides--c-component-extensions"></a>Explicitní přepsání (rozšíření komponent C++)
Toto téma popisuje postup explicitní přepsání člena rozhraní nebo základní třída. S názvem (explicitní) přepsání lze používat pouze přepsat metodu s odvozené metodu, která má jiný název.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 **Syntaxe**  
  
```  
  
      overriding-function-declarator = type::function [,type::function] { overriding-function-definition }  
overriding-function-declarator = function { overriding-function-definition }  
```  
  
 **Parametry**  
  
 *přepsání deklarátor – funkce*  
 Návratový typ, název a argument seznam přepsání funkce.  Všimněte si, že není nutné mít stejný název jako funkce přepsání přepsání funkce.  
  
 *Typ*  
 Základní typ, který obsahuje funkce, která se přepsat.  
  
 *funkce*  
 Čárkami oddělený seznam jedné nebo více názvy funkcí pro přepsání.  
  
 *přepsání definice funkce*  
 Funkce text příkazů, které definují přepsání funkce.  
  
 **Poznámky**  
  
 Použijte explicitní přepsání, chcete-li vytvořit alias pro podpis metody nebo poskytovat různé implementace pro metody pole stejným podpisem.  
  
 Informace o změně chování zděděné typy a členy zděděné typu najdete v tématu [přepsat specifikátory](../windows/override-specifiers-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Poznámky**  
  
 Pro informace o explicitní přepsání v nativním kódu nebo kód kompilovat s **/clr:oldSyntax**, najdete v části [explicitní přepsání](../cpp/explicit-overrides-cpp.md).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu ukazuje jednoduchý, implicitní override a implementace člena v základní rozhraní není pomocí explicitní přepsání.  
  
```  
// explicit_override_1.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
}  
```  
  
 **Output**  
  
```Output  
X::f override of I1::f  
```  
  
 **Příklad**  
  
 Následující příklad kódu ukazuje, jak implementovat všechny členy rozhraní běžné podpisem pomocí syntaxe explicitní přepsání.  
  
```  
  
// explicit_override_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
interface struct I2 {  
   virtual void f();  
};  
  
ref struct X : public I1, I2 {  
   virtual void f() = I1::f, I2::f {  
      System::Console::WriteLine("X::f override of I1::f and I2::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   I2 ^ MyI2 = gcnew X;  
   MyI -> f();  
   MyI2 -> f();  
}  
```  
  
 **Output**  
  
```Output  
X::f override of I1::f and I2::f  
X::f override of I1::f and I2::f  
```  
  
 **Příklad**  
  
 Následující příklad kódu ukazuje, jak funkce přepsání, může mít jiný název z funkce, které implementuje.  
  
```  
// explicit_override_3.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void g() = I1::f {  
      System::Console::WriteLine("X::g");  
   }  
};  
  
int main() {  
   I1 ^ a = gcnew X;  
   a->f();  
}  
```  
  
 **Output**  
  
```Output  
X::g  
```  
  
 **Příklad**  
  
 Následující příklad kódu ukazuje implementace explicitního rozhraní, která implementuje kolekce bezpečného typu.  
  
```  
// explicit_override_4.cpp  
// compile with: /clr /LD  
using namespace System;  
ref class R : ICloneable {  
   int X;  
  
   virtual Object^ C() sealed = ICloneable::Clone {  
      return this->Clone();  
   }  
  
public:  
   R() : X(0) {}  
   R(int x) : X(x) {}  
  
   virtual R^ Clone() {  
      R^ r = gcnew R;  
      r->X = this->X;  
      return r;  
   }  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)