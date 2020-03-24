---
title: Obecné třídy (C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
ms.openlocfilehash: 78f4bf3abb98aab5e626e8ada538a22bdbca2912
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172357"
---
# <a name="generic-classes-ccli"></a>Obecné třídy (C++/CLI)

Obecná třída je deklarována pomocí následujícího formuláře:

## <a name="syntax"></a>Syntaxe

```cpp
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

Ve výše uvedené syntaxi jsou použity následující výrazy:

*atribut*<br/>
Volitelné Další deklarativní informace. Další informace o atributech a třídách atributů naleznete v tématu Attributes.

*klíč třídy*<br/>
Buď **Class** , nebo **TypeName**

*identifikátorů parametrů typu*, čárkami oddělený seznam identifikátorů určujících názvy parametrů typu.

*klauzule CONSTRAINT*<br/>
Seznam (neoddělený čárkami) klauzulí **WHERE, které** určují omezení pro parametry typu. Má podobu:

> **kde** *Type-Parameter-Identifier* **:** *Constraint-list*  **...**

*omezení – seznam*<br/>
*třída nebo rozhraní*[`,` *...* ]

*usnadnění – modifikátory*<br/>
Modifikátory dostupnosti pro obecnou třídu. Pro prostředí Windows Runtime je jediným povoleným modifikátorem **privátní**. Pro modul CLR (Common Language Runtime) jsou povolené modifikátory **soukromé** a **veřejné**.

*RID*<br/>
Název obecné třídy, libovolný platný C++ identifikátor.

*modifikátory*<br/>
Volitelné Povolené modifikátory zahrnují **zapečetěné** a **abstraktní**.

*seznam Base-list*<br/>
Seznam obsahující jednu základní třídu a všechna implementovaná rozhraní, která jsou oddělená čárkami.

*tělo třídy*<br/>
Tělo třídy, obsahující pole, členské funkce atd.

*deklarátory*<br/>
Deklarace všech proměnných tohoto typu. Příklad: `^`*identifikátor*[`,`...]

Můžete deklarovat obecné třídy, jako jsou ty (Všimněte si, že **Třída** klíčového slova se dá použít místo **TypeName**). V tomto příkladu `ItemType`, `KeyType` a `ValueType`, jsou neznámé typy, které jsou zadány v místě, kde typ. `HashTable<int, int>` je konstruovaný typ `HashTable<KeyType, ValueType>`obecného typu. Řadu různých konstruovaných typů lze vytvořit z jednoho obecného typu. Vytvořené typy vytvořené z obecných tříd jsou zpracovány jako jakýkoli jiný typ ref class.

```cpp
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

Oba typy hodnot (buď předdefinované typy typu **int** nebo **Double**, nebo uživatelsky definované hodnoty) a typy odkazů mohou být použity jako argument obecného typu. Syntaxe v rámci obecné definice je stejná bez ohledu na ni. Syntakticky, neznámý typ je považován za typ odkazu. Modul runtime však dokáže určit, zda je typ, který je skutečně použit, typ hodnoty a nahradí příslušný generovaný kód přímým přístupem ke členům. Typy hodnot použité jako argumenty obecného typu nejsou v krabici, takže neutrpěly snížení výkonu spojené se zabalením. Syntaxe použitá v těle obecného by měla být `T^` a `->` namísto `.`. Jakékoli použití [ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md) pro parametr typu bude vhodným způsobem interpretováno modulem runtime jako jednoduché vytvoření typu hodnoty, je-li argumentem typu hodnotový typ.

Můžete také deklarovat obecnou třídu s [omezeními na parametry obecného typu (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md) pro typy, které lze použít pro parametr typu. V následujícím příkladu jakýkoli typ použitý pro `ItemType` musí implementovat rozhraní `IItem`. Pokus o použití **int**, například, který neimplementuje `IItem`, by vytvořil chybu při kompilaci, protože argument typu nesplňuje omezení.

```cpp
// generic_classes_2.cpp
// compile with: /clr /c
interface class IItem {};
generic <class ItemType>
where ItemType : IItem
ref class Stack {};
```

Obecné třídy ve stejném oboru názvů nelze přečítat pouze změnou čísla nebo typů parametrů typu. Nicméně pokud každá třída žije v jiném oboru názvů, mohou být přetíženy. Zvažte například následující dvě třídy `MyClass` a `MyClass<ItemType>`v oborech názvů `A` a `B`. Dvě třídy pak mohou být přetíženy v třetím oboru názvů C:

```cpp
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

Základní třídu a základní rozhraní nemůžou být parametry typu. Základní třída však může zahrnovat parametr typu jako argument, jako v následujícím případě:

```cpp
// generic_classes_4.cpp
// compile with: /clr /c
generic <typename ItemType>
interface class IInterface {};

generic <typename ItemType>
ref class MyClass : IInterface<ItemType> {};
```

Konstruktory a destruktory jsou spouštěny jednou pro každou instanci objektu (jako obvykle); statické konstruktory jsou spouštěny jednou pro každý konstruovaný typ.

## <a name="fields-in-generic-classes"></a>Pole v obecných třídách

Tato část ukazuje použití instance a statických polí v obecných třídách.

### <a name="instance-variables"></a>Proměnné instance

Proměnné instance obecné třídy mohou mít typy a proměnné inicializátorů, které obsahují parametry typu z nadřazené třídy.

## <a name="example"></a>Příklad

V následujícím příkladu jsou vytvořeny tři různé instance obecné třídy MyClass\<ItemType > pomocí příslušných argumentů typu (**int**, **Double**a **String**).

```cpp
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

Při vytváření nového obecného typu se vytvoří nové instance všech statických proměnných a spustí se libovolný statický konstruktor pro tento typ.

Statické proměnné mohou používat libovolné parametry typu z ohraničující třídy.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití statických polí a statického konstruktoru v rámci obecné třídy.

```cpp
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

## <a name="methods-in-generic-classes"></a>Metody v obecných třídách

Metody v obecných třídách mohou být obecně obecné; neobecné metody budou implicitně parametrizované parametrem typu třídy.

Následující zvláštní pravidla platí pro metody v rámci obecných tříd:

- Metody v obecných třídách mohou používat parametry typu jako parametry, návratové typy nebo místní proměnné.

- Metody v obecných třídách mohou používat Open nebo Closed konstruované typy jako parametry, návratové typy nebo místní proměnné.

### <a name="non-generic-methods-in-generic-classes"></a>Neobecné metody v obecných třídách

Metody v obecných třídách, které nemají žádné další parametry typu, se obvykle označují jako neobecné, přestože jsou implicitně parametrizované ohraničující obecnou třídou.

Podpis neobecné metody může obsahovat jeden nebo více parametrů typu ohraničující třídy, a to buď přímo, nebo v otevřeném konstruovaném typu. Příklad:

`void MyMethod(MyClass<ItemType> x) {}`

Tělo těchto metod může také používat tyto parametry typu.

## <a name="example"></a>Příklad

Následující příklad deklaruje neobecnou metodu, `ProtectData`, uvnitř obecné třídy, `MyClass<ItemType>`. Metoda používá parametr typu třídy `ItemType` v jeho podpisu v otevřeném konstruovaném typu.

```cpp
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

## <a name="generic-methods-in-generic-classes"></a>Obecné metody v obecných třídách

Obecné metody lze deklarovat jak v obecných, tak i v neobecných třídách. Příklad:

## <a name="example"></a>Příklad

```cpp
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

Neobecná metoda je stále obecná v tom smyslu, že je parametrizovaná parametrem typu třídy, ale nemá žádné další parametry typu.

Všechny typy metod v obecných třídách mohou být obecné, včetně statických, instancí a virtuálních metod.

## <a name="example"></a>Příklad

Následující příklad ukazuje deklaraci a použití obecných metod v rámci obecných tříd:

```cpp
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

## <a name="using-nested-types-in-generic-classes"></a>Použití vnořených typů v obecných třídách

Stejně jako u běžných tříd můžete deklarovat jiné typy uvnitř obecné třídy. Deklarace vnořené třídy je implicitně Parametrizovaná parametry typu vnější deklarace třídy. Proto je pro každý vytvořený vnější typ definována samostatná vnořená třída. Například v deklaraci

```cpp
// generic_classes_5.cpp
// compile with: /clr /c
generic <typename ItemType>
ref struct Outer {
   ref class Inner {};
};
```

Typ `Outer<int>::Inner` není stejný jako typ `Outer<double>::Inner`.

Stejně jako u obecných metod v obecných třídách lze definovat další parametry typu pro vnořený typ. Použijete-li stejné názvy parametrů typů ve vnitřní a vnější třídě, parametr vnitřního typu bude skrývat parametr vnějšího typu.

```cpp
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

Vzhledem k tomu, že neexistuje žádný způsob, jak odkazovat na parametr vnějšího typu, kompilátor vytvoří v této situaci upozornění.

Při vytvoření vnořených obecných typů jsou pojmenovány parametry typu pro vnější typ nezahrnuté v seznamu parametrů typu pro vnitřní typ, i když je vnitřní typ implicitně parametrizovaný parametrem typu vnějšího typu. Ve výše uvedeném případě by byl název konstruovaného typu `Outer<int>::Inner<string>`.

Následující příklad ukazuje sestavení a čtení propojeného seznamu pomocí vnořených typů v obecných třídách.

## <a name="example"></a>Příklad

```cpp
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

## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>Vlastnosti, události, indexery a operátory v obecných třídách

- Vlastnosti, události, indexery a operátory mohou použít parametry typu nadřazené obecné třídy jako návratové hodnoty, parametry nebo lokální proměnné, jako například, když `ItemType` je parametr typu třídy:

    ```cpp
    public ItemType MyProperty {}
    ```

- Vlastnosti, události, indexery a operátory nelze nastavovat jako parametrizované.

## <a name="example"></a>Příklad

Tento příklad ukazuje deklarace vlastnosti instance v rámci obecné třídy.

```cpp
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

Následující příklad ukazuje obecnou třídu s událostí.

```cpp
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

Pravidla pro deklarování a použití obecných struktur jsou stejná jako u obecných tříd, s výjimkou rozdílů uvedených v referenčních informacích C++ o jazyce jazyka Visual.

## <a name="example"></a>Příklad

Následující příklad deklaruje obecnou strukturu, `MyGenStruct`, s jedním polem, `myField`a přiřazuje hodnoty různých typů (**int**, **Double**, `String^`) do tohoto pole.

```cpp
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

[Obecné typy](generics-cpp-component-extensions.md)
