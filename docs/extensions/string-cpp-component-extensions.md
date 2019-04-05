---
title: Řetězce (C + +/ CLI a C + +/ CX)
ms.date: 10/08/2018
ms.topic: reference
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
ms.openlocfilehash: 8440ddf510f99618c28a6b6d585c8628df85f9cb
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038545"
---
# <a name="string--ccli-and-ccx"></a>Řetězce (C + +/ CLI a C + +/ CX)

Modul Windows Runtime a modul common language runtime představují řetězce jako objekty, jejichž přidělenou paměť je spravována automaticky. To znamená není nutné explicitně zahodit paměti pro řetězec při ukončení řetězce proměnné překročí obor nebo aplikace. K označení, že se automaticky spravovat dobu života objektu string, deklarujte typ řetězce s [popisovač objektu (^)](handle-to-object-operator-hat-cpp-component-extensions.md) modifikátor.

## <a name="windows-runtime"></a>prostředí Windows Runtime

Architektura modulu Windows Runtime vyžaduje, aby `String` datový typ nacházet v `Platform` oboru názvů. Pro usnadnění práce, budou také poskytuje jazyk Visual C++ `string` datový typ, který je synonymum pro `Platform::String`v `default` oboru názvů.

### <a name="syntax"></a>Syntaxe

```cpp
// compile with /ZW
using namespace Platform;
using namespace default;
   Platform::String^ MyString1 = "The quick brown fox";
   String^ MyString2 = "jumped over the lazy dog.";
   String^ MyString3 = "Hello, world!";
```

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Při kompilaci s `/clr`, kompilátor převede řetězcové literály řetězce typu <xref:System.String>. Pro zachování zpětné kompatibility s existujícím kódem existuje jsou dvě výjimky:

- Zpracování výjimek. Při vyvolání řetězcového literálu kompilátor zachytí ho jako řetězcový literál.

- Odvození šablony. Řetězcový literál je předána jako argument šablony, kompilátor neprovede konverzi na <xref:System.String>. Mějte na paměti, bude řetězcové literály, které jsou předány jako obecný argument povýšen <xref:System.String>.

Kompilátor také obsahuje integrovanou podporu pro tři operátory, které můžete přizpůsobit jejich chování můžete přepsat:

- System::String ^ – operátor + (System::String, System::String);

- System::String ^ (System::Object, System::String); + – operátor

- System::String ^ (System::String, System::Object); + – operátor

Při předání <xref:System.String>, kompilátor pole, v případě potřeby a pak je zřetězí objekt (s ToString) s řetězcem.

> [!NOTE]
> Znak stříšky ("^") označuje, že deklarovaná proměnná je popisovač pro C + +/ CLI spravovaných objektů.

Další informace najdete v části [řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru:   **/CLR**

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje zřetězení a porovnávání řetězců.

```cpp
// string_operators.cpp
// compile with: /clr
// In the following code, the caret ("^") indicates that the
// declared variable is a handle to a C++/CLI managed object.
using namespace System;

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   // variables of System::String returning a System::String
   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   // accessing a character in the string
   Console::WriteLine(a[2]);

   // concatenation of three System::Strings
   Console::WriteLine(a + b + c);

   // concatenation of a System::String and string literal
   Console::WriteLine(a + "zzz");

   // you can append to a System::String^
   Console::WriteLine(a + 1);
   Console::WriteLine(a + 'a');
   Console::WriteLine(a + 3.1);

   // test System::String^ for equality
   a += b;
   Console::WriteLine(a);
   a = b;
   if (a == b)
      Console::WriteLine("a and b are equal");

   a = "abc";
   if (a != b)
      Console::WriteLine("a and b are not equal");

   // System:String^ and tracking reference
   String^% rstr1 = a;
   Console::WriteLine(rstr1);

   // testing an empty System::String^
   String^ n;
   if (n == nullptr)
      Console::WriteLine("n is empty");
}
```

```Output
abcdef

abcghi

ghiabc

c

abcdefghi

abczzz

abc1

abc97

abc3.1

abcdef

a and b are equal

a and b are not equal

abc

n is empty
```

Následující příklad ukazuje, že lze provést přetížení operátorů poskytované kompilátoru a, že kompilátor bude najít přetížení funkce na základě <xref:System.String> typu.

```cpp
// string_operators_2.cpp
// compile with: /clr
using namespace System;

// a string^ overload will be favored when calling with a String
void Test_Overload(const char * a) {
   Console::WriteLine("const char * a");
}
void Test_Overload(String^ a) {
   Console::WriteLine("String^ a");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, String^ b) {
   return ("overloaded +(String^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(Object^ a, String^ b) {
   return ("overloaded +(Object^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, Object^ b) {
   return ("overloaded +(String^ a, Object^ b)");
}

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   Test_Overload("hello");
   Test_Overload(d);
}
```

```Output
overloaded +(String^ a, String^ b)

overloaded +(String^ a, Object^ b)

overloaded +(Object^ a, String^ b)

String^ a

const char * a
```

Následující příklad ukazuje, že kompilátor rozlišuje mezi nativní řetězce a <xref:System.String> řetězce.

```cpp
// string_operators_3.cpp
// compile with: /clr
using namespace System;
int func() {
   throw "simple string";   // const char *
};

int func2() {
   throw "string" + "string";   // returns System::String
};

template<typename T>
void func3(T t) {
   Console::WriteLine(T::typeid);
}

int main() {
   try {
      func();
   }
   catch(char * e) {
      Console::WriteLine("char *");
   }

   try {
      func2();
   }
   catch(String^ str) {
      Console::WriteLine("String^ str");
   }

   func3("string");   // const char *
   func3("string" + "string");   // returns System::String
}
```

```Output
char *

String^ str

System.SByte*

System.String
```

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)<br/>
[Řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md)<br/>
[/clr (Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)