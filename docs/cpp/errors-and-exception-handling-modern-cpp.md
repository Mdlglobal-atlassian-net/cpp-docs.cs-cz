---
title: Ošetření chyb a výjimek (moderní verze jazyka C++)
ms.date: 05/07/2019
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: bb27a92347b327e22afc4f6bb2fb248c12290cae
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222141"
---
# <a name="errors-and-exception-handling-modern-c"></a>Ošetření chyb a výjimek (moderní verze jazyka C++)

V moderním jazyce C++, ve většině scénářů je použití výjimky upřednostňovaný způsob hlášení a zpracování logických chyb a chyb za běhu. To platí zejména když zásobník může obsahovat několik volání funkce mezi funkce, která zjistí chyby a funkci, která se má kontext k určení, jak ji zpracovat. Výjimky představují formální, dobře definovaný způsob kód, který zjistí chyby, předat tuto informací výše v zásobníku volání.

Chyby programu lze obecně rozdělit do dvou kategorií: chyby logiky, které jsou způsobeny chybou při programování, například Chyba "index je mimo rozsah" a chyby za běhu, které jsou mimo kontrolu programátora, například "není k dispozici síťové služby" došlo k chybě. V programování ve stylu jazyka C a modelu COM zpráv o chybách spravuje tak, že vrací hodnotu, která představuje kód chyby nebo stavovým kódem pro určitou funkci nebo nastavením globální proměnné, který může volající volitelně získat po každém volání funkce pro naleznete v tématu Určuje, zda byly hlášeny chyby. Například programování v modelu COM používá k předání chyby volajícímu návratovou hodnotu HRESULT a rozhraní API systému Win32 má funkci GetLastError k načtení poslední chyby, která byla ohlášena v zásobníku volání. V obou těchto případech je to na volajícím kód rozpoznat a reagovat na něj. Pokud volající nezpracuje explicitně kód chyby, může program spadnout bez varování nebo pokračovat v provádění chybných data a poskytovat nesprávné výsledky.

V moderním jazyce C++ jsou preferovány výjimky z následujících důvodů:

- Výjimka vynutí, aby volající kód rozpoznal chybovou podmínku a zpracoval ji. Neošetřené výjimky zastaví spuštění programu.

- Výjimka přejde k bodu v zásobníku volání, který může chybu zpracovat. Dílčí funkce mohou umožnit přenesení výjimky. Nemají koordinaci s jinými vrstvami.

- Mechanismus uvolnění zásobníku výjimek odstraní všechny objekty v oboru podle přesně definovaných pravidel, jakmile dojde k výjimce.

- Výjimka umožňuje čisté oddělení mezi kódem, který rozpozná chybu a kód, který zpracovává chybu.

Následující zjednodušený příklad zobrazuje syntaxi potřebnou pro vyvolávání a zachycování výjimek v jazyce C++.

```cpp

#include <stdexcept>
#include <limits>
#include <iostream>

using namespace std;

void MyFunc(int c)
{
    if (c > numeric_limits< char> ::max())
        throw invalid_argument("MyFunc argument too large.");
    //...
}

int main()
{
    try
    {
        MyFunc(256); //cause an exception to throw
    }

    catch (invalid_argument& e)
    {
        cerr << e.what() << endl;
        return -1;
    }
    //...
    return 0;
}
```

Výjimky v C++ se podobají těm v jazycích, jako je C# nebo Java. V **zkuste** blokovat, pokud je výjimka *vyvolána* bude *zachycena* prvním přiřazeným **catch** bloku, jehož typ odpovídá typu došlo k výjimce. Jinými slovy spuštění přejde z **throw** příkazu **catch** příkazu. Pokud není nalezen žádný použitelný blok catch, `std::terminate` je vyvolána a program je ukončen. V jazyce C++ může být vyvolán libovolný typ; ale doporučujeme, abyste vyvolali typ odvozený přímo nebo nepřímo ze `std::exception`. V předchozím příkladu, typ výjimky [invalid_argument](../standard-library/invalid-argument-class.md), je definován ve standardní knihovně v [ \<stdexcept – >](../standard-library/stdexcept.md) hlavičkový soubor. C++ neposkytuje a nevyžaduje, **nakonec** blok k Ujistěte se, že jsou všechny prostředky uvolněny, pokud je vyvolána výjimka. Získávání prostředků je idiom inicializace (RAII), který používá inteligentní ukazatele, poskytuje požadované funkce vyčištění prostředků. Další informace najdete v tématu [jak: Návrh pro bezpečnost výjimek](../cpp/how-to-design-for-exception-safety.md). Informace o mechanismu uvolnění zásobníku C++ naleznete v tématu [výjimky a Unwinding zásobníku](../cpp/exceptions-and-stack-unwinding-in-cpp.md).

## <a name="basic-guidelines"></a>Základní pokyny

Robustní zpracování chyby je o něco náročnější v jakémkoli programovacím jazyce. Přestože výjimky poskytují několik funkcí, které podporují dobré zpracování chyb, se nedá udělal všechnu práci za vás. Chcete-li začít využívat výhod mechanismu výjimek, mějte na paměti výjimky při návrhu vašeho kódu.

- Použití nepodmíněných výrazů ke kontrole chyb, které by nikdy neměly vzniknout. Výjimky použijte ke kontrole chyb, které mohou nastat, například chyby při ověřování vstupních parametrů veřejných funkcí. Další informace najdete v tématu v části s názvem **výjimky vs. Kontrolní výrazy**.

