---
title: "Kompilátoru (úroveň 3) upozornění C4996 | Microsoft Docs"
ms.custom: 
ms.date: 06/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4996
dev_langs: C++
helpviewer_keywords: C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
caps.latest.revision: "34"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c034da079fe015bcad78d0bbc956df80e17beae3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4996"></a>C4996 kompilátoru upozornění (úroveň 3)

Kompilátor byla zjištěna nepoužívané deklarace.  
  
Toto upozornění nebo chyby má několik možných významy, v závislosti na kontextu.  
  
C4996 nastane, když kompilátor narazí funkce nebo proměnná, která je označena jako [zastaralé](../../cpp/deprecated-cpp.md) pomocí `__declspec(deprecated)` modifikátor. Při pokusu o přístup k funkci, člen třídy nebo typedef, který má C ++ 14 také objeví toto upozornění `[[deprecated]]` atribut. Další informace najdete v tématu [standardní atributy C++](../../cpp/attributes2.md). Vám pomůže tento atribut sami ve vašich knihovnách upozornit vaši klienti o zastaralé funkce, definice TypeDef nebo členy.  
  
Několik funkcí, členské funkce, funkce šablon a globální proměnné v knihovnách v sadě Visual Studio jsou označené jako zastaralé. Tato funkce může mít jiný název upřednostňované, může být nebezpečné, nebo mít hodnotu typu variant bezpečnější, nebo může být zastaralý. Mnoho chybové zprávy zahrnují navrhované náhradou za zastaralé funkce nebo globální proměnné.  
  
Chcete-li tento problém vyřešit, obvykle doporučujeme že měnit kód místo toho použít navrhované bezpečnější nebo aktualizované funkce a globální proměnné. Pokud potřebujete použít existující funkce nebo proměnné přenositelnost z důvodů, může být vypnuto upozornění.  
  
Upozornění pro konkrétní řádek kódu můžete vypnout pomocí [upozornění](../../preprocessor/warning.md) – Direktiva pragma `#pragma warning(suppress : 4996)`. Můžete vypnout ho v souboru s použitím – Direktiva pragma upozornění `#pragma warning(disable : 4996)`. Můžete vypnout ho globálně v sestavení příkazového řádku pomocí **/wd4996** možnost příkazového řádku. Chcete-li vypnout upozornění pro projekt sady Visual Studio IDE, otevřete **stránky vlastností** dialogovém okně, vyberte **vlastnosti konfigurace**, **C/C++**,  **Rozšířené** stránky a upravit **zakázat konkrétní varování** vlastnost přidat `4996`.  Makra preprocesoru také můžete vypnout určité určité třídy upozornění na zastaralost používá v knihovnách. Tyto makra jsou popsané níže.  
  
Zde jsou některé z knihovny zdrojů C4996.  
  
## <a name="posix-function-names"></a>Názvy POSIX – funkce  
  
**POSIX název pro tuto položku je zastaralý. Místo toho použijte název vyhovující ISO C a C++:** *nový_název*. **V nápovědě online podrobnosti.**  
  
Microsoft má přejmenovat, některé funkce POSIX v CRT tak, aby odpovídala C99 a C ++ 03 pravidla pro názvy definované implementací globální funkce. Jenom původní názvy POSIX jsou zastaralé, není funkce sami. Ve většině případů do název funkce POSIX vytvoří standardní vyhovující název byl přidán úvodní podtržítka. Kompilátor vydá upozornění vyřazení pro původní název funkce a navrhne upřednostňovaný název.  
  
Chcete-li tento problém vyřešit, obvykle doporučujeme že měnit kód místo toho použít názvy návrhy funkcí. Aktualizované názvy jsou však specifické pro společnost Microsoft. Pokud budete muset použít stávající názvy funkcí pro přenositelnost důvodů, je tato upozornění vypnout. Funkce POSIX jsou stále k dispozici v knihovně v části původní názvy.  
  
Chcete-li vypnout upozornění na zastaralost pro tyto funkce, definujte makro preprocesoru **_CRT_NONSTDC_NO_WARNINGS**. Můžete definovat to na příkazovém řádku zahrnutím možnost `/D_CRT_NONSTDC_NO_WARNINGS`. Chcete-li toto makro definovat v sadě Visual Studio, otevřete **stránky vlastností** dialogové okno pro váš projekt. Rozbalte položku **vlastnosti konfigurace**, **C/C++**, **preprocesor**. V **Definice preprocesoru**, přidejte `_CRT_NONSTDC_NO_WARNINGS`. Zvolte **OK** uložíte, a pak znovu sestavte projekt. K definování této makro pouze v konkrétní zdrojové soubory, přidejte řádek `#define _CRT_NONSTDC_NO_WARNINGS` před všech řádků, které obsahuje soubor hlaviček.  
  
