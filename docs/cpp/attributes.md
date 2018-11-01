---
title: Atributy v jazyce C++
ms.date: 06/01/2018
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: a4d24324165f3cce60d259adf6e3d21638296cf8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471822"
---
# <a name="attributes-in-c"></a>Atributy v jazyce C++

Standard jazyka C++ definuje sadu atributů a také umožňuje dodavatelům kompilátor definovat vlastní atributy (v oboru názvů specifického pro dodavatele), ale je potřeba kompilátory rozpoznat pouze tyto atributy, které jsou definované ve standardu.

V některých případech se standardní atributy překrývat s parametry declspec specifických pro kompilátor. V jazyce Visual C++, můžete použít `[[deprecated]]` atribut namísto použití `declspec(deprecated)` a atribut bude rozpoznán kompilátorem jakékoli splňující podmínky. Pro všechny ostatní declspec parametry, jako je například dllimport a dllexport není dosud žádný ekvivalent atribut tak nutné nadále používat declspec syntaxe. Atributy nemají vliv na systém typů a nemění se význam programu. Kompilátory ignorují atribut hodnoty, které není povědomý.

**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): V rámci seznam atributů, můžete zadat obor názvů pro všechny názvy pomocí jediného **pomocí** představení:

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>Standard jazyka C++ atributy

V C ++ 11 atributy poskytují standardizovaný způsob, jak anotovat konstruktory jazyka C++ (včetně, ale jiné třídy, funkce, proměnné a bloky) společně s dalšími informacemi, který může nebo nemusí být specifické pro výrobce. Kompilátor můžete použít tyto informace ke generování informační zprávy, nebo použít zvláštní logiku při kompilaci kódu s atributy. Kompilátor ignoruje všechny atributy, které nebylo rozpoznáno, což znamená, že nelze definovat vlastní atributy pomocí této syntaxe. Atributy jsou uzavřeny v dvojitých hranatými závorkami:

```cpp
[[deprecated]]
void Foo(int);
```

Atributy představují standardizované alternativou k rozšíření specifické pro výrobce, jako je například direktivy #pragma __declspec() (Visual C++), nebo &#95; &#95;atribut&#95; &#95; (GNU). Nicméně stále musíte použít konstrukce specifické pro výrobce pro většinu účelů. Standardní aktuálně určuje následující atributy, které by měl rozpoznávat vyhovující kompilátoru:

- `[[noreturn]]` Určuje, že funkce nikdy nevrátí; jinými slovy vždy vyvolá výjimku. Kompilátor můžete upravit jeho kompilace pravidla pro `[[noreturn]]` entity.

- `[[carries_dependency]]` Určuje, že funkce šíří data závislostí řazení s ohledem na synchronizaci vláken. Atribut lze použít na jeden nebo více parametrů, chcete-li určit, že argument předaný přenáší závislostí do těla funkce. Atribut lze použít pro funkce samotná, chcete-li určit, že návratová hodnota představuje závislost mimo funkci. Kompilátor může použít tyto informace pro generování kódu efektivnější.

- `[[deprecated]]` **Visual Studio 2015 a novější:** Určuje, že funkce není určena pro použití a nemusí existovat v budoucích verzích rozhraní knihovny. Kompilátor může být využit k vygenerování informační zpráva, když kód klienta se pokusí o volání funkce. Můžete použít k deklaraci třídy, název typedef, proměnné, nestatický datový člen, funkce, obor názvů, výčtu, enumerátor nebo specializace šablony.

- `[[fallthrough]]` **Visual Studio 2017 a novější:** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` atribut lze použít v kontextu [přepnout](switch-statement-cpp.md) příkazy jako Nápověda pro kompilátor (nebo každému, kdo čte kód), která je určena fallthrough chování. Kompilátor Visual C++ aktuálně neupozorňuje fallthrough chování, takže tento atribut nemá žádný účinek chování kompilátoru.

- `[[nodiscard]]` **Visual Studio 2017 verze 15.3 nebo novější:** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) určuje, že návratová hodnota funkce není určena pro zahodí. Vyvolá upozornění C4834, jak je znázorněno v tomto příkladu:

   ```cpp
   [[nodiscard]]
   int foo(int i) { return i * i; }

   int main()
   {
       foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
       return 0;
   }
   ```

- `[[maybe_unused]]` **Visual Studio 2017 verze 15.3 nebo novější:** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) určuje, že proměnné, funkce, třídy, definice typedef, nestatický datový člen, výčtu nebo specializace šablony záměrně nelze použít. Kompilátor nevyvolá upozornění při označení entity `[[maybe_unused]]` se nepoužívá. Entita, která je deklarována bez atributu můžete později se znova deklarovat s atributem a naopak. Entity se považuje za označené po jeho první deklaraci, která je označena se analyzují a zbytek překlad aktuální překladové jednotce.

## <a name="microsoft-specific-attributes"></a>Atributy specifické pro společnost Microsoft

- `[[gsl::suppress(rules)]]` Tento atribut specifické pro společnost Microsoft se používá pro potlačení varování z programů, které vynucují [pokyny pro podporu knihovny (GSL)](https://github.com/Microsoft/GSL) pravidla v kódu. Zvažte například tento fragment kódu:

    ```cpp
    void main()
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

   V příkladu vyvolává tato upozornění:

   - 26494 (typ pravidla 5: objekt vždy inicializujte.)

   - 26485 (rozsah pravidla 3: rozklad pole na ukazatel.)

   - 26481 (hranice Rule 1: Nepoužívejte aritmetiku ukazatele. Použijte rozsah.)

   První dva upozornění vyvolat při kompilaci tohoto kódu s nástrojem analýza kódu CppCoreCheck nainstalovaná a aktivovaná. Ale třetí upozornění neaktivuje z důvodu atribut. Celý profil můžete potlačit pomocí zápisu [[gsl::suppress(bounds)]] bez zahrnutí příslušné pravidlo číslo. Podle dokumentu C++ Core Guidelines jsou navrženy k usnadnění psaní kódu lepší a bezpečnější. Atribut potlačit usnadňuje Chcete-li vypnout upozornění, pokud nejsou potřebná.