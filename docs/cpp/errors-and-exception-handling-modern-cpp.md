---
title: Moderní C++ osvědčené postupy pro výjimky a zpracování chyb
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: 85a8bf0f64681387cbee63f273fda5ce93ab7ad5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245869"
---
# <a name="modern-c-best-practices-for-exceptions-and-error-handling"></a>Moderní C++ osvědčené postupy pro výjimky a zpracování chyb

V moderních C++scénářích je ve většině scénářů preferovaný způsob, jak ohlásit a zpracovávat chyby logiky a běhové chyby, použití výjimek. To platí zejména v případě, že zásobník může obsahovat několik volání funkcí mezi funkcí, která detekuje chybu, a funkcí, která má kontext pro informace o tom, jak je zpracovat. Výjimky poskytují formální a jasně definovaný způsob pro kód, který detekuje chyby pro předání informací v zásobníku volání.

Chyby programu jsou obecně rozděleny do dvou kategorií: logické chyby, které jsou způsobeny chybami programování, například chyba "index mimo rozsah", a chyby za běhu, které jsou mimo kontrolu programátora, například "nedostupná síťová služba". Chyba. V programování ve stylu C a v modelu COM je zasílání zpráv o chybách spravováno buď vrácením hodnoty, která představuje chybový kód, nebo stavového kódu pro konkrétní funkci, nebo nastavením globální proměnné, kterou může volající volitelně načíst po každém volání funkce k zobrazení. zda byly chyby hlášeny. Například programování modelu COM používá návratovou hodnotu HRESULT pro sdělování chyb volajícímu a Win32 API má funkci GetLastError k načtení poslední chyby, která byla hlášena zásobníkem volání. V obou těchto případech je až volající rozpoznávat kód a reagovat na něj odpovídajícím způsobem. Pokud volající explicitně nezpracovává kód chyby, může program selhat bez upozornění nebo pokračovat v provádění se špatnými daty a poskytovat nesprávné výsledky.

Výjimky jsou upřednostňovány v C++ moderních případech z následujících důvodů:

- Výjimka vynutí volání kódu pro rozpoznání chybového stavu a jeho zpracování. Neošetřené výjimky zastaví provádění programu.

- Výjimka odkazuje na bod v zásobníku volání, který může chybu zpracovat. Mezilehlé funkce můžou umožnit šíření výjimky. Není nutné je koordinovat s jinými vrstvami.

- Mechanismus uvolnění zásobníku výjimek zničí všechny objekty v rozsahu podle jasně definovaných pravidel po vyvolání výjimky.

- Výjimka umožňuje čisté oddělení mezi kódem, který detekuje chybu, a kódem, který zpracovává chybu.

Následující zjednodušený příklad ukazuje nezbytnou syntaxi pro vyvolání a zachycení výjimek v C++.

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

Výjimky se C++ podobají těm v jazycích, jako je C# například a Java. V bloku **Try** , pokud je *vyvolána* výjimka, bude *zachycena* prvním přidruženým blokem **catch** , jehož typ odpovídá typu výjimky. Jinými slovy, provádění přejde z příkazu **throw** do příkazu **catch** . Pokud se nenajde žádný použitelný blok catch, vyvolá se `std::terminate` a program se ukončí. V C++, může být vyvolán libovolný typ; Nicméně doporučujeme, abyste vyvolali typ odvozený přímo nebo nepřímo z `std::exception`. V předchozím příkladu je typ výjimky [invalid_argument](../standard-library/invalid-argument-class.md)definován ve standardní knihovně v souboru hlaviček [\<stdexcept >](../standard-library/stdexcept.md) . C++neposkytuje a nevyžaduje, aby se zajistilo, že všechny prostředky jsou uvolněny, pokud je vyvolána výjimka. RAII (získání prostředku) idiom, který používá inteligentní ukazatele, poskytuje požadované funkce pro vyčištění prostředků. Další informace naleznete v tématu [How to: Design for Exception Safety](how-to-design-for-exception-safety.md). Informace o mechanismu odvíjení C++ zásobníku naleznete v tématu [výjimky a odvíjení zásobníku](exceptions-and-stack-unwinding-in-cpp.md).

## <a name="basic-guidelines"></a>Základní pokyny

Robustní zpracování chyb je náročné v jakémkoli programovacím jazyce. I když výjimky poskytují několik funkcí, které podporují zpracování dobrých chyb, nemůžou dělat veškerou práci za vás. Aby bylo možné využít výhody mechanismu výjimek, pamatujte při návrhu kódu na výjimky.

- Použijte kontrolní výrazy pro kontrolu chyb, které by nikdy neměly nastat. Použijte výjimky ke kontrole chyb, které mohou nastat, například chyby při ověřování vstupu u parametrů veřejných funkcí. Další informace naleznete v části s názvem **výjimky vs. kontrolní výrazy**.

- Použijte výjimky, pokud kód, který zpracovává chybu, může být oddělen od kódu, který detekuje chybu pomocí jednoho nebo více zasahujících volání funkcí. Zvažte, zda používat chybové kódy místo v cyklech kritických pro výkon, když kód, který zpracovává chybu, je pevně spojený s kódem, který ho detekuje.

