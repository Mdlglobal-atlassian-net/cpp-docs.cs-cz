---
title: New (nový slot v tabulce vtable) (rozšíření komponent C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: b5dc0f490da43b4a2a2befa22f2902e7bfce51ca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420917"
---
# <a name="new-new-slot-in-vtable--c-component-extensions"></a>new (nový slot v tabulce vtable) (rozšíření komponent C++)

**Nové** – klíčové slovo určuje, že virtuální člen získá novou patici ve vtable.

## <a name="all-runtimes"></a>Všechny moduly runtime

(Neexistují žádné poznámky o této funkci jazyka, které platí pro všechny moduly runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

V modulu Windows Runtime není podporován.

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="remarks"></a>Poznámky

V `/clr` kompilace, **nové** označuje, že virtuální člen získá novou patici ve vtable; že funkci nepřepisuje metodu základní třídy.

**nové** způsobí, že modifikátor newslot být přidán do IL pro funkci.  Další informace o newslot naleznete v tématu:

- [Metoda MethodInfo.GetBaseDefinition](https://msdn.microsoft.com/library/system.reflection.methodinfo.getbasedefinition.aspx)

- [Výčet MethodAttributes](https://msdn.microsoft.com/library/system.reflection.methodattributes.aspx)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad ukazuje účinek **nové**.

```cpp
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

```Output
C::f() called

D::f() called

D::g() called

D::g() called

E::f() called
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)<br/>
[Override – specifikátory](../windows/override-specifiers-cpp-component-extensions.md)