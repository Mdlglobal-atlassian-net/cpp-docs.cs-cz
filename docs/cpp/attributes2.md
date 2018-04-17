---
title: Atributy C++ Standard | Microsoft Docs
ms.custom: ''
ms.date: 03/28/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: d2dcce6b0e289588c426792a334ee4ec38d1ab5f
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="attributes-in-c"></a>Atributy v jazyce C++

Standardní C++ definuje sadu atributů a také umožňuje dodavatelům kompilátoru definovat vlastní atributy (v oboru názvů specifické pro dodavatele), ale kompilátory jsou nutné k rozpoznat pouze ty atributy, které jsou definované ve standardu.

V některých případech standardní atributy překrývat s declspec kompilátoru specifické parametry. V jazyce Visual C++, můžete použít `[[deprecated]]` atribut místo použití `declspec(deprecated)` a atribut rozpozná pomocí jakékoli kompilátoru vyhovující. Pro všechny ostatní declspec parametry, jako je například příkazů dllimport a dllexport není jako ještě žádný atribut ekvivalent proto musíte pokračovat v použití declspec syntaxe. Atributy neovlivní systém typů a nemění se význam program. Kompilátory Ignorovat hodnoty atributu, který se nerozpoznali.

**Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): V oboru seznam atributů, můžete zadat obor názvů pro všechny názvy s jedním `using` představení:

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>Atributy C++ Standard

Atributy v C ++ 11, zajištění standardizovaného způsobu umožňuje anotaci konstrukce C++ (včetně mimo jiné třídy, funkce, proměnné a bloky) společně s dalšími informacemi, který může nebo nemusí být specifické pro dodavatele. Kompilátor můžete použít tyto informace k vygenerování informační zprávy, nebo použít zvláštní logiku při kompilaci kódu s atributy. Kompilátor ignoruje všechny atributy, které nelze rozpoznat, což znamená, že nelze definovat vlastní atributy pomocí této syntaxe. Atributy jsou uzavřeny do hranatých závorek dvojité:

```cpp
[[deprecated]]
void Foo(int);
```

Atributy představují standardizované alternativa k rozšíření specifické pro dodavatele, jako je například direktivy jazyka #pragma, __declspec() (Visual C++), nebo &#95; &#95;atribut&#95; &#95; (GNU). Ale bude stále potřebujete použít konstrukce specifické pro dodavatele pro většinu účelů. Standardní aktuálně určuje následující atributy, které by měl rozpoznat vyhovující kompilátoru:

- `[[noreturn]]` Určuje, že funkce nikdy vrátí; jinými slovy vždy vyvolá výjimku. Kompilátor můžete upravit jeho kompilace pravidla pro `[[noreturn]]` entity.

- `[[carries_dependency]]` Určuje, že funkce rozšíří data závislostí řazení s ohledem na synchronizace vláken. Atribut je použít pro jeden nebo více parametrů, chcete-li určit, že argument předaný představuje závislost do tělo funkce. Atribut je použít pro funkci samostatně, chcete-li určit, že návratová hodnota představuje závislost mimo funkci. Kompilátor můžete použít tyto informace pro generování kódu efektivnější.

- `[[deprecated]]` **Visual Studio 2015 a novější:** Určuje, že funkce není určena pro použití a nemusí existovat v budoucích verzích rozhraní knihovny. Kompilátor můžete použít ke generování informační zpráva, když se pokusí kód klienta pro volání funkce. Můžete použít k prohlášení o třídu, název typedef, proměnné, nestatické datový člen, funkce, obor názvů, výčet, enumerátor nebo specializace šablony.  

- `[[fallthrough]]` **Visual Studio 2017 a novější:** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` atribut lze použít v kontextu [přepínač](switch-statement-cpp.md) příkazy jako nápovědu pro kompilátor (nebo každý, kdo čtení kód) určený fallthrough chování. – Kompilátor Visual C++ aktuálně neupozorňuje na fallthrough chování, takže tento atribut má chování kompilátoru žádný vliv.

- `[[nodiscard]]` **Visual Studio 2017 verze 15.3 a novější:** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) určuje, že není určen návratovou hodnotu funkce budou zahozeny. Vyvolá upozornění C4834, jak je uvedeno v následujícím příkladu:

   ```cpp
   [[nodiscard]]
   int foo(int i) { return i * i; }

   int main()
   {
       foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
       return 0;
   }
   ```

- `[[maybe_unused]]` **Visual Studio 2017 verze 15.3 a novější:** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) určuje, že proměnné, funkce, třídu, typedef, nestatické datový člen, výčet nebo specializace šablony záměrně nelze použít. Kompilátor neupozorňuje, když je označený entity `[[maybe_unused]]` nepoužívá. Entita, která je deklarovaná bez atribut lze deklarovat později s atributem a naopak. Entita je považován za označeny po jeho první deklaraci, která je označena se analyzují a zbytek překlad aktuální jednotky překladu.

## <a name="microsoft-specific-attributes"></a>Atributy specifické pro společnost Microsoft

- `[[gsl::suppress(rules)]]` Tento atribut specifické pro společnost Microsoft se používá pro potlačení upozornění z programů, které vynucují [pokyny podpory knihovny (GSL)](https://github.com/Microsoft/GSL) pravidla v kódu. Představte si třeba tento fragment kódu:

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

   V příkladu vyvolá tato upozornění:

   - 26494 (typ pravidla 5: vždy inicializovat objekt.)

   - 26485 (rozsah pravidla 3: žádná pole pro decay ukazatele.)

   - 26481 (pravidlo 1 rozsah: Nepoužívejte aritmetika ukazatele. Značka span místo toho použijte.)

   První dva upozornění fire při kompilaci tento kód pomocí nástroje Analýza kódu CppCoreCheck nainstalovaná a aktivovaná. Ale kvůli atribut není fire třetí upozornění. Celý rozsah profilu můžete potlačit tím, že zápis [[gsl::suppress(bounds)]] bez zahrnutí číslo konkrétní pravidlo. Pokyny pro základní C++ jsou navrženy pro usnadňuje psaní kódu lepší a bezpečnější. Atribut potlačit usnadňuje vypnout upozornění v případě, že nejsou chtěli.