## <a name="unsafe-crt-library-functions"></a>Unsafe – funkce knihovny CRT  
  
 **Tato funkce nebo proměnná může nebezpečný. Zvažte použití***safe_version* **místo.   Chcete-li zakázat vyřazení, použijte _CRT_SECURE_NO_WARNINGS.  V nápovědě online podrobnosti.**  
  
 Microsoft se nepoužívá, některé funkce CRT a standardní knihovny C++ a globální prvky považuje bezpečnější verze. Ve většině případů nepoužívané funkce povolit nezaškrtnuté čtení nebo oprávnění k zápisu do vyrovnávací paměti, které může vést k zabezpečení závažné problémy. Kompilátor vydá upozornění vyřazení pro tyto funkce a navrhne upřednostňované funkce.  
  
 Chcete-li tento problém vyřešit, doporučujeme, abyste použili funkce nebo proměnná *safe_version* místo. Pokud jste ověřili, že není možné přepsat vyrovnávací paměti nebo overread dochází k výskytu kódu a kód důvodů přenositelnost nelze změnit, můžete vypnout upozornění.  
   
 Chcete-li vypnout upozornění na zastaralost pro tyto funkce v CRT, definovat **_CRT_SECURE_NO_WARNINGS**. Chcete-li vypnout upozornění na zastaralé globální proměnné, definovat **_CRT_SECURE_NO_WARNINGS_GLOBALS**. Další informace o těchto zastaralé funkce a globální prvky najdete v tématu [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md) a [bezpečné knihovny: standardní knihovna C++](../../standard-library/safe-libraries-cpp-standard-library.md).  
  
## <a name="unsafe-standard-library-functions"></a>Nezabezpečený funkce standardní knihovny  
  
 **' – std::** *Název_funkce* **::\_Unchecked\_iterátory::\_Deprecate' volat na – std::** *Název_funkce* **s parametry, které může nebezpečné - toto volání spoléhá na volajícího, aby zkontrolujte správnost předané hodnoty. Tato upozornění zakážete pomocí parametru -D_SCL_SECURE_NO_WARNINGS. Najdete v dokumentaci o tom, jak používat Visual C++, iterátory zaškrtnutí.**  
  
Toto upozornění se zobrazí u sestavení ladicí verze, vzhledem k tomu, že určité funkce standardní knihovny C++ šablony Neprovádět kontrolu parametry správnost. Ve většině případů to je, protože není dostatek informace jsou k dispozici funkce ke kontrole kontejneru rozsah, nebo protože iterátory může být nesprávně použitá pomocí funkce. Toto upozornění pomáhá identifikovat používá tyto funkce, protože může být zdrojem celistvosti v programu. Další informace najdete v tématu [zaškrtnutí iterátory](../../standard-library/checked-iterators.md).  
  
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
  
Pokud jste ověřili, že váš kód nemůže mít došlo k chybě v funkce standardní knihovny, které aktivují toto upozornění přetečení vyrovnávací paměti, můžete toto upozornění vypnout. Chcete-li vypnout upozornění pro tyto funkce, definovat **_SCL_SECURE_NO_WARNINGS**.   
  
## <a name="example-checked-iterators-enabled"></a>Příklad: Checked – iterátory povoleno  
  
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
  
## <a name="unsafe-mfc-or-atl-code"></a>Nezabezpečený MFC nebo ATL kód  
  
C4996 může také nastat, pokud používáte MFC nebo ATL funkcí, které byly zastaralé z bezpečnostních důvodů.  
  
Chcete-li tento problém vyřešit, důrazně doporučujeme změnit kód místo toho použít aktualizované funkce.  
  
Informace o tom, jak potlačit tato upozornění najdete v tématu [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings).  
  
## <a name="obsolete-crt-functions-and-variables"></a>Zastaralé funkce CRT a proměnné  
  
**Tato funkce nebo proměnná byla nahrazena novější funkce knihovny nebo operačního systému. Zvažte použití** *new_item* **místo. V nápovědě online podrobnosti.**  
  
Některé funkce knihovny a globální proměnné jsou zastaralé jako zastaralé. Tyto funkce a proměnné může být odebrány v budoucí verzi knihovny Kompilátor vydá upozornění vyřazení pro tyto položky a navrhne upřednostňované alternativní.  
  
Chcete-li tento problém vyřešit, doporučujeme že změnit kód pro použití navrhované funkce nebo proměnná.  
  
Chcete-li vypnout upozornění na zastaralost pro tyto položky, definovat **_CRT_OBSOLETE_NO_WARNINGS**. Další informace naleznete v dokumentaci pro zastaralé funkce nebo proměnná.  
  
## <a name="example-marshalling-errors-in-clr-code"></a>Příklad: Zařazování chybami v kódu CLR  
  
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
  
