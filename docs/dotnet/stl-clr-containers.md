---
title: "STL/CLR – kontejnery | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 21ebfee07e9faa35046ccfd1cb88894b45dab7c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stlclr-containers"></a>STL/CLR – kontejnery
Knihovny STL/CLR má stejné kontejnerů, které se nacházejí ve standardní knihovně C++, ale běží ve spravovaném prostředí rozhraní .NET Framework. Pokud jste již obeznámeni s standardní knihovna C++, STL/CLR je nejlepší způsob, jak pokračovat v používání dovedností, které jste již vytvořili při upgradu kódu k cíli common language runtime (CLR).  
  
 Tento dokument obsahuje přehled kontejnery STL/CLR, jako jsou požadavky na elementy kontejnerů, typy prvky můžete vložit do kontejnerů, a vlastnictví problémy se elementy v kontejnerech. Kde je to vhodné, jsou uvedené rozdíly mezi nativní standardní knihovna C++ a STL/CLR.  
  
## <a name="requirements-for-container-elements"></a>Požadavky na elementy kontejneru  
 Všechny prvky vloženy do kontejnerů standardní knihovna C++ musí orientují určitá pravidla. Další informace najdete v tématu [požadavky na elementy kontejnerů STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md).  
  
## <a name="valid-container-elements"></a>Elementy kontejneru platný  
 STL/CLR – kontejnery mohou obsahovat jednu ze dvou typů elementů:  
  
-   Zpracovává odkazové typy.  
  
-   Odkazové typy.  
  
-   Hodnota typy.  
  
 Pevně určené typy hodnot nelze vložit do jakéhokoli z kontejnerů STL/CLR.  
  
### <a name="handles-to-reference-types"></a>Obslužné rutiny pro odkazové typy  
 Popisovač pro typ odkazu můžete vložit do kontejneru STL/CLR. Popisovač v jazyce C++ pro CLR je obdobou ukazatel v nativním kódu C++. Další informace najdete v tématu [operátor popisovače objektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md).  
  
#### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vložit popisovač pro objekt zaměstnanec do [cliext::set](../dotnet/set-stl-clr.md).  
  
```  
// cliext_container_valid_reference_handle.cpp  
// compile with: /clr  
  
#include <cliext/set>  
  
using namespace cliext;  
using namespace System;  
  
ref class Employee  
{  
public:  
    // C++ Standard Library containers might require a public constructor, so it  
    // is a good idea to define one.  
    Employee() :  
        name(nullptr),  
        employeeNumber(0) { }  
  
    // All C++ Standard Library containers require a public copy constructor.  
    Employee(const Employee% orig) :  
        name(orig.name),  
        employeeNumber(orig.employeeNumber) { }  
  
    // All C++ Standard Library containers require a public assignment operator.  
    Employee% operator=(const Employee% orig)  
    {  
        if (this != %orig)  
        {  
            name = orig.name;  
            employeeNumber = orig.employeeNumber;  
        }  
  
        return *this;  
    }  
  
    // All C++ Standard Library containers require a public destructor.  
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
 Je také možné vložit do kontejneru STL/CLR typu odkazu (nikoli popisovač pro typu odkazu.). Hlavní rozdíl je, že při odstranění kontejner odkazové typy destruktoru pro všechny elementy uvnitř tohoto kontejneru. Destruktory pro tyto elementy nebude volat v kontejneru popisovačů pro odkazové typy.  
  
#### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vložení do objektu zaměstnanců `cliext::set`.  
  
```  
// cliext_container_valid_reference.cpp  
// compile with: /clr  
  
#include <cliext/set>  
  
using namespace cliext;  
using namespace System;  
  
ref class Employee  
{  
public:  
    // C++ Standard Library containers might require a public constructor, so it  
    // is a good idea to define one.  
    Employee() :  
        name(nullptr),  
        employeeNumber(0) { }  
  
    // All C++ Standard Library containers require a public copy constructor.  
    Employee(const Employee% orig) :  
        name(orig.name),  
        employeeNumber(orig.employeeNumber) { }  
  
    // All C++ Standard Library containers require a public assignment operator.  
    Employee% operator=(const Employee% orig)  
    {  
        if (this != %orig)  
        {  
            name = orig.name;  
            employeeNumber = orig.employeeNumber;  
        }  
  
        return *this;  
    }  
  
    // All C++ Standard Library containers require a public destructor.  
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
  
### <a name="unboxed-value-types"></a>Hodnota typy  
 Typ hodnota můžete také vložit do kontejneru STL/CLR. Typ hodnota je typu hodnoty, která dosud nebyla *do pole* do odkazového typu.  
  
 Element typu hodnota může být jeden z typů standardní hodnotu, jako `int`, nebo hodnotu definovanou uživatelem typu, může být například `value class`. Další informace najdete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)  
  
#### <a name="example"></a>Příklad  
 Následující příklad upraví tak, že zaměstnanec třídy typ hodnoty v prvním příkladu. Tento typ hodnoty se pak vloží do `cliext::set` stejně jako v prvním příkladu.  
  
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
  
 Pokud se pokusíte vložit popisovač pro typ hodnoty do kontejneru, [C3225 Chyba kompilátoru](../error-messages/compiler-errors-2/compiler-error-c3225.md) se vygeneruje.  
  
### <a name="performance-and-memory-implications"></a>Výkon a důsledky paměti  
 Při určování, zda se má použít k odkazování typy nebo typy hodnot jako elementy kontejneru obslužné rutiny, je nutné zvážit několik různých faktorů. Pokud se rozhodnete použít typy hodnot, mějte na paměti, že kopii elementu přišla pokaždé, když vložíte elementu do kontejneru. Pro malé objekty nemělo by se jednat o problém, ale pokud jsou objekty vkládání velké, může sníží výkon. Navíc pokud používáte typy hodnot, není možné uložit jeden element v několika kontejnerů ve stejnou dobu, protože každý kontejner by měla mít vlastní kopii elementu.  
  
 Pokud se rozhodnete použít obslužné rutiny pro odkazové typy místo, může zvýšit výkon, protože není nutné vytvářet kopii elementu, pokud bude vložen do kontejneru. Navíc na rozdíl od s typy hodnot stejného elementu může existovat v několika kontejnerů. Ale pokud se rozhodnete použít obslužné rutiny, můžete pečlivě zkontrolujte, zda popisovač platná a zda odkazuje na objekt nebyl odstraněn jinde v programu.  
  
## <a name="ownership-issues-with-containers"></a>Vlastnictví problémy s kontejnery  
 Kontejnery STL/CLR fungovat na sémantiku hodnotu. Pokaždé, když vložíte elementu do kontejneru, je vložena kopii tohoto prvku. Pokud chcete získat sémantiku jako odkaz, můžete vložit popisovač pro objekt, nikoli samotného objektu.  
  
 Při volání nešifrované nebo erase – metoda kontejner objektů popisovač, nejsou objekty, které obslužné rutiny pro zpracování odkazovat na uvolnit z paměti. Se musí explicitně odstranit objekt, nebo, tyto objekty jsou umístěny na spravovaná halda povolit uvolňování uvolnit paměť, jakmile Určuje, že objekt již používá.  
  
## <a name="see-also"></a>Viz také  
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)