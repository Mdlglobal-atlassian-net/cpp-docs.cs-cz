---
title: Zabalení (rozšíření komponent C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- boxing, Visual C++
ms.assetid: b5fd2c98-c578-4f83-8257-6dd663478665
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a23029f8347990abaa8b2e6ecc65e0c3037c6eb
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583791"
---
# <a name="boxing--c-component-extensions"></a>Zabalení (rozšíření komponent C++)

Kompilátor Visual C++ můžete převést typy hodnot k objektům v procesu nazývaného *zabalení*a převedení objektů na typy hodnot v procesu nazývaného *rozbalení*.

## <a name="all-runtimes"></a>Všechny moduly runtime

(Neexistují žádné poznámky o této funkci jazyka, které platí pro všechny moduly runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

C + +/ CX podporuje syntaxi ve zkráceném tvaru pro typy hodnot zabalení a rozbalení typy odkazů. Typ hodnoty je zabalená, když je přiřazen k proměnné typu `Object`. `Object` Proměnná je instance nezabalená, když je přiřazen do proměnné typu hodnoty a nezabalený typ. je uveden v závorkách, což znamená, když je objektová proměnná přetypována na typ hodnoty.

```cpp
  Platform::Object^
  object_variable  = value_variable;
value_variable = (value_type) object_variable;
```

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

### <a name="examples"></a>Příklady

Následující kód například polí a unboxes `DateTime` hodnotu. Nejprve příklad získá `DateTime` hodnotu, která představuje aktuální datum a čas a přiřadí ji k `DateTime` proměnné. Pak bude `DateTime` je zabalená, tak, že ji přiřadíte `Object` proměnné. Nakonec je nejprve vybalen zabalené hodnoty tak, že ji přiřadíte do jiného `DateTime` proměnné.

Příklad testování, vytvořit `BlankApplication` projektu, nahraďte `BlankPage::OnNavigatedTo()` metoda a pak zadejte zarážky za uzavírací závorku a přiřazení k proměnné `str1`. Pokud v příkladu dosáhne uzavírací závorku, podívejte se `str1`.

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

Další informace najdete v tématu [zabalení (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh969554.aspx).

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Kompilátor Visual C++ teď typů do hodnot polí <xref:System.Object>. To je možné z důvodu převodu definované kompilátorem převést hodnotu typů do <xref:System.Object>.

Zabalení a rozbalení povolit typy hodnot jsou považovány za objekty. Typy hodnot včetně struktury typů a vestavěné typy, například int, může být převeden do a z typu <xref:System.Object>.

Další informace naleznete v tématu:

- [Postupy: Explicitní žádost o zabalení](../dotnet/how-to-explicitly-request-boxing.md)

- [Postupy: Vytváření typů hodnot pomocí výrazu gcnew s použitím implicitního zabalení](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)

- [Postupy: Rozbalení](../dotnet/how-to-unbox.md)

- [Standardní převody a implicitní zabalení](../dotnet/standard-conversions-and-implicit-boxing.md)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující ukázka ukazuje, jak implicitní zabalení funguje.

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

[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)