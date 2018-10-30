---
title: Upozornění (úroveň 3) C4996 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4996
dev_langs:
- C++
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ed220aad7dd90ff2b5ca97c4cf5160fd4d00ed4
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204571"
---
# <a name="compiler-warning-level-3-c4996"></a>Kompilátor upozornění (úroveň 3) C4996

Kompilátor zjistil nepoužívané deklarace. **Toto upozornění je vždy záměrné zprávu od autora knihovny nebo zahrnuté záhlaví souboru, že byste neměli používat deprecated symbol bez nutnosti porozumět důsledky.** Skutečné upozornění je určená modifikátor vyřazení nebo atribut v lokalitě deklarace.

Toto jsou některé běžné C4996 zprávy generované běhové knihovny jazyka C a standardní knihovny, ale o vyčerpávající seznam. Pomocí odkazů nebo si přečtěte o způsoby, chcete-li tento problém vyřešit, nebo chcete-li vypnout upozornění.

- [POSIX název pro tuto položku je zastaralý. Místo toho použijte název splňující podmínky ISO C a C++: *nový_název*. Najdete v online nápovědě pro podrobnosti.](#posix-function-names)

- [Tato funkce nebo proměnná může nebezpečné. Zvažte použití *safe_version* místo. Chcete-li zakázat vyřazení, použijte \_CRT\_SECURE\_ne\_upozornění.  Najdete v online nápovědě pro podrobnosti.](#unsafe-crt-library-functions)

- ["std::*Název_funkce*::\_Unchecked\_iterátory::\_Deprecate" volání std::*Název_funkce*s parametry, které mohou nebezpečné – toto volání spoléhá na že volající zkontroluje správnost předaných hodnot. Tato upozornění zakážete pomocí parametru -D_SCL_SECURE_NO_WARNINGS. O tom, jak používat Visual C++ Checked Iterators naleznete v dokumentaci](#unsafe-standard-library-functions)

- [Tato funkce nebo proměnná byla nahrazena novější funkce knihovny nebo operačního systému. Zvažte použití *new_item* místo. Najdete v online nápovědě pro podrobnosti.](#obsolete-crt-functions-and-variables)

## <a name="cause"></a>příčina

C4996 nastane, pokud kompilátor narazí, funkce nebo proměnná, která je označena jako [zastaralé](../../cpp/deprecated-cpp.md) pomocí `__declspec(deprecated)` modifikátor, nebo když se pokusíte o přístup k funkci, člen třídy nebo definice typedef, která má C ++ 14 [ \[ \[zastaralé\] \] ](../../cpp/attributes.md) atribut. Můžete použít `__declspec(deprecated)` modifikátor nebo `[[deprecated]]` atribut sami v knihovnách nebo hlavičkové soubory k upozornění klientů o zastaralé funkce, proměnné, členy a definice TypeDef.

## <a name="remarks"></a>Poznámky

Mnoho funkcí, členské funkce, šablony funkce a globální proměnné v knihovnách v sadě Visual Studio jsou označeny jako *zastaralé*. Tyto funkce jsou zastaralé, protože může pojmenovali jinak upřednostňované, může být nebezpečné nebo mít bezpečnější variantu, nebo může být zastaralá. Řada zpráv o zastarání zahrnují navrhované náhrada za zastaralé funkce nebo globální proměnné.

Chcete-li vyřešit tento problém, obvykle doporučujeme že po provedení změny kódu místo toho použít navrhované bezpečnější nebo aktualizované funkce a globální proměnné. Pokud je potřeba použít existující funkce nebo proměnné z důvodu přenositelnosti, upozornění můžete vypnout.

### <a name="to-turn-the-warning-off-without-fixing-the-issue"></a>Chcete-li vypnout upozornění bez opravy problému

Upozornění pro konkrétního řádku kódu můžete vypnout pomocí [upozornění](../../preprocessor/warning.md) – Direktiva pragma, `#pragma warning(suppress : 4996)`. Můžete také vypnout upozornění v rámci souboru pomocí direktivy pragma upozornění `#pragma warning(disable : 4996)`.

Můžete vypnout upozornění globálně v sestaveních příkazového řádku s použitím **/wd4996** možnost příkazového řádku.

Chcete-li vypnout upozornění pro celý projekt v integrovaném vývojovém prostředí sady Visual Studio:

- Otevřít **stránky vlastností** dialogové okno pro váš projekt. Informace o tom, jak pomocí dialogového okna stránky vlastností naleznete v tématu [stránky vlastností](../../ide/property-pages-visual-cpp.md).
- Vyberte **vlastnosti konfigurace**, **C/C++**, **Upřesnit** stránky.
- Upravit **zakázat specifická upozornění** vlastnost přidat `4996`. Zvolte **OK** změny.

Chcete-li vypnout určité konkrétní třídy upozornění na zastaralost používají v knihovnách můžete také použít makra preprocesoru. Tato makra jsou popsané níže.

Chcete-li definovat makro preprocesoru v sadě Visual Studio:

- Otevřít **stránky vlastností** dialogové okno pro váš projekt. Informace o tom, jak pomocí dialogového okna stránky vlastností naleznete v tématu [stránky vlastností](../../ide/property-pages-visual-cpp.md).
- Rozbalte **vlastnosti konfigurace > C/C++ > preprocesor**.
- V **Definice preprocesoru** vlastnost, přidejte název makra. Zvolte **OK** uložte a pak znovu sestavit projekt.

Chcete-li definovat makro pouze v konkrétní zdrojové soubory, přidejte řádek `#define EXAMPLE_MACRO_NAME` před všech řádků, které obsahuje soubor hlaviček.

## <a name="specific-c4996-messages"></a>C4996 specifická

Tady jsou některé běžné zdroje C4996 upozornění a chyb.

### <a name="posix-function-names"></a>Názvy funkcí v rámci specifikace POSIX

**POSIX název pro tuto položku je zastaralý. Místo toho použijte název splňující podmínky ISO C a C++:** *nový_název*. **Najdete v online nápovědě pro podrobnosti.**

Microsoft má přejmenovat, některé funkce POSIX v souladu s normou C99 a C ++ 03 pravidla pro názvy definované implementací globální funkce CRT. Jenom původní názvy POSIX jsou zastaralé, ne samotné funkce. Ve většině případů vedoucí znaku podtržítka přidal do názvu funkce POSIX k vytvoření názvu standardní splňující podmínky. Kompilátor vyvolá upozornění na zastaralost pro původní název funkce a navrhne upřednostňovaný název.

Chcete-li vyřešit tento problém, obvykle doporučujeme že po provedení změny kódu místo toho použít názvy navrhované funkce. Aktualizované názvy jsou však specifické pro společnost Microsoft. Pokud je potřeba použít existující názvy funkcí pro přenositelnost z důvodů, můžete vypnout tato upozornění. Funkce POSIX jsou stále k dispozici v knihovně v části původní názvy.

Chcete-li vypnout upozornění na zastaralost pro tyto funkce, definujte makro preprocesoru  **\_CRT\_NONSTDC\_ne\_upozornění**. Můžete definovat toto makro v příkazovém řádku zahrnutím možnost `/D_CRT_NONSTDC_NO_WARNINGS`.

### <a name="unsafe-crt-library-functions"></a>Nebezpečné funkce knihovny CRT

**Tato funkce nebo proměnná může nebezpečné. Zvažte použití** *safe_version* **místo. Chcete-li zakázat vyřazení, použijte \_CRT\_SECURE\_ne\_upozornění.  Najdete v online nápovědě pro podrobnosti.**

Microsoft se nepoužívá, některé funkce CRT a standardní knihovny C++ a globální prvky ve prospěch bezpečnější verze. Zastaralé funkce ve většině případů povolit zaškrtnuté políčko pro čtení nebo zápisu do vyrovnávací paměti, což může způsobit vážné bezpečnostní problémy. Kompilátor vyvolá upozornění na zastaralost pro tyto funkce a navrhne Preferovaná funkce.

Chcete-li vyřešit tento problém, doporučujeme, abyste použili funkci nebo proměnnou *safe_version* místo. Pokud jste ověřili, že není možné přepisování vyrovnávací paměti nebo overread vyskytuje v kódu a nelze změnit kód pro přenositelnost z důvodů, můžete vypnout upozornění.

Chcete-li vypnout upozornění na zastaralost pro tyto funkce v CRT, definujte  **\_CRT\_SECURE\_ne\_upozornění**. Chcete-li vypnout upozornění na zastaralé globální proměnné, definujte  **\_CRT\_SECURE\_ne\_upozornění\_GLOBALS**. Další informace o těchto zastaralé funkce a globální prvky najdete v tématu [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md) a [bezpečné knihovny: standardní knihovny C++](../../standard-library/safe-libraries-cpp-standard-library.md).

### <a name="unsafe-standard-library-functions"></a>Nezabezpečený funkce standardní knihovny

__"std::__*Název_funkce*__::\_Unchecked\_iterátory::\_Deprecate" volání std::__*Název_funkce* **s parametry, které mohou nebezpečné – toto volání spoléhá na že volající zkontroluje správnost předaných hodnot. Chcete-li zakázat toto upozornění, použijte -D\_SCL\_SECURE\_ne\_upozornění. O tom, jak používat Visual C++ Checked Iterators naleznete v dokumentaci**

Toto upozornění se zobrazí v sestavení ladění, protože některé šablony funkce standardní knihovny C++ nekontrolují správnost parametrů. Ve většině případů jde, protože není dostatek informací je k dispozici funkce pro kontrolu hranice kontejneru, nebo iterátory může být použit s funkce nesprávně. Toto upozornění vám pomůže určit tyto funkce používá, protože mohou být zdrojem vážné bezpečnostní díry ve svém programu. Další informace najdete v tématu [Checked Iterators](../../standard-library/checked-iterators.md).

Například toto upozornění se zobrazí v režimu ladění v případě předat ukazatel element `std::copy` místo prostého pole. Chcete-li vyřešit tento problém, použijte odpovídajícím způsobem deklarované pole, tak knihovny můžete zkontrolovat mezí pole a proveďte kontrolu hranic.

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

Se několik algoritmů standardní knihovny aktualizovat tak, aby verze "duální rozsah" v C ++ 14. Pokud používáte duální rozsah verzí, poskytuje druhého rozsahu nezbytné kontroly hranic:

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

Tento příklad ukazuje několik způsobů další standardní knihovny můžou sloužit k kontrola využití iterátoru, a pokud není zaškrtnuto využití může být nebezpečné:

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

Pokud jste ověřili, že váš kód nemůže mít funkce standardní knihovny, které aktivuje toto upozornění při přetečení vyrovnávací paměti, můžete toto upozornění vypněte. Chcete-li vypnout upozornění pro tyto funkce, definujte  **\_SCL\_SECURE\_ne\_upozornění**.

### <a name="checked-iterators-enabled"></a>Checked – iterátory povoleno

C4996 může také dojít, pokud nepoužíváte kontrolovaný iterátor při kompilaci s `_ITERATOR_DEBUG_LEVEL` definována jako 1 nebo 2. To je nastavena na 2 ve výchozím nastavení pro sestavení s režimem ladění a na hodnotu 0 pro prodejní buildy. Zobrazit [Checked Iterators](../../standard-library/checked-iterators.md) Další informace.

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

### <a name="unsafe-mfc-or-atl-code"></a>Nezabezpečený MFC nebo ATL kód

C4996 se také použití knihovny MFC nebo ATL funkce, které se přestaly z bezpečnostních důvodů.

Chcete-li vyřešit tento problém, důrazně doporučujeme že po provedení změny kódu místo toho použít aktualizované funkce.

Informace o tom, jak tato upozornění potlačit, naleznete v tématu [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings).

### <a name="obsolete-crt-functions-and-variables"></a>Zastaralé CRT funkce a proměnné

**Tato funkce nebo proměnná byla nahrazena novější funkce knihovny nebo operačního systému. Zvažte použití** *new_item* **místo. Najdete v online nápovědě pro podrobnosti.**

Některé funkce knihovny a globální proměnné jsou zastaralé jako zastaralé. Tyto funkce a proměnné může být odebrán v budoucí verzi knihovny. Kompilátor vyvolá upozornění na zastaralost pro tyto položky a navrhne upřednostňovaná alternativa.

Chcete-li vyřešit tento problém, doporučujeme, abyste že po provedení změny kódu pro použití navrhované funkce nebo proměnná.

Chcete-li vypnout upozornění na zastaralost pro tyto položky, definovat  **\_CRT\_zastaralé\_ne\_upozornění**. Další informace najdete v tématu v dokumentaci k zastaralé funkci nebo proměnnou.

### <a name="marshalling-errors-in-clr-code"></a>Zařazování chybami v kódu CLR

C4996 se také při použití zařazovací knihovny CLR. V tomto případě je C4996 chybou, nikoli upozorněním. K této chybě dochází, když použijete [marshal_as](../../dotnet/marshal-as.md) k převodu mezi dvěma datovými typy, které vyžadují [marshal_context Class](../../dotnet/marshal-context-class.md). Tato chyba může zobrazit také když zařazovací knihovna nepodporuje převod. Další informace o zařazovací knihovně naleznete v tématu [Overview of Marshaling in C++](../../dotnet/overview-of-marshaling-in-cpp.md).

Tento příklad vygeneruje C4996, protože zařazovací knihovna vyžaduje kontext pro převod z `System::String` k `const char *`.

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

## <a name="example-user-defined-deprecated-function"></a>Příklad: Uživatelem definované zastaralé funkce

Volající upozornit, když už doporučujeme použití určitých funkcí můžete použít atribut nepoužívané ve svém vlastním kódu. V tomto příkladu se vygeneruje C4996 pro řádek, na kterém je deklarována zastaralé funkce a pro řádek, na kterém je tato funkce použita.

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

__declspec(deprecated) void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```
