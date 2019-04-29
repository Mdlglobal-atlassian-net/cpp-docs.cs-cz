---
title: Hodnotové třídy a struktury (C++/CX)
ms.date: 12/30/2016
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
ms.openlocfilehash: 5b9b50ba7200439e9ce648c53d52ce37226f61d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384982"
---
# <a name="value-classes-and-structs-ccx"></a>Hodnotové třídy a struktury (C++/CX)

A *hodnotu struktury* nebo *hodnotu třídy* je Windows Runtime kompatibilní POD ("prostý stará datová struktura"). Má pevnou velikost a skládá se z pole. na rozdíl od ref class nemá žádné vlastnosti.

Následující příklady ukazují, jak deklarovat a inicializovat struktuře hodnot.

```

// in mainpage.xaml.h:
    value struct TestStruct
    {
        Platform::String^ str;
        int i;
    };

    value struct TestStruct2
    {
        TestStruct ts;
        Platform::String^ str;
        int i;
    };

// in mainpage.cpp:
    // Initialize a value struct with an int and String
    TestStruct ts = {"I am a TestStruct", 1};

    // Initialize a value struct that contains
    // another value struct, an int and a String
    TestStruct2 ts2 = {{"I am a TestStruct", 1}, "I am a TestStruct2", 2};

    // Initialize value struct members individually.
    TestStruct ts3;
    ts3.i = 108;
    ts3.str = "Another way to init a value struct.";
```

Když proměnné hodnotového typu je přiřazena do jiné proměnné, hodnota je zkopírována, tak, aby každý dvě proměnné, které má svou vlastní kopii dat. A *hodnotu struktury* je struktura pevné velikosti, která obsahuje pouze veřejné polí a je deklarována pomocí `value struct` – klíčové slovo.

A *hodnotu třídy* je stejně jako `value struct` s tím rozdílem, že jeho musí být explicitně polím přístupnost public. Je deklarovaná příkazem using `value class` – klíčové slovo.

Hodnota třídy nebo struktury hodnota může obsahovat pouze základní číselné typy, výčet tříd, polí `Platform::String^`, nebo [Platform::ibox – \<T > ^](../cppcx/platform-ibox-interface.md) kde T je číselný typ nebo výčet. třída nebo hodnota třídy nebo struktury. `IBox<T>^` Pole může mít hodnotu `nullptr`– Toto je způsob implementace C++ konceptu *typy s možnou hodnotou*.

Hodnota třídy nebo struktury hodnota obsahuje `Platform::String^` nebo `IBox<T>^` typu jako člen není `memcpy`– možnost.

Protože všechny členy `value class` nebo `value struct` jsou veřejné a vyhoví se emitovat do metadat, standardní C++ typy nejsou povolené jako členy. Tím se liší od referenční třídy, které mohou obsahovat `private` nebo `internal` standardní typy C++...

Následující fragment kódu deklaruje `Coordinates` a `City` typy jako hodnota struktury. Všimněte si, že jeden z `City` je datové členy `GeoCoordinates` typu. A `value struct` může obsahovat jiné hodnoty struktury jako členy.

[!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]

## <a name="parameter-passing-for-value-types"></a>Předávání pro typy hodnot parametrů

Pokud máte jako parametr funkce nebo metoda typ hodnoty, je obvykle předávána podle hodnoty. Pro větší objekty to může způsobit problémy s výkonem. Typy v hodnot Visual Studio2013 a dřívějších verzí C++/CX byly vždy předán podle hodnoty. V sadě Visual Studio 2015 a novější můžete předat typy hodnot, podle odkazu nebo podle hodnoty.

Chcete-li deklarovat parametr, který předává typ hodnoty podle hodnoty, použijte kód podobný tomuto:

```
void Method1(MyValueType obj);
```

Chcete-li deklarovat parametr, který předává hodnotový typ podle odkazu, použijte odkaz symbol (&), viz následující příklad:

```
void Method2(MyValueType& obj);
```

Typ uvnitř Method2 je odkaz na MyValueType a funguje stejně jako s typem odkazu ve standardním jazyce C++.

Při volání z jiného jazyka, jako je C# – metoda1 nemusíte používat `ref` nebo `out` – klíčové slovo. Při volání Method2 použít `ref` – klíčové slovo.

```
Method2(ref obj);
```

Ukazatel symbol (*) můžete použít také k předání typu hodnoty podle odkazu. Chování s ohledem na volajícím v jiných jazycích je stejný (volající C# používá `ref` – klíčové slovo), ale v metodě, typ je ukazatel na typ hodnoty.

## <a name="nullable-value-types"></a>Typy s možnou hodnotou Null

Jak už bylo zmíněno dříve, hodnotová třída nebo struktura hodnota může mít pole typu [Platform::ibox –\<T > ^](../cppcx/platform-ibox-interface.md)– například `IBox<int>^`. Toto pole může mít číselnou hodnotu, která platí pro `int` typ, nebo může mít hodnotu `nullptr`. Pole s možnou hodnotou Null lze předat jako argument na metodu, jejíž parametr je deklarovaný jako nepovinný nebo kdekoli jinde, který není hodnotový typ musí mít hodnotu.

Následující příklad ukazuje, jak inicializovat struktura, která obsahuje pole, s možnou hodnotou Null.

```
public value struct Student
{
    Platform::String^ Name;
    int EnrollmentYear;
    Platform::IBox<int>^ GraduationYear; // Null if not yet graduated.
};
//To create a Student struct, one must populate the nullable type.
MainPage::MainPage()
{
    InitializeComponent();

    Student A;
    A.Name = "Alice";
    A.EnrollmentYear = 2008;
    A.GraduationYear = ref new Platform::Box<int>(2012);

    Student B;
    B.Name = "Bob";
    B.EnrollmentYear = 2011;
    B.GraduationYear = nullptr;

    IsCurrentlyEnrolled(A);
    IsCurrentlyEnrolled(B);
}
bool MainPage::IsCurrentlyEnrolled(Student s)
{
    if (s.GraduationYear == nullptr)
    {
        return true;
    }
    return false;
}
```

Hodnota struktury samotné se dají vytvořit s možnou hodnotou Null stejným způsobem, jak je znázorněno zde:

```

public value struct MyStruct
{
public:
    int i;
    Platform::String^ s;
};

public ref class MyClass sealed
{
public:
    property Platform::IBox<MyStruct>^ myNullableStruct;
};
```

## <a name="see-also"></a>Viz také:

[Systém typů (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)<br/>
[Referenční třídy a struktury (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)
