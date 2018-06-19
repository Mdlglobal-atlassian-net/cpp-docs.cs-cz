---
title: Hodnota třídy a struktury (C + +/ CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b623e706fae0dfd8fca6b9aaf217e76b27dbbda
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090710"
---
# <a name="value-classes-and-structs-ccx"></a>Hodnota třídy a struktury (C + +/ CX)
A *hodnotu struktura* nebo *třídy hodnoty* je Windows Runtime kompatibilní POD ("prostý původní struktura dat"). To má pevnou velikost a se skládá z pole pouze; na rozdíl od ref třídu má žádné vlastnosti.  
  
 Následující příklady ukazují, jak deklarace a inicializace struktury hodnotu.  
  
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
  
 Pokud proměnná typ hodnoty je přiřazen jiné proměnné, hodnota je kopírovat, tak, aby každý dvě proměnné, které má svou vlastní kopii dat. A *hodnotu struktura* je struktura pevné velikosti, která obsahuje pouze veřejný datová pole a je deklarovaný s použitím `value struct` – klíčové slovo.  
  
 A *třídy hodnoty* je podobně jako `value struct` s tím rozdílem, že jeho pole musí být explicitně poskytnut veřejnou dostupnost. Je deklarovaný s použitím `value class` – klíčové slovo.  
  
 Třídy hodnotu nebo hodnotu struktury může obsahovat jenom základní číselnými typy, výčet tříd polí `Platform::String^`, nebo [Platform::IBox \<T > ^](../cppcx/platform-ibox-interface.md) kde T představuje číselného typu nebo výčtu ve třídě nebo hodnota třídě nebo struktuře. `IBox<T>^` Pole může mít hodnotu `nullptr`– jedná se jak C++ implementuje koncept *typy s možnou hodnotou Null hodnot*.  
  
 Hodnota třídě nebo struktuře hodnotu, která obsahuje `Platform::String^` nebo `IBox<T>^` zadejte jako člena není `memcpy`-možné.  
  
 Protože všichni členové `value class` nebo `value struct` jsou veřejné a je vložen do metadat, Standardní typy C++ nejsou povoleny jako členy. To se liší od ref třídy, které mohou obsahovat `private` nebo `internal` standardní typy C++...  
  
 Následující fragment kódu deklaruje `Coordinates` a `City` typy jako hodnota struktury. Všimněte si, že jedna z `City` je datových členů `GeoCoordinates` typu. A `value struct` může obsahovat jiné struktury hodnotu jako členy.  
  
 [!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]  
  
## <a name="parameter-passing-for-value-types"></a>Předávání u typů hodnot parametrů  
 Pokud máte hodnotu zadejte jako parametr funkce nebo metody, je obvykle předán podle hodnoty. Pro větší objekty to může způsobit problémy s výkonem. Ve Visual Studio2013 a starší, hodnota typy v jazyce C + +/ CX byly vždy předaná hodnota. V sadě Visual Studio 2015 a novější můžete předat hodnotu typy odkazem nebo hodnota.  
  
 Deklarovat parametr, který předá typ hodnoty podle hodnoty, použijte kód takto:  
  
```  
void Method1(MyValueType obj);  
```  
  
 Parametr, který předá typ hodnoty odkazem deklarovat, použít odkaz na znak (&), jako v následujícím příkladu:  
  
```  
void Method2(MyValueType& obj);  
```  
  
 Typ uvnitř Method2 je odkaz na MyValueType a funguje stejným způsobem jako odkaz na typ v jazyce C++ standardní.  
  
 Při volání Method1 z jiném jazyce, jako je C#, není potřeba použít `ref` nebo `out` – klíčové slovo. Při volání Method2 použít `ref` – klíčové slovo.  
  
```  
Method2(ref obj);  
```  
  
 Ukazatel symbol (*) můžete použít také k předání odkazem typ hodnoty. Chování s ohledem na volající v jiných jazycích je stejné (volající v C# pomocí `ref` – klíčové slovo), ale v metodě, typ je ukazatel na typ hodnoty.  
  
## <a name="nullable-value-types"></a>typy hodnot s povolenou hodnotou Null  
 Jak už bylo zmíněno dříve, může mít hodnotu třídě nebo struktuře hodnotu pole typu [Platform::IBox\<T > ^](../cppcx/platform-ibox-interface.md)– například `IBox<int>^`. Toto pole může mít libovolnou číselnou hodnotu, která platí pro `int` typ, nebo může mít hodnotu `nullptr`. Může předat pole s možnou hodnotou null jako argument jehož parametr je deklarován jako volitelnou metodu nebo kdekoliv jinde, který typ hodnoty není potřeba mít hodnotu.  
  
 Následující příklad ukazuje, jak se inicializovat struktura, která obsahuje pole, s možnou hodnotou Null.  
  
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
  
 Hodnota struktury samotné se dají vytvořit s možnou hodnotou Null stejným způsobem, jak je vidět tady:  
  
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
 [Systém typů (C + +/ CX)](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)   
 [Referenční třídy a struktury (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)