---
title: Řetězec (C++/CLI a C++/CX)
ms.date: 10/08/2018
ms.topic: reference
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
ms.openlocfilehash: b9da900ffbfff34dc596d8981095d8285bf37208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171941"
---
# <a name="string--ccli-and-ccx"></a>Řetězec (C++/CLI a C++/CX)

Prostředí Windows Runtime a modul CLR (Common Language Runtime) reprezentují řetězce jako objekty, jejichž přidělená paměť je spravovaná automaticky. To znamená, že nemusíte explicitně vyhazovat paměť pro řetězec, když se řetězcová proměnná dostane mimo rozsah nebo končí vaše aplikace. Chcete-li určit, že životnost objektu String má být spravována automaticky, deklarujte typ řetězce pomocí modifikátoru [popisovače objektu (^)](handle-to-object-operator-hat-cpp-component-extensions.md) .

## <a name="windows-runtime"></a>prostředí Windows Runtime

Architektura prostředí Windows Runtime vyžaduje, aby byl datový typ `String` umístěný v oboru názvů `Platform`. Pro usnadnění práce poskytuje vizuál C++ také `string` datový typ, což je synonymum pro `Platform::String`v oboru názvů `default`.

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

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Při kompilaci s `/clr`kompilátor převede řetězcové literály na řetězce typu <xref:System.String>. Aby se zachovala zpětná kompatibilita se stávajícím kódem, existují dvě výjimky:

- Zpracování výjimek. Při vyvolání řetězcového literálu bude kompilátor zachytit jako řetězcový literál.

- Odpočty šablon Při předání řetězcového literálu jako argumentu šablony jej kompilátor nepřevede na <xref:System.String>. Všimněte si, že řetězcové literály předané jako obecný argument budou povýšeny na <xref:System.String>.

Kompilátor také obsahuje integrovanou podporu pro tři operátory, které lze přepsat pro přizpůsobení jejich chování:

- System:: String ^ – operátor + (System:: String, System:: String);

- System:: String ^ – operátor + (System:: Object, System:: String);

- System:: String ^ – operátor + (System:: String, System:: Object);

Při předání <xref:System.String>, kompilátor bude v případě potřeby v případě potřeby a zřetězení objektu (s ToString) s řetězcem.

> [!NOTE]
> Stříška ("^") označuje, že deklarovaná proměnná je popisovačem spravovaného objektu C++/CLI.

Další informace naleznete v tématu [řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: **/CLR**

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

Následující příklad ukazuje, že lze přetížit operátory poskytované kompilátorem a že kompilátor najde přetížení funkce na základě typu <xref:System.String>.

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

Následující příklad ukazuje, že kompilátor rozlišuje nativní řetězce a <xref:System.String> řetězce.

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

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)<br/>
[Řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md)<br/>
[/clr (kompilace modulu Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)
