---
title: Chytré ukazatele (moderní verze jazyka C++)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: a18a5daa45f4f913b6b6dd714956f8592ca0a8d0
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246344"
---
# <a name="smart-pointers-modern-c"></a>Chytré ukazatele (moderní verze jazyka C++)

In modern C++ programming, the Standard Library includes *smart pointers*, which are used to help ensure that programs are free of memory and resource leaks and are exception-safe.

## <a name="uses-for-smart-pointers"></a>Použití inteligentních ukazatelů

Smart pointers are defined in the `std` namespace in the [\<memory>](../standard-library/memory.md) header file. They are crucial to the [RAII](objects-own-resources-raii.md) or *Resource Acquisition Is Initialization* programming idiom. Hlavním cílem tohoto idiomu je zajistit, aby k pořízení prostředků docházelo v okamžiku inicializace objektu tak, aby všechny prostředky pro objekt byly vytvořeny a připraveny v jednom řádku kódu. Z praktického pohledu je hlavní zásadou idiomu RAII přiřadit vlastnictví libovolného prostředku přiděleného haldou – například dynamicky přidělené paměti nebo obslužným rutinám systémového objektu – objektu přidělenému zásobníkem, jehož destruktor obsahuje kód pro odstranění nebo uvolnění prostředku a také případný související čisticí kód.

Ve většině případů platí, že když inicializujete nezpracovaný ukazatel nebo obslužnou rutinu prostředku ukazující na skutečný prostředek, je třeba předat ukazatel inteligentnímu ukazateli okamžitě. V moderním jazyce C++ se nezpracované ukazatele používají pouze v malých blocích kódu s omezeným rozsahem, smyčkách nebo pomocných funkcích, kde je výkon velmi důležitý a neexistuje možnost záměny vlastnictví.

Následující příklad porovnává deklaraci nezpracovaného a inteligentního ukazatele.