- Pro každou funkci, která může vyvolat nebo šířit výjimku, poskytněte jednu ze tří záruk výjimky: silnou záruku, základní záruku, nebo výjimku (s výjimkou). Další informace naleznete v tématu [How to: Design for Exception Safety](how-to-design-for-exception-safety.md).

- Vyvolejte výjimky podle hodnoty a zachyťte je podle odkazu. Nezachyťte, co nemůžete zpracovat.

- Nepoužívejte specifikace výjimek, které jsou zastaralé v C++ 11. Další informace naleznete v části s názvem **Specifikace výjimek a s výjimkou**.

- Použijte standardní typy výjimek knihovny, když se používají. Odvodit typy vlastních výjimek z hierarchie [třídy Exception](../standard-library/exception-class.md) .

- Nepovolujte výjimky pro únik z destruktorů nebo funkcí pro zrušení přidělení paměti.

## <a name="exceptions-and-performance"></a>Výjimky a výkon

Mechanismus výjimek má velmi minimální náklady na výkon, pokud není vyvolána žádná výjimka. Je-li vyvolána výjimka, náklady na průchod zásobníku a unwind je zhruba srovnatelné s náklady na volání funkce. Další datové struktury jsou požadovány ke sledování zásobníku volání po zadání bloku **Try** a další pokyny jsou požadovány pro odvinutí zásobníku, pokud je vyvolána výjimka. Ve většině scénářů ale náklady na výkon a nároky na paměť nejsou významné. Nepříznivý dopad výjimek na výkon je pravděpodobně významný pouze pro velmi náročné systémy, nebo v případě kritických smyček pro výkon, kde je pravděpodobně k chybě často docházet, a kód pro jeho zpracování je pevně spojen s kódem, který je nahlásí. V žádném případě není možné zjistit skutečné náklady na výjimky bez profilování a měření. I ve výjimečných případech, kdy jsou náklady významné, je můžete zvážit oproti zvýšené správnosti, jednodušší údržbě a dalším výhodám, které jsou poskytovány dobře navrženými zásadami výjimek.

## <a name="exceptions-vs-assertions"></a>Výjimky vs. kontrolní výrazy

Výjimky a kontrolní výrazy jsou dva odlišné mechanismy pro detekci běhových chyb v programu. Použijte výrazy pro testování podmínek během vývoje, které by neměly mít nikdy hodnotu true, pokud je veškerý kód správný. Neexistuje žádný bod ke zpracování takové chyby pomocí výjimky, protože chyba indikuje, že něco v kódu musí být opraveno a nereprezentuje podmínku, kterou musí program obnovit v době běhu. Kontrolní výraz zastaví provádění v příkazu, aby bylo možné zkontrolovat stav programu v ladicím programu. výjimka pokračuje v provádění z první odpovídající obslužné rutiny catch. Použijte výjimky pro kontrolu chybových stavů, které mohou nastat v době běhu, i když je kód správný, například "soubor nebyl nalezen" nebo "nedostatek paměti". Můžete chtít provést obnovení z těchto podmínek, a to i v případě, že obnovení pouze vytvoří výstup zprávy do protokolu a ukončí program. Vždy kontrolujte argumenty na veřejné funkce pomocí výjimek. I v případě, že je vaše funkce bezchybná, možná nebudete mít úplnou kontrolu nad argumenty, které jí uživatel může předat.

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>C++výjimky oproti výjimkám Windows SEH

C i C++ programy můžou používat mechanismus strukturovaného zpracování výjimek (SEH) v operačním systému Windows. Koncepty v SEH se podobají těm v C++ výjimkách, s tím rozdílem, že SEH používá **__try**, **__except**a **__finally** konstrukce místo **Try** a **catch**. V kompilátoru Microsoft C++ (MSVC) se C++ výjimky implementují pro SEH. Při psaní C++ kódu však použijte syntaxi C++ výjimky.

Další informace o SEH naleznete v tématu [strukturované zpracování výjimek (C/C++)](structured-exception-handling-c-cpp.md).

## <a name="exception-specifications-and-noexcept"></a>Specifikace výjimek a s výjimkou

Specifikace výjimek byly představeny C++ jako způsob, jak určit výjimky, které může funkce vyvolat. Nicméně specifikace výjimek ukázaly problematický postup a jsou zastaralé v konceptu standardu C++ 11. Doporučujeme, abyste nepoužívali specifikace výjimek s výjimkou `throw()`, což naznačuje, že funkce neumožňuje únik žádné výjimky. Pokud je nutné použít specifikace výjimek typu `throw(`*typ*`)`, uvědomte si, že MSVC odkládá ze standardu v určitých ohledech. Další informace naleznete v tématu [Specifikace výjimek (throw)](exception-specifications-throw-cpp.md). `noexcept` specifikátor je představena v jazyce C++ 11 jako upřednostňovaná alternativa k `throw()`.

## <a name="see-also"></a>Viz také:

[Postupy: Rozhraní mezi kódem výjimek a ostatním kódem](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
