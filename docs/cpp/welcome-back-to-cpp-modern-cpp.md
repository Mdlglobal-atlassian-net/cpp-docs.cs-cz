---
title: C++ vás vítá zpět (moderní verze jazyka C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 1f59395001722244cb407ef07ed8a301f08df85b
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624762"
---
# <a name="welcome-back-to-c-modern-c"></a>C++ vás vítá zpět (moderní verze jazyka C++)

C++je jedním z nejčastěji používaných programovacích jazyků na světě. Dobře zapsané C++ programy jsou rychlé a efektivní. Jazyk je flexibilnější než ostatní jazyky, protože ho můžete použít k vytvoření široké škály aplikací, od zábavy a zajímavých her až po vysoce výkonný vědecký software, pro ovladače zařízení, vložené programy a klientské aplikace systému Windows. Po víc než 20 let C++ se používá k řešení problémů, jako jsou tyto a spousta dalších. To, co neznáte, je, že rostoucí C++ počet programátorů rozloží dowdyé programování ve stylu C včera a má místo toho C++ používají moderní.

Jeden z původních požadavků pro C++ byl zpětně kompatibilní s jazykem C. C++ Od té doby se vyvinulo několik iterací – C s třídami, pak původní C++ specifikace jazyka a potom mnoho dalších vylepšení. Z důvodu tohoto dědictví C++ se často označuje jako vícenásobný programovací jazyk. V C++nástroji můžete provádět čistě procedurální programování ve stylu jazyka C, které zahrnuje nezpracované ukazatele, pole, řetězce znaků zakončené hodnotou null, vlastní datové struktury a další funkce, které mohou umožňovat skvělý výkon, ale mohou také zadávat chyby a složitost.  Vzhledem k tomu, že programování ve stylu jazyka C je fraught s nástrah, jedním z nalezených C++ cílů pro bylo, aby programy byly typově bezpečné a snadněji zapisovaly, rozšířily a udržovaly. Na začátku, C++ vydaná přidaná programovací paradigmata jako objektově orientované programování. V průběhu let byly funkce přidány do jazyka společně s vysoce testovanými standardními knihovnami datových struktur a algoritmů. Jsou to tyto dodatky, které vedly C++ k modernímu stylu.

Moderní C++ zvýraznění:

- Rozsah založený na zásobníku místo haldy nebo statického globálního rozsahu.

- Automatické odvození typu namísto explicitních názvů typů.

- Inteligentní ukazatele namísto nezpracovaných ukazatelů.

- typy `std::string` a `std::wstring` (viz [\<řetězec >](../standard-library/string.md)) místo nezpracovaných `char[]` polí.

- Knihovny standardních knihoven jako `vector`, `list`a `map` místo nezpracovaných polí nebo vlastních kontejnerů. [ C++ ](../standard-library/cpp-standard-library-header-files.md) Viz [\<vector >](../standard-library/vector.md), [\<seznamu >](../standard-library/list.md)a [\<map](../standard-library/map.md)>.

- C++Standardní [algoritmy](../standard-library/algorithm.md) knihovny místo ručních kódovaných.

- Výjimky, pro hlášení a zpracování chybových podmínek.

- Bezplatná komunikace mezi vlákny pomocí C++ standardní knihovny `std::atomic<>` (viz [\<atomická >](../standard-library/atomic.md)) namísto jiných mechanismů komunikace mezi vlákny.

- Vložené [funkce lambda](../cpp/lambda-expressions-in-cpp.md) namísto malých funkcí implementovaných samostatně.

- Pro smyčky založené na rozsahu pro zápis robustnějších smyček, které pracují s poli, C++ standardními kontejnery knihovny a kolekcemi prostředí Windows Runtime ve formuláři `for ( for-range-declaration : expression )`. Toto je součást základní jazykové podpory. Další informace naleznete v tématu [Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md).

Vyvinuli jsme také samotný C++ jazyk. Porovnejte následující fragmenty kódu. Tento příklad ukazuje, jak se používají C++:

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

Tady je postup, jak se stejné věc dosahuje C++v moderním:

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

V moderním C++případě nemusíte používat nové a odstranit nebo explicitní zpracování výjimek, protože místo toho můžete použít inteligentní ukazatele. Když použijete funkce **automatického** typu odvození a [lambda](../cpp/lambda-expressions-in-cpp.md), můžete napsat kód rychleji, posílit a pochopit ho lépe. A **pro** smyčku založené na rozsahu je čistící, jednodušší použití a méně náchylná k nezamýšleným chybám než **ve stylu C** smyčky. Můžete použít často používaný text s minimálními řádky kódu k zápisu vaší aplikace. A můžete provádět tyto výjimky bezpečného kódu a paměti a nemusíte se s nimi zabývat žádným kódem přidělení/zrušením.

Moderní C++ společnost zahrnuje dva druhy polymorfismu: kompilace, prostřednictvím šablon a běhu prostřednictvím dědičnosti a virtualizace. Můžete kombinovat dva druhy polymorfismu a skvělého efektu. Šablona C++ standardní knihovny `shared_ptr` používá interní virtuální metody k provedení zjevně snadného typu mazání. Ale nepoužívejte virtualizaci pro polymorfismus, když je šablona lepší volbou. Šablony můžou být velmi výkonné.

Pokud přecházíte C++ z jiného jazyka, zejména ze spravovaného jazyka, ve kterém je většina typů odkazových typů, a velmi málo jsou typy hodnot, víte, C++ že třídy jsou typy hodnot standardně. Ale můžete je zadat jako referenční typy pro povolení polymorfního chování, které podporuje objektově orientované programování. Užitečná perspektiva: typy hodnot jsou více o ovládacím prvku paměť a rozložení, typy odkazů jsou více o základních třídách a virtuálních funkcích pro podporu polymorfismu. Ve výchozím nastavení jsou typy hodnot zkopírovány – každý má kopírovací konstruktor a operátor přiřazení kopie. Pokud zadáte typ odkazu, zpřístupněte třídu jako nekopírovatelné – zakažte kopírovací konstruktor a operátor přiřazení kopie – a použijte virtuální destruktor, který podporuje polymorfismus. Typy hodnot jsou také informace o obsahu, který při zkopírování poskytují dvě nezávislé hodnoty, které lze upravit samostatně. Ale typy odkazů jsou o identitě – jaký typ objektu je – a z tohoto důvodu jsou někdy označovány jako polymorfní typy.

C++má návratu, protože je opět zapnutý král. Jazyky jako Java a C# jsou vhodné, pokud je důležitá produktivita programátora, ale zobrazují se jejich omezení, pokud jsou výkon a výkon nejdůležitější. Pro zajištění vysoké efektivity a výkonu, zejména na zařízeních s omezeným hardwarem, C++není nic Beats moderní.

Nejedná se o moderní jazyk, ale také o vývojářských nástrojích. Visual Studio umožňuje robustní a efektivní všechny části vývojového cyklu. Zahrnuje nástroje pro správu životního cyklu aplikací (ALM), rozšíření IDE, jako je IntelliSense, mechanizmy přívětivé nástrojem, jako je XAML a sestavování, ladění a mnoho dalších nástrojů.

Články v této části dokumentace poskytují obecné pokyny a osvědčené postupy pro nejdůležitější funkce a techniky pro psaní moderních C++ programů.

- [C++Systém typů](../cpp/cpp-type-system-modern-cpp.md)

- [Jednotná inicializace a delegování konstruktorů](../cpp/uniform-initialization-and-delegating-constructors.md)

- [Životnost objektů a Správa prostředků](../cpp/object-lifetime-and-resource-management-modern-cpp.md)

- [Prostředky ve vlastnictví objektů (RAII)](../cpp/objects-own-resources-raii.md)

- [Inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md)

- [Ukazatel na implementaci pro zapouzdření při kompilaci](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)

- [Kontejnery](../cpp/containers-modern-cpp.md)

- [Algoritmy](../cpp/algorithms-modern-cpp.md)

- [Formátování řetězců a I/O (moderní C++)](../cpp/string-and-i-o-formatting-modern-cpp.md)

- [Zpracování chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md)

- [Přenositelnost v hranicích ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md)

Další informace najdete v článku o Stack Overflow, [které C++ idiomy jsou zastaralé v c++ 11](https://stackoverflow.com/questions/9299101/which-c-idioms-are-deprecated-in-c11).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Výrazy lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Tabulka C++ shody jazyka Microsoft](../overview/visual-cpp-language-conformance.md)