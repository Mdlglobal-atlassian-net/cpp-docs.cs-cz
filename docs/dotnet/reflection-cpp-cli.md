---
title: Reflexe (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
- plug-ins [C++]
- reflection [C++}, plug-ins
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
ms.openlocfilehash: 9d7d2623608d7dab27de78567582c7043468e98f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444015"
---
# <a name="reflection-ccli"></a>Reflexe (C++/CLI)

Reflexe umožňuje známé datové typy se zkontroloval za běhu. Reflexe umožňuje výčet datových typů v daném sestavení a lze zjistit členy daného class nebo hodnotového typu. To platí bez ohledu na to, zda byl typ známé nebo odkazované v době kompilace. Díky tomu reflexe užitečná funkce pro vývoj a nástroje pro správu kódu.

Mějte na paměti, že zadaný název sestavení se silným názvem (viz [vytvoření a použití sestavení](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)), který obsahuje sestavení verze, jazykovou verzi a podpisové informace. Všimněte si také, že název oboru názvů, ve kterém je definován typ dat, může být načten spolu s názvem základní třídy.

Nejběžnější způsob přístupu k funkcím reflexe, je prostřednictvím <xref:System.Object.GetType%2A> metody. Tato metoda poskytuje [System::Object](https://msdn.microsoft.com/library/system.object.aspx), ze které jsou odvozeny všechny třídy uvolnění paměti.

> [!NOTE]
> Reflexe na .exe vytvořených pomocí kompilátoru jazyka Visual C++ je povolen, pouze pokud je sestavován .exe **/CLR: pure** nebo **/CLR: safe** – možnosti kompilátoru. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není k dispozici v sadě Visual Studio 2017. Zobrazit [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) Další informace.

Další informace najdete v tématu [System.Reflection Namespace](https://msdn.microsoft.com/library/system.reflection.aspx)

## <a name="example-gettype"></a>Příklad: GetType

`GetType` Metoda vrací ukazatel na <xref:System.Type> třídu objektu, který popisuje typ, na kdy je založena na objekt. ( **Typ** objekt neobsahuje žádné informace specifické pro instanci.) Jedna položka je úplný název typu, který je možné zobrazit takto:

Všimněte si, že název typu obsahuje úplného oboru, ve kterém je definován typ, včetně oboru názvů, a zda je zobrazena v syntaxi .NET s tečkou jako operátor rozlišení rozsahu.

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

Typy hodnot lze použít s `GetType` fungovat stejně, ale musí být nejprve zabaleny.

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

Stejně jako u `GetType` metody [typeid](../windows/typeid-cpp-component-extensions.md) operátor vrací ukazatel na **typ** objektu, takže tento kód označuje název typu **System.Int32**. Zobrazení názvů typů je nejzákladnější funkce reflexe, ale potenciálně užitečnější technikou je kontrola nebo zjištění platné hodnoty pro výčtové typy. To můžete udělat pomocí statické **Enum::GetNames** funkce, která vrací pole řetězců, každý obsahující hodnotu výčtu v textové podobě.  Následující příklad načte pole řetězců, které popisuje hodnoty výčtu hodnoty pro **možnosti** výčtu (CLR) a zobrazí je ve smyčce.

Pokud je přidána čtvrtá možnost **možnosti** výčet, tento kód bude hlásit nové možnost bez nutnosti rekompilace, i když výčtu je definována v samostatném sestavení.

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

## <a name="example-gettype-members-and-properties"></a>Příklad: GetType členy a vlastnosti

`GetType` Objekt podporuje několik členů a vlastností, které můžete použít k prozkoumání typu. Tento kód načte a zobrazí některé z těchto informací:

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

Reflexe umožňuje také výčet typů v rámci sestavení a členy v rámci třídy. Abychom si předvedli tuto funkci, definujte jednoduchou třídu:

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

## <a name="example-inspection-of-assemblies"></a>Příklad: Kontrola sestavení

Pokud výše uvedený kód je zkompilován do knihovny DLL s názvem vcpp_reflection_6.dll, pak můžete reflexe pro kontrolu obsahu tohoto sestavení. To zahrnuje použití statické funkce rozhraní API reflexe [Assembly::Load](https://msdn.microsoft.com/library/system.reflection.assembly.load.aspx) načíst sestavení. Tato funkce vrátí adresu **sestavení** objekt, který může být dotazován o moduly a typy v rámci.

Jakmile systém reflexe úspěšně načte sestavení pole **typ** objekty získáte pomocí [Assembly::GetTypes](https://msdn.microsoft.com/library/system.reflection.assembly.gettypes.aspx) funkce. Každý prvek pole obsahuje informace o jiný typ, i když v tomto případě je definována pouze jednu třídu. Využitím smyčky, každý **typ** v tomto poli je dotazován členy typu pomocí **Type::GetMembers** funkce. Tato funkce vrací pole **MethodInfo** objekty, každý objekt, který obsahuje informace o členskou funkci, datový člen nebo vlastnost v typu.

Všimněte si, že seznam metod zahrnuje funkce explicitně definované v **TestClass** a funkce se implicitně dědí z **System::Object** třídy. Jako součást popisovaný v .NET, nikoli v jazyce Visual C++ syntaxi vlastnosti se zobrazí jako základní datový člen přístupný funkce get/set. Funkce get/set se v tomto seznamu zobrazí jako běžné metody. Reflexe je podporované prostřednictvím modul common language runtime není kompilátorem jazyka Visual C++.

I když jste použili tento kód ke kontrole sestavení, které jste definovali, můžete také použít tento kód ke kontrole sestavení .NET. Například pokud měnit TestAssembly na mscorlib, pak se zobrazí seznam všech typů a metod, které jsou definovány v mscorlib.dll.

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

## <a name="implement"></a> Postupy: implementace architektury komponenty modulu Plugin pomocí reflexe

Následující příklady kódu znázorňují použití reflexe implementace jednoduché "modulu plug-in" architektury. První odkaz je aplikace a druhá je modul plug-in. Aplikace je formulář více dokumentů, které naplňuje sebe pomocí nalezené v knihovně DLL modulu plug-in jako argument příkazového řádku k dispozici žádné třídy založené na formulářích.

Pokusí se načíst zadané sestavení pomocí aplikace <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> metody. Pokud úspěšné, typy v sestavení jsou uvedené použití <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> metody. Každý typ je pak odhalena použitím kompatibility <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> metody. V tomto příkladu třídy v zadané sestavení musí být odvozen z <xref:System.Windows.Forms.Form> třídu k určení jako modul plug-in.

Instance třídy kompatibilní se pak vytvářejí s <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> metodu, která přijímá <xref:System.Type> jako argument a vrátí ukazatel na novou instanci. Každá nová instance poté připojen k formuláři a zobrazit.

Všimněte si, <xref:System.Reflection.Assembly.Load%2A> metoda nepřijímá žádné názvy sestavení, které mají příponu souboru. Hlavní funkce v aplikaci ořízne všechny zadané přípony, tak v následujícím příkladu kódu funguje v obou případech.

### <a name="example"></a>Příklad

Následující kód definuje aplikaci, která přijímá moduly plug-in. Název sestavení musí být zadaná jako první argument. Toto sestavení by měl obsahovat alespoň jednu veřejnou <xref:System.Windows.Forms.Form> odvozeného typu.

```cpp
// plugin_application.cpp
// compile with: /clr /c
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;

ref class PluggableForm : public Form  {
public:
   PluggableForm() {}
   PluggableForm(Assembly^ plugAssembly) {
      Text = "plug-in example";
      Size = Drawing::Size(400, 400);
      IsMdiContainer = true;

      array<Type^>^ types = plugAssembly->GetTypes( );
      Type^ formType = Form::typeid;

      for (int i = 0 ; i < types->Length ; i++) {
         if (formType->IsAssignableFrom(types[i])) {
            // Create an instance given the type description.
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));
            if (f) {
               f->Text = types[i]->ToString();
               f->MdiParent = this;
               f->Show();
            }
         }
      }
   }
};

int main() {
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");
   Application::Run(gcnew PluggableForm(a));
}
```

### <a name="example"></a>Příklad

Následující kód definuje tři třídy odvozené od <xref:System.Windows.Forms.Form>. Pokud název výsledný název sestavení je předán do spustitelného souboru v předchozí ukázce, každá z těchto tří tříd, se zjistí a vytvoření instance navzdory tomu, že byly všechny neznámé hostování aplikace v době kompilace.

```cpp
// plugin_assembly.cpp
// compile with: /clr /LD
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;
using namespace System::Drawing;

public ref class BlueForm : public Form {
public:
   BlueForm() {
      BackColor = Color::Blue;
   }
};

public ref class CircleForm : public Form {
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);
   }
};

public ref class StarburstForm : public Form {
public:
   StarburstForm(){
      BackColor = Color::Black;
   }
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      Pen^ p = gcnew Pen(Color::Red, 2);
      Random^ r = gcnew Random( );
      Int32 w = ClientSize.Width;
      Int32 h = ClientSize.Height;
      for (int i=0; i<100; i++) {
         float x1 = w / 2;
         float y1 = h / 2;
         float x2 = r->Next(w);
         float y2 = r->Next(h);
         args->Graphics->DrawLine(p, x1, y1, x2, y2);
      }
   }
};
```

## <a name="enumerate"></a> Postupy: výčet datových typů v sestaveních pomocí reflexe

Následující kód ukazuje výčet veřejných typů a členů pomocí <xref:System.Reflection>.

Zadaný název sestavení, v místním adresáři nebo v mezipaměti GAC, následující kód se pokusí otevřít sestavení a načíst popisy. V případě úspěchu, zobrazí se s jeho veřejné členy jednotlivých typů.

Všimněte si, že <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> vyžaduje, že se používá bez přípony souboru. Proto pomocí "mscorlib.dll" jako argument příkazového řádku se nezdaří, zatímco použití pouze "mscorlib" způsobí zobrazení typů rozhraní .NET Framework. Pokud je poskytnut žádný název sestavení, kód rozpozná a typů v rámci aktuálního sestavení sestav (EXE, vyplývající z tohoto kódu).

### <a name="example"></a>Příklad

```cpp
// self_reflection.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;
using namespace System::Collections;

public ref class ExampleType {
public:
   ExampleType() {}
   void Func() {}
};

int main() {
   String^ delimStr = " ";
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ args = Environment::CommandLine->Split( delimiter );

// replace "self_reflection.exe" with an assembly from either the local
// directory or the GAC
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");
   Console::WriteLine(a);

   int count = 0;
   array<Type^>^ types = a->GetTypes();
   IEnumerator^ typeIter = types->GetEnumerator();

   while ( typeIter->MoveNext() ) {
      Type^ t = dynamic_cast<Type^>(typeIter->Current);
      Console::WriteLine("   {0}", t->ToString());

      array<MemberInfo^>^ members = t->GetMembers();
      IEnumerator^ memberIter = members->GetEnumerator();
      while ( memberIter->MoveNext() ) {
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);
         Console::Write("      {0}", mi->ToString( ) );
         if (mi->MemberType == MemberTypes::Constructor)
            Console::Write("   (constructor)");

         Console::WriteLine();
      }
      count++;
   }
   Console::WriteLine("{0} types found", count);
}
```

## <a name="see-also"></a>Viz také:

- [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
