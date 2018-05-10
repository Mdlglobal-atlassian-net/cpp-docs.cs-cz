---
title: Obecné třídy (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07a5cb6abaca56901af26895b1304a9b7079ced9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="generic-classes-ccli"></a>Obecné třídy (C++/CLI)
Obecné třídy je deklarován v následující podobě:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[attributes]  
generic <class-key type-parameter-identifier(s)>  
[constraint-clauses]  
[accessibility-modifiers] ref class identifier  [modifiers]  
[: base-list]   
{  
class-body  
} [declarators] [;]  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výše uvedené syntaxe se používají následující termíny:  
  
 `attributes` (volitelné)  
 Další deklarativní informace. Další informace o atributy a třídy atributů najdete v tématu atributy.  
  
 *klíč třídy*  
 Buď `class` nebo `typename`  
  
 *Typ-parametr-identifikátory*,  
 Seznam oddělený čárkami identifikátorů zadání názvy parametrů typu.  
  
 *omezení – klauzule*  
 Seznam (není oddělených čárkami) **kde** klauzule určující omezení pro parametry typu. Má podobu:  
  
 `where`  *identifikátor typu parametru*`:`*seznamu omezení*   `...`  
  
 *seznam omezení*  
 *Třída nebo rozhraní*[`,` *...* ]  
  
 *Modifikátory dostupnosti*  
 Modifikátory dostupnosti pro obecná třída Pro prostředí Windows Runtime pouze povolené Modifikátor je `private`. Pro modul CLR, jsou povolené modifikátory `private` a `public`.  
  
 *Identifikátor*  
 Název třídy Obecné, všechny platný identifikátor C++.  
  
 *Modifikátory* (volitelné)  
 Povolené modifikátory zahrnují `sealed` a **abstraktní**.  
  
 *základní seznam*  
 Seznam obsahující jeden základní třídy a všechny implementují rozhraní, všechny oddělených čárkami.  
  
 *text – třída*  
 Tělo třídy, která obsahuje pole, členské funkce atd.  
  
 *Deklarátory*  
 Deklarace žádné proměnné tohoto typu. Příklad: `^` *identifikátor*[`,` ...]  
  
 Obecné třídy takovéto můžou deklarovat (Všimněte si, že klíčové slovo **třída** lze namísto **typename**). V tomto příkladu `ItemType`, `KeyType` a `ValueType` jsou neznámé typy, které jsou určené v místě, kde typ. `HashTable<int, int>` je vytvořený typ obecného typu `HashTable<KeyType, ValueType>`. Počet různých sestavené typy konstruovat z jednoho obecného typu. Sestavené typy, které se vytvářejí na základě obecné třídy jsou zpracovány jako libovolný jiný typ třídy ref.  
  
```  
// generic_classes_1.cpp  
// compile with: /clr  
using namespace System;  
generic <typename ItemType>  
ref struct Stack {  
   // ItemType may be used as a type here  
   void Add(ItemType item) {}  
};  
  
generic <typename KeyType, typename ValueType>  
ref class HashTable {};  
  
// The keyword class may be used instead of typename:  
generic <class ListItem>  
ref class List {};  
  
int main() {  
   HashTable<int, Decimal>^ g1 = gcnew HashTable<int, Decimal>();  
}  
```  
  
 Obou typů hodnot (buď předdefinované typy, jako `int` nebo `double`, nebo hodnotu definovanou uživatelem typy) a odkazové typy může být použita jako argument obecného typu. Syntaxe v rámci obecné definice je stejný bez ohledu na to. Neznámý typ syntakticky, považuje, jako by šlo odkazového typu. Modul runtime je však možné, určit, zda typu použitého ve skutečnosti je typu hodnoty a nahraďte příslušné generovaný kód pro přímý přístup k členy. Typy hodnot, které jsou použity jako argumenty obecného typu nejsou do pole a proto se nebude vyskytovat snížení výkonu, které jsou přidružené k zabalení. By měl být použit v textu Obecná syntaxe **T ^** a '**->**, místo provedení'**.**'. Jakékoli použití [nové, gcnew ref](../windows/ref-new-gcnew-cpp-component-extensions.md) pro typ parametru se správně interpretovat modulem runtime jako vytvoření jednoduchého typu hodnoty Pokud argument typ je typ hodnoty.  
  
 Můžete také deklarovat obecné třídy s [omezení obecných parametrů typů (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md) na typy, které lze použít pro parametr typu. V následujícím příkladu použít kterýkoli typ pro `ItemType` musí implementovat `IItem` rozhraní. Pokus o použití `int`, například které neimplementuje `IItem`, by vytvořit k chybě kompilace, protože argument typu nesplňuje omezení.  
  
```  
// generic_classes_2.cpp  
// compile with: /clr /c  
interface class IItem {};  
generic <class ItemType>  
where ItemType : IItem  
ref class Stack {};  
```  
  
 Obecné třídy v oboru názvů stejné nemohou být přetíženy pouze změnou počet nebo různé typy parametrů typu. Ale pokud každá třída žije v jiný obor názvů, se může být přetížený. Zvažte například následující dvě třídy `MyClass` a `MyClass<ItemType>`, v oborech názvů `A` a `B`. Dvě třídy mohou být přetíženy pak v třetí oboru názvů C:  
  
```  
// generic_classes_3.cpp  
// compile with: /clr /c  
namespace A {  
   ref class MyClass {};  
}  
  
namespace B {  
   generic <typename ItemType>   
   ref class MyClass2 { };  
}  
  
namespace C {  
   using namespace A;  
   using namespace B;  
  
   ref class Test {  
      static void F() {  
         MyClass^ m1 = gcnew MyClass();   // OK  
         MyClass2<int>^ m2 = gcnew MyClass2<int>();   // OK  
      }  
   };  
}  
```  
  
 Základní třída a základní rozhraní nemohou mít parametry typu. Základní třída však může zahrnovat parametr typu jako argument, jako v následujícím případě:  
  
```  
// generic_classes_4.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
interface class IInterface {};  
  
generic <typename ItemType>  
ref class MyClass : IInterface<ItemType> {};  
```  
  
 Konstruktory a destruktory jsou spustit jednou pro každou instanci objektu (obvyklým); statické konstruktory jsou spustit jednou pro každý typ vytvořený.  
  
## <a name="fields-in-generic-classes"></a>Pole v obecné třídy  
 Tato část ukazuje použití instance a statických polí v obecné třídy.  
  
### <a name="instance-variables"></a>Instance proměnné  
 Instance proměnné obecná třída může mít typy a proměnné inicializátory, které zahrnují všechny parametry typu z nadřazených tříd.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, tři různé instance obecná třída MyClass\<ItemType >, se vytváří pomocí příslušného typu argumentů (`int`, **dvojité**, a **řetězec**).  
  
```  
// generics_instance_fields1.cpp  
// compile with: /clr  
// Instance fields on generic classes  
using namespace System;  
  
generic <typename ItemType>  
ref class MyClass {  
// Field of the type ItemType:  
public :  
   ItemType field1;  
   // Constructor using a parameter of the type ItemType:  
   MyClass(ItemType p) {  
     field1 = p;   
   }  
};  
  
int main() {  
   // Instantiate an instance with an integer field:  
   MyClass<int>^ myObj1 = gcnew MyClass<int>(123);  
   Console::WriteLine("Integer field = {0}", myObj1->field1);  
  
   // Instantiate an instance with a double field:  
   MyClass<double>^ myObj2 = gcnew MyClass<double>(1.23);  
   Console::WriteLine("Double field = {0}", myObj2->field1);  
  
   // Instantiate an instance with a String field:  
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>("ABC");  
   Console::WriteLine("String field = {0}", myObj3->field1);  
   }  
```  
  
```Output  
Integer field = 123  
Double field = 1.23  
String field = ABC  
```  
  
## <a name="static-variables"></a>Statické proměnné  
 Při vytváření nové obecného typu jsou vytvořeny nové instance všechny statické proměnné a všechny statického konstruktoru pro tento typ je provedena.  
  
 Statické proměnné můžete použít všechny parametry typu z nadřazených tříd.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití statická pole a statického konstruktoru v rámci obecné třídy.  
  
```  
// generics_static2.cpp  
// compile with: /clr  
using namespace System;  
  
interface class ILog {  
   void Write(String^ s);  
};  
  
ref class DateTimeLog : ILog {  
public:  
   virtual void Write(String^ s) {  
      Console::WriteLine( "{0}\t{1}", DateTime::Now, s);  
   }  
};  
  
ref class PlainLog : ILog {  
public:  
   virtual void Write(String^ s) { Console::WriteLine(s); }  
};  
  
generic <typename LogType>  
where LogType : ILog  
ref class G {  
   static LogType s_log;  
  
public:  
   G(){}  
   void SetLog(LogType log) { s_log = log; }  
   void F() { s_log->Write("Test1"); }  
   static G() { Console::WriteLine("Static constructor called."); }     
};  
  
int main() {  
   G<PlainLog^>^ g1 = gcnew G<PlainLog^>();  
   g1->SetLog(gcnew PlainLog());  
   g1->F();  
  
   G<DateTimeLog^>^ g2 = gcnew G<DateTimeLog^>();  
   g2->SetLog(gcnew DateTimeLog());  
  
   // prints date  
   // g2->F();  
}  
```  
  
```Output  
Static constructor called.  
Static constructor called.  
Static constructor called.  
Test1  
```  
  
## <a name="methods-in-generic-classes"></a>Metody v obecné třídy  
 Metody v obecné třídy mohou být obecný sami; metody neobecnou budou implicitně parametry podle parametr typu třídy.  
  
 Následující zvláštní pravidla platí při metod v rámci obecné třídy:  
  
-   Jako parametry, návratové typy nebo lokální proměnné, můžete použít metody v obecné třídy parametry typu.  
  
-   Metody v obecné třídy můžete použít otevřené nebo zavřené sestavené typy jako parametry, návratové typy nebo lokální proměnné.  
  
### <a name="non-generic-methods-in-generic-classes"></a>Metody neobecnou v obecné třídy  
 Metody v obecné třídy, které mají žádné další typ parametry se obvykle označují jako neobecnou i když jsou implicitně parametry podle nadřazených obecná třída.  
  
 Podpis neobecnou metodu může obsahovat jeden nebo více parametrů typu nadřazených třídy, buď přímo, nebo v otevřeném typu vytvořený. Příklad:  
  
 `void MyMethod(MyClass<ItemType> x) {}`  
  
 Text těchto metod můžete také použít tyto parametry typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje neobecnou metodu `ProtectData`, uvnitř obecná třída `MyClass<ItemType>`. Metoda používá parametr typu třídy `ItemType` v jeho podpisu v otevřeném typu vytvořený.  
  
```  
// generics_non_generic_methods1.cpp  
// compile with: /clr  
// Non-generic methods within a generic class.  
using namespace System;  
  
generic <typename ItemType>  
ref class MyClass {  
public:  
   String^ name;  
   ItemType data;  
  
   MyClass(ItemType x) {  
      data = x;  
   }  
  
   // Non-generic method using the type parameter:  
   virtual void ProtectData(MyClass<ItemType>^ x) {  
      data = x->data;  
   }  
};  
  
// ItemType defined as String^  
ref class MyMainClass: MyClass<String^> {  
public:  
   // Passing "123.00" to the constructor:  
   MyMainClass(): MyClass<String^>("123.00") {  
      name = "Jeff Smith";   
   }   
  
   virtual void ProtectData(MyClass<String^>^ x) override {  
      x->data = String::Format("${0}**", x->data);  
   }  
  
   static void Main() {  
      MyMainClass^ x1 = gcnew MyMainClass();  
  
      x1->ProtectData(x1);  
      Console::WriteLine("Name: {0}", x1->name);  
      Console::WriteLine("Amount: {0}", x1->data);  
   }  
};  
  
int main() {  
   MyMainClass::Main();  
}  
```  
  
```Output  
Name: Jeff Smith  
Amount: $123.00**  
```  
  
## <a name="generic-methods-in-generic-classes"></a>Obecné metody v obecné třídy  
 Obecné metody v obecné a neobecné třídy můžou deklarovat. Příklad:  
  
## <a name="example"></a>Příklad  
  
```  
// generics_method2.cpp  
// compile with: /clr /c  
generic <typename Type1>  
ref class G {  
public:  
   // Generic method having a type parameter  
   // from the class, Type1, and its own type  
   // parameter, Type2  
   generic <typename Type2>  
   void Method1(Type1 t1, Type2 t2) { F(t1, t2); }  
  
   // Non-generic method:  
   // Can use the class type param, Type1, but not Type2.  
   void Method2(Type1 t1) { F(t1, t1); }  
  
   void F(Object^ o1, Object^ o2) {}  
};  
```  
  
 Neobecnou metodu je stále Obecné v tom smyslu, že je parametry podle parametr typu třída, ale nemá žádné další typ parametry.  
  
 Všechny typy metod v obecných tříd může být statické Obecné, včetně, instanci a virtuální metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje deklarování a použití obecné metody v rámci obecné třídy:  
  
```  
// generics_generic_method2.cpp  
// compile with: /clr  
using namespace System;  
generic <class ItemType>  
ref class MyClass {  
public:  
   // Declare a generic method member.  
   generic <class Type1>  
   String^ MyMethod(ItemType item, Type1 t) {  
      return String::Concat(item->ToString(), t->ToString());  
   }  
};  
  
int main() {  
   // Create instances using different types.  
   MyClass<int>^ myObj1 = gcnew MyClass<int>();  
   MyClass<String^>^ myObj2 = gcnew MyClass<String^>();  
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>();  
  
   // Calling MyMethod using two integers.  
   Console::WriteLine("MyMethod returned: {0}",  
            myObj1->MyMethod<int>(1, 2));  
  
   // Calling MyMethod using an integer and a string.  
   Console::WriteLine("MyMethod returned: {0}",  
            myObj2->MyMethod<int>("Hello #", 1));  
  
   // Calling MyMethod using two strings.  
   Console::WriteLine("MyMethod returned: {0}",  
       myObj3->MyMethod<String^>("Hello ", "World!"));  
  
   // generic methods can be called without specifying type arguments  
   myObj1->MyMethod<int>(1, 2);  
   myObj2->MyMethod<int>("Hello #", 1);  
   myObj3->MyMethod<String^>("Hello ", "World!");  
}  
```  
  
```Output  
MyMethod returned: 12  
MyMethod returned: Hello #1  
MyMethod returned: Hello World!  
```  
  
## <a name="using-nested-types-in-generic-classes"></a>Použití vnořené typy v obecné třídy  
 Stejně jako s běžné třídy, můžou deklarovat jiné typy uvnitř obecné třídy. Vnořené třídy deklaraci je implicitně parametry podle parametry typu deklarace vnější třídy. Proto je pro každý vytvořený vnější typ definované odlišné vnořené třídy. Například v deklaraci,  
  
```  
// generic_classes_5.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
ref struct Outer {  
   ref class Inner {};  
};  
```  
  
 Typ vnější\<int >:: vnitřní není stejný jako typ vnější\<dvojité >:: vnitřní.  
  
 Stejně jako u obecné metody v obecné třídy lze definovat další typ parametry pro vnořené typy. Pokud použijete stejné názvy parametrů typu ve třídě vnitřní a vnější, parametr typu vnitřní skryje parametr vnější typu.  
  
```  
// generic_classes_6.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
ref class Outer {  
   ItemType outer_item;   // refers to outer ItemType  
  
   generic <typename ItemType>  
   ref class Inner {  
      ItemType inner_item;   // refers to Inner ItemType  
   };  
};  
```  
  
 Vzhledem k tomu, že neexistuje žádný způsob, jak odkazovat na parametr vnější typu, kompilátor vygeneruje upozornění v této situaci.  
  
 Když jsou pojmenované sestavené vnořené obecné typy, parametr typu pro typ vnějšího není zahrnutý v seznamu Typ parametru pro vnitřní typ Přestože vnitřní typ je implicitně parametry podle parametr typu vnější typu. V případě výše uvedený název typu sestavené bude vnější\<int >:: vnitřní\<řetězec >.  
  
 Následující příklad ukazuje, vytváření a čtení odkazovaného seznamu pomocí vnořené typy v obecné třídy.  
  
## <a name="example"></a>Příklad  
  
```  
// generics_linked_list.cpp  
// compile with: /clr  
using namespace System;  
generic <class ItemType>  
ref class LinkedList {  
// The node class:  
public:  
   ref class Node {  
   // The link field:  
   public:  
      Node^ next;  
      // The data field:  
      ItemType item;   
   } ^first, ^current;  
};  
  
ref class ListBuilder {  
public:  
   void BuildIt(LinkedList<double>^ list) {  
      /* Build the list */  
      double m[5] = {0.1, 0.2, 0.3, 0.4, 0.5};  
      Console::WriteLine("Building the list:");  
  
      for (int n=0; n<=4; n++) {  
         // Create a new node:  
         list->current = gcnew LinkedList<double>::Node();  
  
         // Assign a value to the data field:  
         list->current->item = m[n];  
  
         // Set the link field "next" to be the same as   
         // the "first" field:  
         list->current->next = list->first;  
  
         // Redirect "first" to the new node:  
         list->first = list->current;  
  
         // Display node's data as it builds:  
         Console::WriteLine(list->current->item);  
      }  
   }  
  
   void ReadIt(LinkedList<double>^ list) {  
      // Read the list  
      // Make "first" the "current" link field:  
      list->current = list->first;  
      Console::WriteLine("Reading nodes:");  
  
      // Read nodes until current == null:  
      while (list->current != nullptr) {  
         // Display the node's data field:  
         Console::WriteLine(list->current->item);  
  
         // Move to the next node:  
         list->current = list->current->next;  
      }  
   }  
};  
  
int main() {  
   // Create a list:  
   LinkedList<double>^ aList = gcnew LinkedList<double>();  
  
   // Initialize first node:  
   aList->first = nullptr;  
  
   // Instantiate the class, build, and read the list:   
   ListBuilder^ myListBuilder = gcnew ListBuilder();  
   myListBuilder->BuildIt(aList);  
   myListBuilder->ReadIt(aList);  
}  
```  
  
```Output  
Building the list:  
0.1  
0.2  
0.3  
0.4  
0.5  
Reading nodes:  
0.5  
0.4  
0.3  
0.2  
0.1  
```  
  
## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>Vlastnosti, události, indexery a operátory v obecné třídy  
  
-   Vlastnosti, události, indexery a operátory můžete použít jako návratové hodnoty, parametrů nebo místní proměnné, jako např. kdy parametry typu nadřazených obecné třídy `ItemType` je parametr typu třídy:  
  
    ```  
    public ItemType MyProperty {}  
    ```  
  
-   Vlastnosti, události, indexery a operátory nelze sami nastavit parametry.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje deklarace vlastnost instance v rámci obecné třídy.  
  
```  
// generics_generic_properties1.cpp  
// compile with: /clr  
using namespace System;  
  
generic <typename ItemType>  
ref class MyClass {  
private:  
   property ItemType myField;  
  
public:  
   property ItemType MyProperty {  
      ItemType get() {  
         return myField;   
      }  
      void set(ItemType value) {  
         myField = value;  
      }  
   }  
};  
  
int main() {  
   MyClass<String^>^ c = gcnew MyClass<String^>();  
   MyClass<int>^ c1 = gcnew MyClass<int>();  
  
   c->MyProperty = "John";  
   c1->MyProperty = 234;  
  
   Console::Write("{0}, {1}", c->MyProperty, c1->MyProperty);  
}  
```  
  
```Output  
John, 234  
```  
  
## <a name="example"></a>Příklad  
 Další příklad ukazuje obecné třídy s událostí.  
  
```  
// generics_generic_with_event.cpp  
// compile with: /clr  
// Declare a generic class with an event and  
// invoke events.  
using namespace System;  
  
// declare delegates  
generic <typename ItemType>  
delegate void ClickEventHandler(ItemType);  
  
// generic class that defines events  
generic <typename ItemType>  
ref class EventSource {  
public:  
   // declare the event OnClick  
   event ClickEventHandler<ItemType>^ OnClick;   
   void FireEvents(ItemType item) {  
      // raises events  
      OnClick(item);  
   }  
};  
  
// generic class that defines methods that will called when  
// event occurs  
generic <typename ItemType>  
ref class EventReceiver {  
public:  
   void OnMyClick(ItemType item) {  
     Console::WriteLine("OnClick: {0}", item);  
   }  
};  
  
int main() {  
   EventSource<String^>^ MyEventSourceString =  
                   gcnew EventSource<String^>();  
   EventSource<int>^ MyEventSourceInt = gcnew EventSource<int>();  
   EventReceiver<String^>^ MyEventReceiverString =  
                   gcnew EventReceiver<String^>();  
   EventReceiver<int>^ MyEventReceiverInt = gcnew EventReceiver<int>();  
  
   // hook handler to event  
   MyEventSourceString->OnClick += gcnew ClickEventHandler<String^>(  
       MyEventReceiverString, &EventReceiver<String^>::OnMyClick);  
   MyEventSourceInt->OnClick += gcnew ClickEventHandler<int>(  
             MyEventReceiverInt, &EventReceiver<int>::OnMyClick);  
  
   // invoke events  
   MyEventSourceString->FireEvents("Hello");  
   MyEventSourceInt->FireEvents(112);  
  
   // unhook handler to event  
   MyEventSourceString->OnClick -= gcnew ClickEventHandler<String^>(  
        MyEventReceiverString, &EventReceiver<String^>::OnMyClick);  
   MyEventSourceInt->OnClick -= gcnew ClickEventHandler<int>(  
        MyEventReceiverInt, &EventReceiver<int>::OnMyClick);  
}  
```  
  
## <a name="generic-structs"></a>Obecné struktury  
 Pravidla pro deklarování a použití obecné struktur jsou stejné jako v případě obecné třídy, s výjimkou rozdíly v uvedených v referenční příručka jazyka Visual C++.  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje obecná struktura, `MyGenStruct`, s jedním polem `myField`a přiřadí hodnoty různých typů (`int`, **dvojité**, **řetězec ^**) do tohoto pole.  
  
```  
// generics_generic_struct1.cpp  
// compile with: /clr  
using namespace System;  
  
generic <typename ItemType>  
ref struct MyGenStruct {  
public:  
   ItemType myField;  
  
   ItemType AssignValue(ItemType item) {  
      myField = item;  
      return myField;  
   }  
};  
  
int main() {  
   int myInt = 123;  
   MyGenStruct<int>^ myIntObj = gcnew MyGenStruct<int>();  
   myIntObj->AssignValue(myInt);  
   Console::WriteLine("The field is assigned the integer value: {0}",  
            myIntObj->myField);  
  
   double myDouble = 0.123;  
   MyGenStruct<double>^ myDoubleObj = gcnew MyGenStruct<double>();  
   myDoubleObj->AssignValue(myDouble);  
   Console::WriteLine("The field is assigned the double value: {0}",  
            myDoubleObj->myField);  
  
   String^ myString = "Hello Generics!";  
   MyGenStruct<String^>^ myStringObj = gcnew MyGenStruct<String^>();  
   myStringObj->AssignValue(myString);  
   Console::WriteLine("The field is assigned the string: {0}",  
            myStringObj->myField);  
}  
```  
  
```Output  
The field is assigned the integer value: 123  
The field is assigned the double value: 0.123  
The field is assigned the string: Hello Generics!  
```  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy](../windows/generics-cpp-component-extensions.md)