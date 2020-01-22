---
title: Atributy vC++
ms.date: 05/06/2019
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: 5967974d419299778e4aadaa235ee21c62e16d34
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518293"
---
# <a name="attributes-in-c"></a>Atributy vC++

C++ Standard definuje sadu atributů a také umožňuje dodavatelům kompilátoru definovat jejich vlastní atributy (v rámci oboru názvů specifického pro dodavatele), ale kompilátory jsou požadovány pro rozpoznání pouze těch atributů definovaných ve standardu.

V některých případech se standardní atributy překrývají s parametry declspec specifickými pro kompilátor. V jazyce C++Visual můžete použít atribut `[[deprecated]]` namísto použití `declspec(deprecated)` a atribut bude rozpoznán jakýmkoli podformou kompilátoru. Pro všechny ostatní parametry declspec, jako je dllimport a dllexport, neexistuje žádný ekvivalent atributu, takže musíte dál používat syntaxi declspec. Atributy neovlivňují systém typů a nezmění význam programu. Kompilátory ignorují hodnoty atributů, které nerozpoznávají.

**Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): v oboru seznamu atributů můžete zadat obor názvů pro všechny názvy s jedním **pomocí** představení:

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>C++Standardní atributy

V jazyce C++ 11 poskytují atributy standardizované možnosti pro anotaci C++ konstrukcí (mimo jiné třídy, funkce, proměnné a bloky) s dalšími informacemi, které mohou nebo nemusí být specifické pro dodavatele. Kompilátor může tyto informace využít ke generování informativních zpráv nebo k použití speciální logiky při kompilování kódu s atributy. Kompilátor ignoruje všechny atributy, které nerozpoznají, což znamená, že nemůžete definovat vlastní atributy pomocí této syntaxe. Atributy jsou uzavřeny dvojitými hranatými závorkami:

```cpp
[[deprecated]]
void Foo(int);
```

Atributy představuje standardizovanou alternativu k rozšířením specifickým pro dodavatele, jako jsou direktivy #pragma, __declspec C++() ( &#95; &#95;vizuál&#95; &#95; ) nebo atribut (GNU). Pro většinu účelů ale budete stále muset použít konstrukce specifické pro konkrétní dodavatele. Standard aktuálně určuje následující atributy, které má vyhovující kompilátor rozpoznat:

- `[[noreturn]]` určuje, že funkce nikdy nevrátí hodnotu; Jinými slovy, vždy vyvolá výjimku. Kompilátor může upravit svá pravidla kompilace pro entity `[[noreturn]]`.

- `[[carries_dependency]]` určuje, že funkce šíří řazení závislosti dat s ohledem na synchronizaci vláken. Atribut lze použít na jeden nebo více parametrů, chcete-li určit, že argument předaný argumentu přenese závislost na tělo funkce. Atribut lze použít pro samotnou funkci, chcete-li určit, že návratová hodnota přenese závislost mimo funkci. Kompilátor může tyto informace použít ke generování efektivnějšího kódu.

- `[[deprecated]]` **Visual Studio 2015 a novější:** určuje, že funkce není určena pro použití, a v budoucích verzích rozhraní knihovny nemusí existovat. Kompilátor může použít k vygenerování informační zprávy, když se klientský kód pokusí zavolat funkci. Dá se použít na deklaraci třídy, definice typu typedef-Name, proměnné, nestatického datového člena, funkce, oboru názvů, výčtu, výčtu nebo specializace šablony.

- `[[fallthrough]]` **Visual Studio 2017 a novější:** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)) atribut `[[fallthrough]]` lze použít v kontextu příkazů [Switch](switch-statement-cpp.md) jako pomocný parametr kompilátoru (nebo kdokoli, kdo čte kód), že chování fallthrough je určeno. Kompilátor společnosti C++ Microsoft aktuálně neupozorňuje na chování fallthrough, takže tento atribut nemá žádný vliv na chování kompilátoru.

- `[[nodiscard]]` **Visual Studio 2017 verze 15,3 a novější:** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)) určuje, že návratová hodnota funkce není určena k zahození. Vyvolává upozornění C4834, jak je znázorněno v následujícím příkladu:

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]` **Visual Studio 2017 verze 15,3 a novější:** (k dispozici s [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)) určuje, že proměnná, funkce, třída, typedef, nestatický datový člen, výčet nebo specializace šablon mohou být záměrně nepoužitelné. Kompilátor neupozorní, pokud není použita entita označená `[[maybe_unused]]`. Entita, která je deklarována bez atributu, může být později znovu deklarována s atributem a naopak. Entita se považuje za označenou jako první deklaraci, která je označena jako analyzovaná, a pro zbytek překladu aktuální jednotky překladu.

## <a name="microsoft-specific-attributes"></a>Atributy specifické pro společnost Microsoft

- `[[gsl::suppress(rules)]]` tento atribut specifický pro společnost Microsoft se používá pro potlačení varování od kontrol, které vynutilí [pokyny pro podporu knihoven (GSL)](https://github.com/Microsoft/GSL) v kódu. Zvažte například tento fragment kódu:

    ```cpp
    int main()
    {
        int arr[10]; // GSL warning 26494 will be fired
        int* p = arr; // GSL warning 26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning 26481 suppressed
            p = q--; // GSL warning 26481 suppressed
        }
    }
    ```

  Tento příklad vyvolává tato upozornění:

  - 26494 (pravidlo typu 5: vždy inicializace objektu.)

  - 26485 (pravidlo hranice 3: žádné pole pro ukazatel Decay)

  - 26481 (pravidlo vazby 1: Nepoužívejte aritmetický ukazatel. Místo toho použijte rozpětí.)

  První dvě upozornění se aktivují při kompilování tohoto kódu s nainstalovaným a aktivovaným nástrojem pro analýzu kódu CppCoreCheck. Ale třetí upozornění se neaktivuje kvůli atributu. Celý profil mezí můžete potlačit zápisem [[GSL:: potlačit (bounds)]] bez zahrnutí konkrétního čísla pravidla. C++ Základní pokyny jsou navržené tak, aby vám pomohly psát lepší a bezpečnější kód. Atribut potlačit usnadňuje vypnutí upozornění, když nejsou žádoucí.
  