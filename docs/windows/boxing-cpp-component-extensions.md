---
title: "Zabalení (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: boxing, Visual C++
ms.assetid: b5fd2c98-c578-4f83-8257-6dd663478665
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8d597466204aa17475ee732b77f321464ccc010
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="boxing--c-component-extensions"></a>Zabalení (rozšíření komponent C++)
Visual C++ compiler můžete převést typy hodnot k objektům v procesu označovaného jako *zabalení*a převést objekty do typy hodnot v procesu označovaného jako *rozbalení*.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 (Používají se žádné poznámky pro tuto funkci jazyka, které platí pro všechny moduly runtime.)  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 C + +/ CX podporuje syntaxi ve zkráceném tvaru pro typy hodnot zabalení a rozbalení odkazové typy. Typ hodnoty je zabalená, když je přiřazený k proměnné typu `Object`. `Object` Proměnná nezabalený, když je přiřazen k proměnné typu hodnota a nezabalený typ určený v závorkách; to znamená, když je proměnná objektu přetypovat na typ hodnoty.  
  
```  
  
  Platform::Object^  
  object_variable  = value_variable;  
value_variable = (value_type) object_variable;  
  
```  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
### <a name="examples"></a>Příklady  
 Následující kód například polí a unboxes `DateTime` hodnotu. V příkladu nejdřív získá hodnotu data a času, který představuje aktuální datum a čas a přiřadí ji k proměnné data a času. Pak je podle jeho přiřazení proměnné objektu zabalená, datum a čas. Nakonec zabalené hodnoty je nezabalený přiřazením jiné proměnné, data a času.  
  
 Chcete-li otestovat v příkladu, vytvoření projektu BlankApplication, nahraďte metodu BlankPage::OnNavigatedTo() a pak zadat zarážky na pravou hranatou závorku a přiřazení proměnné str1. Pokud v příkladu dosáhne pravá závorka, podívejte se na str1.  
  
```  
  
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
 Kompilátor Visual C++ teď typů k hodnot polí <xref:System.Object>.  To je možné z důvodu převodu z kompilátoru definované pro převod typů hodnot do <xref:System.Object>.  
  
 Zabalení a rozbalení povolit hodnotu typy jsou považovány za objekty. Typy hodnot, včetně struktura typů a vestavěné typy, jako je například int, mohou být převedeny do a z typu <xref:System.Object>.  
  
 Další informace naleznete v tématu:  
  
-   [Postupy: explicitní žádost o zabalení](../dotnet/how-to-explicitly-request-boxing.md)  
  
-   [Postupy: pomocí výrazu gcnew vytváření typů hodnot s použitím implicitního zabalení](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)  
  
-   [Postupy: Unbox](../dotnet/how-to-unbox.md)  
  
-   [Standardní převody a implicitní zabalení](../dotnet/standard-conversions-and-implicit-boxing.md)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
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
  
 **Výstup**  
  
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
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)