- Použijte výjimky, pokud kód, který zpracuje chybu, může být oddělen od kódu, který rozpozná chybu podle jednoho nebo více síťová volání funkce. Zvažte, zda radši nepoužít kódy chyb ve smyčkách výkonově kritického po kód, který zpracovává chyby, těsně spjat s kódem, který je rozpoznává.

- Pro každou funkci, která může vyvolat nebo propagovat výjimku, poskytuje jednu ze tří záruk výjimky: silnou záruku, základní záruku nebo záruku nothrow (noexcept). Další informace najdete v tématu [jak: Návrh pro bezpečnost výjimek](../cpp/how-to-design-for-exception-safety.md).

- Vyvolání výjimky podle hodnoty, jejich zachycení podle reference. Nezachycujte, co nemůžete zpracovat.

- Nepoužívejte specifikace výjimek, které jsou zastaralé v C ++ 11. Další informace najdete v tématu v části s názvem **specifikace výjimek a noexcept**.

- Standardní typy výjimek knihovny použijte, pokud jsou uplatněny. Odvozujte vlastní typy výjimek z [tříd výjimek](../standard-library/exception-class.md) hierarchie.

- Nepovolovat výjimkám unikat z destruktorů nebo funkcí navracení paměti.

## <a name="exceptions-and-performance"></a>Výjimky a výkon

Mechanismus výjimek má minimální vliv zatížení, pokud není vyvolána žádná výjimka. Pokud je vyvolána výjimka, náklady na průchod zásobníku a unwinding jsou zhruba srovnatelné s náklady na volání funkce. Další datové struktury jsou nutné ke sledování zásobníku volání po **zkuste** zadání bloku a další pokyny jsou nezbytné k uvolnění zásobníku, pokud je vyvolána výjimka. Ale ve většině případů náklady na výkon a paměť není důležité. Je nepříznivý vliv výjimek na výkon bude významný pouze v systémech velmi omezenou pamětí, nebo v kritickém pro výkon opakuje cyklus, ve kterém chyba by mohla nastat pravidelně a kód pro vyřešení je těsně spjat s kód, který podává hlášení. V každém případě je možné zjistit skutečné náklady výjimek bez profilování a měření. Dokonce i ve vzácných případech kdy jsou náklady významné, je můžete naváží ji proti zvýšenou správností, jednodušší udržovatelností a dalšími výhodami, které jsou k dispozici v dobře navržené výjimky zásad.

## <a name="exceptions-vs-assertions"></a>Výjimky vs. kontrolní výrazy

Výjimky a kontrolní výrazy jsou dva odlišné mechanismy pro detekci chyb za běhu v programu. Použijte nepodmíněné výrazy pro testování podmínek během vývoje, který by měl mít nikdy hodnotu true, pokud váš kód je správný. Neexistuje žádný smysl zpracovávat takové chyby pomocí výjimky, protože chyby označují, že něco v kódu má být opraveno a nereprezentuje podmínku, která má program obnovit v době běhu. Metoda assert zastaví provedení u příkazu, takže si můžete prohlédnout stav programu v ladicím programu; Výjimka pokračuje v provádění od první vhodné catch obslužné rutiny. Pomocí výjimky chybové stavů, které mohou nastat za běhu i v případě, že váš kód je správný, například "soubor nebyl nalezen" nebo "nedostatek"paměti. Můžete chtít obnovit z těchto podmínek, i v případě obnovení pouze výstupů zprávy do protokolu a ukončení programu. Vždy kontrolujte argumenty pro veřejné funkce pomocí výjimek. I v případě, že je vaše funkce bez chyb, pravděpodobně nemáte úplnou kontrolu nad argumenty, které uživatel může předat do ní.

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>Výjimky jazyka C++ a výjimky Windows SEH

Programy jazyka C i C++ mohou používat strukturovaných výjimek (SEH) mechanismu v operačním systému Windows pro zpracování. Základní pojmy v SEH se podobají těm v C++ výjimky, s tím rozdílem, že SEH používá **__try**, **__except**, a **__finally** vytvoří místo **akci**  a **catch**. V Microsoftu C++ kompilátor (MSVC) C++ výjimky jsou implementovány pro SEH. Při psaní kódu jazyka C++ však použijte synax výjimek C++.

Další informace o knihovnách SEH naleznete v tématu [strukturovaného zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

## <a name="exception-specifications-and-noexcept"></a>Specifikace výjimek a noexcept

Specifikace výjimek byly zavedeny v C++ jako způsob, jak určit výjimky, které může funkce vyvolat. Specifikace výjimek však ukázaly jako problematické v praxi a jsou zastaralé v C ++ 11 koncept standardu. Doporučujeme, abyste nepoužívejte specifikace výjimek s výjimkou `throw()`, což znamená, že funkce umožňuje žádné únikové výjimky. Pokud je nutné použít specifikace výjimek typu `throw(` *typ*`)`, mějte na paměti, že MSVC se liší od standardu určitým způsobem. Další informace najdete v tématu [specifikace výjimek (throw)](../cpp/exception-specifications-throw-cpp.md). `noexcept` Specifikátor byl představen v C ++ 11 upřednostňovaná alternativa k `throw()`.

## <a name="see-also"></a>Viz také:

[Postupy: Rozhraní mezi kódem výjimek a ostatním kódem](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[C++ vás vítá zpět (moderní verze jazyka C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
