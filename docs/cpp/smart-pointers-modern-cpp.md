---
title: Chytré ukazatele (moderní verze jazyka C++)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: 0e93ce033649f5654595ae23a5f10da347879718
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365541"
---
# <a name="smart-pointers-modern-c"></a>Chytré ukazatele (moderní verze jazyka C++)

V moderním programování jazyka C++ obsahuje standardní knihovna *inteligentní ukazatele*, které pomáhají zajistit, aby programy byly bez paměti a nevracení prostředků a jsou bezpečné pro výjimky.

## <a name="uses-for-smart-pointers"></a>Použití inteligentních ukazatelů

Inteligentní ukazatele jsou definovány `std` v oboru názvů v [ \<paměťové>](../standard-library/memory.md) souboru záhlaví. Jsou rozhodující pro [RAII](objects-own-resources-raii.md) nebo *získávání zdrojů je inicializace* programování idiom. Hlavním cílem tohoto idiomu je zajistit, aby k pořízení prostředků docházelo v okamžiku inicializace objektu tak, aby všechny prostředky pro objekt byly vytvořeny a připraveny v jednom řádku kódu. Z praktického pohledu je hlavní zásadou idiomu RAII přiřadit vlastnictví libovolného prostředku přiděleného haldou – například dynamicky přidělené paměti nebo obslužným rutinám systémového objektu – objektu přidělenému zásobníkem, jehož destruktor obsahuje kód pro odstranění nebo uvolnění prostředku a také případný související čisticí kód.

Ve většině případů platí, že když inicializujete nezpracovaný ukazatel nebo obslužnou rutinu prostředku ukazující na skutečný prostředek, je třeba předat ukazatel inteligentnímu ukazateli okamžitě. V moderním jazyce C++ se nezpracované ukazatele používají pouze v malých blocích kódu s omezeným rozsahem, smyčkách nebo pomocných funkcích, kde je výkon velmi důležitý a neexistuje možnost záměny vlastnictví.

Následující příklad porovnává deklaraci nezpracovaného a inteligentního ukazatele.

