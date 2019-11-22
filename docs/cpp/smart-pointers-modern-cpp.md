---
title: Chytré ukazatele (moderní verze jazyka C++)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: 293dca7cce4cffce83e474ff4f2e7753d18882c2
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303355"
---
# <a name="smart-pointers-modern-c"></a>Chytré ukazatele (moderní verze jazyka C++)

V moderním C++ programování standardní knihovna obsahuje *inteligentní ukazatele*, které vám pomohou zajistit, aby programy neobsahovaly paměť a nevracení prostředků a jsou bezpečné pro výjimky.

## <a name="uses-for-smart-pointers"></a>Použití inteligentních ukazatelů

Inteligentní ukazatele jsou definovány v oboru názvů `std` v souboru hlaviček [\<> paměti](../standard-library/memory.md) . Jsou zásadní pro [RAII](objects-own-resources-raii.md) nebo *získávání prostředků je* programování idiom. Hlavním cílem tohoto idiomu je zajistit, aby k pořízení prostředků docházelo v okamžiku inicializace objektu tak, aby všechny prostředky pro objekt byly vytvořeny a připraveny v jednom řádku kódu. Z praktického pohledu je hlavní zásadou idiomu RAII přiřadit vlastnictví libovolného prostředku přiděleného haldou – například dynamicky přidělené paměti nebo obslužným rutinám systémového objektu – objektu přidělenému zásobníkem, jehož destruktor obsahuje kód pro odstranění nebo uvolnění prostředku a také případný související čisticí kód.

Ve většině případů platí, že když inicializujete nezpracovaný ukazatel nebo obslužnou rutinu prostředku ukazující na skutečný prostředek, je třeba předat ukazatel inteligentnímu ukazateli okamžitě. V moderním jazyce C++ se nezpracované ukazatele používají pouze v malých blocích kódu s omezeným rozsahem, smyčkách nebo pomocných funkcích, kde je výkon velmi důležitý a neexistuje možnost záměny vlastnictví.

Následující příklad porovnává deklaraci nezpracovaného a inteligentního ukazatele.

