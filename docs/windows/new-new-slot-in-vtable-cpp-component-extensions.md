---
title: New (nový slot v tabulce vtable) (C++ Component Extensions) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7189909f3cff84d2bb1a767e4ddeda817bcd6128
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="new-new-slot-in-vtable--c-component-extensions"></a>new (nový slot v tabulce vtable) (rozšíření komponent C++)
`new` – Klíčové slovo znamená, že se členem virtuální získat nový slot v tabulce vtable.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 (Používají se žádné poznámky pro tuto funkci jazyka, které platí pro všechny moduly runtime.)  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Není podporována v prostředí Windows Runtime.  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Poznámky**  
  
 V **/CLR** kompilace, `new` označuje, že bude člena virtuální získat nový slot v tabulce vtable; že funkce nemůže přepsat metodu základní třídy.  
  
 `new` způsobí, že modifikátor newslot mají být přidány do IL pro funkci.  Další informace o newslot najdete v tématu:  
  
-   [MethodInfo.GetBaseDefinition – metoda](https://msdn.microsoft.com/en-us/library/system.reflection.methodinfo.getbasedefinition.aspx)  
  
-   [MethodAttributes – výčet](https://msdn.microsoft.com/en-us/library/system.reflection.methodattributes.aspx)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad ukazuje účinek `new`.  
  
```  
// newslot.cpp  
// compile with: /clr  
ref class C {  
public:  
   virtual void f() {  
      System::Console::WriteLine("C::f() called");  
   }  
  
   virtual void g() {  
      System::Console::WriteLine("C::g() called");  
   }  
};  
  
ref class D : public C {  
public:  
   virtual void f() new {  
      System::Console::WriteLine("D::f() called");  
   }  
  
   virtual void g() override {  
      System::Console::WriteLine("D::g() called");  
   }  
};  
  
ref class E : public D {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("E::f() called");  
   }  
};  
  
int main() {  
   D^ d = gcnew D;  
   C^ c = gcnew D;  
  
   c->f();   // calls C::f  
   d->f();   // calls D::f  
  
   c->g();   // calls D::g  
   d->g();   // calls D::g  
  
   D ^ e = gcnew E;  
   e->f();   // calls E::f  
}  
```  
  
 **Output**  
  
```Output  
C::f() called  
  
D::f() called  
  
D::g() called  
  
D::g() called  
  
E::f() called  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)   
 [Override – specifikátory](../windows/override-specifiers-cpp-component-extensions.md)