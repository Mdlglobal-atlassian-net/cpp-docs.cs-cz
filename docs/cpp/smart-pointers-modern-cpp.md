---
title: Chytré ukazatele (moderní verze jazyka C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c92a0a6030f8e46fb52beee0bf8fd661b47cdf95
ms.sourcegitcommit: cff1a8a49f0cd50f315a250c5dd27e15c173845f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2018
---
# <a name="smart-pointers-modern-c"></a>Chytré ukazatele (moderní verze jazyka C++)
Při programování pro moderní C++, obsahuje standardní knihovna *inteligentní ukazatele*, které se používají k zajištění programy, které jsou volné paměti a prostředek nevracení a jsou bezpečné pro výjimky.  
  
## <a name="uses-for-smart-pointers"></a>Použití inteligentních ukazatelů  
 Chytré ukazatele jsou definovány v `std` oboru názvů v [ \<paměti >](../standard-library/memory.md) soubor hlaviček. Jsou zásadní význam pro [RAII](../cpp/objects-own-resources-raii.md) nebo *prostředků pořízení je inicializace* programovací stylu. Hlavním cílem tohoto idiomu je zajistit, aby k pořízení prostředků docházelo v okamžiku inicializace objektu tak, aby všechny prostředky pro objekt byly vytvořeny a připraveny v jednom řádku kódu. Z praktického pohledu je hlavní zásadou idiomu RAII přiřadit vlastnictví libovolného prostředku přiděleného haldou – například dynamicky přidělené paměti nebo obslužným rutinám systémového objektu – objektu přidělenému zásobníkem, jehož destruktor obsahuje kód pro odstranění nebo uvolnění prostředku a také případný související čisticí kód.  
  
 Ve většině případů platí, že když inicializujete nezpracovaný ukazatel nebo obslužnou rutinu prostředku ukazující na skutečný prostředek, je třeba předat ukazatel inteligentnímu ukazateli okamžitě. V moderním jazyce C++ se nezpracované ukazatele používají pouze v malých blocích kódu s omezeným rozsahem, smyčkách nebo pomocných funkcích, kde je výkon velmi důležitý a neexistuje možnost záměny vlastnictví.  
  
 Následující příklad porovnává deklaraci nezpracovaného a inteligentního ukazatele.  
  
 [!code-cpp[smart_pointers_intro#1](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]  
  
 Jak je v příkladu vidět, inteligentní ukazatel je šablona třídy, která je deklarována v zásobníku a inicializována pomocí nezpracovaného ukazatele, který odkazuje na objekt přidělený haldou. Po inicializaci inteligentní ukazatel vlastní nezpracovaný ukazatel. To znamená, že inteligentní ukazatel je odpovědný za odstranění paměti, kterou nezpracovaný ukazatel určuje. Destruktor inteligentního ukazatele obsahuje volání pro odstranění. Protože inteligentní ukazatel je deklarován v zásobníku, jeho destruktor je vyvolán, když se inteligentní ukazatel dostane mimo rozsah, i když někde dále v zásobníku dojde k výjimce.  
  
 Přístup k zapouzdřené ukazatele pomocí známých ukazatel operátory, `->` a `*`, která třída chytré ukazatele přetížení vrátit zapouzdřené nezpracovaná ukazatele.  
  
 Idiom inteligentního ukazatele v jazyce C++ se podobá vytvoření objektu v jazycích jako např. C#, kde vytvoříte objekt a necháte systém, aby se ve správný čas postaral o jeho odstranění. Rozdíl je v tom, že na pozadí neběží žádný samostatný systém uvolňování paměti. Paměť je spravována prostřednictvím standardních pravidel oboru C++, takže běhové prostředí je rychlejší a efektivnější.  
  
> [!IMPORTANT]
>  Vždy vytvářejte inteligentní ukazatele na samostatném řádku kódu, nikdy v seznamu parametrů, aby nedocházelo k mírnému úniku prostředků kvůli některým pravidlům přidělování seznamu parametrů.  
  
 Následující příklad ukazuje způsob `unique_ptr` inteligentní ukazatel typu ze standardní knihovny C++ může zapouzdřit ukazatel na velkého objektu.  
  
 [!code-cpp[smart_pointers_intro#2](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]  
  
 Příklad demonstruje následující základní kroky pro použití inteligentních ukazatelů.  
  
1.  Deklarujte inteligentní ukazatel jako automatickou (místní) proměnnou. (Nepoužívejte `new` nebo `malloc` výraz pro inteligentní ukazatele sám sebe.)  
  
2.  U parametru typu zadejte typ odkazování zapouzdřeného ukazatele.  
  
3.  Předat nezpracovaná ukazatel `new`-ed objektu v konstruktoru chytré ukazatele. (Některé funkce nástrojů nebo konstruktory inteligentního ukazatele to provedou za vás.)  
  
4.  Použít přetížené `->` a `*` operátory pro přístup k objektu.  
  
5.  Umožněte inteligentnímu ukazateli odstranit objekt.  
  
 Inteligentní ukazatele jsou navrženy tak, aby byly co nejúčinnější z hlediska paměti i výkonu. Například pouze datový člen v `unique_ptr` je zapouzdřené ukazatele. To znamená, že `unique_ptr` je přesně stejnou velikost jako tento ukazatel čtyři bajtů nebo osm bajtů. Přístup k zapouzdřené ukazatel s použitím chytré ukazatele přetížený * a -> operátory není výrazně pomalejší než přímo přístup k nezpracované ukazatele.  
  
 Inteligentní ukazatele mají své vlastní členské funkce, které jsou přístupné pomocí zápisu „tečka“. Například některé standardní knihovna C++ chytré ukazatele mít resetování členské funkce, která uvolní vlastnictví ukazatele. To je užitečné, pokud chcete uvolnit paměť vlastněnou inteligentním ukazatelem předtím, než se inteligentní ukazatel dostane mimo rozsah platnosti, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[smart_pointers_intro#3](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]  
  
 Inteligentní ukazatele obvykle umožňují přímý přístup k příslušnému nezpracovanému ukazateli. Chytré ukazatele standardní knihovna C++ mít `get` – členská funkce pro tento účel a `CComPtr` má veřejné `p` člen třídy. Díky poskytnutí přímého přístupu k podkladový ukazateli můžete použít inteligentní ukazatel ke správě paměti ve vlastním kódu, a zároveň předávat nezpracovaný ukazatel kódu, který nepodporuje inteligentní ukazatele.  
  
 [!code-cpp[smart_pointers_intro#4](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]  
  
## <a name="kinds-of-smart-pointers"></a>Typy inteligentních ukazatelů  
 V následující části jsou shrnuty různé druhy inteligentních ukazatelů, které jsou k dispozici v programovacím prostředí Windows, včetně popisu, kdy je vhodné je použít.  
  
 **Chytré ukazatele knihovny C++ Standard**  
 Tyto inteligentní ukazatele představují první volbu pro zapouzdření ukazatelů do objektů POCO.  
  
-   `unique_ptr`   
     Povolují právě jednoho vlastníka podkladového ukazatele. Použít jako výchozí volba pro objektů POCO, pokud nejste jisti, že potřebujete `shared_ptr`. Lze je přesunout na nového vlastníka, nikoli však kopírovat nebo sdílet. Nahradí `auto_ptr`, který je zastaralý. Porovnání `boost::scoped_ptr`. `unique_ptr` malé a efektivní; velikost je jeden ukazatel a podporuje odkazy rvalue pro rychlé vložení a načtení ze standardní knihovny C++ kolekcí. Soubor hlaviček: `<memory>`. Další informace najdete v tématu [postupy: vytváření a používání instancí ukazatelů unique_ptr](../cpp/how-to-create-and-use-unique-ptr-instances.md) a [unique_ptr – třída](../standard-library/unique-ptr-class.md).  
  
-   `shared_ptr`   
     Inteligentní ukazatel s počítáním referencí Tento typ je vhodný, když chcete přiřadit jeden nezpracovaný ukazatel více vlastníkům, například, když vrátíte kopii ukazatele z kontejneru, ale chcete zachovat originál. Nezpracovaná ukazatele neodstraní dokud všechny `shared_ptr` vlastníky se nachází mimo obor nebo jinak udělili až vlastnictví. Má velikost dva ukazatele; jeden pro objekt a jeden pro sdílený kontrolní blok, který obsahuje počet odkazů. Soubor hlaviček: `<memory>`. Další informace najdete v tématu [postupy: vytváření a používání instancí ukazatelů shared_ptr](../cpp/how-to-create-and-use-shared-ptr-instances.md) a [shared_ptr – třída](../standard-library/shared-ptr-class.md).  
  
-   `weak_ptr`   
    Chytré ukazatele zvláštní případ pro použití ve spojení s `shared_ptr`. A `weak_ptr` poskytuje přístup k objektu, který je vlastněn jeden nebo více `shared_ptr` instance, ale není součástí počítání odkazů. Použijte ho, chcete-li objekt sledovat, ale nepotřebujete ho ponechat ve stavu alive. V některých případech nutné pro přerušení Kruhové odkazy mezi `shared_ptr` instance. Soubor hlaviček: `<memory>`. Další informace najdete v tématu [postupy: vytváření a používání instancí ukazatelů weak_ptr](../cpp/how-to-create-and-use-weak-ptr-instances.md) a [weak_ptr – třída](../standard-library/weak-ptr-class.md).  
  
 **Chytré ukazatele pro objekty modelu COM (programování Classic Windows)**  
 Při práci s objekty COM zabalte ukazatele rozhraní do příslušného typu inteligentního ukazatele. Knihovna ATL definuje řadu inteligentních ukazatelů pro různé účely. Můžete také `_com_ptr_t` inteligentní ukazatel typu, který kompilátor používá při vytváření Obálka – třídy z soubory .tlb. Jedná se o nejlepší volbu, pokud nechcete zahrnovat hlavičkové soubory ATL.  
  
 [CComPtr – třída](../atl/reference/ccomptr-class.md)  
 Tuto volbu použijte, dokud nenastane situace, že nemůžete použít knihovnu ATL. Provede pomocí při počítání referencí `AddRef` a `Release` metody. Další informace najdete v tématu [postupy: vytvoření a použití CComPtr a CComQIPtr instance](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).  
  
 [CComQIPtr – třída](../atl/reference/ccomqiptr-class.md)  
 Podobá `CComPtr` , ale také poskytuje zjednodušenou syntaxi pro volání `QueryInterface` na objekty modelu COM. Další informace najdete v tématu [postupy: vytvoření a použití CComPtr a CComQIPtr instance](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).  
  
 [CComHeapPtr – třída](../atl/reference/ccomheapptr-class.md)  
 Chytré ukazatele na objekty, které používají `CoTaskMemFree` na uvolnění paměti.  
  
 [CComGITPtr – třída](../atl/reference/ccomgitptr-class.md)  
 Inteligentní ukazatel rozhraní, která se získávají z tabulky globálního rozhraní (GIT).  
  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)  
 Podobá `CComQIPtr` funkcí, ale není závislá na ATL hlavičky.  
  
 **Chytré ukazatele ATL pro objekty objektů POCO**  
 Kromě inteligentních ukazatelů pro objekty COM definuje ATL také inteligentní ukazatele a kolekce inteligentních ukazatelů pro objekty POCO. V classic programování v systému Windows, jsou tyto typy užitečné alternativy standardní knihovna C++ kolekcí, zejména v případě, že kód přenositelnost není povinný, nebo pokud nechcete kombinovat s programovacími modely standardní knihovny C++ a ATL.  
  
 [CAutoPtr – třída](../atl/reference/cautoptr-class.md)  
 Inteligentní ukazatel, který vynucuje jedinečné vlastnictví převodem vlastnictví na kopii. Srovnatelná nepoužívané `std::auto_ptr` třídy.  
  
 [CHeapPtr – třída](../atl/reference/cheapptr-class.md)  
 Chytré ukazatele pro objekty, které jsou přiděleny pomocí C [malloc](../c-runtime-library/reference/malloc.md) funkce.  
  
 [CAutoVectorPtr – třída](../atl/reference/cautovectorptr-class.md)  
 Chytré ukazatele pro pole, které jsou přiděleny pomocí `new[]`.  
  
 [CAutoPtrArray – třída](../atl/reference/cautoptrarray-class.md)  
 Třídy, který zapouzdřuje pole `CAutoPtr` elementy.  
  
 [CAutoPtrList – třída](../atl/reference/cautoptrlist-class.md)  
 Třídy, který zapouzdřuje metody pro práci s seznam `CAutoPtr` uzlů.  
  
## <a name="see-also"></a>Viz také  
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)   
