---
title: C++ vás vítá zpět (moderní verze jazyka C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 08563f6a67ec7105da688d566d71d8ea15cb8cec
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334622"
---
# <a name="welcome-back-to-c-modern-c"></a>C++ vás vítá zpět (moderní verze jazyka C++)

C++ je jedním z nejpoužívanějších programovacích jazyků na světě. Kvalitně napsané C++ programy jsou rychlé a efektivní. Jazyk je flexibilnější než ostatní jazyky, protože slouží k vytvoření široké škály aplikací, od zábavných a vzrušujících her, přes vysoce výkonný vědecký software, ovladače zařízení, vložené programy a klientské aplikace Windows. Více než 20 let bylo C++ využíváno k řešení problémů, jako je tento a mnoho dalších. Co možná nevíte je, že rostoucí počet programátorů C++ mají složit staromódní programování ve stylu jazyka C včerejška a místo toho používají moderní jazyk C++.

Jeden z původních požadavků jazyka C++ byla zpětná kompatibilita s jazykem C. Od té doby se jazyk C++ vyvinul skrze několik iterací — C s třídami, poté původní specifikací jazyka C++ a pak řadou dalších vylepšení. Z důvodu tohoto dědictví C++ se často označuje jako programovací jazyk více paradigmaty. V jazyce C++ vám pomůžou používat čistě procedurální programování ve stylu C, které zahrnuje surové ukazatele, pole, řetězce znaků zakončených znakem null, vlastní datové struktury a další funkce, které dovolují skvělý výkon, ale mohou také zanášet chyby a složitost.  Protože podobných nástrah je programování ve stylu jazyka C, jeden z cílů při vytvoření jazyka C++ bylo zajistit bezpečnost typů a usnadňují zápis, rozšiřitelnost a údržbu programů. Zpočátku C++ zahrnoval paradigmata programování jako je objektově orientované programování. V průběhu let funkce byly přidány pro určitý jazyk, spolu s široce testovanými standardními knihovnami datových struktur a algoritmů. Je tyto doplňky, které jste provedli moderní styl C++ je to možné.

Moderní jazyk C++ zvýrazňuje:

- Rozsah založený na zásobníku namísto haldy nebo globálního statického oboru.

- Automatické odvození typu namísto explicitních názvů typů.

- Inteligentní ukazatele namísto ukazatelů raw.

- `std::string` a `std::wstring` typy (viz [ \<řetězec >](../standard-library/string.md)) namísto nezpracovaných `char[]` pole.

- [Standardní knihovny C++](../standard-library/cpp-standard-library-header-files.md) kontejnery, jako jsou `vector`, `list`, a `map` namísto polí raw nebo vlastních kontejnerů. Zobrazit [ \<vektoru >](../standard-library/vector.md), [ \<seznamu >](../standard-library/list.md), a [ \<mapy >](../standard-library/map.md).

- Standardní knihovny C++ [algoritmy](../standard-library/algorithm.md) místo ručně kódovaných.

- Výjimky pro hlášení a zpracování podmínek chyby.

- Komunikace mezi vlákny pomocí standardní knihovny C++ bez zámku `std::atomic<>` (viz [ \<atomické >](../standard-library/atomic.md)) namísto jiných mechanismů komunikace mezi vlákny.

- Vložené [lambda funkce](../cpp/lambda-expressions-in-cpp.md) namísto samostatné implementace malé funkce.

- Rozsah smyček for založených na zápis robustnějších smyček, které pracují s pole, kontejnery standardní knihovny C++ a prostředí Windows Runtime kolekcí ve formě `for ( for-range-declaration : expression )`. To je součástí základní jazykové podpory. Další informace najdete v tématu [Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md).

Samotný jazyk C++ prošel také vývojem. Porovnejte následující fragmenty kódu. Tento ukazuje, jak věci mají být používány v C++:

```cpp
#include <vector>

void f()
{
    // Assume circle and shape are user-defined types
    circle* p = new circle( 42 );
    vector<shape*> v = load_shapes();

    for( vector<circle*>::iterator i = v.begin(); i != v.end(); ++i ) {
        if( *i && **i == *p )
            cout << **i << " is a match\n";
    }

    // CAUTION: If v's pointers own the objects, then you
    // must delete them all before v goes out of scope.
    // If v's pointers do not own the objects, and you delete
    // them here, any code that tries to dereference copies
    // of the pointers will cause null pointer exceptions.
    for( vector<circle*>::iterator i = v.begin();
            i != v.end(); ++i ) {
        delete *i; // not exception safe
    }

    // Don't forget to delete this, too.
    delete p;
} // end f()
```

Zde je, jak lze provést totéž v moderním jazyce C++:

```cpp
#include <memory>
#include <vector>

void f()
{
    // ...
    auto p = make_shared<circle>( 42 );
    vector<shared_ptr<shape>> v = load_shapes();

    for( auto& s : v )
    {
        if( s && *s == *p )
        {
            cout << *s << " is a match\n";
        }
    }
}
```

V moderním jazyce C++ nemusíte používat new/delete ani explicitní zpracování výjimek, protože můžete místo toho použít inteligentní ukazatele. Při použití **automaticky** odvození typu a [funkci lambda](../cpp/lambda-expressions-in-cpp.md), můžete napsat kód rychleji, upevnit ho a lépe ho chápat. A range-based **pro** smyčky je přehlednější, jednodušší a méně náchylná k neúmyslným chybám než C-style **pro** smyčky. Často používaný text spolu s minimálními řádky kódu můžete použít k zápisu do aplikace. A ujistěte se, že kód, bezpečným pro výjimky a paměť a mít žádné přidělování a navracení zpět nebo chybové kódy pro řešení.

Moderní jazyk C++ zahrnuje dva druhy polymorfismu: kompilace pomocí šablon a běh prostřednictvím dědičnosti a virtualizace. Je možné kombinovat dva druhy polymorfismů pro velký vliv. Šablona standardní knihovny C++ `shared_ptr` používá virtuální metody k provedení jeho mazání zjevně výmazu typu. Ale nepřehánějte to s využíváním virtualizace pro polymorfismus když šablona je lepší volbou. Šablony mohou být velmi účinné.

Pokud přecházíte na C++ z jiného jazyka, zejména ze spravovaných jazyků, ve kterém se většina typů odkazových typech a velmi málo jsou typy hodnot vědět, že třídy C++ typy hodnot ve výchozím nastavení. Ale můžete je specifikovat jako referenční typy, a povolit tak polymorfní chování podporující objektově orientované programování. Užitečná Perspektiva: typy hodnot jsou informace o paměti a řízení rozložení, typy odkazů jsou další informace o základních tříd a virtuálních funkcí pro podporu polymorfismu. Ve výchozím nastavení jsou typy hodnot kopírovatelné – každá má konstruktor kopie a operátor přiřazení kopie. Při zadávání typu odkazu, nastavte třídu, aby nekopírovatelných – zakažte konstruktor kopie a operátor přiřazení kopie a použijte virtuální destruktor, který podporuje polymorfismus. Typy hodnot jsou také o obsahu, které při jejich kopírování, poskytují dvě nezávislé hodnoty, které můžete upravit samostatně. Ale typy odkazů jsou o identitě – co druh objektu jde – a z tohoto důvodu jsou někdy označovány jako polymorfní typy.

C++ dochází k návratu protože výkon má znovu. Jazyky jako Java a C# jsou vhodné, pokud je důležitá produktivita programátora, ale zobrazit svá omezení při napájení výkon se projeví. Vysoké účinnosti a výkonu, zejména v zařízeních, která mají omezený hardware Nic nepřekoná moderního C++.

Nejen jazyk je moderní, nástroje pro vývoj jsou moc. Visual Studio činí všechny části cyklu vývoje je robustní a efektivní. Zahrnuje nástroje Application Lifecycle Management (ALM), vylepšení IDE, jako například IntelliSense, mechanismů vhodných nástrojů, jako jsou XAML a sestavení, ladění a mnoho dalších nástrojů.

Články v této části dokumentace poskytují podrobné pokyny a osvědčené postupy pro nejdůležitější funkce a postupy při vytváření moderních programy v jazyce C++.

- [C++ – systém typů](../cpp/cpp-type-system-modern-cpp.md)

- [Jednotná inicializace a delegování konstruktorů](../cpp/uniform-initialization-and-delegating-constructors.md)

- [Životní cyklus objektů a Správa prostředků](../cpp/object-lifetime-and-resource-management-modern-cpp.md)

- [Prostředky ve vlastnictví objektů (RAII)](../cpp/objects-own-resources-raii.md)

- [Inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md)

- [Ukazatel na implementaci pro zapouzdření za kompilace](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)

- [Kontejnery](../cpp/containers-modern-cpp.md)

- [Algoritmy](../cpp/algorithms-modern-cpp.md)

- [Řetězec a vstupně-výstupních operací formátování (moderní verze jazyka C++)](../cpp/string-and-i-o-formatting-modern-cpp.md)

- [Ošetření chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md)

- [Přenositelnost u rozhraní ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md)

Další informace najdete v článku Stack Overflow [idiomy v jazyce C++ která se považují za zastaralé v C ++ 11](https://stackoverflow.com/questions/9299101/which-c-idioms-are-deprecated-in-c11).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Výrazy lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Shoda jazyka Visual C++](../visual-cpp-language-conformance.md)