[!code-cpp[smart_pointers_intro#1](codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

Jak je v příkladu vidět, inteligentní ukazatel je šablona třídy, která je deklarována v zásobníku a inicializována pomocí nezpracovaného ukazatele, který odkazuje na objekt přidělený haldou. Po inicializaci inteligentní ukazatel vlastní nezpracovaný ukazatel. To znamená, že inteligentní ukazatel je odpovědný za odstranění paměti, kterou nezpracovaný ukazatel určuje. Destruktor inteligentního ukazatele obsahuje volání pro odstranění. Protože inteligentní ukazatel je deklarován v zásobníku, jeho destruktor je vyvolán, když se inteligentní ukazatel dostane mimo rozsah, i když někde dále v zásobníku dojde k výjimce.

Přístup zapouzdřený ukazatel pomocí známé `->` `*`operátory ukazatele a , které smart pointer třídy přetížení vrátit zapouzdřený ukazatel raw.

Idiom inteligentního ukazatele v jazyce C++ se podobá vytvoření objektu v jazycích jako např. C#, kde vytvoříte objekt a necháte systém, aby se ve správný čas postaral o jeho odstranění. Rozdíl je v tom, že na pozadí neběží žádný samostatný systém uvolňování paměti. Paměť je spravována prostřednictvím standardních pravidel oboru C++, takže běhové prostředí je rychlejší a efektivnější.

> [!IMPORTANT]
> Vždy vytvářejte inteligentní ukazatele na samostatném řádku kódu, nikdy v seznamu parametrů, aby nedocházelo k mírnému úniku prostředků kvůli některým pravidlům přidělování seznamu parametrů.

Následující příklad ukazuje, `unique_ptr` jak inteligentní ukazatel typu ze standardní knihovny C++ lze použít k zapouzdření ukazatel na velký objekt.

[!code-cpp[smart_pointers_intro#2](codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

Příklad demonstruje následující základní kroky pro použití inteligentních ukazatelů.

1. Deklarujte inteligentní ukazatel jako automatickou (místní) proměnnou. (Nepoužívejte **nový** nebo `malloc` výraz na samotný inteligentní ukazatel.)

1. U parametru typu zadejte typ odkazování zapouzdřeného ukazatele.

1. Předá nezpracovaný ukazatel na **nový**objekt -ed v konstruktoru inteligentní houževnatého ukazatele. (Některé funkce nástrojů nebo konstruktory inteligentního ukazatele to provedou za vás.)

1. Použijte přetížené `->` `*` a operátory pro přístup k objektu.

1. Umožněte inteligentnímu ukazateli odstranit objekt.

Inteligentní ukazatele jsou navrženy tak, aby byly co nejúčinnější z hlediska paměti i výkonu. Například jediný datový člen `unique_ptr` v je zapouzdřený ukazatel. To znamená, že `unique_ptr` má přesně stejnou velikost jako tento ukazatel, buď čtyři bajty nebo osm bajtů. Přístup k zapouzdřený ukazatel pomocí inteligentní ukazatel přetížené * a -> operátory není výrazně pomalejší než přístup k nezpracovaná ukazatele přímo.

Inteligentní ukazatele mají své vlastní členské funkce, které jsou přístupné pomocí zápisu "tečka". Například některé inteligentní ukazatele standardní knihovny C++ mají funkci resetování člena, která uvolňuje vlastnictví ukazatele. To je užitečné, pokud chcete uvolnit paměť vlastněnou inteligentním ukazatelem předtím, než se inteligentní ukazatel dostane mimo rozsah platnosti, jak je znázorněno v následujícím příkladu.

[!code-cpp[smart_pointers_intro#3](codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

Inteligentní ukazatele obvykle umožňují přímý přístup k příslušnému nezpracovanému ukazateli. Inteligentní ukazatele standardní knihovny jazyka `get` C++ mají `CComPtr` pro tento `p` účel člennou funkci a mají člena veřejné třídy. Díky poskytnutí přímého přístupu k podkladový ukazateli můžete použít inteligentní ukazatel ke správě paměti ve vlastním kódu, a zároveň předávat nezpracovaný ukazatel kódu, který nepodporuje inteligentní ukazatele.

[!code-cpp[smart_pointers_intro#4](codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Druhy inteligentních ukazatelů

V následující části jsou shrnuty různé druhy inteligentních ukazatelů, které jsou k dispozici v programovacím prostředí Windows, včetně popisu, kdy je vhodné je použít.

### <a name="c-standard-library-smart-pointers"></a>Inteligentní ukazatele standardní knihovny c++

Tyto inteligentní ukazatele představují první volbu pro zapouzdření ukazatelů do objektů POCO.

- `unique_ptr`<br/>
   Povolují právě jednoho vlastníka podkladového ukazatele. Použijte jako výchozí volbu pro POCO, pokud `shared_ptr`s jistotou nevíte, že požadujete . Lze je přesunout na nového vlastníka, nikoli však kopírovat nebo sdílet. Nahrazuje `auto_ptr`, který je zastaralé. Porovnejte s `boost::scoped_ptr`. `unique_ptr`je malý a efektivní; velikost je jeden ukazatel a podporuje rvalue odkazy pro rychlé vkládání a načítání z kolekcí standardní knihovny C++. Soubor záhlaví: `<memory>`. Další informace naleznete v [tématu How to: Create and Use unique_ptr Instances](how-to-create-and-use-unique-ptr-instances.md) and [unique_ptr Class](../standard-library/unique-ptr-class.md).

- `shared_ptr`<br/>
   Inteligentní ukazatel s počítáním referencí Tento typ je vhodný, když chcete přiřadit jeden nezpracovaný ukazatel více vlastníkům, například, když vrátíte kopii ukazatele z kontejneru, ale chcete zachovat originál. Nezpracovaný ukazatel není odstraněn, dokud všichni `shared_ptr` vlastníci přešli mimo rozsah nebo jinak se vzdali vlastnictví. Má velikost dva ukazatele; jeden pro objekt a jeden pro sdílený kontrolní blok, který obsahuje počet odkazů. Soubor záhlaví: `<memory>`. Další informace naleznete v [tématu How to: Create and Use shared_ptr Instances](how-to-create-and-use-shared-ptr-instances.md) and [shared_ptr Class](../standard-library/shared-ptr-class.md).

- `weak_ptr`<br/>
    Speciální inteligentní ukazatel pro použití `shared_ptr`ve spojení s . A `weak_ptr` poskytuje přístup k objektu, který `shared_ptr` je vlastněn jednou nebo více instancí, ale neúčastní se počítání odkazů. Použijte ho, chcete-li objekt sledovat, ale nepotřebujete ho ponechat ve stavu alive. V některých případech je vyžadováno přerušení cyklické odkazy mezi `shared_ptr` instancemi. Soubor záhlaví: `<memory>`. Další informace naleznete v [tématu How to: Create and Use weak_ptr Instances](how-to-create-and-use-weak-ptr-instances.md) and [weak_ptr Class](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>Inteligentní ukazatele pro objekty COM (klasické programování systému Windows)

Při práci s objekty COM zabalte ukazatele rozhraní do příslušného typu inteligentního ukazatele. Knihovna ATL definuje řadu inteligentních ukazatelů pro různé účely. Můžete také použít `_com_ptr_t` inteligentní typ ukazatele, který kompilátor používá, když vytváří třídy obálky ze souborů TLB. Jedná se o nejlepší volbu, pokud nechcete zahrnovat hlavičkové soubory ATL.

[Třída CComPtr](../atl/reference/ccomptr-class.md)<br/>
Tuto volbu použijte, dokud nenastane situace, že nemůžete použít knihovnu ATL. Provádí počítání odkazů `AddRef` pomocí `Release` metod a. Další informace naleznete v [tématu How to: Create and Use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Třída CComQIPtr](../atl/reference/ccomqiptr-class.md)<br/>
Podobá `CComPtr` se, ale také poskytuje `QueryInterface` zjednodušenou syntaxi pro volání objektů COM. Další informace naleznete v [tématu How to: Create and Use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Třída CComHeapPtr](../atl/reference/ccomheapptr-class.md)<br/>
Inteligentní ukazatel na `CoTaskMemFree` objekty, které slouží k uvolnění paměti.

[Třída CComGITPtr](../atl/reference/ccomgitptr-class.md)<br/>
Inteligentní ukazatel rozhraní, která se získávají z tabulky globálního rozhraní (GIT).

[_com_ptr_t – třída](com-ptr-t-class.md)<br/>
Podobá `CComQIPtr` se funkce, ale nezávisí na hlavičkách ATL.

### <a name="atl-smart-pointers-for-poco-objects"></a>Inteligentní ukazatele ATL pro objekty POCO

Kromě inteligentní ukazatele pro objekty COM, ATL také definuje inteligentní ukazatele a kolekce inteligentní ukazatele, pro prosté staré objekty C++ (POCO). V klasickém programování systému Windows jsou tyto typy užitečnými alternativami k kolekcím standardní knihovny jazyka C++, zejména pokud není vyžadována přenositelnost kódu nebo pokud nechcete kombinovat programovací modely standardní knihovny jazyka C++ a knihovny ATL.

[Třída CAutoPtr](../atl/reference/cautoptr-class.md)<br/>
Inteligentní ukazatel, který vynucuje jedinečné vlastnictví převodem vlastnictví na kopii. Srovnatelné se zastaralou `std::auto_ptr` třídou.

[Třída CHeapPtr](../atl/reference/cheapptr-class.md)<br/>
Inteligentní ukazatel pro objekty, které jsou přiděleny pomocí funkce C [malloc.](../c-runtime-library/reference/malloc.md)

[Třída CAutoVectorPtr](../atl/reference/cautovectorptr-class.md)<br/>
Inteligentní ukazatel pro pole, která `new[]`jsou přidělena pomocí .

[Třída CAutoPtrArray](../atl/reference/cautoptrarray-class.md)<br/>
Třída, která zapouzdřuje pole `CAutoPtr` prvků.

[Třída CAutoPtrList](../atl/reference/cautoptrlist-class.md)<br/>
Třída, která zapouzdřuje metody `CAutoPtr` pro manipulaci se seznamem uzlů.

## <a name="see-also"></a>Viz také

[Ukazatele](pointers-cpp.md)<br/>
[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
