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
ms.openlocfilehash: 71850807f6332f31195ef9bafbd9468f48cb6fb3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041423"
---
# <a name="generic-classes-ccli"></a>Obecné třídy (C++/CLI)

Obecná třída je deklarována pomocí následující tvar:

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

Ve výše uvedené syntaxe se používají následující termíny:

*atributy*<br/>
(Volitelné) Další informace o deklarativní. Další informace o atributu třídy a atributy naleznete v tématu atributy.

*klíč třídy*<br/>
Buď **třídy** nebo **typename**

*Typ – parametr-identifikátory*, čárkami oddělený seznam identifikátorů určující názvy parametrů typu.

*constraint-clauses*<br/>
Seznam (nikoli oddělený čárkami) **kde** klauzule určující omezení pro parametry typu. Má podobu:

> **kde** *identifikátor typu parametru* **:** *seznam omezení***...**

*seznam omezení*<br/>
*Třída nebo rozhraní*[`,` *...* ]

*Modifikátory dostupnosti*<br/>
Modifikátory dostupnosti pro obecná třída. Prostředí Windows Runtime je jediný povolený modifikátor **privátní**. Pro modul common language runtime, jsou povolené modifikátory **privátní** a **veřejné**.

*identifikátor*<br/>
Název obecná třída libovolný platný identifikátor C++.

*modifikátory*<br/>
(Volitelné) Povolené modifikátory zahrnují **zapečetěné** a **abstraktní**.

*Base-list*<br/>
Seznam obsahující jednu základní třídu a žádné implementovaná rozhraní, všechny oddělených čárkami.

*class-body*<br/>
Text třídu obsahující pole, členské funkce atd.

*deklarátory*<br/>
Deklarace proměnných tohoto typu. Příklad: `^` *identifikátor*[`,` ...]

Je možné deklarovat obecné třídy takovéto (Všimněte si, že klíčové slovo **třídy** může být použita místo **typename**). V tomto příkladu `ItemType`, `KeyType` a `ValueType` jsou neznámé typy, které jsou uvedeny v místě, kde typ. `HashTable<int, int>` konstruovaný typ obecného typu je `HashTable<KeyType, ValueType>`. Počet různých sestavené typy lze zkonstruovat z jednoho obecného typu. Sestavené typy vytvořený z obecné třídy jsou zpracovány stejně jako jakýkoli jiný typ referenční třídy.

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

Oba typy hodnot (buď předdefinované typy, jako **int** nebo **double**, nebo hodnotu definovanou uživatelem typy) a typy odkazů může sloužit jako argument obecného typu. Syntaxe v definici obecného je stejný bez ohledu na to. Neznámý typ je zpracováván syntakticky, jako by šlo typ odkazu. Modul runtime je však možné, která určí, zda skutečně používá typ je typ hodnoty a nahraďte příslušné generovaný kód pro přímý přístup ke členům. Hodnota typy použité jako argumenty obecného typu nejsou v poli a proto není trpí snížení výkonu, které jsou přidružené k zabalení. By měl být použit v těle obecné syntaxe `T^` a `->` místo `.`. Jakékoli použití [ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md) pro typ parametru se správně interpretovat modulem runtime jako jednoduchým vytvořením hodnotového typu Pokud typ argumentu je typ hodnoty.

Můžete také deklarovat obecná třída s atributem [omezení parametrů obecných typů (C + +/ CLI)](constraints-on-generic-type-parameters-cpp-cli.md) na typy, které lze použít pro parametr typu. V následujícím příkladu používá libovolný typ pro `ItemType` musí implementovat `IItem` rozhraní. Pokus o použití **int**, například která neimplementuje `IItem`, byste mohli vytvořit chybu v době kompilace, protože argumentů typu nevyhovuje omezením.

```cpp
// generic_classes_2.cpp
// compile with: /clr /c
interface class IItem {};
generic <class ItemType>
where ItemType : IItem
ref class Stack {};
```

Obecné třídy v oboru názvů stejný nemohou být přetíženy pouze změnou číslo nebo typy parametrů typu. Ale pokud každá třída nachází jiný obor názvů, mohou být přetíženy. Představte si třeba následující dvě třídy `MyClass` a `MyClass<ItemType>`, v oborech názvů `A` a `B`. Dvě třídy mohou být přetíženy pak v oboru názvů třetí C:

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

Základní třídu a základní rozhraní nemůže být parametry typu. Základní třídy však může zahrnovat parametr typu jako argument, jako v následujících případech:

```cpp
// generic_classes_4.cpp
// compile with: /clr /c
generic <typename ItemType>
interface class IInterface {};

generic <typename ItemType>
ref class MyClass : IInterface<ItemType> {};
```

Konstruktory a destruktory jsou spouštěny jednou pro každou instanci objektu (obvyklým); statické konstruktory jsou spouštěny jednou pro každý konstruovaný typ.

## <a name="fields-in-generic-classes"></a>Pole v obecné třídy

Tato část ukazuje použití statických polí v obecné třídy a instance.

### <a name="instance-variables"></a>Proměnné instance