[!code-cpp[smart_pointers_intro#1](codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

Jak je v příkladu vidět, inteligentní ukazatel je šablona třídy, která je deklarována v zásobníku a inicializována pomocí nezpracovaného ukazatele, který odkazuje na objekt přidělený haldou. Po inicializaci inteligentní ukazatel vlastní nezpracovaný ukazatel. To znamená, že inteligentní ukazatel je odpovědný za odstranění paměti, kterou nezpracovaný ukazatel určuje. Destruktor inteligentního ukazatele obsahuje volání pro odstranění. Protože inteligentní ukazatel je deklarován v zásobníku, jeho destruktor je vyvolán, když se inteligentní ukazatel dostane mimo rozsah, i když někde dále v zásobníku dojde k výjimce.

Přístup k zapouzdřenému ukazateli pomocí známých operátorů ukazatelů `->` a `*`, které třídy inteligentního ukazatele přetěžuje, aby vracely zapouzdřený nezpracovaný ukazatel.

Idiom inteligentního ukazatele v jazyce C++ se podobá vytvoření objektu v jazycích jako např. C#, kde vytvoříte objekt a necháte systém, aby se ve správný čas postaral o jeho odstranění. Rozdíl je v tom, že na pozadí neběží žádný samostatný systém uvolňování paměti. Paměť je spravována prostřednictvím standardních pravidel oboru C++, takže běhové prostředí je rychlejší a efektivnější.

> [!IMPORTANT]
>  Vždy vytvářejte inteligentní ukazatele na samostatném řádku kódu, nikdy v seznamu parametrů, aby nedocházelo k mírnému úniku prostředků kvůli některým pravidlům přidělování seznamu parametrů.

Následující příklad ukazuje, jak lze typ inteligentního ukazatele `unique_ptr` ze C++ standardní knihovny použít k zapouzdření ukazatele na rozsáhlý objekt.

[!code-cpp[smart_pointers_intro#2](codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

Příklad demonstruje následující základní kroky pro použití inteligentních ukazatelů.

1. Deklarujte inteligentní ukazatel jako automatickou (místní) proměnnou. (Nepoužívejte výraz **New** nebo `malloc` na samotném inteligentním ukazateli.)

1. U parametru typu zadejte typ odkazování zapouzdřeného ukazatele.

1. Předejte nezpracovaný ukazatel do objektu **New**-Ed v konstruktoru inteligentního ukazatele. (Některé funkce nástrojů nebo konstruktory inteligentního ukazatele to provedou za vás.)

1. Pro přístup k objektu použijte přetížené operátory `->` a `*`.

1. Umožněte inteligentnímu ukazateli odstranit objekt.

Inteligentní ukazatele jsou navrženy tak, aby byly co nejúčinnější z hlediska paměti i výkonu. Například jediný datový člen v `unique_ptr` je zapouzdřený ukazatel. To znamená, že `unique_ptr` má přesně stejnou velikost jako tento ukazatel, buď čtyři bajty, nebo osm bajtů. Přístup k zapouzdřenému ukazateli pomocí přetížených operátorů inteligentního ukazatele * a-> není výrazně pomalejší než přímý přístup k nezpracovaným ukazatelům.

Inteligentní ukazatele mají své vlastní členské funkce, které jsou k dispozici pomocí notace "tečka". Například některé C++ standardní inteligentní ukazatele knihovny mají funkci resetovat členskou funkci, která uvolní vlastnictví ukazatele. To je užitečné, pokud chcete uvolnit paměť vlastněnou inteligentním ukazatelem předtím, než se inteligentní ukazatel dostane mimo rozsah platnosti, jak je znázorněno v následujícím příkladu.

[!code-cpp[smart_pointers_intro#3](codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

Inteligentní ukazatele obvykle umožňují přímý přístup k příslušnému nezpracovanému ukazateli. C++Inteligentní ukazatele standardní knihovny mají pro tento účel `get` členskou funkci a `CComPtr` je veřejným členem třídy `p`. Díky poskytnutí přímého přístupu k podkladový ukazateli můžete použít inteligentní ukazatel ke správě paměti ve vlastním kódu, a zároveň předávat nezpracovaný ukazatel kódu, který nepodporuje inteligentní ukazatele.

[!code-cpp[smart_pointers_intro#4](codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Druhy inteligentních ukazatelů

V následující části jsou shrnuty různé druhy inteligentních ukazatelů, které jsou k dispozici v programovacím prostředí Windows, včetně popisu, kdy je vhodné je použít.

### <a name="c-standard-library-smart-pointers"></a>C++Inteligentní ukazatele standardní knihovny

Tyto inteligentní ukazatele představují první volbu pro zapouzdření ukazatelů do objektů POCO.

- `unique_ptr`<br/>
   Povolují právě jednoho vlastníka podkladového ukazatele. Použijte jako výchozí volbu pro POCO, pokud si nejste jisti, že potřebujete `shared_ptr`. Lze je přesunout na nového vlastníka, nikoli však kopírovat nebo sdílet. Nahrazuje `auto_ptr`, která je zastaralá. Porovnejte `boost::scoped_ptr`. `unique_ptr` je malý a efektivní; velikost je jeden ukazatel a podporuje odkazy rvalue pro rychlé vkládání a načítání z C++ kolekcí standardních knihoven. Hlavičkový soubor: `<memory>`. Další informace naleznete v tématu [How to: Create and Use Unique_ptr Instances](how-to-create-and-use-unique-ptr-instances.md) and [unique_ptr Class](../standard-library/unique-ptr-class.md).

- `shared_ptr`<br/>
   Inteligentní ukazatel s počítáním referencí Tento typ je vhodný, když chcete přiřadit jeden nezpracovaný ukazatel více vlastníkům, například, když vrátíte kopii ukazatele z kontejneru, ale chcete zachovat originál. Nezpracovaný ukazatel se neodstraní, dokud všichni vlastníci `shared_ptr` neprošli rozsahem nebo pokud mají jiné vlastnictví. Má velikost dva ukazatele; jeden pro objekt a jeden pro sdílený kontrolní blok, který obsahuje počet odkazů. Hlavičkový soubor: `<memory>`. Další informace naleznete v tématu [How to: Create and Use Shared_ptr Instances](how-to-create-and-use-shared-ptr-instances.md) and [shared_ptr Class](../standard-library/shared-ptr-class.md).

- `weak_ptr`<br/>
    Inteligentní ukazatel speciálního případu pro použití ve spojení s `shared_ptr`. `weak_ptr` poskytuje přístup k objektu, který je vlastněn jednou nebo více `shared_ptr` instancemi, ale není součástí počítání odkazů. Použijte ho, chcete-li objekt sledovat, ale nepotřebujete ho ponechat ve stavu alive. V některých případech se vyžaduje pro přerušení cyklických odkazů mezi instancemi `shared_ptr`. Hlavičkový soubor: `<memory>`. Další informace naleznete v tématu [How to: Create and Use Weak_ptr Instances](how-to-create-and-use-weak-ptr-instances.md) and [weak_ptr Class](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>Inteligentní ukazatele pro objekty COM (klasické programování v systému Windows)

Při práci s objekty COM zabalte ukazatele rozhraní do příslušného typu inteligentního ukazatele. Knihovna ATL definuje řadu inteligentních ukazatelů pro různé účely. Můžete také použít `_com_ptr_t` typ inteligentního ukazatele, který kompilátor používá při vytváření obálkových tříd ze souborů. tlb. Jedná se o nejlepší volbu, pokud nechcete zahrnovat hlavičkové soubory ATL.

[CComPtr – třída](../atl/reference/ccomptr-class.md)<br/>
Tuto volbu použijte, dokud nenastane situace, že nemůžete použít knihovnu ATL. Provádí počítání odkazů pomocí metod `AddRef` a `Release`. Další informace najdete v tématu [Postupy: vytváření a používání instancí CComPtr a CComQIPtr](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[CComQIPtr – třída](../atl/reference/ccomqiptr-class.md)<br/>
Se podobá `CComPtr`, ale také poskytuje zjednodušenou syntaxi pro volání `QueryInterface` objektů COM. Další informace najdete v tématu [Postupy: vytváření a používání instancí CComPtr a CComQIPtr](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[CComHeapPtr – třída](../atl/reference/ccomheapptr-class.md)<br/>
Inteligentní ukazatel na objekty, které používají `CoTaskMemFree` k uvolnění paměti.

[CComGITPtr – třída](../atl/reference/ccomgitptr-class.md)<br/>
Inteligentní ukazatel rozhraní, která se získávají z tabulky globálního rozhraní (GIT).

[_com_ptr_t – třída](com-ptr-t-class.md)<br/>
Se podobá `CComQIPtr` ve funkcích, ale nezávisí na hlavičkách ATL.

### <a name="atl-smart-pointers-for-poco-objects"></a>Inteligentní ukazatele ATL pro objekty POCO

Kromě inteligentních ukazatelů pro objekty modelu COM ATL také definuje inteligentní ukazatele a kolekce inteligentních ukazatelů pro prosté staré C++ objekty (POCO). V klasickém programování v systému Windows jsou tyto typy užitečnou C++ alternativou pro standardní kolekce knihoven, zejména v případě, že není vyžadován přenositelnost kódu nebo pokud nechcete kombinovat programové modely C++ standardní knihovny a knihovny ATL.

[CAutoPtr – třída](../atl/reference/cautoptr-class.md)<br/>
Inteligentní ukazatel, který vynucuje jedinečné vlastnictví převodem vlastnictví na kopii. Porovnatelný z nepoužívané `std::auto_ptr` třídy.

[CHeapPtr – třída](../atl/reference/cheapptr-class.md)<br/>
Inteligentní ukazatel pro objekty, které jsou přiděleny [pomocí funkce C](../c-runtime-library/reference/malloc.md) .

[CAutoVectorPtr – třída](../atl/reference/cautovectorptr-class.md)<br/>
Inteligentní ukazatel pro pole, která jsou přidělena pomocí `new[]`.

[CAutoPtrArray – třída](../atl/reference/cautoptrarray-class.md)<br/>
Třída, která zapouzdřuje pole `CAutoPtr` prvků.

[CAutoPtrList – třída](../atl/reference/cautoptrlist-class.md)<br/>
Třída, která zapouzdřuje metody pro práci se seznamem `CAutoPtr`ch uzlů.

## <a name="see-also"></a>Viz také:

[Ukazatele](pointers-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
