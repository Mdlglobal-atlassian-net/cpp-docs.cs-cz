---
title: Nezpracované ukazatele (C++)
description: Používání nezpracovaných ukazatelů v nástrojiC++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 9ea498c254bc37dc8dc550232127cb2db3bc0886
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74250658"
---
# <a name="raw-pointers-c"></a>Nezpracované ukazatele (C++)

Ukazatel je typ proměnné, která ukládá adresu objektu v paměti a slouží k přístupu k tomuto objektu. *Nezpracovaný ukazatel* je ukazatel, jehož doba života není ovládána zapouzdřeným objektem, jako je [inteligentní ukazatel](smart-pointers-modern-cpp.md). Nezpracovanému ukazateli se dá přiřadit adresa jiné proměnné bez ukazatele, nebo se mu dá přiřadit hodnota [nullptr](nullptr.md). Ukazatel, kterému nebyla přiřazena hodnota, obsahuje náhodná data.

Ukazatel lze také *odkázat* , aby se načetla hodnota objektu, na který odkazuje. *Operátor přístupu členů* poskytuje přístup k členům objektu.

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

Ukazatel může ukazovat na typový objekt nebo na **typ void**. Když program přidělí novému objektu [haldě](https://wikipedia.org/wiki/Heap) v paměti, obdrží adresu tohoto objektu ve formě ukazatele. Tyto ukazatele se nazývají *vlastnící ukazatele*; vlastnící ukazatel (nebo jeho kopie) se musí použít k explicitnímu odstranění objektu, který je přidělen haldě, pokud již není potřeba. Při odstranění paměti dojde k *nevrácení paměti* z důvodu nedostupnosti paměti pro žádný jiný program v počítači. Další informace najdete v tématu [operátory New a DELETE](new-and-delete-operators.md).

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

Ukazatel (Pokud není deklarován jako **const**) lze zvýšit nebo snížit tak, aby odkazoval na nové umístění v paměti. Tato metoda se nazývá *aritmetický ukazatel* a používá se v programování ve stylu C k iterování nad prvky v polích nebo v jiných datových strukturách. Ukazatel **const** nelze nastavit tak, aby odkazoval na jiné umístění v paměti a v tomto smyslu je velmi podobný [odkazu](references-cpp.md). Další informace naleznete v tématu [const a volatile ukazatele](const-and-volatile-pointers.md).

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    const char* str = "Hello world";

    const int c = 1;
    const int* pconst = &c; // declare a non-const pointer to const int
    const int c2 = 2;
    pconst = &c2;  // OK pconst itself isn't const
    const int* const pconst2 = &c; 
    // pconst2 = &c2; // Error! pconst2 is const.
```

V 64 operačních systémech má ukazatel velikost 64 bitů; velikost ukazatele systému určuje, kolik paměti může mít. Všechny kopie ukazatele ukazují do stejného umístění v paměti. Ukazatele (spolu s referencemi) se často používají C++ k předávání větších objektů do a z funkcí, protože je obvykle mnohem efektivnější zkopírovat 64 bitovou adresu objektu, než zkopírovat celý objekt. Při definování funkce zadejte parametry ukazatele jako **const** , pokud nechcete, aby funkce změnila objekt. Obecně platí, že odkazy **const** jsou preferovaným způsobem, jak předat objekty funkcím, pokud hodnota objektu může být **nullptr**.

[Ukazatelé na funkce](#pointers_to_functions) povolují předání funkcí do jiných funkcí a používají se pro "zpětná volání" v programování ve stylu jazyka C. Moderní C++ používá pro tento účel [výrazy lambda](lambda-expressions-in-cpp.md) .

## <a name="initialization-and-member-access"></a>Inicializace a přístup ke členu

Následující příklad ukazuje, jak deklarovat nezpracovaný ukazatel a inicializovat jej s objektem přiděleným pro haldu a poté, jak jej použít. Zobrazuje také několik rizik spojených s nezpracovanými ukazateli. (Pamatujte na to, že se jedná o programování ve stylu C++C a ne moderní!)

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
void func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
void func_B(MyClass mc)
{
    // mc here is a regular object, not a pointer.
    // Use the "." operator to access members.
    // This statement modifies only the local copy of mc.
    mc.num = 21;
    std::cout << "Local copy of mc:";
    mc.print(); // "Erika, 21"
}


int main()
{
    // Use the * operator to declare a pointer type
    // Use new to allocate and initialize memory
    MyClass* pmc = new MyClass{ 108, "Nick" };

    // Prints the memory address. Usually not what you want.
    std:: cout << pmc << std::endl;

    // Copy the pointed-to object by dereferencing the pointer
    // to access the contents of the memory location.
    // mc is a separate object, allocated here on the stack
    MyClass mc = *pmc;

    // Declare a pointer that points to mc using the addressof operator
    MyClass* pcopy = &mc;

    // Use the -> operator to access the object's public members
    pmc->print(); // "Nick, 108"

    // Copy the pointer. Now pmc and pmc2 point to same object!
    MyClass* pmc2 = pmc;

    // Use copied pointer to modify the original object
    pmc2->name = "Erika";
    pmc->print(); // "Erika, 108"
    pmc2->print(); // "Erika, 108"

    // Pass the pointer to a function.
    func_A(mc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*mc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    delete(pmc); // don't forget to give memory back to operating system!
   // delete(pmc2); //crash! memory location was already deleted
}
```

## <a name="pointer-arithmetic-and-arrays"></a>Aritmetické operace s ukazateli a pole

Ukazatele a pole spolu úzce souvisejí. Když je pole předáno hodnotou do funkce, je předáno jako ukazatel na první prvek. Následující příklad ukazuje následující důležité vlastnosti ukazatelů a polí:

- operátor `sizeof` vrací celkovou velikost pole v bajtech.
- Chcete-li určit počet prvků, vydělte celkový počet bajtů velikostí jednoho elementu
- Když se předává pole do funkce, *Decays* se na typ ukazatele.
- operátor `sizeof`, když se aplikuje na ukazatel, vrátí velikost ukazatele, 4 bajty na platformě x86 nebo 8 bajtů na platformě x64.

```cpp
#include <iostream>

void func(int arr[], int length)
{
    // returns pointer size. not useful here.
    size_t test = sizeof(arr);

    for(int i = 0; i < length; ++i)
    {
        std::cout << arr[i] << " ";
    }
}

int main()
{

    int i[5]{ 1,2,3,4,5 };
    // sizeof(i) = total bytes
    int j = sizeof(i) / sizeof(i[0]);
    func(i,j);
}
```

Některé aritmetické operace lze provést na nekonstantních ukazatelích, aby odkazovaly na nové umístění v paměti. Ukazatel lze zvýšit a snížit pomocí operátorů **++** , **+=** , **-=** a **--** . Tato technika se dá použít v polích a je obzvláště užitečná ve vyrovnávací paměti netypových dat. **Typ void\*** zvyšuje velikost **znaku** (1 bajt). Zadaný ukazatel se zvyšuje podle velikosti typu, na který odkazuje.

Následující příklad ukazuje, jak lze použít aritmetický ukazatel pro přístup k jednotlivým pixelům v rastrovém obrázku v systému Windows. Všimněte si použití **New** a **Delete**a operátoru dereference. 

```cpp
#include <Windows.h>
#include <fstream>

using namespace std;

int main()
{

    BITMAPINFOHEADER header;
    header.biHeight = 100; // Multiple of 4 for simplicity.
    header.biWidth = 100;
    header.biBitCount = 24;
    header.biPlanes = 1;
    header.biCompression = BI_RGB;
    header.biSize = sizeof(BITMAPINFOHEADER);

    constexpr int bufferSize = 30000;
    unsigned char* buffer = new unsigned char[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned char* begin = &buffer[0];
    unsigned char* end = &buffer[0] + bufferSize;
    unsigned char* p = begin;
    constexpr int pixelWidth = 3;
    constexpr int borderWidth = 2;

    while (p < end)
    {
            // Is top or bottom edge?
        if ((p < begin + header.biWidth * pixelWidth * borderWidth)
            || (p > end - header.biWidth * pixelWidth * borderWidth)
            // Is left or right edge?
            || (p - begin) % (header.biWidth * pixelWidth) < (borderWidth * pixelWidth)
            || (p - begin) % (header.biWidth * pixelWidth) > ((header.biWidth - borderWidth) * pixelWidth))
        {
            *p = 0x0; // Black
        }
        else
        {
            *p = 0xC3; // Gray
        }
        p++; // Increment one byte sizeof(unsigned char).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<char*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<char*>(&header), sizeof(header));
    wf.write(reinterpret_cast<char*>(begin), bufferSize);

    delete[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="void-pointers"></a>void * ukazatele

Ukazatel na **void** jednoduše odkazuje na umístění nezpracované paměti. Někdy je nutné použít ukazatele **void\*** , například při předávání mezi C++ kódem a funkcemi jazyka C. 

Když je typový ukazatel přetypování na ukazatel typu void, obsah umístění v paměti se nemění, ale informace o typu jsou ztraceny, takže nemůžete provádět operace zvýšení nebo snížení. Umístění paměti lze přetypovat například z MyClass * na void * a zpět na MyClass *. Tyto operace jsou v podstatě náchylné k chybám a vyžadují Skvělé opatrnosti, aby se předešlo chybám. Moderní C++ nedoporučuje použití ukazatelů typu void, pokud není nezbytně nutné.

```cpp

//func.c
void func(void* data, int length)
{
    char* c = (char*)(data);

    // fill in the buffer with data
    for (int i = 0; i < length; ++i)
    {
        *c = 0x41;
        ++c;
    }
}

// main.cpp
#include <iostream>

extern "C"
{
    void func(void* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = new MyClass{10, "Marian"};
    void* p = static_cast<void*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator new to allocate untyped memory block
    void* pvoid = operator new(1000);
    for(char* c = static_cast<char*>(pvoid); pvoid < &pvoid + 1000; ++c)
    {
        *c = 0x00;
    }
    func(pvoid, 1000);
    char ch = static_cast<char*>(pvoid)[0];
    std::cout << ch << std::endl; // 'A'
    operator delete(p);
}
```

## <a name="pointers_to_functions"></a>Ukazatele na funkce

V programování ve stylu jazyka C jsou ukazatele funkcí používány primárně pro předávání funkcí jiným funkcím. V tomto scénáři volající může přizpůsobit chování funkce beze změny. V moderních C++ [výrazech lambda](lambda-expressions-in-cpp.md) poskytují stejnou schopnost s vyšším zabezpečením typu a dalšími výhodami.

Deklarace ukazatele na funkci určuje signaturu, kterou musí mít ukazatel na odkaz na funkci:

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
void (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

Následující příklad ukazuje funkci `combine`, která přijímá jako parametr jakoukoliv funkci, která přijímá `std::string` a vrací `std::string`. V závislosti na funkci, která je předána `combine`, buď dopřed nebo přiřaďte řetězec.

```cpp
#include <iostream>
#include <string>

using namespace std;

string base {"hello world"};

string append(string s)
{
    return base.append(" ").append(s);
}

string prepend(string s)
{
    return s.append(" ").append(base);
}

string combine(string s, string(*g)(string a))
{
    return (*g)(s);
}

int main()
{
    cout << combine("from MSVC", append) << "\n";
    cout << combine("Good morning and", prepend) << "\n";
}
```

## <a name="see-also"></a>Viz také:

[Inteligentní ukazatele](smart-pointers-modern-cpp.md)
[operátora dereference: *](indirection-operator-star.md)<br/>
[Operátor address-of: &](address-of-operator-amp.md)</br>
[Vítejte zpět naC++](welcome-back-to-cpp-modern-cpp.md)
