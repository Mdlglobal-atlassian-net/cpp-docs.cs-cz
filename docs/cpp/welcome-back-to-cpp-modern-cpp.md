---
title: "Vítejte zpět do C++ (moderní verze jazyka C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 45cb4bb1537f7d897b1dd53ada413e73a54162ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="welcome-back-to-c-modern-c"></a>C++ vás vítá zpět (moderní verze jazyka C++)
C++ je jednou z nejčastěji používané programovací jazyky na světě. Rychlé a efektivní nejsou správně vytvořená C++ programy. Jazyk je flexibilnější než ostatní jazyky, protože slouží k vytvoření širokou škálu aplikace – z fun a zajímavé hry, vědecké softwaru vysoce výkonné, ovladače zařízení, vložené programy a klientských aplikací systému Windows. Víc než 20 let C++ jsou využívány k řešení problémů, jako jsou tyto a mnohé další. Co možná nevíte, je, že se zvyšující číslo programátory v jazyce C++ mít přeloženy až dowdy programování stylu jazyka C včerejšek a místo toho donned moderní verze jazyka C++.  
  
 Jedním z původní požadavků pro jazyk C++ byl zpětnou kompatibilitu s jazykem C. Od té doby se má C++ vyvinuly prostřednictvím několika iterací – C s třídami, pak původní specifikace jazyka C++ a pak mnoho dalších vylepšení. Z důvodu této dědictví C++ se často označuje jako více zlepší programovací jazyk. V jazyce C++ můžete to udělat čistě procesní programování stylu jazyka C, který zahrnuje nezpracovaná ukazatele, pole, řetězce ukončené hodnotou null znaků, vlastní datové struktury a další funkce, které může povolit vysoký výkon, ale můžete také vytvořit chyby a složitost.  Vzhledem k tomu, že programování stylu jazyka C s perils takovéto fraught, jedním z cílů jejího založení pro jazyk C++ byl bezpečnost typů a usnadňují zápisu, rozšíření a údržbu. aby se aplikace. Časná na C++ kterých je založena programovací vzorů například objektově orientované programování. V průběhu let funkce přidané jazyk, společně s vysoce testována standardní knihovny datové struktury a algoritmů. Tyto doplňky, které udělali styl moderní C++ možné je.  
  
 Klade důraz moderní verze jazyka C++:  
  
-   Na základě zásobníku rozsah místo heap nebo statické globální rozsah.  
  
-   Odvození typu automaticky namísto názvů explicitního typu.  
  
-   Chytré ukazatele místo nezpracovaná ukazatele.  
  
-   `std::string`a `std::wstring` typy (viz [ \<řetězec >](../standard-library/string.md)) namísto nezpracovaná `char[]` pole.  
  
-   [Standardní knihovna C++](../standard-library/cpp-standard-library-header-files.md) jako kontejnery `vector`, `list`, a `map` místo nezpracovaná pole nebo vlastní kontejnerů. V tématu [ \<vektoru >](../standard-library/vector.md), [ \<seznamu >](../standard-library/list.md), a [ \<mapy >](../standard-library/map.md).  
  
-   Standardní knihovna C++ [algoritmy](../standard-library/algorithm.md) místo ručně programového těch, které jsou.  
  
-   Výjimky pro sestavu a popisovač chybové stavy.  
  
-   Zámek bez komunikaci mezi vlákno pomocí standardní knihovna C++ `std::atomic<>` (najdete v části [ \<atomic >](../standard-library/atomic.md)) namísto jiných mechanismů komunikace mezi vlákno.  
  
-   Vložené [lambda funkce](../cpp/lambda-expressions-in-cpp.md) místo malé funkce implementována samostatně.  
  
-   Na základě rozsahu pro smyčky zápis robustnější cykly, které pracují se pole, kontejnery standardní knihovna C++ a prostředí Windows Runtime kolekce ve tvaru `for ( for-range-declaration : expression )`. Toto je část základní jazyková podpora. Další informace najdete v tématu [na základě rozsahu pro příkaz (C++)](../cpp/range-based-for-statement-cpp.md).  
  
 Je také odvozen jazyka C++, sám sebe. Porovnejte následující fragmenty kódu. Tato ukazuje, jak použít věcí v C++:  
  
```cpp  
// circle and shape are user-defined types  
circle* p = new circle( 42 );   
vector<shape*> v = load_shapes();  
  
for( vector<circle*>::iterator i = v.begin(); i != v.end(); ++i ) {  
    if( *i && **i == *p )  
        cout << **i << " is a match\n";  
}  
  
for( vector<circle*>::iterator i = v.begin();  
        i != v.end(); ++i ) {  
    delete *i; // not exception safe  
}  
  
delete p;  
```  
  
 Zde je, jak se provádí samé v moderní verze jazyka C++:  
  
