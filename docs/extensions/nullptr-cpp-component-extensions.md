---
title: nullptr (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 02da716959deb7fcffa7a63a8308279a765c4569
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172111"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C++/CLI a C++/CX)

Klíčové slovo **nullptr** reprezentuje *hodnotu ukazatele s hodnotou null*. Použijte hodnotu ukazatele s hodnotou null k označení, že popisovač objektu, vnitřní ukazatel nebo nativní typ ukazatele neodkazuje na objekt.

Použijte **nullptr** s buď spravovaným, nebo nativním kódem. Kompilátor vygeneruje vhodné, ale různé pokyny pro spravované a nativní hodnoty nulového ukazatele. Informace o použití standardní C++ verze tohoto klíčového slova ISO naleznete v tématu [nullptr](../cpp/nullptr.md).

Klíčové slovo **__nullptr** je klíčové slovo specifické pro společnost Microsoft, které má stejný význam jako **nullptr**, ale platí pouze pro nativní kód. Použijete-li **nullptr** s nativnímC++ C/kódem a potom zkompilujete pomocí možnosti kompilátoru [/CLR](../build/reference/clr-common-language-runtime-compilation.md) , kompilátor nemůže určit, zda **nullptr** označuje nativní nebo spravovaný hodnotu nulového ukazatele. Chcete-li záměr vyjasnit pro kompilátor, použijte **nullptr** k určení spravované hodnoty nebo **__nullptr** k určení nativní hodnoty.

Klíčové slovo **nullptr** je ekvivalentní **žádnému** v Visual Basic a **null** v C#.

## <a name="usage"></a>Využití

Klíčové slovo **nullptr** lze použít kdekoli lze použít popisovač, nativní ukazatel nebo argument funkce.

Klíčové slovo **nullptr** není typu a není podporováno pro použití s:

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (i když `throw (Object^)nullptr;` bude fungovat)

Klíčové slovo **nullptr** lze použít při inicializaci následujících typů ukazatelů:

- Nativní ukazatel

- prostředí Windows Runtime popisovač

- Spravovaný popisovač

- Spravovaný vnitřní ukazatel

Klíčové slovo **nullptr** se dá použít k otestování, jestli je odkaz na ukazatel nebo popisovač NULL, než se použije odkaz.

Volání funkcí mezi jazyky, které používají hodnoty nulového ukazatele pro kontrolu chyb, by měla být interpretována správně.

Nemůžete inicializovat popisovač na nulu; použít lze pouze **nullptr** . Přiřazení konstanty 0 k popisovači objektu vytvoří zabalený `Int32` a přetypování na `Object^`.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že klíčové slovo **nullptr** lze použít všude, kde lze použít argument, nativní ukazatel nebo argument funkce. A příklad ukazuje, že klíčové slovo **nullptr** lze použít ke kontrole odkazu před jeho použitím.

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

Následující příklad kódu ukazuje, že **nullptr** a Zero lze v nativních ukazatelích použít zaměnitelné.

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

Následující příklad kódu ukazuje, že **nullptr** je interpretován jako popisovač libovolného typu nebo nativní ukazatel na libovolný typ. V případě přetížení funkce s popisovači na různé typy bude vygenerována chyba nejednoznačnosti. **Nullptr** by musel být explicitně přetypování na typ.

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

Následující příklad kódu ukazuje, že funkce přetypování **nullptr** je povolena a vrací ukazatel nebo popisovač typu přetypování, který obsahuje hodnotu **nullptr** .

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

Následující příklad kódu ukazuje, že pokud jsou popisovače deklarovány a nejsou explicitně inicializovány, jsou ve výchozím nastavení inicializovány na **nullptr**.

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

Následující příklad kódu ukazuje, že **nullptr** lze přiřadit nativnímu ukazateli při kompilaci pomocí `/clr`.

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>Požadavky

Možnost kompilátoru: (Nepožadováno; podporováno všemi možnostmi generování kódu, včetně `/ZW` a `/clr`)

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)
