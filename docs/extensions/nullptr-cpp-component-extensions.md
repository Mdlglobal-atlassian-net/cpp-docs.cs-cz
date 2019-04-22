---
title: nullptr (C++vyhodnocovací a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 05aaaa8a0d0056e0f5318f5e9329d90824760728
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040826"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C++vyhodnocovací a C++/CX)

**Nullptr** – klíčové slovo představuje *hodnota ukazatele s hodnotou null*. Použijte hodnotu ukazatele null k označení, že popisovač objektu, vnitřní ukazatel nebo typ nativní ukazatel neukazuje na objekt.

Použití **nullptr** se spravovaným nebo nativním kódem. Kompilátor vydá odpovídající ale mírně se pokyny, jak hodnoty spravovaný a nativní ukazatel s hodnotou null. Informace o používání verze standard C++ ISO klíčového slova, najdete v tématu [nullptr](../cpp/nullptr.md).

**__Nullptr** – klíčové slovo je klíčové slovo specifické pro společnost Microsoft, který má stejný význam jako **nullptr**, ale platí pro pouze nativního kódu. Pokud používáte **nullptr** s nativním C/C++ kódu a poté zkompilovat s [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru, kompilátor nemůže určit, zda **nullptr** označuje nativní nebo spravovaný hodnotou ukazatele null. Aby váš záměr vymazat pro kompilátor použít **nullptr** můžete zadat spravované hodnotu nebo **__nullptr** můžete zadat hodnotu native.

**Nullptr** – klíčové slovo je ekvivalentní **nic** v jazyce Visual Basic a **null** v jazyce C#.

## <a name="usage"></a>Použití

**Nullptr** – klíčové slovo mohou být použity kdekoli lze použít argument funkce, nativní ukazatel nebo popisovač.

**Nullptr** – klíčové slovo se nejedná o typ a není podporována pro použití se službou:

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (i když `throw (Object^)nullptr;` bude fungovat)

**Nullptr** – klíčové slovo lze použít při inicializaci následující typy ukazatelů:

- Nativní ukazatel

- Popisovač modulu Windows Runtime

- Spravované popisovač

- Spravovaná vnitřní ukazatel

**Nullptr** – klíčové slovo lze použít k testování, pokud ukazatel nebo popisovač odkaz má hodnotu null, před použitím odkazu.

Volání funkcí mezi jazyky, které používají hodnoty ukazatele s hodnotou null pro kontrolu chyb by měl být interpretován správně.

Nelze inicializovat popisovače na hodnotu nula; pouze **nullptr** lze použít. Vytvoří přiřazení konstanty 0 na popisovač objektu zabalený `Int32` a přetypování na `Object^`.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že **nullptr** – klíčové slovo se dá použít bez ohledu na to popisovač, nativní ukazatele, nebo můžete použít argument funkce. A tento příklad ukazuje, že **nullptr** – klíčové slovo lze použít ke kontrole odkaz, než bude použit.

```cpp
// mcpp_nullptr.cpp
// compile with: /clr
value class V {};
ref class G {};
void f(System::Object ^) {}

int main() {
// Native pointer.
   int *pN = nullptr;
// Managed handle.
   G ^pG = nullptr;
   V ^pV1 = nullptr;
// Managed interior pointer.
   interior_ptr<V> pV2 = nullptr;
// Reference checking before using a pointer.
   if (pN == nullptr) {}
   if (pG == nullptr) {}
   if (pV1 == nullptr) {}
   if (pV2 == nullptr) {}
// nullptr can be used as a function argument.
   f(nullptr);   // calls f(System::Object ^)
}
```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že **nullptr** a nula zaměnitelné na nativní ukazatele.

```cpp
// mcpp_nullptr_1.cpp
// compile with: /clr
class MyClass {
public:
   int i;
};

int main() {
   MyClass * pMyClass = nullptr;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");

   pMyClass = 0;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");
}
```

```Output
pMyClass == nullptr

pMyClass == 0

pMyClass == nullptr

pMyClass == 0
```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že **nullptr** je interpretován jako popisovač pro libovolný typ nebo nativní ukazatel na libovolný typ. V případě přetížení funkcí s úchyty pro různé typy, bude vygenerována chyba nejednoznačnost. **Nullptr** musel být explicitně přetypován na typ.

```cpp
// mcpp_nullptr_2.cpp
// compile with: /clr /LD
void f(int *){}
void f(int ^){}

void f_null() {
   f(nullptr);   // C2668
   // try one of the following lines instead
   f((int *) nullptr);
   f((int ^) nullptr);
}
```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že přetypování **nullptr** je povolen a vrátí ukazatel nebo popisovač, který obsahuje typ přetypování **nullptr** hodnotu.

```cpp
// mcpp_nullptr_3.cpp
// compile with: /clr /LD
using namespace System;
template <typename T>
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type

int main() {
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)

   // Delete the following line to resolve.
   f(nullptr);

   f(0);   // T = int, call f(int)
}
```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že **nullptr** lze použít jako parametr funkce.

```cpp
// mcpp_nullptr_4.cpp
// compile with: /clr
using namespace System;
void f(Object ^ x) {
   Console::WriteLine("test");
}

int main() {
   f(nullptr);
}
```

```Output
test
```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že obslužné rutiny jsou deklarovány a nebyly explicitně inicializovány, jsou inicializovány na výchozí **nullptr**.

```cpp
// mcpp_nullptr_5.cpp
// compile with: /clr
using namespace System;
ref class MyClass {
public:
   void Test() {
      MyClass ^pMyClass;   // gc type
      if (pMyClass == nullptr)
         Console::WriteLine("NULL");
   }
};

int main() {
   MyClass ^ x = gcnew MyClass();
   x -> Test();
}
```

```Output
NULL
```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že **nullptr** je možné přiřadit na nativní ukazatel při kompilaci s `/clr`.

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>Požadavky

– Možnost kompilátoru: (Není vyžadováno; podporuje všechny možnosti generování kódu, včetně `/ZW` a `/clr`)

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)