```cpp  
#include <memory>  
#include <vector>  
// ...  
// circle and shape are user-defined types  
auto p = make_shared<circle>( 42 );  
vector<shared_ptr<shape>> v = load_shapes();  
  
for( auto& s : v ) {  
    if( s && *s == *p )  
        cout << *s << " is a match\n";  
} 
```  
  
 V moderní verze jazyka C++ nemusíte používat nový nebo odstranění nebo zpracování, protože se místo toho používají chytré ukazatele explicitní výjimek. Při použití `auto` zadejte odvození a [lambda funkce](../cpp/lambda-expressions-in-cpp.md), můžete napsat kód rychlejší, posílit ho a pochopit lepší. A `for_each` je čisticí, snadněji používat a méně náchylná k neočekávaným chybám než `for` smyčky. Standardní společně s minimálním řádků kódu můžete použít k zápisu aplikace. A můžete nastavit tento kód výjimky bezpečných a bezpečných paměti a obsahovat žádné kódy přidělování a navracení zpět nebo chyba řešit.  
  
 Moderní verze jazyka C++ zahrnuje dva druhy polymorfismus: kompilaci, prostřednictvím šablon a běhu prostřednictvím dědičnosti a virtualizace. Je možné kombinovat dva druhy polymorfismus na velký vliv. Standardní knihovna C++ šablony `shared_ptr` používá interní virtuální metody k provádění jeho zjevně snadné typ vymazání. Ale nepoužívejte přepsání virtualizaci pro polymorfismus při šablony je vhodnější. Šablony může být velmi mocné.  
  
 Pokud jste přicházející do C++ z jiném jazyce, zejména ze spravovaných jazyk, ve kterém většinu typů jsou odkazové typy a jen v několika jsou typy hodnot vědět, že třídy C++ typy hodnot ve výchozím nastavení. Ale můžete je zadat jako odkazové typy povolit polymorfní chování, která podporuje objektově orientované programování. Užitečné perspektivy: Další informace o paměti a řízení rozložení, odkazové typy jsou další informace o základní třídy a virtuální funkce pro podporu polymorfismus jsou typy hodnot. Ve výchozím nastavení jsou typy hodnot kopírovatelná – každá má kopírovacího konstruktoru a operátor přiřazení kopírování. Když zadáváte odkazového typu, je třída bez kopírovatelná – zakázat kopírovacího konstruktoru a operátor přiřazení pro kopírování – a používat virtuální destruktor, která podporuje polymorfismus. Typy hodnot jsou také o obsahu, které při kopírování, získáte dvě nezávislé hodnoty, které lze upravit samostatně. Odkazové typy jsou o identitě, ale – co druh objektu je – a z tohoto důvodu se někdy označují jako polymorfní typy.  
  
 C++ obrody dochází, protože power je král znovu. Jazyky jako Java a C# jsou vhodné, když je důležité programátory produktivitu, ale po prvořadý a celkového výkonu se zobrazit jejich omezením. Pro vysoce účinné a výkonu, zejména u zařízení, která mají omezenou hardware Nic nepřekoná moderní verze jazyka C++.  
  
 Jenom je moderní jazyk, jsou nástroje pro vývoj, příliš. [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]Díky všech součástí cyklu vývoje robustní a efektivní. Obsahuje nástroje pro správu životního cyklu aplikací (ALM), vylepšení IDE jako IntelliSense, nástroj friendly mechanismy jako XAML a sestavování, ladění a mnoho dalších nástrojů.  
  
 Články v této části dokumentace poskytují souhrnné pokyny a osvědčené postupy pro nejdůležitější funkce a techniky pro zápis moderní C++ – programy.  
  
-   [C++ – systém typů](../cpp/cpp-type-system-modern-cpp.md)  
  
-   [Jednotná inicializace a delegování konstruktorů](../cpp/uniform-initialization-and-delegating-constructors.md)  
  
-   [Životní cyklus objektů a Správa prostředků](../cpp/object-lifetime-and-resource-management-modern-cpp.md)  
  
-   [Vlastní prostředky objektů (RAII)](../cpp/objects-own-resources-raii.md)  
  
-   [Chytré ukazatele](../cpp/smart-pointers-modern-cpp.md)  
  
-   [Pimpl pro zapouzdření kompilace](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)  
  
-   [Kontejnery](../cpp/containers-modern-cpp.md)  
  
-   [Algoritmy](../cpp/algorithms-modern-cpp.md)  
  
-   [Řetězec a vstupně-výstupních operací formátování (moderní verze jazyka C++)](../cpp/string-and-i-o-formatting-modern-cpp.md)  
  
-   [Ošetření chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md)  
  
-   [Přenositelnost u rozhraní ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md)  
  
 Další informace najdete v článku StackOverflow [co idioms C++ jsou zastaralé v C ++ 11](http://go.microsoft.com/fwlink/?LinkId=402836)  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Lambda – výrazy](../cpp/lambda-expressions-in-cpp.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)  
 [Přizpůsobení jazyka Visual C++](../visual-cpp-language-conformance.md)  
