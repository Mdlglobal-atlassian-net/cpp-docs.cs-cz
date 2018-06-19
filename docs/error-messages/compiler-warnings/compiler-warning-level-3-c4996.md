---
title: Kompilátoru (úroveň 3) upozornění C4996 | Microsoft Docs
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
ms.openlocfilehash: a6af8a8ff3cde50ea8b196e7f293874998547ec0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315396"
---
# <a name="compiler-warning-level-3-c4996"></a>C4996 kompilátoru upozornění (úroveň 3)

Kompilátor byla zjištěna nepoužívané deklarace. **Toto upozornění je vždy záměrné zprávu od autora do knihovny nebo zahrnuté záhlaví souboru byste neměli používat, je zastaralé symbol možné důsledky, neměňte.** Skutečné upozornění je určena modifikátor vyřazení nebo atributu v lokalitě deklarace. 

Toto jsou některé běžné C4996 zprávy generované běhové knihovny jazyka C a standardní knihovny, ale nejsou vyčerpávající seznam. Na následujících odkazech nebo přečtěte si způsoby, jak vyřešit problém, nebo k vypnutí upozornění. 

- [POSIX název pro tuto položku je zastaralý. Místo toho použijte název vyhovující ISO C a C++: *nový_název*. V nápovědě online podrobnosti.](#posix-function-names)

- [Tato funkce nebo proměnná může nebezpečný. Zvažte použití *safe_version* místo. Chcete-li zakázat vyřazení, použijte \_CRT\_zabezpečeného\_ne\_upozornění.  V nápovědě online podrobnosti.](#unsafe-crt-library-functions)

- [' – std::*Název_funkce*::\_Unchecked\_iterátory::\_Deprecate' volat na – std::*Název_funkce*s parametry, které může nebezpečné - toto volání spoléhá na volající zkontrolujte správnost předané hodnoty. Tato upozornění zakážete pomocí parametru -D_SCL_SECURE_NO_WARNINGS. Najdete v dokumentaci o tom, jak používat Visual C++, iterátory zaškrtnutí.](#unsafe-standard-library-functions)

- [Tato funkce nebo proměnná byla nahrazena novější funkce knihovny nebo operačního systému. Zvažte použití *new_item* místo. V nápovědě online podrobnosti.](#obsolete-crt-functions-and-variables)

## <a name="cause"></a>příčina

C4996 nastane, když kompilátor narazí funkce nebo proměnná, která je označena jako [zastaralé](../../cpp/deprecated-cpp.md) pomocí `__declspec(deprecated)` modifikátor, nebo při pokusu o přístup k funkci, člen třídy nebo typedef, který má C ++ 14 [ \[ \[zastaralé\] \] ](../../cpp/attributes.md) atribut. Můžete použít `__declspec(deprecated)` modifikátor nebo `[[deprecated]]` atribut sami knihovny nebo hlavičkových souborů k upozornění klientů o zastaralé funkce, proměnné, definice TypeDef nebo členy.

## <a name="remarks"></a>Poznámky

Mnoho funkcí, členské funkce, funkce šablon a globální proměnné v knihovnách v sadě Visual Studio jsou označeny jako *zastaralé*. Tyto funkce jsou zastaralé, protože může mít jiný název upřednostňované, může být nebezpečné nebo obsahují bezpečnější variantu, nebo může být zastaralý. Mnoho vyřazení zprávy obsahují návrhy náhradou za zastaralé funkce nebo – globální proměnná.

Chcete-li tento problém vyřešit, obvykle doporučujeme že měnit kód místo toho použít navrhované bezpečnější nebo aktualizované funkce a globální proměnné. Pokud potřebujete použít existující funkce nebo proměnné přenositelnost z důvodů, může být vypnuto upozornění.

### <a name="to-turn-the-warning-off-without-fixing-the-issue"></a>Chcete-li upozornění vypnout bez opravy problému

Upozornění pro konkrétní řádek kódu můžete vypnout pomocí [upozornění](../../preprocessor/warning.md) – Direktiva pragma, `#pragma warning(suppress : 4996)`. Můžete také vypnout upozornění v souboru s použitím – Direktiva pragma upozornění, `#pragma warning(disable : 4996)`.

Můžete vypnout upozornění globálně v sestavení příkazového řádku pomocí **/wd4996** možnost příkazového řádku.

Chcete-li vypnout upozornění pro celý projekt v integrovaném vývojovém prostředí sady Visual Studio:

- Otevřete **stránky vlastností** dialogové okno pro váš projekt. Informace o tom, jak používat dialogové okno stránky vlastností najdete v tématu [stránky vlastností](../../ide/property-pages-visual-cpp.md).
- Vyberte **vlastnosti konfigurace**, **C/C++**, **Upřesnit** stránky.
- Upravit **zakázat konkrétní varování** vlastnost přidat `4996`. Zvolte **OK** proveďte změny.

Makra preprocesoru také můžete vypnout určité určité třídy upozornění na zastaralost používá v knihovnách. Tyto makra jsou popsané níže.

Chcete-li definovat makro preprocesoru v sadě Visual Studio:

- Otevřete **stránky vlastností** dialogové okno pro váš projekt. Informace o tom, jak používat dialogové okno stránky vlastností najdete v tématu [stránky vlastností](../../ide/property-pages-visual-cpp.md).
- Rozbalte položku **vlastnosti konfigurace > C/C++ > Preprocessor**.
- V **Definice preprocesoru** vlastnost, přidejte název makra. Zvolte **OK** uložíte, a pak znovu sestavte projekt.

K definování makra pouze v konkrétní zdrojové soubory, přidejte řádek `#define EXAMPLE_MACRO_NAME` před všech řádků, které obsahuje soubor hlaviček.

## <a name="specific-c4996-messages"></a>Zprávy specifické pro C4996

Zde jsou některé běžné zdroje C4996 upozornění a chyb.

### <a name="posix-function-names"></a>Názvy POSIX – funkce

**POSIX název pro tuto položku je zastaralý. Místo toho použijte název vyhovující ISO C a C++:** *nový_název*. **V nápovědě online podrobnosti.**

Microsoft má přejmenovat, některé funkce POSIX v CRT tak, aby odpovídala C99 a C ++ 03 pravidla pro názvy definované implementací globální funkce. Jenom původní názvy POSIX jsou zastaralé, není funkce sami. Ve většině případů do název funkce POSIX vytvoří standardní vyhovující název byl přidán úvodní podtržítka. Kompilátor vydá upozornění vyřazení pro původní název funkce a navrhne upřednostňovaný název.

Chcete-li tento problém vyřešit, obvykle doporučujeme že měnit kód místo toho použít názvy návrhy funkcí. Aktualizované názvy jsou však specifické pro společnost Microsoft. Pokud budete muset použít stávající názvy funkcí pro přenositelnost důvodů, je tato upozornění vypnout. Funkce POSIX jsou stále k dispozici v knihovně v části původní názvy.

Chcete-li vypnout upozornění na zastaralost pro tyto funkce, definujte makro preprocesoru  **\_CRT\_NONSTDC\_ne\_upozornění**. Toto makro na příkazovém řádku můžete definovat zahrnutím možnost `/D_CRT_NONSTDC_NO_WARNINGS`.


### <a name="unsafe-crt-library-functions"></a>Unsafe – funkce knihovny CRT

 **Tato funkce nebo proměnná může nebezpečný. Zvažte použití** *safe_version* **místo. Chcete-li zakázat vyřazení, použijte \_CRT\_zabezpečeného\_ne\_upozornění.  V nápovědě online podrobnosti.**

 Microsoft se nepoužívá, některé funkce CRT a standardní knihovny C++ a globální prvky považuje bezpečnější verze. Ve většině případů nepoužívané funkce povolit nezaškrtnuté čtení nebo oprávnění k zápisu do vyrovnávací paměti, které může vést k zabezpečení závažné problémy. Kompilátor vydá upozornění vyřazení pro tyto funkce a navrhne upřednostňované funkce.

 Chcete-li tento problém vyřešit, doporučujeme, abyste použili funkce nebo proměnná *safe_version* místo. Pokud jste ověřili, že není možné přepsat vyrovnávací paměti nebo overread dochází k výskytu kódu a kód důvodů přenositelnost nelze změnit, můžete vypnout upozornění.
 
 Chcete-li vypnout upozornění na zastaralost pro tyto funkce v CRT, definovat  **\_CRT\_zabezpečeného\_ne\_upozornění**. Chcete-li vypnout upozornění na zastaralé globální proměnné, definovat  **\_CRT\_zabezpečeného\_ne\_upozornění\_GLOBALS**. Další informace o těchto zastaralé funkce a globální prvky najdete v tématu [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md) a [bezpečné knihovny: standardní knihovna C++](../../standard-library/safe-libraries-cpp-standard-library.md).

### <a name="unsafe-standard-library-functions"></a>Nezabezpečený funkce standardní knihovny

__' – std::__*Název_funkce*__::\_Unchecked\_iterátory::\_Deprecate' volat na – std::__*Název_funkce* **s parametry, které může nebezpečné - toto volání spoléhá na volajícího, aby zkontrolujte správnost předané hodnoty. Chcete-li zakázat toto upozornění, použijte -D\_SCL\_zabezpečeného\_ne\_upozornění. Najdete v dokumentaci o tom, jak používat Visual C++, iterátory zaškrtnutí.**

Toto upozornění se zobrazí u sestavení ladicí verze, vzhledem k tomu, že určité funkce standardní knihovny C++ šablony Neprovádět kontrolu parametry správnost. Ve většině případů to je, protože není dostatek informace jsou k dispozici funkce ke kontrole kontejneru rozsah, nebo protože iterátory může být nesprávně použitá pomocí funkce. Toto upozornění pomáhá identifikovat používá tyto funkce, protože může být zdrojem závažné celistvosti v programu. Další informace najdete v tématu [zaškrtnutí iterátory](../../standard-library/checked-iterators.md).

Například toto upozornění se zobrazí v režimu ladění Pokud předáte k elementu ukazatel na `std::copy` místo prostý pole. Chcete-li tento problém vyřešit, použijte správně deklarované pole, tak můžete zkontrolovat rozsahy pole a proveďte kontrolu hranice knihovny.

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

Několik standardní knihovny algoritmů byly aktualizovány tak, aby měl "duální rozsah" verze v C ++ 14. Pokud používáte verze duální rozsahu, druhého rozsahu obsahuje nezbytné hranice kontrola:

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

Tento příklad ukazuje několik další způsoby standardní knihovna slouží ke kontrole iterator využití, a pokud není zaškrtnuto využití může být nebezpečné:

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

Pokud jste ověřili, že váš kód nemůže mít došlo k chybě v funkce standardní knihovny, které aktivují toto upozornění přetečení vyrovnávací paměti, můžete toto upozornění vypnout. Chcete-li vypnout upozornění pro tyto funkce, definovat  **\_SCL\_zabezpečeného\_ne\_upozornění**.

### <a name="checked-iterators-enabled"></a>Checked – iterátory povoleno

C4996 může také nastat, pokud nepoužíváte zaškrtnutý iterátor, když kompilujete s `_ITERATOR_DEBUG_LEVEL` definován jako 1 nebo 2. Má hodnotu 2 ve výchozím nastavení pro režim sestavení pro ladění a 0 pro maloobchodní sestavení. V tématu [zaškrtnutí iterátory](../../standard-library/checked-iterators.md) Další informace.

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

C4996 může také nastat, pokud používáte MFC nebo ATL funkcí, které byly zastaralé z bezpečnostních důvodů.

Chcete-li tento problém vyřešit, důrazně doporučujeme změnit kód místo toho použít aktualizované funkce.

Informace o tom, jak potlačit tato upozornění najdete v tématu [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings).

### <a name="obsolete-crt-functions-and-variables"></a>Zastaralé funkce CRT a proměnné

**Tato funkce nebo proměnná byla nahrazena novější funkce knihovny nebo operačního systému. Zvažte použití** *new_item* **místo. V nápovědě online podrobnosti.**

Některé funkce knihovny a globální proměnné jsou zastaralé jako zastaralé. Tyto funkce a proměnné může být odebrány v budoucí verzi knihovny Kompilátor vydá upozornění vyřazení pro tyto položky a navrhne upřednostňované alternativní.

Chcete-li tento problém vyřešit, doporučujeme že změnit kód pro použití navrhované funkce nebo proměnná.

Chcete-li vypnout upozornění na zastaralost pro tyto položky, definovat  **\_CRT\_zastaralé\_ne\_upozornění**. Další informace naleznete v dokumentaci pro zastaralé funkce nebo proměnná.

### <a name="marshalling-errors-in-clr-code"></a>Zařazování chybami v kódu CLR

C4996 může dojít také při použití knihovny zařazování CLR. V tomto případě je C4996 chybou, nikoli upozorněním. K této chybě dojde, pokud používáte [marshal_as](../../dotnet/marshal-as.md) pro převod mezi dvěma datovými typy, které potřebují [marshal_context – třída](../../dotnet/marshal-context-class.md). Můžete také získat tato chyba, když knihovny zařazování nepodporuje převod. Další informace o knihovně zařazování najdete v tématu [přehled zařazování v jazyku C++](../../dotnet/overview-of-marshaling-in-cpp.md).

Tento příklad generuje C4996, protože vyžaduje kontext převést z knihovny zařazování `System::String` k `const char *`.

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

Volající upozornit, když už doporučujeme použití určitých funkcí, můžete použít atribut nepoužívané v kódu. V tomto příkladu se generuje C4996 pro řádek, u kterého je deklarovaná zastaralé funkce a pro řádek, na kterém se používá funkce.

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