Proměnné instance obecné třídy můžete mít typy a proměnné inicializátory, které zahrnují všechny parametry typu z nadřazené třídy.

## <a name="example"></a>Příklad

V následujícím příkladu tři různé instance obecné třídy MyClass\<ItemType >, jsou vytvořeny pomocí příslušného typu argumentů (**int**, **double**a **řetězec**).

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

Vytvoření nové obecného typu se nové instance všechny statické proměnné se vytvářejí a jakékoli statického konstruktoru pro daný typ je.

Statické proměnné můžete použít všechny parametry typu z nadřazené třídy.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití statické položky a statický konstruktor v rámci obecné třídy.

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

## <a name="methods-in-generic-classes"></a>Metody v obecné třídy

Metody v obecné třídy mohou být obecný. Obecné metody se implicitně parametrizovány parametrem typu třídy.

Následující zvláštní pravidla platí pro metody v rámci obecných tříd:

- Metody v obecné třídy můžete použít parametry typu jako parametry, návratových typů nebo lokální proměnné.

- Metody v obecné třídy můžete použít otevřeno nebo zavřeno sestavené typy jako parametry, návratových typů nebo lokální proměnné.

### <a name="non-generic-methods-in-generic-classes"></a>Neobecné metody v obecné třídy

Metody v obecných tříd, které mají parametry žádné další typ se obvykle označují jako neobecnou i když jsou implicitně parametrizován nadřazené obecné třídy.

Podpis neobecnou metodu může obsahovat minimálně jeden parametr typu nadřazené třídy, buď přímo, nebo v otevřeném typu vytvořený. Příklad:

`void MyMethod(MyClass<ItemType> x) {}`

Text z těchto metod můžete také použít tyto parametry typu.

## <a name="example"></a>Příklad

Následující příklad deklaruje neobecnou metodu `ProtectData`, uvnitř obecných tříd `MyClass<ItemType>`. Metoda používá parametr typu třídy `ItemType` v podpisu v otevřeném typu vytvořený.

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

## <a name="generic-methods-in-generic-classes"></a>Obecné metody v obecné třídy

Je možné deklarovat obecných metod v obecných a neobecných třídách. Příklad:

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

Neobecnou metodu je stále generická v tom smyslu, že je parametrizovány parametrem typu třídy, ale nemá žádné parametry další typu.

Všechny typy metod v obecné třídy může být obecné, včetně statické, instance a virtuální metody.

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

## <a name="using-nested-types-in-generic-classes"></a>Použití vnořených typů v obecné třídy

Stejně jako běžné třídy lze deklarovat jiné typy uvnitř obecné třídy. Deklarace vnořených tříd je implicitně parametrizován parametry typu deklarace vnější třídy. Proto odlišné vnořené třídy je definována pro každý vytvořený vnějšího typu. Například v deklaraci

```cpp
// generic_classes_5.cpp
// compile with: /clr /c
generic <typename ItemType>
ref struct Outer {
   ref class Inner {};
};
```

Typ `Outer<int>::Inner` není stejný jako typ `Outer<double>::Inner`.

Stejně jako u obecných metod v obecné třídy lze definovat další typy parametrů pro vnořeného typu. Pokud používáte stejné názvy parametrů typů ve třídě vnitřní a vnější, vnitřní typ parametru skryje parametr vnějšího typu.

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

Protože neexistuje žádný způsob, jak odkazovat na parametr typu vnějšího, kompilátor vytvoří upozornění v této situaci.

Když jsou pojmenovány konstruovaný vnořených obecných typech, parametr typu vnějšího typu není součástí seznam parametrů typu pro typ vnitřní i v případě, že vnitřní typ implicitně parametrizován parametr typu vnějšího typu. Ve výše uvedeném případě by se název konstruovaný typ `Outer<int>::Inner<string>`.

Následující příklad ukazuje vytváření a čtení odkazovaného seznamu pomocí vnořené typy obecných tříd.

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

## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>Vlastnosti, události, indexery a operátory v obecné třídy

- Vlastnosti, události, indexery a operátoři mohou použít parametry typu Obecné ohraničující třídy jako návratové hodnoty, parametry nebo lokální proměnné, třeba při `ItemType` je parametr typu třídy:

    ```cpp
    public ItemType MyProperty {}
    ```

- Vlastnosti, události, indexery a operátory nelze sami parametrizovat.

## <a name="example"></a>Příklad

Tento příklad ukazuje deklarace vlastnost instance v rámci obecné třídy.

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

Další příklad ukazuje obecnou třídu s událostí.

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

Pravidla pro deklarování a použití obecných struktur jsou stejné jako u obecných tříd, s výjimkou rozdílů, které jste si poznamenali v referenční dokumentace jazyka Visual C++.

## <a name="example"></a>Příklad

Následující příklad deklaruje o obecnou strukturu `MyGenStruct`, s jedním polem `myField`a přiřadí hodnoty různých typů (**int**, **double**, `String^`) do tohoto pole.

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

## <a name="see-also"></a>Viz také:

[Obecné typy](generics-cpp-component-extensions.md)