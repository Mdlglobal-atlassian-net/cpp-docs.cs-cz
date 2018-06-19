---
title: Řetězec (rozšíření komponent C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cfab95c400aad949f06a559fffbdb42993910bb7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889237"
---
# <a name="string--c-component-extensions"></a>String (rozšíření komponent C++)
Podporuje kompilátoru Visual C++ *řetězce*, které jsou objekty, které představují text jako posloupnost znaků. Visual C++ podporuje proměnné řetězec, jehož hodnota je implicitní, a literály, jehož hodnota je řetězec v uvozovkách explicitní.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 Prostředí Windows Runtime a modul common language runtime představují řetězce jako objekty, jejichž přidělené paměti je spravováno automaticky. To znamená není nutné explicitně zahodit paměť pro řetězec při ukončení proměnné vloží řetězec mimo obor nebo aplikace. Pokud chcete označit, že životnosti objektu řetězec spravováno automaticky, deklarovat na řetězcový typ. s [popisovač objektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md) modifikátor.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Architektura prostředí Windows Runtime vyžaduje Visual C++ pro implementaci `String` datový typ v `Platform` oboru názvů. Pro usnadnění vaší práce, Visual C++ také poskytuje `string` datový typ, který se jedná o synonymum `Platform::String`v `default` oboru názvů.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
// compile with /ZW  
using namespace Platform;  
using namespace default;  
   Platform::String^ MyString1 = "The quick brown fox";  
   String^ MyString2 = "jumped over the lazy dog.";  
   String^ MyString3 = "Hello, world!";  
  
```  
  
### <a name="remarks"></a>Poznámky  
 Další příklady a další informace o řetězcích, najdete v části [Platform::String, std::wstring a literály (platforma)](http://msdn.microsoft.com/en-us/ec92fbc6-edf3-4137-a85e-8e29bdb857a8)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime)  
 Toto téma popisuje, jak Visual C++ compiler zpracovává textové literály při spuštění pomocí **/CLR** – možnost kompilátoru. Použít **/CLR**, musíte taky použít modul CLR (CLR), C + +/ CLI syntaxe a spravovaných objektech. Další informace o **/CLR**, najdete v části [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 Při kompilaci s **/CLR**, kompilátor převede textové literály řetězce typu <xref:System.String>. Chcete-li zachovat zpětnou kompatibilitu s existující kód existuje jsou dvě výjimky:  
  
-   Zpracovávání výjimek v jazyce. Pokud je vyvolána řetězcový literál, kompilátor bude catch jako řetězcový literál.  
  
-   Odvození šablony. Když jako šablonu argumentu předána řetězcový literál, kompilátor nebude převeďte ho na <xref:System.String>. Všimněte si, bude textové literály jako obecný argument předaná povýšen <xref:System.String>.  
  
 Kompilátor také obsahuje integrovanou podporu pro tři operátory, které můžete přepsat k přizpůsobení jejich chování:  
  
-   System::String ^ – operátor + (System::String, System::String);  
  
-   System::String ^ + – operátor (System::Object, System::String);  
  
-   System::String ^ + – operátor (System::String, System::Object);  
  
 Když uplyne <xref:System.String>, kompilátor pole, v případě potřeby a pak řetězení objekt (s ToString) s řetězcem.  
  
> [!NOTE]
>  Pomocí kurzoru ("^") označuje, že je deklarovaný proměnná popisovač pro C + +/ CLI spravovaných objektů.  
  
 Další informace najdete v části [řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu ukazuje, zřetězení a porovnávání řetězců.  
  
```cpp  
// string_operators.cpp  
// compile with: /clr  
// In the following code, the caret ("^") indicates that the   
// declared variable is a handle to a C++/CLI managed object.  
using namespace System;  
  
int main() {  
   String ^ a = gcnew String("abc");  
   String ^ b = "def";   // same as gcnew form  
   Object ^ c = gcnew String("ghi");  
  
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
  
   // you can append to a System::String ^  
   Console::WriteLine(a + 1);  
   Console::WriteLine(a + 'a');  
   Console::WriteLine(a + 3.1);  
  
   // test System::String ^ for equality  
   a += b;  
   Console::WriteLine(a);  
   a = b;  
   if (a == b)  
      Console::WriteLine("a and b are equal");  
  
   a = "abc";  
   if (a != b)  
      Console::WriteLine("a and b are not equal");  
  
   // System:String ^ and tracking reference  
   String^% rstr1 = a;  
   Console::WriteLine(rstr1);  
  
   // testing an empty System::String ^  
   String ^ n;  
   if (n == nullptr)  
      Console::WriteLine("n is empty");  
}  
```  
  
 **Output**  
  
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
  
 **Příklad**  
  
 Následující příklad ukazuje, že můžete použít přetížení operátory zadaný kompilátoru a zjistí, že kompilátor přetížení funkce, na základě <xref:System.String> typu.  
  
```cpp  
// string_operators_2.cpp  
// compile with: /clr  
using namespace System;  
  
// a string^ overload will be favored when calling with a String  
void Test_Overload(const char * a) {   
   Console::WriteLine("const char * a");   
}  
void Test_Overload(String ^ a) {   
   Console::WriteLine("String ^ a");   
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(String ^ a, String ^ b) {  
   return ("overloaded +(String ^ a, String ^ b)");  
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(Object ^ a, String ^ b) {  
   return ("overloaded +(Object ^ a, String ^ b)");  
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(String ^ a, Object ^ b) {  
   return ("overloaded +(String ^ a, Object ^ b)");  
}  
  
int main() {  
   String ^ a = gcnew String("abc");  
   String ^ b = "def";   // same as gcnew form  
   Object ^ c = gcnew String("ghi");  
  
   char d[100] = "abc";  
  
   Console::WriteLine(a + b);  
   Console::WriteLine(a + c);  
   Console::WriteLine(c + a);  
  
   Test_Overload("hello");  
   Test_Overload(d);  
}  
```  
  
 **Output**  
  
```Output  
overloaded +(String ^ a, String ^ b)   
  
overloaded +(String ^ a, Object ^ b)   
  
overloaded +(Object ^ a, String ^ b)   
  
String ^ a  
  
const char * a  
```  
  
 **Příklad**  
  
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
  
 **Output**  
  
```Output  
char *  
  
String^ str  
  
System.SByte*  
  
System.String  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)   
 [Řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md)   
 [/clr (kompilace modulu Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)