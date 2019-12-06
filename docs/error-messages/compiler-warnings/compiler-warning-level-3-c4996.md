---
title: Upozornění kompilátoru (úroveň 3) C4996
description: Vysvětluje, proč dochází k C4996 upozornění kompilátoru a popisuje, co s nimi dělat.
ms.date: 11/25/2019
f1_keywords:
- C4996
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
ms.openlocfilehash: 98662dc0b5439c1f8857e4f2ad259793a4d03e41
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898779"
---
# <a name="compiler-warning-level-3-c4996"></a>Upozornění kompilátoru (úroveň 3) C4996

Váš kód používá funkci, člen třídy, proměnnou nebo typedef, která je označena jako *zastaralá*. Symboly jsou zastaralé pomocí modifikátoru [__declspec (nepoužívané)](../../cpp/deprecated-cpp.md) nebo c++ 14 [\[\[zastaralá\]\]](../../cpp/attributes.md) atribut. Skutečná zpráva Upozornění C4996 je určena modifikátorem `deprecated` nebo atributem deklarace.

> [!IMPORTANT]
> Toto upozornění je vždy záměrné zprávy od autora hlavičkového souboru, který deklaruje symbol. Nepoužívejte nepoužívané symboly bez porozumění důsledkům.

## <a name="remarks"></a>Poznámky

Mnoho funkcí, členské funkce, funkce šablon a globální proměnné v knihovnách sady Visual Studio jsou *zastaralé*. Některé, například specifické funkce POSIX a Microsoft, jsou zastaralé, protože nyní mají jiný upřednostňovaný název. Některé funkce běhové knihovny jazyka C jsou zastaralé, protože jsou nezabezpečené a mají bezpečnější variantu. Ostatní jsou zastaralé, protože jsou zastaralé. Zprávy vyřazení obvykle obsahují navrhovanou náhradu za zastaralé funkce nebo globální proměnnou.

## <a name="turn-off-the-warning"></a>Vypnutí upozornění

Pro vyřešení problému s C4996 obvykle doporučujeme změnit kód. Místo toho použijte navrhované funkce a globální proměnné. Pokud pro účely přenositelnosti potřebujete použít existující funkce nebo proměnné, můžete upozornění vypnout.

Chcete-li vypnout upozornění pro konkrétní řádek kódu, použijte direktivu [Warning](../../preprocessor/warning.md) , `#pragma warning(suppress : 4996)`.

Chcete-li vypnout upozornění v rámci souboru, použijte direktivu Warning, `#pragma warning(disable : 4996)`.

Chcete-li upozornění v rámci sestavení příkazového řádku globálně vypnout, použijte možnost příkazového řádku [/wd4996](../../build/reference/compiler-option-warning-level.md) .

Vypnutí upozornění pro celý projekt v integrovaném vývojovém prostředí sady Visual Studio:

1. Otevřete dialogové okno **stránky vlastností** projektu. Informace o tom, jak používat dialogové okno stránky vlastností, najdete na [stránce vlastností](../../build/reference/property-pages-visual-cpp.md).

1. Vyberte stránku **Vlastnosti konfigurace** > stránka pro **upřesnění** **jazyka C/C++**  > .

1. Úpravou vlastnosti **Zakázat specifická upozornění** přidejte `4996`. Kliknutím na **tlačítko OK** změny aplikujte.

Můžete také použít makra preprocesoru pro vypnutí určitých specifických tříd upozornění na vyřazení používané v knihovnách. Tato makra jsou popsána níže.

Definování makra preprocesoru v aplikaci Visual Studio:

1. Otevřete dialogové okno **stránky vlastností** projektu. Informace o tom, jak používat dialogové okno stránky vlastností, najdete na [stránce vlastností](../../build/reference/property-pages-visual-cpp.md).

1. Rozbalte **Vlastnosti konfigurace > předprocesory C/C++ >** .

1. Do vlastnosti **Definice preprocesoru** přidejte název makra. Kliknutím na **tlačítko OK** uložte a znovu sestavte projekt.

Chcete-li definovat makro pouze v konkrétních zdrojových souborech, přidejte řádek, například `#define EXAMPLE_MACRO_NAME` před všechny řádky, které obsahují hlavičkový soubor.

Tady jsou některé běžné zdroje upozornění a chyb C4996:

## <a name="posix-function-names"></a>Názvy funkcí POSIX

**Název POSIX pro tuto položku je zastaralý. Místo toho použijte ISO C a C++ vyhovující název:** *New-name*. **Podrobnosti najdete v online nápovědě.**

Společnost Microsoft přejmenovala některé funkce knihovny POSIX a specifické pro společnost Microsoft v CRT tak, aby splňovaly omezení C99 a C++ 03 u rezervovaných a globálních implementací definovaných názvů. *Pouze názvy jsou zastaralé, nikoli samotné funkce*. Ve většině případů byla do názvu funkce přidána úvodní podtržítko pro vytvoření vyhovujícího názvu. Kompilátor vydá upozornění na zastaralost pro původní název funkce a navrhne preferovaný název.

