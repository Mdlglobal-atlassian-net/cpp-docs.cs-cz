---
title: LINKERŮ LNK2019 chyba nástrojů linkeru
ms.date: 12/15/2017
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.openlocfilehash: 3c4e5578c7b0f496feb4d40933af624f462a31d2
ms.sourcegitcommit: 680a155cc44a38f88bb2b1c5a1ef6dcb7141c011
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252622"
---
# <a name="linker-tools-error-lnk2019"></a>LINKERŮ LNK2019 chyba nástrojů linkeru

Nerozpoznaný externí symbol '*symbol*' odkazovaný ve funkci*Function '*

Zkompilovaný kód pro *funkci* provede odkaz nebo volání *symbolu*, ale tento symbol není definován v žádné z knihoven nebo souborů objektů určených pro linker.

Tato chybová zpráva je následována závažnou chybou [linkerů LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). K opravě chyby LINKERŮ LNK1120 je nutné opravit všechny chyby LINKERŮ LNK2001 a LINKERŮ LNK2019.

## <a name="possible-causes"></a>Možné příčiny

Existuje mnoho způsobů, jak získat tuto chybu, ale všechny z nich zahrnují odkaz na funkci nebo proměnnou, kterou linker nemůže *přeložit*, nebo najít definici pro. Kompilátor může zjistit, že není *deklarován*symbol, ale ne, pokud není *definován*, protože definice může být v jiném zdrojovém souboru nebo knihovně. Pokud je symbol odkazován, ale není definován, linker vygeneruje nevyřešenou chybu externího symbolu.

Tady jsou některé běžné problémy, které způsobují LINKERŮ LNK2019:

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>Soubor objektu nebo knihovna obsahující definici symbolu není propojena.

V aplikaci Visual Studio ověřte, zda je zdrojový soubor obsahující definici sestaven a propojen jako součást projektu. Na příkazovém řádku ověřte, zda je zdrojový soubor obsahující definici zkompilován a zda je výsledný soubor objektu obsažen v seznamu souborů, které mají být propojeny.

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>Deklarace symbolu není napsaná stejně jako definice symbolu.

Ověřte, zda je v deklaraci i v definici správné zadání velkých a malých písmen, a všude, kde je symbol použit nebo volán.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>Použije se funkce, ale typ nebo číslo parametru se neshodují s definicí funkce.

Deklarace funkce se musí shodovat s definicí. Ověřte, zda volání funkce odpovídá deklaraci a zda deklarace odpovídá definici. Kód, který vyvolává funkce šablony, musí mít také odpovídající deklarace funkce šablony, které zahrnují stejné parametry šablony jako definice. Příklad neshody deklarace šablony naleznete v tématu Sample LNK2019e. cpp v oddílu příklady.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Funkce nebo proměnná je deklarovaná, ale není definovaná.

