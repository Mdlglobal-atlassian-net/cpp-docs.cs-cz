---
title: STL/CLR – kontejnery
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: 1787e18cb36c77429cd4957bab167c77d5e25d8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496080"
---
# <a name="stlclr-containers"></a>STL/CLR – kontejnery

Knihovna STL/CLR se skládá z kontejnerů, které jsou podobné těm, nalezeno ve standardní knihovně jazyka C++, ale běží ve spravovaném prostředí .NET Framework. Není pořád aktuální s skutečné standardní knihovny C++ a je zachován z důvodu stále podporuje starší verze.

Tento dokument obsahuje přehled kontejnery v STL/CLR, jako jsou požadavky na prvky kontejneru, typy prvků, můžete vložit do kontejnerů a vlastnictví problémy s prvky v kontejnerech. Kde je to vhodné, jsou uvedené rozdíly mezi nativní standardní knihovny C++ a STL/CLR.

## <a name="requirements-for-container-elements"></a>Požadavky na elementy kontejnerů

Všechny prvky vloženy do kontejnerů STL/CLR musí dodržují určitá pravidla. Další informace najdete v tématu [požadavky na elementy kontejnerů STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md).

## <a name="valid-container-elements"></a>Platný kontejner elementů

Kontejnery STL/CLR může obsahovat jeden ze dvou typů prvků:

- Zpracovává referenční typy.

- Typy odkazů.

- Hodnota typů.

Pevně určené typy hodnot nelze vložit do některé z kontejnerů STL/CLR.

### <a name="handles-to-reference-types"></a>Obslužné rutiny na typy odkazu

Popisovač pro typ odkazu můžete vložit do kontejneru STL/CLR. Popisovač v jazyce C++ pro CLR je obdobou ukazatel v nativním kódu C++. Další informace najdete v tématu [operátor popisovače objektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md).

#### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vložit popisovač pro objekt zaměstnance do [cliext::set](../dotnet/set-stl-clr.md).

```
// cliext_container_valid_reference_handle.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee^ empl1419 = gcnew Employee();
    empl1419->Name = L"Darin Lockert";
    empl1419->EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee^>^ emplSet = gcnew set<Employee^>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="reference-types"></a>Typy odkazů

Je také možné vložit typ odkazu (spíše než popisovač pro typ odkazu) do kontejneru STL/CLR. Hlavní rozdíl je, že když se odstraní kontejner typy odkazů, je zavolán destruktor pro všechny prvky uvnitř tohoto kontejneru. V kontejneru obslužné rutiny na typy odkazu a by volat destruktory pro tyto elementy.

#### <a name="example"></a>Příklad

Následující příklad ukazuje postup vložení objektu do zaměstnance `cliext::set`.

```
// cliext_container_valid_reference.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="unboxed-value-types"></a>Hodnota typů

Můžete také vložit hodnotový typ bez unboxingu do kontejneru STL/CLR. Hodnotový typ bez unboxingu je hodnotový typ, který nebyl *boxed* do typu odkazu.

Element type hodnotu může být jeden z typů standardní hodnotu například `int`, nebo může být typ hodnoty definované uživatelem, například `value class`. Další informace najdete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)

#### <a name="example"></a>Příklad

Následující příklad upravuje v prvním příkladu tak, že zaměstnanci třídy typu hodnoty. Tento typ hodnoty je potom vložen do `cliext::set` stejně jako v prvním příkladu.

```
// cliext_container_valid_valuetype.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

value class Employee
{
public:
    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl.EmployeeNumber, empl.Name);
    }

    return 0;
}
```

Pokud se pokusíte vložit popisovač na typ hodnoty do kontejneru, [Chyba kompilátoru C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) je generován.

### <a name="performance-and-memory-implications"></a>Výkon a paměť důsledky

Při určování, jestli se má použít k odkazování typy nebo typy hodnot jako prvky kontejneru obslužné rutiny, je nutné zvážit několik faktorů. Pokud se rozhodnete použít typy hodnot, mějte na paměti, že kopii tohoto elementu je proveden při každém vložení elementu do kontejneru. Pro malé objekty nesmí se jednat o problém, ale pokud jsou objekty vloženého velké, může dojít k omezení výkonu. Navíc pokud použijete typy hodnot, není možné ukládat jeden element v několika kontejnerů ve stejnou dobu, protože každý kontejner bude mít svou vlastní kopii elementu.

Pokud se rozhodnete použít popisovače k odkazování na typy místo toho, může zvýšit výkon, protože není nutné vytvořit kopii elementu, když je vložen do kontejneru. Navíc na rozdíl od s typy hodnot stejného elementu může existovat v několika kontejnerů. Ale pokud se rozhodnete použít obslužné rutiny, můžete musí pečlivě zkontrolujte, že popisovač je platný a, že objekt, který odkazuje na odstraněný jinde v programu.

## <a name="ownership-issues-with-containers"></a>Potíže s vlastnictvím s kontejnery

Kontejnery v STL/CLR pracovat na hodnotu sémantiku. Pokaždé, když se vkládání elementů do kontejneru, je vložen kopii tohoto prvku. Pokud chcete získat sémantiku jako odkaz, můžete vložit popisovač pro objekt, nikoli samotného objektu.

Při volání nezašifrované podobě nebo vymazat metoda kontejner objektů popisovač, nejsou objekty, které je zachyceno uvolněna z paměti. Můžete explicitně odstraňte objekt, nebo, tyto objekty jsou umístěny na spravované haldě, povolit uvolňování paměti uvolnit paměť, jakmile se určí, že objekt již nejsou déle používány.

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
