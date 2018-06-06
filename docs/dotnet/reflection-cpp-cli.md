---
title: Reflexe (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d41d7f627a50dd1a09f4256fbd8448d82c6d5f27
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705241"
---
# <a name="reflection-ccli"></a>Reflexe (C++/CLI)

Reflexe umožňuje známé datové typy na modulu runtime. Reflexe umožňuje výčet datových typů v daném sestavení a členy daného typu třídy nebo hodnota může být zjištěny. To platí bez ohledu na to, jestli byl typ známý nebo je odkazované v době kompilace. Díky tomu reflexe užitečná pro vývoj a nástroje pro správu kódu.

Upozorňujeme, že zadaný název sestavení se silným názvem (viz [vytvoření a použití sestavení](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)), což zahrnuje verze sestavení, jazykovou verzi a podepisovací informace. Všimněte si také, že název oboru názvů, ve kterém je definovaný datový typ lze načíst, společně s název základní třídy.

Nejběžnější způsob přístupu k funkcím reflexe je prostřednictvím <xref:System.Object.GetType%2A> metoda. Tato metoda je poskytována [System::Object](https://msdn.microsoft.com/en-us/library/system.object.aspx), ze které jsou odvozeny všechny třídy uvolňování paměti.

> [!NOTE]
> Reflexe na .exe vytvořené s nástroji Visual C++ compiler je povoleno pouze v případě, že .exe je sestavena s **/CLR: pure** nebo **/CLR: safe** – možnosti kompilátoru. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není k dispozici v Visual Studio 2017. V tématu [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) Další informace.

Další informace najdete v tématu [System.Reflection Namespace](https://msdn.microsoft.com/en-us/library/system.reflection.aspx)

## <a name="example-gettype"></a>Příklad: GetType

`GetType` Metoda vrátí ukazatel na <xref:System.Type> třídu objektu, který popisuje typ při když je založena objekt. ( **Typ** objekt neobsahuje žádné informace specifické pro instanci.) Jedna položka je úplný název typu, který je možné zobrazit takto:

Všimněte si, název typu zahrnuje úplný obor, ve kterém je definovaný typ, včetně oboru názvů, a že se zobrazí v syntaxi .NET s tečkou jako operátor řešení rozsahu.

```cpp
// vcpp_reflection.cpp
// compile with: /clr
using namespace System;
int main() {
   String ^ s = "sample string";
   Console::WriteLine("full type name of '{0}' is '{1}'", s, s->GetType());
}
```

```Output
full type name of 'sample string' is 'System.String'
```

## <a name="example-boxed-value-types"></a>Příklad: pevně určené typy hodnot

Typy hodnot lze použít s `GetType` také fungovat, ale musí být nejprve zabaleny.

```cpp
// vcpp_reflection_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Int32 i = 100; 
   Object ^ o = i;
   Console::WriteLine("type of i = '{0}'", o->GetType());
}
```

```Output
type of i = 'System.Int32'
```

## <a name="example-typeid"></a>Příklad: identifikátor typeid.

Stejně jako u `GetType` metody [typeid](../windows/typeid-cpp-component-extensions.md) operátor vrací ukazatel na **typ** objektu, takže tento kód označuje název typu **System.Int32**. Názvy typů zobrazení je nejzákladnější funkcí reflexe, ale potenciálně užitečnější technika je kontrola nebo zjištění platné hodnoty pro výčtové typy. Tento krok můžete provést pomocí statické **Enum::GetNames** funkce, která vrací pole řetězců, každá obsahuje hodnotu výčtu v textové podobě.  Následující příklad načte pole řetězců, které popisuje hodnoty výčtu hodnoty pro **možnosti** výčtu (CLR) a zobrazí je ve smyčce.

Pokud je přidána čtvrtá možnost **možnosti** výčtu, tento kód bude hlásit novou možnost bez rekompilace, i v případě, že je výčet definován v samostatném sestavení.

```cpp
// vcpp_reflection_3.cpp
// compile with: /clr
using namespace System;

enum class Options {   // not a native enum
   Option1, Option2, Option3
};

int main() {
   array<String^>^ names = Enum::GetNames(Options::typeid);

   Console::WriteLine("there are {0} options in enum '{1}'", 
               names->Length, Options::typeid);

   for (int i = 0 ; i < names->Length ; i++)
      Console::WriteLine("{0}: {1}", i, names[i]);

   Options o = Options::Option2;
   Console::WriteLine("value of 'o' is {0}", o);
}
```

```Output
there are 3 options in enum 'Options'
0: Option1
1: Option2
2: Option3
value of 'o' is Option2
```

## <a name="example-gettype-members-and-properties"></a>Příklad: Gettype – členové a vlastnosti

`GetType` Objekt podporuje několik členů a vlastnosti, které lze použít k prozkoumání typu. Tento kód načte a zobrazí některé z těchto informací:

```cpp
// vcpp_reflection_4.cpp
// compile with: /clr
using namespace System;
int main() {
   Console::WriteLine("type information for 'String':");
   Type ^ t = String::typeid;

   String ^ assemblyName = t->Assembly->FullName;
   Console::WriteLine("assembly name: {0}", assemblyName);

   String ^ nameSpace = t->Namespace;
   Console::WriteLine("namespace: {0}", nameSpace);

   String ^ baseType = t->BaseType->FullName;
   Console::WriteLine("base type: {0}", baseType);

   bool isArray = t->IsArray;
   Console::WriteLine("is array: {0}", isArray);

   bool isClass = t->IsClass;
   Console::WriteLine("is class: {0}", isClass);
}
```

```Output
type information for 'String':
assembly name: mscorlib, Version=1.0.5000.0, Culture=neutral, 
PublicKeyToken=b77a5c561934e089
namespace: System
base type: System.Object
is array: False
is class: True
```

## <a name="example-enumeration-of-types"></a>Příklad: výčet typů

Reflexe také umožňuje výčet typů v rámci sestavení a členů v rámci třídy. K předvedení tuto funkci, definujte třídu jednoduchý:

```cpp
// vcpp_reflection_5.cpp
// compile with: /clr /LD
using namespace System;
public ref class TestClass {
   int m_i;
public:
   TestClass() {}
   void SimpleTestMember1() {}
   String ^ SimpleMember2(String ^ s) { return s; } 
   int TestMember(int i) { return i; }
   property int Member {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }
};
```

## <a name="example-inspection-of-assemblies"></a>Příklad: kontroly sestavení

Pokud se výše uvedený kód zkompilován do knihovny DLL názvem vcpp_reflection_6.dll, pak můžete reflexe kontrola obsahu tohoto sestavení. To zahrnuje použití statická funkce rozhraní API reflexe [Assembly::Load](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.load.aspx) se načíst sestavení. Tato funkce vrátí adresu **sestavení** objekt, který může být dotazován o modulů a typů v rámci.

Jakmile systém reflexe úspěšně načte sestavení, pole **typ** objekty se načítají pomocí [Assembly::GetTypes](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.gettypes.aspx) funkce. Každý element pole obsahuje informace o jiný typ, i když v tomto případě je definována pouze jednu třídu. Pomocí smyčky, každý **typ** v toto pole je dotazován na členy typu pomocí **Type::GetMembers** funkce. Funkce vrátí hodnotu pole **MethodInfo** objekty, každý objekt obsahující informace o – členská funkce, – datový člen nebo vlastnost v typu.

Všimněte si, že seznam metod zahrnuje funkce explicitně definované v **TestClass** a funkce implicitně zděděno z **System::Object** třídy. Jako součást jsou popsány v rozhraní .NET, ne syntaxe jazyka Visual C++ vlastnosti zobrazí jako základní datový člen přístup funkce get/set. Funkce get nebo nastavení se zobrazí v tomto seznamu jako běžné metody. Reflexe podporuje prostřednictvím modulu CLR, není – kompilátor Visual C++.

I když jste použili tento kód pro zkoumání sestavení, který jste definovali, můžete také použít tento kód pro zkoumání sestavení .NET. Například pokud změníte TestAssembly na mscorlib, pak se zobrazí seznam všech typů a metod, které jsou definovány v mscorlib.dll.

```cpp
// vcpp_reflection_6.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;
using namespace System::Reflection;
int main() {
   Assembly ^ a = nullptr;
   try {
      // load assembly -- do not use file extension
      // will look for .dll extension first
      // then .exe with the filename
      a = Assembly::Load("vcpp_reflection_5");
   }
   catch (FileNotFoundException ^ e) {
      Console::WriteLine(e->Message);
      return -1;
   }

   Console::WriteLine("assembly info:");
   Console::WriteLine(a->FullName);
   array<Type^>^ typeArray = a->GetTypes();

   Console::WriteLine("type info ({0} types):", typeArray->Length);

   int totalTypes = 0;
   int totalMembers = 0;
   for (int i = 0 ; i < typeArray->Length ; i++) {
      // retrieve array of member descriptions
      array<MemberInfo^>^ member = typeArray[i]->GetMembers();

      Console::WriteLine("  members of {0} ({1} members):", 
      typeArray[i]->FullName, member->Length);
      for (int j = 0 ; j < member->Length ; j++) {
         Console::Write("       ({0})", 
         member[j]->MemberType.ToString() );
         Console::Write("{0}  ", member[j]);
         Console::WriteLine("");
         totalMembers++;
      }
      totalTypes++;
   }
   Console::WriteLine("{0} total types, {1} total members",
   totalTypes, totalMembers);
}
```

## <a name="see-also"></a>Viz také:

- [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
