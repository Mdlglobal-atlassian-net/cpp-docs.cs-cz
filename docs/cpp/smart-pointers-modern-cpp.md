---
title: Inteligentní ukazatele (moderní verze jazyka C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2710609cbf20861c77dae1cb0aea327983efef6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098170"
---
# <a name="smart-pointers-modern-c"></a>Chytré ukazatele (moderní verze jazyka C++)

V moderním programování C++ standardní knihovna obsahuje *inteligentní ukazatele*, které se používají k zajištění, že programy jsou volné paměti a dalších prostředků a jsou bezpečné na výjimku.

## <a name="uses-for-smart-pointers"></a>Použití inteligentních ukazatelů

Inteligentní ukazatele se definují v `std` obor názvů v [ \<paměti >](../standard-library/memory.md) hlavičkový soubor. Jsou klíčové pro [RAII](../cpp/objects-own-resources-raii.md) nebo *získání prostředků je inicializace* programovací idiom. Hlavním cílem tohoto idiomu je zajistit, aby k pořízení prostředků docházelo v okamžiku inicializace objektu tak, aby všechny prostředky pro objekt byly vytvořeny a připraveny v jednom řádku kódu. Z praktického pohledu je hlavní zásadou idiomu RAII přiřadit vlastnictví libovolného prostředku přiděleného haldou – například dynamicky přidělené paměti nebo obslužným rutinám systémového objektu – objektu přidělenému zásobníkem, jehož destruktor obsahuje kód pro odstranění nebo uvolnění prostředku a také případný související čisticí kód.

Ve většině případů platí, že když inicializujete nezpracovaný ukazatel nebo obslužnou rutinu prostředku ukazující na skutečný prostředek, je třeba předat ukazatel inteligentnímu ukazateli okamžitě. V moderním jazyce C++ se nezpracované ukazatele používají pouze v malých blocích kódu s omezeným rozsahem, smyčkách nebo pomocných funkcích, kde je výkon velmi důležitý a neexistuje možnost záměny vlastnictví.

Následující příklad porovnává deklaraci nezpracovaného a inteligentního ukazatele.

[!code-cpp[smart_pointers_intro#1](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

Jak je v příkladu vidět, inteligentní ukazatel je šablona třídy, která je deklarována v zásobníku a inicializována pomocí nezpracovaného ukazatele, který odkazuje na objekt přidělený haldou. Po inicializaci inteligentní ukazatel vlastní nezpracovaný ukazatel. To znamená, že inteligentní ukazatel je odpovědný za odstranění paměti, kterou nezpracovaný ukazatel určuje. Destruktor inteligentního ukazatele obsahuje volání pro odstranění. Protože inteligentní ukazatel je deklarován v zásobníku, jeho destruktor je vyvolán, když se inteligentní ukazatel dostane mimo rozsah, i když někde dále v zásobníku dojde k výjimce.

Přístup k zapouzdřenému ukazateli pomocí známých operátorů ukazatele, `->` a `*`, které třída inteligentních ukazatelů přetíží a vrátí zapouzdřený nezpracovaný ukazatel.

Idiom inteligentního ukazatele v jazyce C++ se podobá vytvoření objektu v jazycích jako např. C#, kde vytvoříte objekt a necháte systém, aby se ve správný čas postaral o jeho odstranění. Rozdíl je v tom, že na pozadí neběží žádný samostatný systém uvolňování paměti. Paměť je spravována prostřednictvím standardních pravidel oboru C++, takže běhové prostředí je rychlejší a efektivnější.

> [!IMPORTANT]
>  Vždy vytvářejte inteligentní ukazatele na samostatném řádku kódu, nikdy v seznamu parametrů, aby nedocházelo k mírnému úniku prostředků kvůli některým pravidlům přidělování seznamu parametrů.

Následující příklad ukazuje způsob `unique_ptr` typ inteligentního ukazatele ze standardní knihovny C++ může použít k zapouzdření ukazatele ve velkém objektu.

[!code-cpp[smart_pointers_intro#2](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

Příklad demonstruje následující základní kroky pro použití inteligentních ukazatelů.

1. Deklarujte inteligentní ukazatel jako automatickou (místní) proměnnou. (Nepoužívejte **nové** nebo `malloc` výraz na samotném inteligentním ukazateli.)

1. U parametru typu zadejte typ odkazování zapouzdřeného ukazatele.

1. Předejte nezpracovaný ukazatel **nové**-ed objekt v konstruktoru inteligentního ukazatele. (Některé funkce nástrojů nebo konstruktory inteligentního ukazatele to provedou za vás.)

1. Použijte přetížené `->` a `*` operátory pro přístup k objektu.

1. Umožněte inteligentnímu ukazateli odstranit objekt.

Inteligentní ukazatele jsou navrženy tak, aby byly co nejúčinnější z hlediska paměti i výkonu. Například jediný datový člen v `unique_ptr` je zapouzdřený ukazatel. To znamená, že `unique_ptr` má přesně stejnou velikost jako tento ukazatel čtyř bajtů nebo osmi bajtů. Přístup k zapouzdřenému ukazateli pomocí přetíženého inteligentního ukazatele * a -> operátory není výrazně pomalejší než přímý přístup k nezpracovanému ukazateli přímo.

Inteligentní ukazatele mají své vlastní členské funkce, které jsou přístupné pomocí zápisu „tečka“. Některé inteligentní ukazatele standardní knihovny jazyka C++ například mají funkci obnovení člene, která uvolní vlastnictví ukazatele. To je užitečné, pokud chcete uvolnit paměť vlastněnou inteligentním ukazatelem předtím, než se inteligentní ukazatel dostane mimo rozsah platnosti, jak je znázorněno v následujícím příkladu.

[!code-cpp[smart_pointers_intro#3](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

Inteligentní ukazatele obvykle umožňují přímý přístup k příslušnému nezpracovanému ukazateli. Inteligentní ukazatele standardní knihovny C++ `get` členské funkce pro tento účel a `CComPtr` má veřejnou `p` člena třídy. Díky poskytnutí přímého přístupu k podkladový ukazateli můžete použít inteligentní ukazatel ke správě paměti ve vlastním kódu, a zároveň předávat nezpracovaný ukazatel kódu, který nepodporuje inteligentní ukazatele.

[!code-cpp[smart_pointers_intro#4](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Typy inteligentních ukazatelů

V následující části jsou shrnuty různé druhy inteligentních ukazatelů, které jsou k dispozici v programovacím prostředí Windows, včetně popisu, kdy je vhodné je použít.

### <a name="c-standard-library-smart-pointers"></a>Inteligentní ukazatele knihovny C++ Standard

Tyto inteligentní ukazatele představují první volbu pro zapouzdření ukazatelů do objektů POCO.

- `unique_ptr` Povolují právě jednoho vlastníka podkladového ukazatele. Použijte jako výchozí volbu pro POCO, pokud nejste jisti, že budete potřebovat `shared_ptr`. Lze je přesunout na nového vlastníka, nikoli však kopírovat nebo sdílet. Nahradí `auto_ptr`, který je zastaralý. Porovnat s `boost::scoped_ptr`. `unique_ptr` je malý a efektivní. velikost je jeden ukazatel a podporuje odkazy rvalue pro rychlé vkládání a načítání z kolekcí standardní knihovny C++. Soubor hlaviček: `<memory>`. Další informace najdete v tématu [postupy: vytváření a používání instancí ukazatelů unique_ptr](../cpp/how-to-create-and-use-unique-ptr-instances.md) a [unique_ptr – třída](../standard-library/unique-ptr-class.md).

- `shared_ptr` Referenčně započítaný inteligentního ukazatele. Tento typ je vhodný, když chcete přiřadit jeden nezpracovaný ukazatel více vlastníkům, například, když vrátíte kopii ukazatele z kontejneru, ale chcete zachovat originál. Nezpracovaný ukazatel není odstraněn, dokud všichni `shared_ptr` vlastníky nepřejdou mimo rozsah nebo jinak Nevzdají vlastnictví. Má velikost dva ukazatele; jeden pro objekt a jeden pro sdílený kontrolní blok, který obsahuje počet odkazů. Soubor hlaviček: `<memory>`. Další informace najdete v tématu [postupy: vytváření a používání instancí ukazatelů shared_ptr](../cpp/how-to-create-and-use-shared-ptr-instances.md) a [shared_ptr – třída](../standard-library/shared-ptr-class.md).

- `weak_ptr` Zvláštní případ inteligentní ukazatel pro použití ve spojení s `shared_ptr`. A `weak_ptr` poskytuje přístup k objektu, který je vlastněn jednou nebo více `shared_ptr` instancí, ale se neúčastní počítání odkazů. Použijte ho, chcete-li objekt sledovat, ale nepotřebujete ho ponechat ve stavu alive. Potřebné v některých případech pro přerušení cyklických odkazů mezi `shared_ptr` instancí. Soubor hlaviček: `<memory>`. Další informace najdete v tématu [postupy: vytváření a používání instancí ukazatelů weak_ptr](../cpp/how-to-create-and-use-weak-ptr-instances.md) a [weak_ptr – třída](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>Inteligentní ukazatele pro objekty COM (klasické programování v systému Windows)

Při práci s objekty COM zabalte ukazatele rozhraní do příslušného typu inteligentního ukazatele. Knihovna ATL definuje řadu inteligentních ukazatelů pro různé účely. Můžete také použít `_com_ptr_t` typ inteligentního ukazatele, který kompilátor používá při vytváření obálkových tříd ze souborů .tlb. Jedná se o nejlepší volbu, pokud nechcete zahrnovat hlavičkové soubory ATL.

[CComPtr – třída](../atl/reference/ccomptr-class.md) využit, pokud nemůžete použít knihovnu ATL. Provede součet odkazů pomocí `AddRef` a `Release` metody. Další informace najdete v tématu [postupy: vytvoření a používání instancí objektů CComPtr a CComQIPtr](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[CComQIPtr – třída](../atl/reference/ccomqiptr-class.md) Resembles `CComPtr` , ale také poskytuje zjednodušenou syntaxi pro volání `QueryInterface` v objektech com. Další informace najdete v tématu [postupy: vytvoření a používání instancí objektů CComPtr a CComQIPtr](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Ccomheapptr – třída](../atl/reference/ccomheapptr-class.md) inteligentní ukazatel na objekty, které používají `CoTaskMemFree` k uvolnění paměti.

[Ccomgitptr – třída](../atl/reference/ccomgitptr-class.md) inteligentní ukazatel rozhraní, které jsou získávány z tabulky globálního rozhraní (GIT).

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md) Resembles `CComQIPtr` funkcí, ale nezávisí na hlavičkách ATL.

### <a name="atl-smart-pointers-for-poco-objects"></a>Inteligentní ukazatele ATL pro objekty POCO

Kromě inteligentních ukazatelů pro objekty COM definuje ATL také inteligentní ukazatele a kolekce inteligentních ukazatelů pro objekty POCO. V klasickém programování Windows, jsou tyto typy užitečné alternativy ke kolekcím standardní knihovny C++, zejména v případě, že není požadována přenositelnost kódu nebo pokud nechcete kombinovat modely programování C++ standardní knihovna a ATL.

[Cautoptr – třída](../atl/reference/cautoptr-class.md) inteligentní ukazatel, který vynucuje jedinečné vlastnictví převodem vlastnictví na kopii. Srovnatelné se zastaralou `std::auto_ptr` třídy.

[Cheapptr – třída](../atl/reference/cheapptr-class.md) inteligentní ukazatel pro objekty, které jsou přiřazovány pomocí jazyka C [malloc](../c-runtime-library/reference/malloc.md) funkce.

[Cautovectorptr – třída](../atl/reference/cautovectorptr-class.md) inteligentní ukazatel pro pole, které jsou přiřazovány pomocí `new[]`.

[Cautoptrarray – třída](../atl/reference/cautoptrarray-class.md) třídu, která zapouzdřuje pole `CAutoPtr` elementy.

[Cautoptrlist – třída](../atl/reference/cautoptrlist-class.md) třídu, která zapouzdřuje metody pro práci se seznamem `CAutoPtr` uzly.

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)