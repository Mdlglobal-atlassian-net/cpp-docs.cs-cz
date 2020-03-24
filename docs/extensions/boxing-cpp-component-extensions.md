---
title: ZabaleníC++(/CLI C++a/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- boxing, C++
ms.assetid: b5fd2c98-c578-4f83-8257-6dd663478665
ms.openlocfilehash: 709754e8609406f635444937af93488060167ba9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172604"
---
# <a name="boxing--ccli-and-ccx"></a>ZabaleníC++(/CLI C++a/CX)

Převod typů hodnot na objekty se nazývá *zabalení*a převod objektů na typy hodnot se nazývá *rozbalení*.

## <a name="all-runtimes"></a>Všechny moduly runtime

(Žádné poznámky k této funkci jazyka se nevztahují na všechny moduly runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

C++/CX podporuje zkrácený Syntax pro typy hodnot zabalení a rozbalení typů odkazů. Typ hodnoty je zabalený, když je přiřazen proměnné typu `Object`. `Object` proměnná není zabalena, je-li přiřazena proměnné typu hodnoty a nezabalený typ je uveden v závorkách. To znamená, že když je proměnná objektu převedena na typ hodnoty.

```cpp
  Platform::Object^
  object_variable  = value_variable;
value_variable = (value_type) object_variable;
```

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

### <a name="examples"></a>Příklady

Následující příklad kódu a pole `DateTime` hodnotu. Nejprve příklad získá hodnotu `DateTime`, která představuje aktuální datum a čas a přiřadí ji k proměnné `DateTime`. `DateTime` je zabalené přiřazením k proměnné `Object`. Nakonec je zabalená hodnota nezabalena přiřazením k jiné proměnné `DateTime`.

Chcete-li otestovat příklad, vytvořte `BlankApplication` projektu, nahraďte metodu `BlankPage::OnNavigatedTo()` a pak zadejte zarážky na pravé závorce a přiřazení k proměnné `str1`. Když příklad dosáhne uzavírací závorky, prověřte `str1`.

```cpp
void BlankPage::OnNavigatedTo(NavigationEventArgs^ e)
{
    using namespace Windows::Globalization::DateTimeFormatting;

    Windows::Foundation::DateTime dt, dtAnother;
    Platform::Object^ obj1;

    Windows::Globalization::Calendar^ c =
        ref new Windows::Globalization::Calendar;
    c->SetToNow();
    dt = c->GetDateTime();
    auto dtf = ref new DateTimeFormatter(
                           YearFormat::Full,
                           MonthFormat::Numeric,
                           DayFormat::Default,
                           DayOfWeekFormat::None);
    String^ str1 = dtf->Format(dt);
    OutputDebugString(str1->Data());
    OutputDebugString(L"\r\n");

    // Box the value type and assign to a reference type.
    obj1 = dt;
    // Unbox the reference type and assign to a value type.
    dtAnother = (Windows::Foundation::DateTime) obj1;

    // Format the DateTime for display.
    String^ str2 = dtf->Format(dtAnother);
    OutputDebugString(str2->Data());
}
```

Další informace naleznete v tématu [zabaleníC++(/CX)](../cppcx/boxing-c-cx.md).

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Hodnoty polí kompilátoru, které se mají <xref:System.Object>. To je možné z důvodu převodu typů hodnot na <xref:System.Object>, které jsou definovány kompilátorem.

Zabalení a rozbalení umožňuje považovat typy hodnot za objekty. Typy hodnot, včetně typů struktury a předdefinovaných typů, jako je například int, lze převést na a z typu <xref:System.Object>.

Další informace naleznete v tématu:

- [Postupy: Explicitní žádost o zabalení](../dotnet/how-to-explicitly-request-boxing.md)

- [Postupy: Vytváření typů hodnot pomocí výrazu gcnew s použitím implicitního zabalení](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)

- [Postupy: Rozbalení](../dotnet/how-to-unbox.md)

- [Standardní převody a implicitní zabalení](../dotnet/standard-conversions-and-implicit-boxing.md)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad ukazuje, jak funguje implicitní zabalení.

```cpp
// vcmcppv2_explicit_boxing2.cpp
// compile with: /clr
using namespace System;

ref class A {
public:
   void func(System::Object^ o){Console::WriteLine("in A");}
};

value class V {};

interface struct IFace {
   void func();
};

value class V1 : public IFace {
public:
   virtual void func() {
      Console::WriteLine("Interface function");
   }
};

value struct V2 {
   // conversion operator to System::Object
   static operator System::Object^(V2 v2) {
      Console::WriteLine("operator System::Object^");
      return (V2^)v2;
   }
};

void func1(System::Object^){Console::WriteLine("in void func1(System::Object^)");}
void func1(V2^){Console::WriteLine("in func1(V2^)");}

void func2(System::ValueType^){Console::WriteLine("in func2(System::ValueType^)");}
void func2(System::Object^){Console::WriteLine("in func2(System::Object^)");}

int main() {
   // example 1 simple implicit boxing
   Int32^ bi = 1;
   Console::WriteLine(bi);

   // example 2 calling a member with implicit boxing
   Int32 n = 10;
   Console::WriteLine("xx = {0}", n.ToString());

   // example 3 implicit boxing for function calls
   A^ a = gcnew A;
   a->func(n);

   // example 4 implicit boxing for WriteLine function call
   V v;
   Console::WriteLine("Class {0} passed using implicit boxing", v);
   Console::WriteLine("Class {0} passed with forced boxing", (V^)(v));   // force boxing

   // example 5 casting to a base with implicit boxing
   V1 v1;
   IFace ^ iface = v1;
   iface->func();

   // example 6 user-defined conversion preferred over implicit boxing for function-call parameter matching
   V2 v2;
   func1(v2);   // user defined conversion from V2 to System::Object preferred over implicit boxing
                // Will call void func1(System::Object^);

   func2(v2);   // OK: Calls "static V2::operator System::Object^(V2 v2)"
   func2((V2^)v2);   // Using explicit boxing: calls func2(System::ValueType^)
}
```

```Output
1

xx = 10

in A

Class V passed using implicit boxing

Class V passed with forced boxing

Interface function

in func1(V2^)

in func2(System::ValueType^)

in func2(System::ValueType^)
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