Chcete-li tento problém vyřešit, obvykle doporučujeme změnit kód tak, aby místo toho používal navrhované názvy funkcí. Nicméně aktualizované názvy jsou specifické pro společnost Microsoft. Pokud pro účely přenositelnosti potřebujete použít stávající názvy funkcí, můžete tato upozornění vypnout. Funkce jsou stále k dispozici v knihovně pod původními názvy.

Chcete-li vypnout upozornění na zastaralost pro tyto funkce, definujte makro preprocesoru **\_CRT\_NONSTDC\_žádná\_upozornění**. Toto makro můžete definovat na příkazovém řádku včetně možnosti `/D_CRT_NONSTDC_NO_WARNINGS`.

## <a name="unsafe-crt-library-functions"></a>Nezabezpečené funkce knihovny CRT

**Tato funkce nebo proměnná může být nebezpečná. Místo toho zvažte použití** *bezpečné verze* **. Pokud chcete zakázat zastaralost, použijte \_CRT\_zabezpečení\_žádná\_upozornění.  Podrobnosti najdete v online nápovědě.**

Společnost Microsoft zastarala o C++ některé funkce knihovny CRT a standardní a Globals, protože jsou k dispozici bezpečnější verze. Většina zastaralých funkcí umožňuje nezaškrtnutou možnost přístupu pro čtení nebo zápis do vyrovnávacích pamětí. Jejich zneužití může vést k vážným problémům se zabezpečením. Kompilátor vydá upozornění na vyřazení pro tyto funkce a navrhne upřednostňovanou funkci.

K vyřešení tohoto problému doporučujeme místo toho použít funkci nebo proměnnou *s bezpečnými verzemi* . Někdy nemůžete pro účely přenositelnosti nebo zpětné kompatibility nemůžete. Pečlivě ověřte, že není možné vyrovnávací paměť přepsat nebo přečtení, aby se v kódu stala. Pak můžete upozornění vypnout.

Pokud chcete vypnout upozornění na zastaralost pro tyto funkce v CRT, definujte **\_crt\_zabezpečení\_žádná\_upozornění**.

Pokud chcete vypnout upozornění na zastaralé globální proměnné, definujte **\_CRT\_zabezpečení\_žádná\_upozornění\_Globals**.

Další informace o těchto zastaralých funkcích a globálních funkcích naleznete v tématu [funkce zabezpečení v knihovně CRT](../../c-runtime-library/security-features-in-the-crt.md) a [bezpečné knihovny C++ : standardní knihovna](../../standard-library/safe-libraries-cpp-standard-library.md).

## <a name="unsafe-standard-library-functions"></a>Nezabezpečené funkce standardní knihovny

__std::__ *function_name* __::\_nezaškrtnutou\_iterátory::\_vyřadit z volání std::__ *function_name* **s parametry, které mohou být nebezpečné – tento hovor spoléhá na volajícího, aby zkontroloval, jestli jsou předané hodnoty správné. Pokud chcete toto upozornění zakázat, použijte-D\_SQL\_zabezpečení\_žádná\_upozornění. Podívejte se na dokumentaci, jak používat C++ Zaškrtnuté iterátory Visual.**

Toto upozornění se zobrazí v sestavení ladění, C++ protože některé standardní funkce šablon knihovny nekontrolují správnost parametrů. Často je to proto, že není k dispozici dostatek informací pro funkci pro kontrolu hranic kontejneru. Nebo, protože iterátory mohou být pomocí funkce nesprávně použity. Toto upozornění vám pomůže identifikovat tyto funkce, protože mohou být zdrojem vážných děr zabezpečení v programu. Další informace najdete v tématu [kontrolované iterátory](../../standard-library/checked-iterators.md).

Toto upozornění se například zobrazí v režimu ladění, Pokud předáte ukazatel na prvek `std::copy`namísto jednoduchého pole. Chcete-li tento problém vyřešit, použijte vhodně deklarované pole, aby knihovna mohla kontrolovat rozsahy polí a provádět kontrolu hranic.

```cpp
// C4996_copyarray.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_copyarray.cpp
#include <algorithm>

void example(char const * const src) {
    char dest[1234];
    char * pdest3 = dest + 3;
    std::copy(src, src + 42, pdest3); // C4996
    std::copy(src, src + 42, dest);   // OK, copy can tell that dest is 1234 elements
}
```

Několik algoritmů standardní knihovny se aktualizovalo tak, aby ve verzi C++ 14 byly verze s duálním rozsahem. Používáte-li duální verze rozsahu, druhý rozsah zajišťuje kontrolu potřebných hranic:

```cpp
// C4996_containers.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_containers.cpp
#include <algorithm>

bool example(
    char const * const left,
    const size_t leftSize,
    char const * const right,
    const size_t rightSize)
{
    bool result = false;
    result = std::equal(left, left + leftSize, right); // C4996
    // To fix, try this form instead:
    // result = std::equal(left, left + leftSize, right, right + rightSize); // OK
    return result;
}
```

