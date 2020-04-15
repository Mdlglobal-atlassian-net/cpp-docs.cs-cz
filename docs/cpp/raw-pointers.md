---
title: Nezpracované ukazatele (C++)
description: Jak používat nezpracované ukazatele v jazyce C++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 919447fcab123ce6b838391d3cc295fb8a8fe95e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374669"
---
# <a name="raw-pointers-c"></a>Nezpracované ukazatele (C++)

Ukazatel je typ proměnné, která ukládá adresu objektu v paměti a slouží k přístupu k tomuto objektu. Nezpracovaný *ukazatel* je ukazatel, jehož životnost není řízena zapouzdřením objektu, jako je inteligentní [ukazatel](smart-pointers-modern-cpp.md). Nezpracovaný ukazatel může být přiřazena adresa jiné proměnné bez ukazatele, nebo může být přiřazena hodnota [nullptr](nullptr.md). Ukazatel, kterému nebyla přiřazena hodnota, obsahuje náhodná data.

Ukazatel může být také *odkazováno* načíst hodnotu objektu, který odkazuje na. *Operátor přístupu člena* poskytuje přístup k členům objektu.

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

Ukazatel může ukazovat na zadaný objekt nebo **na void**. Když program přidělí nový objekt na [haldě](https://wikipedia.org/wiki/Heap) v paměti, obdrží adresu tohoto objektu ve formě ukazatele. Tyto ukazatele se nazývají *vlastnící ukazatele*; vlastnící ukazatel (nebo jeho kopie) musí být použit k explicitnímu odstranění objektu přiděleného haldou, pokud již není potřeba. Pokud neodstraníte paměť, bude *nevracení paměti* k dispozici žádnému jinému programu v počítači. Další informace naleznete v [tématu new and delete operators](new-and-delete-operators.md).

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

Ukazatel (pokud není deklarován jako **const)** může být zpřísňován nebo snížen tak, aby odkazuje na nové umístění v paměti. To se nazývá *aritmetika ukazatele* a používá se v programování ve stylu C k iteřovat přes prvky v polích nebo jiných datových struktur. **Const** ukazatel nelze provést přejděte na jiné umístění paměti a v tomto smyslu je velmi podobný [odkaz](references-cpp.md). Další informace naleznete [v tématu const a volatile ukazatele](const-and-volatile-pointers.md).

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

V 64bitových operačních systémech má ukazatel velikost 64 bitů. Velikost ukazatele systému určuje, kolik adresovatelné paměti může mít. Všechny kopie ukazatele odkazují na stejné umístění v paměti. Ukazatele (spolu s odkazy) se používají značně v jazyce C++ předat větší objekty do a z funkcí, protože je obvykle mnohem efektivnější kopírovat 64bitovou adresu objektu, než kopírovat celý objekt. Při definování funkce zadejte parametry ukazatele jako **const,** pokud nechcete, aby funkce upravovala objekt. Obecně **platí const** odkazy jsou upřednostňovaný způsob, jak předat objekty funkce, pokud hodnota objektu může být případně **nullptr**.

[Ukazatele na funkce](#pointers_to_functions) umožňují, aby funkce byly předány jiným funkcím, a používají se pro "zpětná volání" v programování ve stylu Jazyka C. Moderní C++ používá [lambda výrazy](lambda-expressions-in-cpp.md) pro tento účel.

## <a name="initialization-and-member-access"></a>Inicializace a přístup k členům

Následující příklad ukazuje, jak deklarovat nezpracovaný ukazatel a inicializovat jej s objektem přiděleným na haldě a pak jak ho použít. To také ukazuje několik nebezpečí spojených s syrové ukazatele. (Pamatujte si, že je to C-styl programování a ne moderní C ++!)

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

## <a name="pointer-arithmetic-and-arrays"></a>Aritmetika ukazatele a pole

Ukazatele a pole jsou úzce související. Když je pole předáno hodnotou funkci, je předáno jako ukazatel na první prvek. Následující příklad ukazuje následující důležité vlastnosti ukazatelů a polí:

- `sizeof` operátor vrátí celkovou velikost v bajtech pole
- pro určení počtu prvků vydělte celkový počet bajtů velikostí jednoho prvku
- když je pole předáno funkci, *rozkládá* se na typu ukazatele
- Operátor `sizeof` při použití na ukazatel vrátí velikost ukazatele, 4 bajty na x86 nebo 8 bajtů na x64

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

Některé aritmetické operace lze provádět na neconst ukazatele, aby byly přejděte na nové umístění paměti. Ukazatel může být zpřísněn a snížen **++** **+=** pomocí **-=** **--** , a operátory. Tento postup lze použít v polích a je zvláště užitečné ve vyrovnávacích paměti netypových dat. **Neplatné\* ** přírůstky podle velikosti **char** (1 bajt). Zadaný ukazatel se zvětšuje podle velikosti typu, na který odkazuje.

Následující příklad ukazuje, jak lze aritmetiku ukazatele použít pro přístup k jednotlivým obrazovým bodům v bitmapě v systému Windows. Všimněte si použití **new** and **delete**a operátordereference.

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

## <a name="void-pointers"></a>void* ukazatele

Ukazatel **void** jednoduše odkazuje na umístění nezpracované paměti. Někdy je nutné použít **void\* ** ukazatele, například při předávání mezi c++ kód a C funkce.

Pokud je zadaný ukazatel přetypován na ukazatel void, obsah umístění paměti se nezmění, ale informace o typu se ztratí, takže nelze provádět operace přírůstek nebo snížení. Umístění paměti může být přetypována, například z MyClass* pro void* a zpět na MyClass*. Tyto operace jsou ze své podstaty náchylné k chybám a vyžadují velkou péči, aby se zabránilo chybám. Moderní C++ nedoporučuje použití void ukazatele, pokud to není nezbytně nutné.

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
    char* pchar = static_cast<char*>(pvoid);
    for(char* c = pchar; c < pchar + 1000; ++c)
    {
        *c = 0x00;
    }
    func(pvoid, 1000);
    char ch = static_cast<char*>(pvoid)[0];
    std::cout << ch << std::endl; // 'A'
    operator delete(p);
}
```

## <a name="pointers-to-functions"></a><a name="pointers_to_functions"></a>Ukazatele na funkce

V programování ve stylu Jazyka C se ukazatele funkcí používají především k předání funkcí jiným funkcím. V tomto scénáři volající můžete přizpůsobit chování funkce bez úpravy. V moderním jazyce C++ [poskytují výrazy lambda](lambda-expressions-in-cpp.md) stejnou schopnost s větší bezpečností typů a dalšími výhodami.

Deklarace ukazatele funkce určuje podpis, který musí mít funkce špičatá:

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

Následující příklad ukazuje `combine` funkci, která bere jako parametr `std::string` libovolnou `std::string`funkci, která přijímá a vrátí . V závislosti na funkci, `combine` která je předána bude buď předřadit nebo připojit řetězec.

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

## <a name="see-also"></a>Viz také

[Inteligentní ukazatele](smart-pointers-modern-cpp.md)
[Dedirection Operátor: *](indirection-operator-star.md)<br/>
[Operátor address-of: &](address-of-operator-amp.md)</br>
[Vítejte zpět v C++](welcome-back-to-cpp-modern-cpp.md)
