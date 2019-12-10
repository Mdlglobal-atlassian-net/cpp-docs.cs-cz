---
title: STL/CLR – kontejnery
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: bfdbbeb735f98f77046790e21c19dd2d21b9d5c6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988115"
---
# <a name="stlclr-containers"></a>STL/CLR – kontejnery

Knihovna STL/CLR se skládá z kontejnerů, které jsou podobné těm, které C++ se nacházejí ve standardní knihovně, ale běží ve spravovaném prostředí .NET Framework. Není stále aktuální se skutečnou C++ standardní knihovnou a je udržována pro podporu starší verze.

Tento dokument poskytuje přehled kontejnerů v STL/CLR, jako jsou požadavky na prvky kontejneru, typy prvků, které lze vložit do kontejnerů, a problémy s vlastnictvím prvků v kontejnerech. V případě potřeby jsou zmíněny rozdíly C++ mezi nativní standardní knihovnou a STL/CLR.

## <a name="requirements-for-container-elements"></a>Požadavky na prvky kontejneru

Všechny elementy vložené do kontejnerů STL/CLR musí dodržovat určité pokyny. Další informace naleznete v tématu [požadavky na prvky kontejneru STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md).

## <a name="valid-container-elements"></a>Platné elementy kontejneru

Kontejnery STL/CLR mohou obsahovat jeden ze dvou typů prvků:

- Zpracovává odkazy na typy odkazů.

- Odkazové typy.

- Nezabalené typy hodnot.

Do žádného z kontejnerů STL/CLR nemůžete vložit zabalený typ hodnoty.

### <a name="handles-to-reference-types"></a>Zpracovává odkazy na typy odkazů

Můžete vložit popisovač do typu odkazu do kontejneru STL/CLR. Popisovač v C++ cílící na CLR je podobný ukazateli v nativním režimu C++. Další informace najdete v tématu [operátor zpracování objektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md).

#### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vložit popisovač do objektu Employee do [cliext –:: set](../dotnet/set-stl-clr.md).

```cpp
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

Je také možné vložit odkazový typ (spíše než popisovač na odkazový typ) do kontejneru STL/CLR. Hlavní rozdíl je v tom, že při odstranění kontejneru odkazových typů je destruktor volán pro všechny prvky uvnitř daného kontejneru. V kontejneru popisovačů na odkazový typ nebudou volány destruktory pro tyto prvky.

#### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vložit objekt zaměstnance do `cliext::set`.

```cpp
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

### <a name="unboxed-value-types"></a>Nezabalené typy hodnot

Do kontejneru STL/CLR můžete také vložit nezabalený typ hodnoty. Nezabalený typ hodnoty je typ hodnoty, který nebyl *zabalen* do typu odkazu.

Typ hodnoty elementu může být jeden ze standardních typů hodnot, jako je například `int`, nebo může být uživatelem definovaný typ hodnoty, jako je například `value class`. Další informace naleznete v tématu [třídy a struktury](../extensions/classes-and-structs-cpp-component-extensions.md) .

#### <a name="example"></a>Příklad

Následující příklad upraví první příklad tím, že třídu Employee nastaví typ hodnoty. Tento typ hodnoty se pak vloží do `cliext::set` stejně jako v prvním příkladu.

```cpp
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

Pokud se pokusíte vložit popisovač do typu hodnoty do kontejneru, je vygenerována [Chyba kompilátoru C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) .

### <a name="performance-and-memory-implications"></a>Důsledky výkonu a paměti

Je nutné vzít v úvahu několik faktorů při určování, zda použít popisovače pro odkaz na typy nebo hodnoty jako prvky kontejneru. Pokud se rozhodnete použít typy hodnot, zapamatujte si, že kopie elementu je vytvořena pokaždé, když je do kontejneru vložen element. U malých objektů by to nemělo být problém, ale pokud jsou vložené objekty velké, může dojít ke zhoršení výkonu. Také Pokud používáte typy hodnot, není možné uložit jeden element ve více kontejnerech současně, protože každý kontejner by měl svou vlastní kopii elementu.

Pokud se rozhodnete použít popisovače k odkazování na typy, může dojít ke zvýšení výkonu, protože není nutné vytvářet kopii prvku, když je vložen do kontejneru. Kromě toho, na rozdíl od hodnotových typů, může stejný prvek existovat ve více kontejnerech. Pokud se však rozhodnete použít obslužné rutiny, musíte se ujistit, že je popisovač platný a že objekt, na který odkazuje, nebyl odstraněn jinde v programu.

## <a name="ownership-issues-with-containers"></a>Problémy s vlastnictvím kontejnerů

Kontejnery v STL/CLR fungují na sémantikě hodnoty. Pokaždé, když vložíte prvek do kontejneru, je vložena kopie tohoto prvku. Chcete-li získat sémantiku s odkazem na odkaz, můžete místo samotného objektu vložit popisovač objektu.

Když zavoláte metodu Clear nebo Erase kontejneru objektů popisovače, objekty, na které odkazují popisovače, nejsou uvolněny z paměti. Je nutné buď objekt výslovně odstranit, nebo, protože tyto objekty jsou umístěny ve spravované haldě, aby systém uvolňování paměti uvolnil paměť, jakmile zjistí, že objekt již není používán.

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
