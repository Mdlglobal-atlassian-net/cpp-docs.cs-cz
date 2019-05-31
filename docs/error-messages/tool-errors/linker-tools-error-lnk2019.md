---
title: Chyba linkerů LNK2019
ms.date: 12/15/2017
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.openlocfilehash: eb28ff3673c054b8ac1876d8ba736ceddfa5fd1a
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449612"
---
# <a name="linker-tools-error-lnk2019"></a>Chyba linkerů LNK2019

Nerozpoznaný externí symbol "*symbol*'odkazovaný ve funkci'*funkce*.

Zkompilovaný kód pro *funkce* díky odkazu nebo volání *symbol*, ale tento symbol není definovaný v některém z knihovny nebo objektových souborů zadaný v linkeru.

Tato chybová zpráva je následována závažná chyba [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Je nutné opravit všechny LNK2001 a LNK2019 chyby opravit chyby LNK1120.

## <a name="possible-causes"></a>Možné příčiny

Existuje mnoho způsobů, jak se tato chyba, ale všechny z nich zahrnuje odkaz na funkci nebo proměnnou, která linker nemůže *vyřešit*, nebo si najděte definici. Kompilátor může identifikovat při symbol nemá *deklarované*, ale ne když není *definované*, protože definice může být v odlišném zdrojovém souboru nebo knihovny. Pokud symbol je uvedené, ale nikdy definovaný, linker generuje chybu nerozpoznaný externí symbol.

Tady jsou některé běžné problémy, které způsobují LNK2019:

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>Není propojený soubor objektu nebo knihovny, který obsahuje definici symbolu

V sadě Visual Studio ověřte, že zdrojový soubor, který obsahuje definici vytvořené a propojí jako součást vašeho projektu. Na příkazovém řádku ověřte, že zdrojový soubor, který obsahuje definici je zkompilován a výsledný soubor objektu je součástí seznamu souborů určených k propojení.

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>Deklarace symbolu není zadána stejná jako definice symbolu

Zkontrolujte pravopis a velká písmena se používá v deklarace a definice a všude, kde je symbol použít nebo názvem.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>Funkce se používá, ale tento typ nebo počet parametrů se neshodují definice funkce

Deklarace funkce musí odpovídat definici. Ověřte, že volání funkce odpovídá deklaraci a že deklarace odpovídá definici. Kód, který vyvolá funkce šablony musí také mít odpovídající deklarace funkce šablon, které zahrnují stejné parametry šablony jako definice. Příklad neshodě deklarace šablony najdete v ukázce LNK2019e.cpp v části Příklady.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Funkce nebo proměnná je deklarovaná, ale není definovaný.

To obvykle znamená, že deklarace existuje v hlavičkovém souboru, ale je implementována žádná odpovídající definice. Pro členské funkce ani statické datové členy implementace uvést výběr oboru třídy. Příklad najdete v tématu [chybí tělo funkce nebo proměnná](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>Konvence volání se liší mezi funkce deklarace a definice funkce

Konvence volání ([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md), nebo [__vectorcall](../../cpp/vectorcall.md)) jsou zakódovány jako součást upravený název. Ověřte, zda konvence volání je stejný.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>Symbol definovaný v souboru jazyka C, ale deklarovaný bez používání příkazu extern "C" v souboru jazyka C++

Symboly definované v souboru, který je zkompilován jako C mají různé dekorované názvy než symboly, které jsou deklarovány v souboru jazyka C++, pokud nechcete použít [extern "C"](../../cpp/using-extern-to-specify-linkage.md) modifikátor. Zkontrolujte, zda deklarace odpovídá propojení kompilace pro každý symbol. Podobně pokud definici symbolu v souboru jazyka C++, který se použije programu jazyka C, použijte `extern "C"` v definici.

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>Symbol je definován jako statické a později odkazovat mimo soubor

V jazyce C++, na rozdíl od jazyka C [globální konstanty](../../error-messages/tool-errors/global-constants-in-cpp.md) mají `static` propojení. Chcete-li získat vyhnout uvedeným potížím, můžete zahrnout `const` inicializace v záhlaví souborů a součástí této hlavičky souborů .cpp, nebo můžete provést nekonstantní proměnnou a používat konstantní odkaz k němu přistupovat.

### <a name="a-static-member-of-a-class-is-not-defined"></a>Není definovaný statický člen třídy

Statická třída člen musí mít jedinečné definice nebo ji bude porušovat jednu definici pravidla. Statické třídy člena, který nemůže být definována vložením musí být definován v jednom zdrojovém souboru pomocí jeho plně kvalifikovaný název. Pokud není definován vůbec, linker generuje LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Závislost sestavení je definována pouze jako závislost projektu v řešení

V dřívějších verzích sady Visual Studio byla dostatečná tento stupeň závislosti. Od verze Visual Studio 2010, ale Visual Studio vyžaduje [odkaz typu projekt projekt](/visualstudio/ide/managing-references-in-a-project). Pokud váš projekt nemá odkaz typu projekt projekt, může se zobrazit tato chyba linkeru. Přidáte odkaz typu projekt projekt ho opravit.

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Vytvoření konzolové aplikace pomocí nastavení pro aplikace Windows

Pokud se chybová zpráva podobá **nerozpoznaný externí symbol WinMain odkazovaný ve funkci** *Název_funkce*, propojení s použitím **/Subsystem: Console** místo **/Subsystem: Windows**. Další informace o tomto nastavení a pokyny o tom, jak tuto vlastnost nastavit v sadě Visual Studio, najdete v části [/Subsystem (určení subsystému)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Při pokusu o propojení knihoven 64-bit 32bitového kódu nebo knihovny 32-bit do 64bitového kódu

Knihovny a soubory objektů propojené kódu musí být zkompilovaná pro stejnou architekturu jako svůj kód. Ověřte, že knihovny odkazy projektu jsou zkompilovány pro stejnou architekturu jako váš projekt. Ujistěte se, [/Libpath](../../build/reference/libpath-additional-libpath.md) nebo **další adresáře knihoven** cesta možnost používat bodů linkeru pro knihovny, které jsou vytvořené pro správnou architekturu.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>Použijte jiné parametry kompilátoru pro vkládání funkcí v jiných zdrojových souborů

Použití vložených funkcí definovaných v souborech .cpp a kombinování funkce vložené možnosti kompilátoru v jiných zdrojových souborů může způsobit LNK2019. Další informace najdete v tématu [problémy vkládání funkcí](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Použít automatické proměnné mimo jejich rozsah

Automatické proměnné (rozsah funkce) jde použít jenom v rozsahu dané funkce. Tyto proměnné nelze použít deklaraci `extern` a použít v jiných zdrojových souborech. Příklad najdete v tématu [automatické proměnné (rozsah funkce)](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>Volání funkcí instrinsic nebo předejte typy argumentů pro vnitřní funkce, které nejsou podporovány na Cílová architektura

Například, pokud použijete AVX2 vnitřní, ale není zadán [/arch: avx2](../../build/reference/arch-x86.md) – možnost kompilátoru, kompilátor předpokládá, že je vnitřní externí funkce. Místo aby generovala vložené instrukce, kompilátor vygeneruje volání externích symbolů se stejným názvem jako vnitřní objekt. Linker se pokusí vyhledat definice této funkce chybí, vygeneruje LNK2019. Ověřte, zda pouze pomocí vnitřní objekty a typů podporovaných Cílová architektura.

### <a name="you-mix-code-that-uses-native-wchart-with-code-that-doesnt"></a>Kombinovat kód, který používá nativní wchar\_t s kódem, který není

C++jazyk prací, které bylo provedeno v sadě Visual Studio 2005 provedené `wchar_t` nativní typ ve výchozím nastavení. Je nutné použít [/Zc:wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) – možnost kompilátoru generovat kód kompatibilní s knihoven a objektů soubory sestavené v předchozích verzích sady Visual Studio. Pokud se všechny soubory již byly zkompilovány pomocí stejného **/Zc:wchar\_t** nastavením odkazy nemusí odpovídat nekompatibilní typy. Ověřte, že `wchar_t` typy ve všech souborech knihoven a objektů jsou kompatibilní, aktualizace typů, které se používají, nebo pomocí konzistentní **/Zc: wchar_t** nastavení při kompilaci.

## <a name="third-party-library-issues-and-vcpkg"></a>Problémy knihovny třetí strany a Vcpkg

Pokud tato chyba se zobrazí, když se pokoušíte nakonfigurovat knihovny třetích stran jako součást vašeho sestavení, zvažte použití [Vcpkg](../../vcpkg.md), Visual C++ balíček správce k instalaci a vytvoření knihovny. Vcpkg podporuje jejichž [seznam knihoven třetích stran](https://github.com/Microsoft/vcpkg/tree/master/ports)a nastaví vlastnosti konfigurace a závislosti, které vyžaduje pro úspěšné sestavení jako součást vašeho projektu. Další informace najdete v tématu související [blogu Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) příspěvku.

## <a name="diagnosis-tools"></a>Nástroje pro diagnostiku

Může být obtížné zjistit, proč linker nemůže najít definice určitého symbolu. Problém je často, že jste nezahrnuli kód, který obsahuje definici v sestavení nebo sestavení, které jste vytvořili různé možnosti dekorované názvy pro externích symbolů. Existuje několik nástrojů a možností, které vám pomohou diagnostikovat chyby LNK2019.

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) – možnost linkeru vám pomohou určit, které soubory linkeru odkazy. Můžete ověřit, zda je sestavení součástí souboru, který obsahuje definici symbolu.

- [/EXPORTUJE](../../build/reference/dash-exports.md) a [/symboly](../../build/reference/symbols.md) možnosti, které **DUMPBIN** nástroje vám můžou pomoct odhalit symboly, které jsou definovány v souborech DLL a objektů nebo knihoven. Ověřte, že exportovaný dekorované názvy neshoduje s dekorované názvy propojovací program vyhledá.

- **UNDNAME** nástroje lze zobrazit ekvivalentní nedekorovaných externí symbol pro upravený název.

## <a name="examples"></a>Příklady

Tady je několik příkladů kódu, který způsobí chybu LNK2019, spolu s informacemi o tom, jak chybu opravit.

### <a name="a-symbol-is-declared-but-not-defined"></a>Symbol je deklarovaná, ale není definovaný.

V tomto příkladu je externí proměnná deklarovaná, ale není definována:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Tady je další příklad, ve kterém jsou deklarovány proměnné a funkce jako `extern` ale Azure nenabízí žádnou definici:

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

Není-li `i` a `g` jsou definovány v jednom z soubory obsažené v sestavení, linker generuje LNK2019. Opravte chyby zahrnutím souboru se zdrojovým kódem, který obsahuje definice jako část kompilace. Alternativně můžete předat soubory .obj nebo .lib soubory, které obsahují definice do propojovacího programu.

### <a name="a-static-data-member-is-declared-but-not-defined"></a>Statický datový člen je deklarovaná, ale není definovaný.

LNK2019 může dojít také při statický datový člen je deklarovaná, ale není definovaný. Následující ukázka generuje LNK2019 a ukazuje, jak ho opravit.

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

### <a name="declaration-parameters-do-not-match-definition"></a>Deklarace parametrů se neshodují definice

Kód, který vyvolá funkce šablony musí mít odpovídající deklarace šablony funkcí. Deklarace musí obsahovat stejné parametry šablony jako definice. Následující ukázka generuje LNK2019 na uživatelem definovaný operátor a ukazuje, jak ho opravit.

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

### <a name="inconsistent-wchart-type-definitions"></a>Definice typu wchar_t nekonzistentní

Tato ukázka vytvoří knihovnu DLL, která má export, který používá `WCHAR`, která se přeloží na `wchar_t`.

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

Další ukázka používá knihovnu DLL v předchozí ukázce a vygeneruje LNK2019, protože typy unsigned short * a WCHAR\* nejsou stejné.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

Chcete-li tuto chybu vyřešit, změňte `unsigned short` k `wchar_t` nebo `WCHAR`, nebo kompilací LNK2019g.cpp pomocí **/Zc:wchar_t-** .

## <a name="additional-resources"></a>Další zdroje

Další informace o možných příčinách a řešení pro LNK2001 viz otázka na Stack Overflow [co se o chybu nedefinované odkaz/nerozpoznaných externích symbolů a jak ho mám opravit?](https://stackoverflow.com/q/12573816/2002113).

