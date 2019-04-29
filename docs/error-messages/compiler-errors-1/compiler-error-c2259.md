---
title: Compiler Error C2259
ms.date: 11/04/2016
f1_keywords:
- C2259
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
ms.openlocfilehash: 0310f20854185a6f8a5ccb0ce7b087c4d7c5f29d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387068"
---
# <a name="compiler-error-c2259"></a>Compiler Error C2259

'třída' : instanci abstraktní třídy nelze vytvořit

Kód deklaruje instanci abstraktní třídy nebo struktury.

Instanci třídy nebo struktury s jednou nebo více čistě virtuálními funkcemi nelze vytvořit. Chcete-li vytvořit objekty odvozené třídy, musí odvozená třída přepsat všechny čistě virtuální funkce.

Další informace najdete v tématu [implicitně abstraktní třídy](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes).

Následující ukázka generuje C2259:

```
// C2259.cpp
// compile with: /c
class V {
public:
   void virtual func() = 0;
};
class A : public V {};
class B : public V {
public:
   void func();
};
V v;  // C2259, V is an abstract class
A a;  // C2259, A inherits func() as pure virtual
B b;  // OK, B defines func()
```

Upozornění C2259 může být vygenerováno vždy, když odvozujete z rozhraní a metody rozhraní jsou v odvozené třídě implementovány s přístupovým oprávněním jiným než public.  K tomu dochází, protože kompilátor očekává, že metody rozhraní implementované v odvozené třídě budou mít přístup public. Jsou-li členské funkce rozhraní implementovány s více omezujícími přístupovými oprávněními, kompilátor je nepovažuje za implementace metod definovaných v rozhraní, a odvozená třída se tak stává abstraktní třídou.

Existují dvě možná řešení problému:

- Změňte přístupová oprávnění implementovaných metod na public.

- Přiřaďte název implementované metody k názvu rozhraní použitím operátoru vyhodnocení rozsahu pro metody rozhraní implementované v odvozené třídě.

C2259 může dojít v důsledku prací, které bylo provedeno ve Vizuálu C++ 2005, **/Zc: wchar_t** je teď ve výchozím. V takovém případě může být C2599 vyřešit buď kompilací s **/Zc:wchar_t-**, chcete-li získat chování z předchozích verzí, nebo lépe aktualizací typů tak, aby byly kompatibilní. Další informace najdete v tématu [/Zc: wchar_t (wchar_t je nativní typ)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

Následující ukázka generuje C2259:

```
// C2259b.cpp
// compile with: /c
#include <windows.h>

class MyClass {
public:
   // WCHAR now typedef'ed to wchar_t
   virtual void func(WCHAR*) = 0;
};

class MyClass2 : MyClass {
public:
   void func(unsigned short*);
};

MyClass2 x;   // C2259

// OK
class MyClass3 {
public:
   virtual void func(WCHAR*) = 0;
   virtual void func2(wchar_t*) = 0;
   virtual void func3(unsigned short*) = 0;
};

class MyClass4 : MyClass3 {
public:
   void func(WCHAR*) {}
   void func2(wchar_t*) {}
   void func3(unsigned short*) {}
};

MyClass4 y;
```

Následující ukázka generuje C2259:

```
// C2259c.cpp
// compile with: /clr
interface class MyInterface {
   void MyMethod();
};

ref class MyDerivedClass: public MyInterface {
private:
   // Uncomment the following line to resolve.
   // public:
   void MyMethod(){}
   // or the following line
   // void MyInterface::MyMethod() {};
};

int main() {
   MyDerivedClass^ instance = gcnew MyDerivedClass; // C2259
}
```
