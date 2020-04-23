---
title: Hodnotové třídy a struktury (C++/CX)
ms.date: 12/30/2016
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
ms.openlocfilehash: 4a4897f0a3b5c95ffb58e5c9666a2d764d71b3ec
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752891"
---
# <a name="value-classes-and-structs-ccx"></a>Hodnotové třídy a struktury (C++/CX)

*Struktura hodnoty* nebo *třída hodnot* je pod kompatibilní se modulem Windows Runtime ("stará datová struktura plain"). Má pevnou velikost a skládá se pouze z polí; na rozdíl od třídy ref nemá žádné vlastnosti.

Následující příklady ukazují, jak deklarovat a inicializovat struktury hodnot.

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

Pokud je proměnná typu hodnoty přiřazena jiné proměnné, hodnota se zkopíruje tak, aby každá z těchto dvou proměnných má vlastní kopii dat. *Struktura hodnoty* je struktura pevné velikosti, která obsahuje pouze veřejná `value struct` datová pole a je deklarována pomocí klíčového slova.

Hodnota *třídy* je `value struct` stejně jako kromě toho, že jeho pole musí být explicitně veřejné usnadnění přístupu. Deklaruje se `value class` pomocí klíčového slova.

Hodnota struktura nebo třída hodnot může obsahovat jako pole pouze `Platform::String^`základní číselné typy, třídy výčtu nebo [Platform::IBox \<T>^](../cppcx/platform-ibox-interface.md) kde T je číselný typ nebo třída výčtu nebo třída nebo struktura. Pole `IBox<T>^` může mít hodnotu `nullptr`– to je způsob, jakým C++ implementuje koncept typů hodnot s *možnou hodnotou null*.

Hodnota třídy nebo struktury hodnoty, která obsahuje `Platform::String^` nebo `memcpy` `IBox<T>^` typ jako člen není -nelze.

Vzhledem k `value class` tomu, že všechny členy nebo `value struct` jsou veřejné a jsou vydávány do metadat, standardní typy Jazyka C++ nejsou povoleny jako členy. To se liší od ref `private` třídy, které mohou obsahovat nebo `internal` standardní C++ typy..

Následující fragment kódu deklaruje `Coordinates` `City` a typy jako struktury hodnoty. Všimněte si, `City` že jeden `GeoCoordinates` z datových členů je typ. A `value struct` může obsahovat jiné struktury hodnot jako členy.

[!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]

## <a name="parameter-passing-for-value-types"></a>Předávání parametrů pro typy hodnot

Pokud máte typ hodnoty jako parametr funkce nebo metody, je obvykle předán hodnotou. U větších objektů to může způsobit potíže s výkonem. Ve Visual Studio2013 a starší typy hodnot v Jazyce C++/CX byly vždy předány hodnotou. V sadě Visual Studio 2015 a novější můžete předat typy hodnot odkazem nebo hodnotou.

Chcete-li deklarovat parametr, který předává typ hodnoty podle hodnoty, použijte kód takto:

```cpp
void Method1(MyValueType obj);
```

Chcete-li deklarovat parametr, který předává typ hodnoty odkazem, použijte referenční symbol (&), jako v následujícím:

```cpp
void Method2(MyValueType& obj);
```

Typ uvnitř Method2 je odkaz na MyValueType a funguje stejným způsobem jako typ odkazu ve standardním jazyce C++.

Při volání Method1 z jiného jazyka, jako je C#, není nutné použít `ref` nebo `out` klíčové slovo. Při volání Method2 použijte `ref` klíčové slovo.

```
Method2(ref obj);
```

Symbol ukazatele (*) můžete také použít k předání typu hodnoty odkazem. Chování s ohledem na volající v jiných jazycích je stejný `ref` (volající v jazyce C# použít klíčové slovo), ale v metodě je typ ukazatel na typ hodnoty.

## <a name="nullable-value-types"></a>Typy hodnot s povolenou hodnotou Null

Jak již bylo zmíněno dříve, třída hodnoty nebo struktura hodnoty může mít pole typu [Platform::IBox\<T>^](../cppcx/platform-ibox-interface.md)– například . `IBox<int>^` Takové pole může mít libovolnou číselnou `int` hodnotu, která je `nullptr`platná pro typ, nebo může mít hodnotu . Pole s možnou hodnotou null můžete předat jako argument metodě, jejíž parametr je deklarován jako volitelný, nebo kdekoli jinde, kde typ hodnoty nemusí mít hodnotu.

Následující příklad ukazuje, jak inicializovat strukturu, která má pole s možnou hodnotou null.

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

Samotná struktura hodnoty může být prohlášena za neplatnou stejným způsobem, jak je znázorněno zde:

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

## <a name="see-also"></a>Viz také

[Systém typů (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)<br/>
[Referenční třídy a struktury (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)