[!code-cpp[smart_pointers_intro#1](codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

Jak je v příkladu vidět, inteligentní ukazatel je šablona třídy, která je deklarována v zásobníku a inicializována pomocí nezpracovaného ukazatele, který odkazuje na objekt přidělený haldou. Po inicializaci inteligentní ukazatel vlastní nezpracovaný ukazatel. To znamená, že inteligentní ukazatel je odpovědný za odstranění paměti, kterou nezpracovaný ukazatel určuje. Destruktor inteligentního ukazatele obsahuje volání pro odstranění. Protože inteligentní ukazatel je deklarován v zásobníku, jeho destruktor je vyvolán, když se inteligentní ukazatel dostane mimo rozsah, i když někde dále v zásobníku dojde k výjimce.

Access the encapsulated pointer by using the familiar pointer operators, `->` and `*`, which the smart pointer class overloads to return the encapsulated raw pointer.

Idiom inteligentního ukazatele v jazyce C++ se podobá vytvoření objektu v jazycích jako např. C#, kde vytvoříte objekt a necháte systém, aby se ve správný čas postaral o jeho odstranění. Rozdíl je v tom, že na pozadí neběží žádný samostatný systém uvolňování paměti. Paměť je spravována prostřednictvím standardních pravidel oboru C++, takže běhové prostředí je rychlejší a efektivnější.

> [!IMPORTANT]
>  Vždy vytvářejte inteligentní ukazatele na samostatném řádku kódu, nikdy v seznamu parametrů, aby nedocházelo k mírnému úniku prostředků kvůli některým pravidlům přidělování seznamu parametrů.

The following example shows how a `unique_ptr` smart pointer type from the C++ Standard Library could be used to encapsulate a pointer to a large object.

[!code-cpp[smart_pointers_intro#2](codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

Příklad demonstruje následující základní kroky pro použití inteligentních ukazatelů.

1. Deklarujte inteligentní ukazatel jako automatickou (místní) proměnnou. (Do not use the **new** or `malloc` expression on the smart pointer itself.)

1. U parametru typu zadejte typ odkazování zapouzdřeného ukazatele.

1. Pass a raw pointer to a **new**-ed object in the smart pointer constructor. (Některé funkce nástrojů nebo konstruktory inteligentního ukazatele to provedou za vás.)

1. Use the overloaded `->` and `*` operators to access the object.

1. Umožněte inteligentnímu ukazateli odstranit objekt.

Inteligentní ukazatele jsou navrženy tak, aby byly co nejúčinnější z hlediska paměti i výkonu. For example, the only data member in `unique_ptr` is the encapsulated pointer. This means that `unique_ptr` is exactly the same size as that pointer, either four bytes or eight bytes. Accessing the encapsulated pointer by using the smart pointer overloaded * and -> operators is not significantly slower than accessing the raw pointers directly.

Inteligentní ukazatele mají své vlastní členské funkce, které jsou přístupné pomocí zápisu „tečka“. For example, some C++ Standard Library smart pointers have a reset member function that releases ownership of the pointer. To je užitečné, pokud chcete uvolnit paměť vlastněnou inteligentním ukazatelem předtím, než se inteligentní ukazatel dostane mimo rozsah platnosti, jak je znázorněno v následujícím příkladu.

[!code-cpp[smart_pointers_intro#3](codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

Inteligentní ukazatele obvykle umožňují přímý přístup k příslušnému nezpracovanému ukazateli. C++ Standard Library smart pointers have a `get` member function for this purpose, and `CComPtr` has a public `p` class member. Díky poskytnutí přímého přístupu k podkladový ukazateli můžete použít inteligentní ukazatel ke správě paměti ve vlastním kódu, a zároveň předávat nezpracovaný ukazatel kódu, který nepodporuje inteligentní ukazatele.

[!code-cpp[smart_pointers_intro#4](codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Kinds of smart pointers

V následující části jsou shrnuty různé druhy inteligentních ukazatelů, které jsou k dispozici v programovacím prostředí Windows, včetně popisu, kdy je vhodné je použít.

### <a name="c-standard-library-smart-pointers"></a>C++ Standard Library smart pointers

Tyto inteligentní ukazatele představují první volbu pro zapouzdření ukazatelů do objektů POCO.

- `unique_ptr`<br/>
   Povolují právě jednoho vlastníka podkladového ukazatele. Use as the default choice for POCO unless you know for certain that you require a `shared_ptr`. Lze je přesunout na nového vlastníka, nikoli však kopírovat nebo sdílet. Replaces `auto_ptr`, which is deprecated. Compare to `boost::scoped_ptr`. `unique_ptr` is small and efficient; the size is one pointer and it supports rvalue references for fast insertion and retrieval from C++ Standard Library collections. Header file: `<memory>`. For more information, see [How to: Create and Use unique_ptr Instances](how-to-create-and-use-unique-ptr-instances.md) and [unique_ptr Class](../standard-library/unique-ptr-class.md).

- `shared_ptr`<br/>
   Inteligentní ukazatel s počítáním referencí Tento typ je vhodný, když chcete přiřadit jeden nezpracovaný ukazatel více vlastníkům, například, když vrátíte kopii ukazatele z kontejneru, ale chcete zachovat originál. The raw pointer is not deleted until all `shared_ptr` owners have gone out of scope or have otherwise given up ownership. Má velikost dva ukazatele; jeden pro objekt a jeden pro sdílený kontrolní blok, který obsahuje počet odkazů. Header file: `<memory>`. For more information, see [How to: Create and Use shared_ptr Instances](how-to-create-and-use-shared-ptr-instances.md) and [shared_ptr Class](../standard-library/shared-ptr-class.md).

- `weak_ptr`<br/>
    Special-case smart pointer for use in conjunction with `shared_ptr`. A `weak_ptr` provides access to an object that is owned by one or more `shared_ptr` instances, but does not participate in reference counting. Použijte ho, chcete-li objekt sledovat, ale nepotřebujete ho ponechat ve stavu alive. Required in some cases to break circular references between `shared_ptr` instances. Header file: `<memory>`. For more information, see [How to: Create and Use weak_ptr Instances](how-to-create-and-use-weak-ptr-instances.md) and [weak_ptr Class](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>Smart pointers for COM objects (classic Windows programming)

Při práci s objekty COM zabalte ukazatele rozhraní do příslušného typu inteligentního ukazatele. Knihovna ATL definuje řadu inteligentních ukazatelů pro různé účely. You can also use the `_com_ptr_t` smart pointer type, which the compiler uses when it creates wrapper classes from .tlb files. Jedná se o nejlepší volbu, pokud nechcete zahrnovat hlavičkové soubory ATL.

[CComPtr – třída](../atl/reference/ccomptr-class.md)<br/>
Tuto volbu použijte, dokud nenastane situace, že nemůžete použít knihovnu ATL. Performs reference counting by using the `AddRef` and `Release` methods. For more information, see [How to: Create and Use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[CComQIPtr – třída](../atl/reference/ccomqiptr-class.md)<br/>
Resembles `CComPtr` but also provides simplified syntax for calling `QueryInterface` on COM objects. For more information, see [How to: Create and Use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[CComHeapPtr – třída](../atl/reference/ccomheapptr-class.md)<br/>
Smart pointer to objects that use `CoTaskMemFree` to free memory.

[CComGITPtr – třída](../atl/reference/ccomgitptr-class.md)<br/>
Inteligentní ukazatel rozhraní, která se získávají z tabulky globálního rozhraní (GIT).

[_com_ptr_t – třída](com-ptr-t-class.md)<br/>
Resembles `CComQIPtr` in functionality but does not depend on ATL headers.

### <a name="atl-smart-pointers-for-poco-objects"></a>ATL smart pointers for POCO objects

In addition to smart pointers for COM objects, ATL also defines smart pointers, and collections of smart pointers, for plain old C++ objects (POCO). In classic Windows programming, these types are useful alternatives to the C++ Standard Library collections, especially when code portability is not required or when you do not want to mix the programming models of the C++ Standard Library and ATL.

[CAutoPtr – třída](../atl/reference/cautoptr-class.md)<br/>
Inteligentní ukazatel, který vynucuje jedinečné vlastnictví převodem vlastnictví na kopii. Comparable to the deprecated `std::auto_ptr` Class.

[CHeapPtr – třída](../atl/reference/cheapptr-class.md)<br/>
Smart pointer for objects that are allocated by using the C [malloc](../c-runtime-library/reference/malloc.md) function.

[CAutoVectorPtr – třída](../atl/reference/cautovectorptr-class.md)<br/>
Smart pointer for arrays that are allocated by using `new[]`.

[CAutoPtrArray – třída](../atl/reference/cautoptrarray-class.md)<br/>
Class that encapsulates an array of `CAutoPtr` elements.

[CAutoPtrList – třída](../atl/reference/cautoptrlist-class.md)<br/>
Class that encapsulates methods for manipulating a list of `CAutoPtr` nodes.

## <a name="see-also"></a>Viz také:

[Ukazatele](pointers-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
