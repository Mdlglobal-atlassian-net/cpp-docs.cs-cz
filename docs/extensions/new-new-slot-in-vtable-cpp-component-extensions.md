---
title: New (nový slot v tabulce vtable) (C++vyhodnocovací a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
ms.openlocfilehash: c5446e5e84491ff7d736ce3b3af49dacd471c010
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62254484"
---
# <a name="new-new-slot-in-vtable--ccli-and-ccx"></a>New (nový slot v tabulce vtable) (C++vyhodnocovací a C++/CX)

**Nové** – klíčové slovo určuje, že virtuální člen získá novou patici ve vtable.

## <a name="all-runtimes"></a>Všechny moduly runtime

(Neexistují žádné poznámky o této funkci jazyka, které platí pro všechny moduly runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

V modulu Windows Runtime není podporován.

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="remarks"></a>Poznámky

V `/clr` kompilace, **nové** označuje, že virtuální člen získá novou patici ve vtable; že funkci nepřepisuje metodu základní třídy.

**nové** způsobí, že modifikátor newslot být přidán do IL pro funkci.  Další informace o newslot naleznete v tématu:

- <xref:System.Reflection.MethodInfo.GetBaseDefinition?displayProperty=nameWithType>

- <xref:System.Reflection.MethodAttributes?displayProperty=nameWithType>

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

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)<br/>

[override – specifikátory](override-specifiers-cpp-component-extensions.md)