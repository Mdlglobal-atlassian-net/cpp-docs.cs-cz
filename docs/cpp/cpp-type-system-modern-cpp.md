---
title: C++ type system
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
ms.openlocfilehash: 1f12f7505438dc995aaf8a045fd903488e9ff092
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246604"
---
# <a name="c-type-system"></a>C++ type system

The concept of *type* is very important in C++. Všechny proměnné, argumenty funkcí a návratové hodnoty funkcí musí mít typ, aby bylo možné je zkompilovat. Každému výrazu (včetně hodnot literálů) navíc kompilátor před vyhodnocením implicitně přidělí typ. Some examples of types include **int** to store integral values, **double** to store floating-point values (also known as *scalar* data types), or the Standard Library class [std::basic_string](../standard-library/basic-string-class.md) to store text. You can create your own type by defining a **class** or **struct**. Typ určuje velikost paměti, kterou chcete přidělit proměnné (nebo výsledku výrazu), druhy hodnot, které mohou být v dané proměnné uloženy, způsob interpretace těchto hodnot (jako vzorců bitů) a operace, které lze s proměnnou provést. Tento článek obsahuje přehled hlavních funkcí systému typů v jazyce C++.

## <a name="terminology"></a>Terminologie

**Variable**: The symbolic name of a quantity of data so that the name can be used to access the data it refers to throughout the scope of the code where it is defined. In C++, *variable* is generally used to refer to instances of scalar data types, whereas instances of other types are usually called *objects*.

**Object**: For simplicity and consistency, this article uses the term *object* to refer to any instance of a class or structure, and when it is used in the general sense includes all types, even scalar variables.

**POD type** (plain old data): This informal category of data types in C++ refers to types that are scalar (see the Fundamental types section) or are *POD classes*. Třída POD nemá žádné statické datové členy, které nejsou rovněž POD, a nemá žádné uživatelem definované konstruktory, destruktory ani operátory přiřazení. Třída POD navíc nemá žádné virtuální funkce, žádnou základní třídu a žádné soukromé ani chráněné nestatické datové členy. Typy POD se často používají pro výměnu externích dat, například s modulem napsaným v jazyce C (který má pouze typy POD).

## <a name="specifying-variable-and-function-types"></a>Určení typů proměnných a funkcí

C++ is a *strongly typed* language and it is also *statically-typed*; every object has a type and that type never changes (not to be confused with static data objects).
**When you declare a variable** in your code, you must either specify its type explicitly, or use the **auto** keyword to instruct the compiler to deduce the type from the initializer.
**When you declare a function** in your code, you must specify the type of each argument and its return value, or **void** if no value is returned by the function. Výjimkou je použití šablon funkce, které umožňují použití argumentů libovolných typů.

Po prvotním deklarování proměnné nelze její typ později změnit. Můžete však zkopírovat hodnotu proměnné nebo návratové hodnoty funkce do jiné proměnné jiného typu. Such operations are called *type conversions*, which are sometimes necessary but are also potential sources of data loss or incorrectness.

Po deklarování proměnné typu POD důrazně doporučujeme ji inicializovat, což znamená, že jí přiřadíte počáteční hodnotu. Dokud proměnnou neinicializujete, má hodnotu „garbage“, která se skládá z jakýchkoli bitů, které se původně nacházely v daném umístění v paměti. To je důležitý aspekt jazyka C++. Nezapomeňte na něj zejména v případě, že přecházíte z jiného jazyka, který zpracovává inicializaci za vás. Při deklarování proměnné jiného typu třídy než POD zpracovává inicializaci konstruktor.

Následující příklad ukazuje některé jednoduché deklarace proměnných s popisem každé z nich. Příklad také ukazuje, jak kompilátor používá informace o typu k tomu, aby povolil nebo zakázal určité následné operace s proměnnou.

