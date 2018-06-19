---
title: Chyba linkerů Lnk2019 | Microsoft Docs
ms.custom: ''
ms.date: 12/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2019
dev_langs:
- C++
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4323e5f8357da046db7a9403d7c575dfdde566b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301902"
---
# <a name="linker-tools-error-lnk2019"></a>Chyba linkerů LNK2019

nerozpoznané externí symbol '*symbol*'odkazovaný ve funkci'*funkce*.

Zkompilovaný kód pro *funkce* díky odkaz nebo volání *symbol*, ale tento symbol není definován v některé z knihovny nebo zadané linkeru soubory objektu.

Tato chybová zpráva je následován závažná chyba [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Je nutné opravit chyby všechny LNK2001 a LNK2019 opravit chyby LNK1120.

## <a name="possible-causes"></a>Možné příčiny

Existuje mnoho způsobů, jak tato chyba, ale všechny z nich zahrnuje odkaz na funkce nebo proměnná, která nelze linkeru *vyřešit*, nebo najít definici. Symbol není možné určit kompilátor *deklarovaný*, ale není při není *definované*, protože definice může být v různých zdrojového souboru nebo knihovny. Pokud symbol je uvedené, ale nikdy definované, linkeru vygeneruje chybu nerozpoznané externí symbol.

Zde jsou některé běžné problémy, které způsobí LNK2019:

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>Není propojený objektu souboru nebo knihovny, která obsahuje definice symbolu

V sadě Visual Studio ověřte, zda zdrojový soubor, který obsahuje definici je vytvořen a propojené v rámci vašeho projektu. Na příkazovém řádku ověřte, že zdrojový soubor, který obsahuje definici zkompilován a bude výsledný soubor objekt je součástí seznam souborů k propojení.

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>Deklarace symbolu není napsaný stejná jako definice symbolu

Ověřte správné pravopis a velká písmena se používá v deklaraci a definice a kdekoli je symbol použít nebo názvem.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>Funkce se používá, ale typ nebo počet parametrů neodpovídají v definici funkce

Deklarace funkce musí odpovídat definici. Ověřte, že volání funkce odpovídá deklaraci a deklaraci odpovídají definici. Kód, který vyvolá šablony funkce musí mít také odpovídající deklarace funkce šablon, které obsahují stejné parametry šablony jako definice. Příklad neshodě deklarace šablony najdete v ukázkové LNK2019e.cpp v části Příklady.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Funkce nebo proměnná je deklarován, ale není definován

To obvykle znamená deklaraci existuje v záhlaví souboru, ale žádné odpovídající definice je implementována. Členské funkce nebo členy statických dat musí obsahovat implementace modulu pro výběr třídy oboru. Příklad, naleznete v části [chybějící tělo funkce nebo proměnná](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>Konvence volání se liší funkce deklarace a definice funkce

Konvence volání ([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md), nebo [__vectorcall](../../cpp/vectorcall.md)) jsou zakódovány jako součást upravený název. Ověřte, že konvence volání je stejný.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>Symbol je definována v souboru C, ale deklarovaný bez používání příkazu extern "C" v souboru jazyka C++

Symboly definované v souboru, který se zkompiluje jako C mají různé dekorované názvy než symboly deklarován v souboru C++, pokud nechcete použít [extern "C"](../../cpp/using-extern-to-specify-linkage.md) modifikátor. Ověřte, že deklaraci odpovídá propojení kompilace pro každý symbol. Podobně, pokud symbol definujete v C++ soubor, který se použije v programu C +, použijte `extern "C"` v definici.

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>Symbol je definován jako statické a pak později odkazuje mimo soubor

V jazyce C++, na rozdíl od C [globální konstanty](../../error-messages/tool-errors/global-constants-in-cpp.md) mít `static` propojení. Chcete-li získat obejít toto omezení, můžete zahrnout `const` inicializacích v hlavičce souboru a zahrnout této hlavičky do sada souborů, nebo můžete nastavit proměnnou nekonstantní a použít konstantní odkaz k přístupu.

### <a name="a-static-member-of-a-class-is-not-defined"></a>Není definován statický člen třídy

Statická třída člen musí mít jedinečné definice nebo nesplňují jedna definice pravidla. Statická třída člena, který nemůže být definována vložením musí být definovány do jednoho zdrojového souboru pomocí jeho plně kvalifikovaný název. Pokud není definován vůbec, generuje linkeru LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Závislost sestavení je definována pouze v projektu závislosti na řešení

V dřívějších verzích sady Visual Studio byla tato úroveň závislosti dostatečná. Od verze sady Visual Studio 2010, ale Visual Studio vyžaduje [odkaz na projekt na projekt](/visualstudio/ide/managing-references-in-a-project). Pokud projekt nemá odkaz na projekt na projekt, může se zobrazit tato chyba linkeru. Přidejte odkaz projekt na projekt a opravte ji.

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Vytvoření konzolové aplikace s použitím nastavení pro aplikaci systému Windows

Pokud je tato chybová zpráva podobná **nerozpoznané externí symbol WinMain odkazovaný ve funkci** *Název_funkce*, odkaz pomocí **/SUBSYSTEM:CONSOLE** místo **/SUBSYSTEM:WINDOWS**. Další informace o tomto nastavení a pokyny o tom, jak tuto vlastnost nastavit v sadě Visual Studio, najdete v části [/SUBSYSTEM (zadat subsystém)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Pokusíte se do knihovny 64-bit propojit 32bitový kód nebo knihovny 32-bit do 64bitového kódu

Soubory objektů propojené kódu a knihovny musí být zkompilovány pro stejnou architekturu jako váš kód. Ověřte, že v knihovnách odkazy projektu kompilované pro stejnou architekturu jako projektu. Zajistěte, aby [/Libpath](../../build/reference/libpath-additional-libpath.md) nebo **další adresáře knihovny** cesta možnost používají body linkeru do knihoven vytvořené pro správnou architekturu.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>Pomocí možnosti různých kompilátoru pro vkládání funkcí v jiných zdrojových souborů

Pomocí vložená funkce definované v souborech sada a kombinování funkce vložené – možnosti kompilátoru v jiných zdrojových souborů může způsobit LNK2019. Další informace najdete v tématu [problémy vložené funkce](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Použít automatické proměnné mimo jejich oboru

Automatické proměnné (rozsah funkce) lze použít pouze v rámci oboru této funkce. Tyto proměnné nelze deklarovat `extern` a použít v jiné zdrojové soubory. Příklad, naleznete v části [automatické proměnné (rozsah funkce)](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>Volání funkce instrinsic nebo předat vnitřní funkce, které nejsou podporovány ve vaší cílové architektury typy argumentů

Například, pokud použijete AVX2 vnitřní, ale nezadávejte žádné [/ARCH:AVX2](../../build/reference/arch-x86.md) – možnost kompilátoru, kompilátor předpokládá, že se vnitřní externí funkce. Kompilátor místo aby generovala vložené instrukce, vygeneruje volání na symbol externí se stejným názvem jako vnitřní. Když linkeru se pokusí najít definice této funkce chybí, vygeneruje LNK2019. Ověřte, zda pouze pomocí vnitřní objekty a typy podporované ve vaší cílové architektury.

### <a name="you-mix-code-that-uses-native-wchart-with-code-that-doesnt"></a>Kombinovat kód, který používá nativní wchar\_t s kódem, který není

C++ jazyk shoda práci, kterou bylo provedeno v aplikaci Visual C++ 2005 provedené `wchar_t` nativního typu ve výchozím nastavení. Je nutné použít [/Zc:wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) – možnost kompilátoru pro generování kódu, které jsou kompatibilní s soubory knihovny a objekt zkompilovat pomocí starší verze aplikace Visual C++. Pokud sestavili jsme všechny soubory pomocí stejné **/Zc:wchar\_t** nastavení, typ odkazy nemusí odkazující na typy kompatibilní. Ověřte, že `wchar_t` typy v všechny soubory knihovny a objekt jsou kompatibilní, buď tím, že aktualizuje typy, které se používají, nebo pomocí konzistentní **/Zc:** nastavení při kompilaci.

## <a name="third-party-library-issues-and-vcpkg"></a>Knihovna třetích stran problémy a Vcpkg

Pokud se zobrazí tato chyba, když se pokoušíte nakonfigurovat jako součást buildu knihovnu třetích stran, zvažte použití [Vcpkg](../../vcpkg.md), Visual C++ Package Manager k instalaci a sestavení knihovny. Vcpkg podporuje velkou a rostoucí [seznam knihoven jiných výrobců](https://github.com/Microsoft/vcpkg/tree/master/ports)a nastaví vlastnosti konfigurace a závislosti v rámci projektu požadované pro úspěšné sestavení. Další informace najdete v tématu související [Visual C++ Blog](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) post.

## <a name="diagnosis-tools"></a>Nástroje pro diagnostiku

Může být obtížné zjistit, proč linkeru nelze nalézt definici konkrétní symbol. Často problém je, že nebyly zahrnuty kód, který obsahuje definici v buildu nebo sestavení, který jste vytvořili různé možnosti dekorované názvy externí symbolů. Je několik nástrojů a možnosti, které vám mohou pomoci diagnostikovat chyby LNK2019.

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) – možnost linkeru vám pomohou určit, které soubory jsou odkazy na linkeru. Můžete ověřit, zda je soubor, který obsahuje definici symbolu součástí buildu.

- [/EXPORTUJE](../../build/reference/dash-exports.md) a [/symboly](../../build/reference/symbols.md) možnosti **DUMPBIN** nástroj může pomoci zjistit, které značky jsou definovány v vaše soubory .dll a objekt nebo knihovny. Ověřte, že exportovaný dekorované názvy odpovídají dekorované názvy linkeru vyhledávání.

- **UNDNAME** nástroj lze zobrazit ekvivalentní upraveného externí symbol pro upravený název.

## <a name="examples"></a>Příklady

Tady je několik příkladů kódu, který způsobuje chybu LNK2019 spolu s informacemi o tom, jak chybu opravit.

### <a name="a-symbol-is-declared-but-not-defined"></a>Symbol je deklarován, ale není definován

V tomto příkladu je deklarován externí proměnné ale není definován:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Zde je další příklad, kde jsou funkce a proměnné deklarovány jako `extern` , ale je k dispozici žádné definice:

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

Pokud `i` a `g` jsou definovány v jednom z soubory obsažené v sestavení linkeru generuje LNK2019. Chyby lze vyřešit včetně souboru zdrojového kódu, která obsahuje definice jako součást kompilace. Alternativně můžete předat soubory .obj nebo .lib soubory, které obsahují definice, které linkeru.

### <a name="a-static-data-member-is-declared-but-not-defined"></a>Člen statických dat je deklarovaný, ale není definován

LNK2019 může dojít také při členem statických dat je deklarovaný, ale není definován. Následující ukázka generuje LNK2019 a ukazuje, jak ji odstranit.

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

### <a name="declaration-parameters-do-not-match-definition"></a>Parametry prohlášení neodpovídají žádné definice

Kód, který vyvolá šablony funkce musí mít odpovídající deklarace funkce šablon. Deklarace musí obsahovat stejné parametry šablony jako definice. Následující ukázka generuje LNK2019 na uživatelem definované operátor a ukazuje, jak ji odstranit.

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

### <a name="inconsistent-wchart-type-definitions"></a>Definice typů nekonzistentní wchar_t

Tato ukázka vytvoří knihovnu DLL, kterou má exportu, který používá `WCHAR`, který přeloží na `wchar_t`.

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

Další vzorek používá knihovnu DLL v předchozí ukázce a generuje LNK2019, protože typy bez znaménka krátké * a WCHAR\* nejsou stejné.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

 Chcete-li tuto chybu opravit, změňte `unsigned short` k `wchar_t` nebo `WCHAR`, nebo zkompilovat LNK2019g.cpp pomocí **/Zc:wchar_t-**.

## <a name="additional-resources"></a>Další zdroje

Další informace o možných příčinách a řešení pro LNK2001, najdete v článku na Stack Overflow otázku [co je externí symbol chybu nedefinované odkaz nebo nepřeložené a jak ji opravit?](http://stackoverflow.com/q/12573816/2002113).

