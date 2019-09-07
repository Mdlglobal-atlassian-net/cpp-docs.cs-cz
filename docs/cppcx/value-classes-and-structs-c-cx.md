---
title: Třídy hodnot a struktury (C++/CX)
ms.date: 12/30/2016
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
ms.openlocfilehash: 3340c5e387dc58ddcb5348cdc041a58840463995
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740937"
---
# <a name="value-classes-and-structs-ccx"></a>Třídy hodnot a struktury (C++/CX)

*Struktura hodnot* nebo *hodnotová třída* je kompatibilní s prostředí Windows Runtime pod ("jednoduchá stará data struktura"). Má pevnou velikost a skládá se pouze z polí; na rozdíl od ref class nemá žádné vlastnosti.

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

Je-li proměnná typu hodnoty přiřazena jiné proměnné, je hodnota zkopírována tak, aby každá ze dvou proměnných měla svou vlastní kopii dat. Struktura *hodnot* je struktura s pevnou velikostí, která obsahuje pouze veřejná datová pole a je deklarována pomocí `value struct` klíčového slova.

*Hodnotová třída* je stejně jako a `value struct` s tím rozdílem, že její pole musí explicitně předávat veřejné přístupnost. Je deklarována pomocí `value class` klíčového slova.

Struktura hodnot nebo hodnotová třída může obsahovat jako pole pouze základní číselné typy, třídy výčtu, `Platform::String^`nebo [Platform:: iBox \<T > ^](../cppcx/platform-ibox-interface.md) , kde T je číselný typ nebo třída výčtu nebo třída hodnoty nebo struktura. Pole může mít `nullptr`hodnotu – to je způsob, jakým C++ implementuje koncept *typů hodnot s možnou hodnotou null.* `IBox<T>^`

Struktura hodnot třídy nebo hodnoty, která obsahuje `Platform::String^` typ nebo `IBox<T>^` `memcpy`jako člen, není možné.

Vzhledem k tomu, že `value class` všechny `value struct` členy nebo jsou veřejné a jsou generovány do metadat C++ , standardní typy nejsou povoleny jako členy. To se liší od referenčních tříd, které mohou `private` obsahovat `internal` nebo C++ standardní typy.

Následující fragment kódu deklaruje `Coordinates` typy a `City` jako struktury hodnot. Všimněte si, že jeden `City` z datových členů `GeoCoordinates` je typ. `value struct` Může obsahovat jiné struktury hodnot jako členy.

[!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]

## <a name="parameter-passing-for-value-types"></a>Předávání parametrů pro typy hodnot

Pokud máte typ hodnoty jako funkci nebo parametr metody, je obvykle předána hodnotou. U větších objektů to může způsobit problémy s výkonem. V jazyce Visual Studio2013 a dřívějších byly hodnoty typů C++v/CX vždy předány hodnotou. V aplikaci Visual Studio 2015 a novějších lze typy hodnot předat podle odkazu nebo podle hodnoty.

Chcete-li deklarovat parametr, který předává hodnotový typ podle hodnoty, použijte kód podobný následujícímu:

```
void Method1(MyValueType obj);
```

Chcete-li deklarovat parametr, který předává hodnotový typ odkazem, použijte symbol Reference (&), jak je uvedeno níže:

```
void Method2(MyValueType& obj);
```

Typ uvnitř Method2 je odkaz na MyValueType a funguje stejným způsobem jako typ odkazu ve standardu C++.

Pokud voláte – metoda1 z jiného jazyka, například C#, není nutné použít `ref` klíčové slovo or. `out` Při volání Method2 použijte `ref` klíčové slovo.

```
Method2(ref obj);
```

Můžete také použít symbol ukazatele (*) k předání typu hodnoty odkazem. Chování s ohledem na volající v jiných jazycích je stejné (volající v C# použití `ref` klíčového slova), ale v metodě je typ ukazatel na typ hodnoty.

## <a name="nullable-value-types"></a>Typy hodnot s možnou hodnotou null

Jak bylo zmíněno dříve, struktura hodnot třídy nebo hodnoty může mít pole typu [Platform:: iBox\<T > ^](../cppcx/platform-ibox-interface.md) `IBox<int>^`, například. Takové pole může mít libovolnou číselnou hodnotu, která je pro tento `int` typ platná, nebo může mít `nullptr`hodnotu. Pole s možnou hodnotou null můžete předat jako argument metodě, jejíž parametr je deklarován jako volitelný, nebo kdekoli jinde, že typ hodnoty není požadován pro hodnotu.

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

Samotnou strukturu hodnoty lze nastavit jako null, jak je znázorněno zde:

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
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)<br/>
[Referenční třídy a struktury (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)