```cpp
int result = 0;              // Declare and initialize an integer.
double coefficient = 10.8;   // Declare and initialize a floating
                             // point value.
auto name = "Lady G.";       // Declare a variable and let compiler
                             // deduce the type.
auto address;                // error. Compiler cannot deduce a type
                             // without an intializing value.
age = 12;                    // error. Variable declaration must
                             // specify a type or use auto!
result = "Kenny G.";         // error. Can’t assign text to an int.
string result = "zero";      // error. Can’t redefine a variable with
                             // new type.
int maxValue;                // Not recommended! maxValue contains
                             // garbage bits until it is initialized.
```

## <a name="fundamental-built-in-types"></a>Základní (vestavěné) typy

Na rozdíl od některých jazyků nemá C++ žádný univerzální základní typ, z něhož by byly odvozeny všechny ostatní typy. The language includes many *fundamental types*, also known as *built-in types*. This includes numeric types such as **int**, **double**, **long**, **bool**, plus the **char** and **wchar_t** types for ASCII and UNICODE characters, respectively. Most fundamental types (except **bool**, **double**, **wchar_t** and related types) all have unsigned versions, which modify the range of values that the variable can store. For example, an **int**, which stores a 32-bit signed integer, can represent a value from -2,147,483,648 to 2,147,483,647. An **unsigned int**, which is also stored as 32-bits, can store a value from 0 to 4,294,967,295. Celkový počet možných hodnot je ve všech případech stejný, liší se pouze rozsah.

Základní typy jsou rozpoznávány kompilátorem, který má vestavěná pravidla určující, jaké operace lze s jednotlivými typy provádět a jak je lze převést na jiné základní typy. For a complete list of built-in types and their size and numeric limits, see [Fundamental Types](../cpp/fundamental-types-cpp.md).

Následující ilustrace znázorňuje relativní velikosti předdefinovaných typů:

![Size in bytes of built&#45;in types](../cpp/media/built-intypesizes.png "Size in bytes of built&#45;in types")

V následující tabulce jsou uvedeny nejčastěji používané základní typy:

|Typ|Velikost|Komentář|
|----------|----------|-------------|
|int|4 bajty|Výchozí volba pro integrální hodnoty.|
|double|8 bytes|Výchozí volba pro hodnoty s plovoucí desetinnou čárkou.|
|bool|1 bajt|Představuje hodnoty, které mohou být „true“ nebo „false“.|
|char|1 bajt|Používá se pro znaky standardu ASCII ve starších řetězcích stylu C nebo objektů std::string, které nikdy nebude nutné převést do kódování UNICODE.|
|wchar_t|2 bytes|Představuje hodnoty „širokých“ znaků, které mohou být kódovány ve formátu UNICODE (UTF-16 v systému Windows, v jiných operačních systémech se může lišit). This is the character type that is used in strings of type `std::wstring`.|
|unsigned&nbsp;char|1 bajt|C++ has no built-in `byte` type.  Umožňuje znázornit hodnotu bajtu pomocí unsigned char.|
|unsigned int|4 bajty|Výchozí volba pro bitové příznaky.|
|long long|8 bytes|Představuje hodnoty tvořené vysokým celým číslem.|

## <a name="the-void-type"></a>Typ void

The **void** type is a special type; you cannot declare a variable of type **void**, but you can declare a variable of type __void \*__ (pointer to **void**), which is sometimes necessary when allocating raw (un-typed) memory. However, pointers to **void** are not type-safe and generally their use is strongly discouraged in modern C++. In a function declaration, a **void** return value means that the function does not return a value; this is a common and acceptable use of **void**. While the C language required functions that have zero parameters to declare **void** in the parameter list, for example, `fou(void)`, this practice is discouraged in modern C++ and should be declared `fou()`. For more information, see [Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="const-type-qualifier"></a>Kvalifikátor typu const

Jakýkoli vestavěný nebo uživatelem definovaný typ může být kvalifikován pomocí klíčového slova const. Additionally, member functions may be **const**-qualified and even **const**-overloaded. The value of a **const** type cannot be modified after it is initialized.

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.
```

The **const** qualifier is used extensively in function and variable declarations and "const correctness" is an important concept in C++; essentially it means to use **const** to guarantee, at compile time, that values are not modified unintentionally. For more information, see [const](../cpp/const-cpp.md).

A **const** type is distinct from its non-const version; for example, **const int** is a distinct type from **int**. You can use the C++ **const_cast** operator on those rare occasions when you must remove *const-ness* from a variable. For more information, see [Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="string-types"></a>Typy řetězců

Strictly speaking, the C++ language has no built-in string type; **char** and **wchar_t** store single characters - you must declare an array of these types to approximate a string, adding a terminating null value (for example, ASCII `'\0'`) to the array element one past the last valid character (also called a *C-style string*). Psaní řetězců ve stylu C vyžadovalo zapsat mnohem více kódu nebo využít funkce externí knihovny pro tvorbu řetězců. But in modern C++, we have the Standard Library types `std::string` (for 8-bit **char**-type character strings) or `std::wstring` (for 16-bit **wchar_t**-type character strings). These C++ Standard Library containers can be thought of as native string types because they are part of the standard libraries that are included in any compliant C++ build environment. Simply use the `#include <string>` directive to make these types available in your program. (If you are using MFC or ATL, the CString class is also available, but is not part of the C++ standard.) The use of null-terminated character arrays (the C-style strings previously mentioned) is strongly discouraged in modern C++.

## <a name="user-defined-types"></a>Uživateli definované typy

When you define a **class**, **struct**, **union**, or **enum**, that construct is used in the rest of your code as if it were a fundamental type. Má známou velikost v paměti a na kontrolu doby kompilace a doby trvání programu při běhu se vztahují některá pravidla týkající se způsobu jeho použití. Nejdůležitější rozdíly mezi základními typy a typy definovanými uživateli jsou následující:

- Kompilátor neobsahuje žádné předdefinované informace o uživatelském typu. It learns of the type when it first encounters the definition during the compilation process.

- Jako uživatel určujete, jaké operace lze s vaším typem provádět a jak ho lze převést na další typy. K tomu definujete (pomocí přetížení) příslušné operátory, buď jako členy třídy nebo jako nečlenské funkce. For more information, see [Function Overloading](function-overloading.md)

## <a name="pointer-types"></a>Typy ukazatelů

Dating back to the earliest versions of the C language, C++ continues to let you declare a variable of a pointer type by using the special declarator `*` (asterisk). Typ ukazatele ukládá adresu umístění v paměti, kde je uložena skutečná hodnota dat. In modern C++, these are referred to as *raw pointers*, and are accessed in your code through special operators `*` (asterisk) or `->` (dash with greater-than). This is called *dereferencing*, and which one that you use depends on whether you are dereferencing a pointer to a scalar or a pointer to a member in an object. Práce s typy ukazatelů byla dlouhou dobu jedním z nejsložitějších a nejvíce matoucích aspektů vývoje programů v jazycích C a C++. This section outlines some facts and practices to help use raw pointers if you want to, but in modern C++ it’s no longer required (or recommended) to use raw pointers for object ownership at all, due to the evolution of the [smart pointer](../cpp/smart-pointers-modern-cpp.md) (discussed more at the end of this section). Nezpracované ukazatele lze stále s výhodou a bezpečně používat ke sledování objektů, pokud je však potřebujete použít pro vlastnictví objektu, měli byste tak činit s rozvahou a velmi pečlivě promyslet, jak se budou objekty vlastněné těmito ukazateli vytvářet a odstraňovat.

Základní princip, který byste měli znát, je, že deklarací proměnné nezpracovaného ukazatele se přidělí pouze paměť potřebná k uložení adresy umístění v paměti, na které bude ukazatel odkazovat při zrušení reference. Allocation of the memory for the data value itself (also called *backing store*) is not yet allocated. Jinými slovy, deklarováním proměnné nezpracovaného ukazatele vytváříte proměnnou adresy v paměti, nikoli skutečnou datovou proměnnou. Zrušení reference na proměnnou ukazatele, aniž byste se ujistili, že proměnná obsahuje platnou adresu záložního úložiště, způsobí v programu nedefinované chování (obvykle závažnou chybu). Následující příklad ukazuje tento druh chyby:

```cpp
int* pNumber;       // Declare a pointer-to-int variable.
*pNumber = 10;      // error. Although this may compile, it is
                    // a serious error. We are dereferencing an
                    // uninitialized pointer variable with no
                    // allocated memory to point to.
```

V příkladu dochází ke zrušení reference na typ ukazatele bez přidělení paměti, kde by byla uložena skutečná celočíselná data, a bez přidělení platné adresy v paměti. Následující kód tyto chyby opravuje:

```cpp
    int number = 10;          // Declare and initialize a local integer
                              // variable for data backing store.
    int* pNumber = &number;   // Declare and initialize a local integer
                              // pointer variable to a valid memory
                              // address to that backing store.
...
    *pNumber = 41;            // Dereference and store a new value in
                              // the memory pointed to by
                              // pNumber, the integer variable called
                              // "number". Note "number" was changed, not
                              // "pNumber".
```

The corrected code example uses local stack memory to create the backing store that `pNumber` points to. Pro jednoduchost používáme základní typ. In practice, the backing store for pointers are most often user-defined types that are dynamically-allocated in an area of memory called the *heap* (or *free store*) by using a **new** keyword expression (in C-style programming, the older `malloc()` C runtime library function was used). Once allocated, these variables are usually referred to as objects, especially if they are based on a class definition. Memory that is allocated with **new** must be deleted by a corresponding **delete** statement (or, if you used the `malloc()` function to allocate it, the C runtime function `free()`).

However, it is easy to forget to delete a dynamically-allocated object- especially in complex code, which causes a resource bug called a *memory leak*. Z tohoto důvodu se používání nezpracovaných ukazatelů v moderním jazyce C++ nedoporučuje. It is almost always better to wrap a raw pointer in a [smart pointer](../cpp/smart-pointers-modern-cpp.md), which will automatically release the memory when its destructor is invoked (when the code goes out of scope for the smart pointer); by using smart pointers you virtually eliminate a whole class of bugs in your C++ programs. In the following example, assume `MyClass` is a user-defined type that has a public method `DoSomeWork();`

```cpp
void someFunction() {
    unique_ptr<MyClass> pMc(new MyClass);
    pMc->DoSomeWork();
}
  // No memory leak. Out-of-scope automatically calls the destructor
  // for the unique_ptr, freeing the resource.
```

For more information about smart pointers, see [Smart Pointers](../cpp/smart-pointers-modern-cpp.md).

For more information about pointer conversions, see [Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md).

For more information about pointers in general, see [Pointers](../cpp/pointers-cpp.md).

## <a name="windows-data-types"></a>Datové typy ve Windows

In classic Win32 programming for C and C++, most functions use Windows-specific typedefs and #define macros (defined in `windef.h`) to specify the types of parameters and return values. These Windows data types are mostly just special names (aliases) given to C/C++ built-in types. For a complete list of these typedefs and preprocessor definitions, see [Windows Data Types](/windows/win32/WinProg/windows-data-types). Některé tyto funkce typedef, jako např. HRESULT a LCID, jsou užitečné a mají popisný charakter. Jiné, například INT, nemají zvláštní význam a představují pouze aliasy základních typů jazyka C++. Další datové typy systému Windows si zachovaly názvy pocházející z dob programování v jazyce C a 16bitových procesorů a ve světě moderního hardwaru a operačních systémů již nemají místo ani smysl. There are also special data types associated with the Windows Runtime Library, listed as [Windows Runtime base data types](/windows/win32/WinRT/base-data-types). V moderním jazyce C++ platí obecná rada preferovat základní typy C++, pokud typ Windows nesděluje některý další význam o tom, jak má být daná hodnota interpretována.

## <a name="more-information"></a>Další informace

Další informace o systému typů v jazyce C++ naleznete v následujících tématech.

|||
|-|-|
|[Typy hodnot](../cpp/value-types-modern-cpp.md)|Describes *value types* along with issues relating to their use.|
|[Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md)|Popisuje běžné problémy při převodu typů a ukazuje, jak se jim vyhnout.|

## <a name="see-also"></a>Viz také:

[Welcome back to C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