Tento příklad ukazuje několik způsobů, jak lze použít standardní knihovnu ke kontrole využití iterátoru a v případě, že nekontrolované použití může být nebezpečné:

```cpp
// C4996_standard.cpp
// compile with: cl /EHsc /W4 /MDd C4996_standard.cpp
#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    // NOTE: This applies only when raw arrays are
    // given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (i.e. an overrun triggers undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(),
        stdext::make_checked_array_iterator(p7, 16),
        [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator
    // is marked as checked in debug mode, but it performs no checking,
    // so an overrun triggers undefined behavior
    int a8[16];
    int * p8 = a8;
    transform( v.begin(), v.end(),
        stdext::make_unchecked_array_iterator(p8),
        [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

Pokud jste ověřili, že váš kód nemůže mít chybu přetečení vyrovnávací paměti, můžete toto upozornění vypnout. Pokud chcete vypnout upozornění pro tyto funkce, definujte **\_sql\_zabezpečení\_žádná\_upozornění**.

## <a name="checked-iterators-enabled"></a>Zaškrtnuté iterátory povoleny

K C4996 může dojít také v případě, že nepoužíváte zaškrtnutý iterátor, pokud je `_ITERATOR_DEBUG_LEVEL` definováno jako 1 nebo 2. Je nastavené na 2 ve výchozím nastavení pro sestavení režimu ladění a na hodnotu 0 pro maloobchodní buildy. Další informace najdete v tématu [kontrolované iterátory](../../standard-library/checked-iterators.md).

```cpp
// C4996_checked.cpp
// compile with: /EHsc /W4 /MDd C4996_checked.cpp
#define _ITERATOR_DEBUG_LEVEL 2

#include <algorithm>
#include <iterator>

using namespace std;
using namespace stdext;

int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 10, 11, 12 };
    copy(a, a + 3, b + 1);   // C4996
    // try the following line instead:
    // copy(a, a + 3, checked_array_iterator<int *>(b, 3));   // OK
}
```

## <a name="unsafe-mfc-or-atl-code"></a>Nezabezpečený kód knihovny MFC nebo ATL

K C4996 může dojít, pokud používáte funkce MFC nebo ATL, které byly z bezpečnostních důvodů zastaralé.

Chcete-li tento problém vyřešit, důrazně doporučujeme, abyste místo toho změnili kód na použití aktualizovaných funkcí.

Informace o tom, jak potlačit tato upozornění, najdete v tématu [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings).

## <a name="obsolete-crt-functions-and-variables"></a>Zastaralé funkce a proměnné CRT

**Tato funkce nebo proměnná byla nahrazena novější knihovnou nebo funkcí operačního systému. Místo toho zvažte použití** *new_item* **. Podrobnosti najdete v online nápovědě.**

Některé funkce knihovny a globální proměnné jsou zastaralé jako zastaralé. Tyto funkce a proměnné mohou být v budoucí verzi knihovny odebrány. Kompilátor vydá upozornění na zastaralost pro tyto položky a navrhne upřednostňovanou alternativu.

Chcete-li tento problém vyřešit, doporučujeme změnit kód tak, aby používal navrhovanou funkci nebo proměnnou.

Pokud chcete pro tyto položky vypnout upozornění na zastaralost, definujte **\_CRT\_ZAstaralá\_žádná\_upozornění**. Další informace naleznete v dokumentaci pro vystaralou funkci nebo proměnnou.

## <a name="marshaling-errors-in-clr-code"></a>Zařazování chyb v kódu CLR

K C4996 může také dojít při použití zařazovací knihovny CLR. V tomto případě je C4996 chyba, nikoli upozornění. K této chybě dochází, pokud použijete [marshal_as](../../dotnet/marshal-as.md) k převodu mezi dvěma datovými typy, které vyžadují [třídu marshal_context](../../dotnet/marshal-context-class.md). Tato chyba se může zobrazit také v případě, že zařazovací knihovna nepodporuje převod. Další informace o zařazovací knihovně naleznete [v tématu Přehled zařazování v C++ ](../../dotnet/overview-of-marshaling-in-cpp.md).

Tento příklad generuje C4996, protože zařazovací knihovna vyžaduje kontext pro převod z `System::String` na `const char *`.

```cpp
// C4996_Marshal.cpp
// compile with: /clr
// C4996 expected
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = marshal_as<const char*>( message );
   return 0;
}
```

## <a name="example-user-defined-deprecated-function"></a>Příklad: uživatelem definovaná vystaralá funkce

Nepoužívané atributy můžete použít ve vlastním kódu k upozornění volajících, když už nedoporučujete používat určité funkce. V tomto příkladu se C4996 generuje na dvou místech: jeden pro řádek, na kterém je vystaralá funkce deklarována, a jednu pro řádek, kde je funkce použita.

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

[[deprecated]]
void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```