To obvykle znamená, že v hlavičkovém souboru existuje deklarace, ale není implementována žádná vyhovující definice. U členských funkcí nebo statických datových členů musí implementace zahrnovat selektor oboru třídy. Příklad naleznete v tématu [chybějící tělo funkce nebo proměnná](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>Konvence volání je v rámci deklarace funkce a definice funkce odlišná.

Konvence volání ([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)nebo [__vectorcall](../../cpp/vectorcall.md)) jsou kódovány jako součást dekorované názvy. Ověřte, zda je konvence volání shodná.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>Symbol je definovaný v souboru jazyka C, ale deklarovaný bez použití extern "C" v C++ souboru.

Symboly definované v souboru, který je kompilován jako C, mají různé dekorované názvy než symboly deklarované C++ v souboru, pokud nepoužijete modifikátor [extern "C"](../../cpp/using-extern-to-specify-linkage.md) . Ověřte, zda deklarace odpovídá propojení kompilace pro každý symbol. Podobně pokud definujete symbol v C++ souboru, který bude používán programem jazyka C, použijte v definici `extern "C"`.

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>Symbol je definovaný jako statický a později se na něj odkazuje mimo tento soubor.

V C++na rozdíl od jazyka C [globální konstanty](../../error-messages/tool-errors/global-constants-in-cpp.md) mají propojení `static`. Chcete-li se tomuto omezení vyhnout, můžete do hlavičkového souboru zahrnout inicializace `const` a zahrnout tuto hlavičku do souborů. cpp, nebo můžete nastavit proměnnou jako nekonstantní a použít pro přístup k ní konstantní odkaz.

### <a name="a-static-member-of-a-class-is-not-defined"></a>Statický člen třídy není definovaný.

Člen statické třídy musí mít jedinečnou definici, nebo bude porušovat pravidlo jedné definice. Člen statické třídy, který nelze definovat jako inline, musí být definován v jednom zdrojovém souboru pomocí plně kvalifikovaného názvu. Pokud není vůbec definováno, linker vygeneruje LINKERŮ LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Závislost sestavení je definovaná jenom jako závislost projektu v řešení.

V dřívějších verzích sady Visual Studio byla tato úroveň závislosti dostačující. Počínaje sadou Visual Studio 2010 ale Visual Studio vyžaduje [odkaz typu projekt-projekt](/visualstudio/ide/managing-references-in-a-project). Pokud projekt nemá odkaz typu projekt-projekt, může se zobrazit tato chyba linkeru. Přidejte odkaz typu projekt-projekt k opravě.

### <a name="an-entry-point-is-not-defined"></a>Vstupní bod není definován.

Kód aplikace musí definovat vhodný vstupní bod: `main` nebo `wmain` pro konzolové aplikace, `WinMain` nebo `wWinMain` pro aplikace systému Windows. Další informace naleznete v tématu [Main: Startup programu](../../cpp/main-program-startup.md) nebo [funkce WinMain](/windows/win32/api/winbase/nf-winbase-winmain). Chcete-li použít vlastní vstupní bod, určete možnost linkeru [/entry (symbol vstupního bodu)](../../build/reference/entry-entry-point-symbol.md) . 

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Pomocí nastavení pro aplikaci systému Windows sestavíte konzolovou aplikaci.

Pokud je chybová zpráva podobná **nevyřešenému externímu symbolu WinMain, na který odkazuje funkce** *function_name*, propojte pomocí **/SUBSYSTEM: Console** namísto **/SUBSYSTEM: Windows**. Další informace o tomto nastavení a pokyny k nastavení této vlastnosti v sadě Visual Studio naleznete v tématu [/Subsystem (určení subsystému)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Pokusíte se propojit 64 knihoven s 32 bitovým kódem nebo 32-bitové knihovny až ke kódu na 64-bit.

Knihovny a soubory objektů propojené s vaším kódem musí být kompilovány pro stejnou architekturu jako váš kód. Ověřte, zda jsou knihovny, na které projekt odkazuje, kompilovány pro stejnou architekturu jako projekt. Zajistěte, aby [/LIBPATH](../../build/reference/libpath-additional-libpath.md) nebo další možnosti cesty **adresáře knihovny** používané linkerem odkazovaly na knihovny sestavené pro správnou architekturu.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>Pro vkládání funkcí v různých zdrojových souborech použijete jiné možnosti kompilátoru.

Použití zapsaných funkcí definovaných v souborech. cpp a kombinování možností kompilátoru pro vkládání funkcí v různých zdrojových souborech může způsobit LINKERŮ LNK2019. Další informace najdete v tématu [problémy s vkládáním funkcí](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Používáte automatické proměnné mimo jejich rozsah

Automatické proměnné (rozsah funkce) lze použít pouze v rozsahu této funkce. Tyto proměnné nelze deklarovat `extern` a použít je v jiných zdrojových souborech. Příklad naleznete v tématu [automatické proměnné (rozsah funkce)](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>Zavoláte funkce instrinsic nebo předáte typy argumentů do vnitřních funkcí, které nejsou v cílové architektuře podporované.

Například pokud použijete vnitřní AVX2, ale nezadáte možnost kompilátoru [/arch: AVX2](../../build/reference/arch-x86.md) , kompilátor předpokládá, že vnitřní je externí funkce. Namísto generování vložené instrukce kompilátor vygeneruje volání externímu symbolu se stejným názvem jako vnitřní. Když se linker pokusí najít definici této chybějící funkce, vygeneruje LINKERŮ LNK2019. Ověřte, že používáte jenom vnitřní objekty a typy podporované cílovou architekturou.

### <a name="you-mix-code-that-uses-native-wchar_t-with-code-that-doesnt"></a>Můžete kombinovat kód, který používá nativní WCHAR @ no__t-0t s kódem, který není

C++práce v jazyku, která byla provedena v rámci sady Visual Studio 2005, provedla ve výchozím nastavení nativní typ `wchar_t`. K vygenerování kódu kompatibilního s knihovnou a soubory objektů kompilovaných pomocí starších verzí sady Visual Studio je nutné použít možnost [/Zc: wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Compiler. Pokud nejsou všechny soubory kompilovány pomocí stejného nastavení **/Zc: WCHAR @ no__t-1T** , odkazy na typ se nemusí překládat na kompatibilní typy. Ověřte, zda jsou typy `wchar_t` ve všech knihovnách a souborech objektů kompatibilní, buď aktualizací používaných typů nebo pomocí konzistentního nastavení **/Zc: wchar_t** při kompilaci.

## <a name="third-party-library-issues-and-vcpkg"></a>Problémy s knihovnou třetích stran a Vcpkg

Pokud se tato chyba zobrazí při pokusu o konfiguraci knihovny třetí strany v rámci sestavení, zvažte použití [Vcpkg](../../vcpkg.md), správce balíčků Visual C++ , k instalaci a sestavení knihovny. Vcpkg podporuje velký a rostoucí [seznam knihoven třetích stran](https://github.com/Microsoft/vcpkg/tree/master/ports)a nastavuje všechny vlastnosti konfigurace a závislosti vyžadované pro úspěšná sestavení v rámci projektu. Další informace najdete v souvisejícím [ C++ blogovém](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) příspěvku.

## <a name="diagnosis-tools"></a>Nástroje pro diagnostiku

Může být obtížné zjistit, proč linker nemůže najít konkrétní definici symbolu. Často se jedná o problém, že jste nezahrnuli kód, který obsahuje definici v sestavení, nebo možnosti sestavení vytvořily různé dekorované názvy externích symbolů. K dispozici je několik nástrojů a možností, které vám pomůžou diagnostikovat chybu LINKERŮ LNK2019.

- [/Verbose](../../build/reference/verbose-print-progress-messages.md) možnost linkeru vám pomůže určit soubory, na které linker odkazuje. To vám může pomáhat ověřit, zda je soubor, který obsahuje definici symbolu, součástí sestavení.

- Možnosti [/EXPORTS](../../build/reference/dash-exports.md) a [/Symbols](../../build/reference/symbols.md) nástroje **DUMPBIN** vám pomůžou zjistit, které symboly jsou definované v souboru. dll a objektu nebo knihovně. Ověřte, že vyexportované dekorované názvy odpovídají dekorovaným názvům, které linker vyhledává.

- Nástroj **UNDNAME** může zobrazit ekvivalentní neupravený externí symbol pro dekorované jméno.

## <a name="examples"></a>Příklady

Zde je několik příkladů kódu, které způsobují chybu LINKERŮ LNK2019, spolu s informacemi o tom, jak chybu opravit.

### <a name="a-symbol-is-declared-but-not-defined"></a>Symbol je deklarovaný, ale není definovaný.

V tomto příkladu je deklarována externí proměnná, ale není definována:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Tady je další příklad, kde proměnná a funkce jsou deklarovány jako `extern`, ale není k dispozici žádná definice:

```cpp
// LNK2019c.cpp
// Compile by using: cl /EHsc LNK2019c.cpp
// LNK2019 expected
extern int i;
extern void g();
void f() {
   i++;
   g();
}
int main() {}
```

Pokud `i` a `g` jsou definovány v jednom ze souborů obsažených v sestavení, linker vygeneruje LINKERŮ LNK2019. Chyby můžete opravit zahrnutím souboru zdrojového kódu, který obsahuje definice v rámci kompilace. Alternativně můžete předat soubory. obj nebo soubory. lib obsahující definice pro linker.

### <a name="a-static-data-member-is-declared-but-not-defined"></a>Statický datový člen je deklarovaný, ale není definovaný.

LINKERŮ LNK2019 může také nastat, pokud je deklarován statický datový člen, ale není definován. Následující ukázka vygeneruje LINKERŮ LNK2019 a ukazuje, jak ji opravit.

```cpp
// LNK2019b.cpp
// Compile by using: cl /EHsc LNK2019b.cpp
// LNK2019 expected
struct C {
   static int s;
};

// Uncomment the following line to fix the error.
// int C::s;

int main() {
   C c;
   C::s = 1;
}
```

### <a name="declaration-parameters-do-not-match-definition"></a>Parametry deklarace se neshodují s definicí.

Kód, který vyvolává funkce šablony, musí mít odpovídající deklarace funkce šablony. Deklarace musí zahrnovat stejné parametry šablony jako definice. Následující ukázka generuje LINKERŮ LNK2019 na uživatelsky definovaném operátoru a ukazuje, jak ho opravit.

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration does not match the definition below:
   friend ostream& operator<<(ostream&, Test&);
   // To fix, replace the line above with the following:
   // template<typename T> friend ostream& operator<<(ostream&, Test<T>&);
};

template<typename T>
ostream& operator<<(ostream& os, Test<T>& tt) {
   return os;
}

int main() {
   Test<int> t;
   cout << "Test: " << t << endl;   // LNK2019 unresolved external
}
```

### <a name="inconsistent-wchar_t-type-definitions"></a>Nekonzistentní definice typu wchar_t

Tato ukázka vytvoří knihovnu DLL, která má export, který používá `WCHAR`, který se přeloží na `wchar_t`.

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

Další ukázka používá knihovnu DLL v předchozí ukázce a generuje LINKERŮ LNK2019, protože typy unsigned short * a WCHAR @ no__t-0 nejsou stejné.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

Chcete-li tuto chybu opravit, změňte `unsigned short` na `wchar_t` nebo `WCHAR` nebo zkompilujte LNK2019g. cpp pomocí parametru **/Zc: wchar_t-** .

## <a name="additional-resources"></a>Další materiály a zdroje informací

Další informace o možných příčinách a řešeních pro LINKERŮ LNK2001 najdete v Stack Overflow otázce [co je nedefinovaná reference/nevyřešená chyba externího symbolu a jak ji mám opravit?](https://stackoverflow.com/q/12573816/2002113).

