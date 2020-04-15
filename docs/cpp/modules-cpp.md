---
title: Přehled modulů v C++
ms.date: 12/13/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: Moduly v jazyce C++20 poskytují moderní alternativu k souborům hlaviček.
ms.openlocfilehash: cd45be1dee888c8caeb65b7ff002ac8fee1ecbe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370762"
---
# <a name="overview-of-modules-in-c"></a>Přehled modulů v C++

C++20 představuje *moduly*, moderní řešení pro komponentizaci c++ knihoven a programů. Modul je sada souborů zdrojového kódu, které jsou kompilovány nezávisle na [jednotkách překladu,](https://wikipedia.org/wiki/Translation_unit_(programming)) které je importují. Moduly eliminují nebo výrazně snižují mnoho problémů spojených s používáním souborů hlaviček a také potenciálně zkracují dobu kompilace. Makra, direktivy preprocesoru a neexportované názvy deklarované v modulu nejsou viditelné, a proto nemají žádný vliv na kompilaci jednotky překladu, která modul importuje. Moduly můžete importovat v libovolném pořadí bez obav o redefinice maker. Deklarace v jednotce importu překladu se neúčastní přenastavení přetížení nebo vyhledávání názvů v importovaném modulu. Po zkompilování modulu jednou jsou výsledky uloženy v binárním souboru, který popisuje všechny exportované typy, funkce a šablony. Tento soubor může být zpracován mnohem rychleji než soubor záhlaví a může být znovu použit kompilátorem na každém místě, kde je modul importován v projektu.

Moduly lze používat vedle sebe se soubory hlaviček. Zdrojový soubor jazyka C++ může importovat moduly a také #include soubory hlaviček. V některých případech lze soubor záhlaví importovat jako modul, nikoli textově #included preprocesorem. Doporučujeme, aby nové projekty používaly moduly, nikoli soubory hlaviček, jak je to možné. Pro větší existující projekty v rámci aktivního vývoje doporučujeme experimentovat s převodem starších záhlaví na moduly, abyste zjistili, zda se zobrazí smysluplné snížení doby kompilace.

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>Povolení modulů v kompilátoru Microsoft C++

Od Visual Studio 2019 verze 16.2 moduly nejsou plně implementovány v kompilátoru Microsoft C++. Funkci moduly můžete použít k vytvoření modulů s jedním oddílem a k importu modulů standardní knihovny poskytovaných společností Microsoft. Chcete-li povolit podporu modulů, kompilujte s [/experimental:module](../build/reference/experimental-module.md) a [/std:c++latest](../build/reference/std-specify-language-standard-version.md). V projektu sady Visual Studio klepněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a zvolte **vlastnosti**. Nastavte rozevírací **seznam Konfigurace** na **Všechny konfigurace**a pak zvolte **Vlastnosti** > konfigurace**C/C++** > **Jazyk** > **Povolit moduly C++ (experimentální).**

Modul a kód, který spotřebovává musí být zkompilován se stejnými možnostmi kompilátoru.

## <a name="consume-the-c-standard-library-as-modules"></a>Využití standardní knihovny jazyka C++ jako modulů

Ačkoli není zadán standardem C++ 20, společnost Microsoft umožňuje importovat jako moduly její implementaci standardní knihovny jazyka C++. Importem standardní knihovny jazyka C++ jako modulů, nikoli #including prostřednictvím souborů hlaviček, můžete potenciálně urychlit dobu kompilace v závislosti na velikosti projektu. Knihovna je komponentována do následujících modulů:

- std.regex poskytuje obsah \<hlavičkového regulárního>
- std.filesystem poskytuje obsah \<souborového systému záhlaví>
- std.memory poskytuje obsah \<paměti záhlaví>
- std.threading poskytuje obsah záhlaví \< \<atomické>, condition_variable>, \< \<budoucí>, \< \<mutex>, shared_mutex> a> podprocesů
- std.core poskytuje vše ostatní ve standardní knihovně C++

Chcete-li tyto moduly využívat, stačí přidat prohlášení importu do horní části souboru zdrojového kódu. Příklad:

```cpp
import std.core;
import std.regex;
```

Chcete-li využívat modul Microsoft Standard Library, zkompilujte program s [možnostmi /EHsc](../build/reference/eh-exception-handling-model.md) a [/MD.](../build/reference/md-mt-ld-use-run-time-library.md)

## <a name="basic-example"></a>Základní příklad

Následující příklad ukazuje jednoduchou definici modulu ve zdrojovém souboru s názvem **Foo.ixx**. Přípona **.ixx** je vyžadována pro soubory rozhraní modulu v sadě Visual Studio. V tomto příkladu obsahuje soubor rozhraní definici funkce, stejně jako deklarace. Definice však mohou být také umístěny v jednom nebo více samostatných souborech (jak je znázorněno v pozdějším příkladu). Exportmodul **Foo** prohlášení označuje, že tento soubor je `Foo`primární rozhraní pro modul s názvem . Modifikátor `f()` **exportu** na označuje, `Foo` že tato funkce bude viditelná při importu jiným programem nebo modulem. Všimněte si, že modul `Bar`odkazuje na obor názvů .

```cpp
export module Foo;

#define ANSWER 42

namespace Bar
{
   int f_internal() {
        return ANSWER;
      }

   export int f() {
      return f_internal();
   }
}
```

Soubor **MyProgram.cpp** používá **prohlášení importu** pro přístup k `Foo`názvu, který je exportován programem . Všimněte si, že název `Bar` je viditelný zde, ale ne všechny jeho členy. Všimněte si `ANSWER` také, že makro není viditelné.

```cpp

import Foo;
import std.core;

using namespace std;

int main()
{
   cout << "The result of f() is " << Bar::f() << endl; // 42
   // int i = Bar::f_internal(); // C2039
   // int j = ANSWER; //C2065
}

```

Prohlášení o importu se může zobrazit pouze v globálním oboru.

## <a name="implementing-modules"></a>Implementační moduly

Můžete vytvořit modul s jedním souborem rozhraní (.ixx), který exportuje názvy a zahrnuje implementace všech funkcí a typů. Můžete také umístit implementace do jednoho nebo více samostatných souborů implementace, podobně jako se používají soubory .h a CPP. Klíčové slovo **exportu** se používá pouze v souboru rozhraní. Soubor implementace můžete **importovat** jiný modul, ale nelze **exportovat** žádné názvy. Soubory implementace mohou být pojmenovány s libovolnou příponou. Soubor rozhraní a sada implementačních souborů, které jej zpět jsou považovány za speciální druh překladu jednotky zvané *modul jednotky*. Název, který je deklarován v libovolném souboru implementace, je automaticky viditelný ve všech ostatních souborech v rámci stejné jednotky modulu.

U větších modulů můžete modul rozdělit na více modulových jednotek *nazývaných oddíly*. Každý oddíl se skládá ze souboru rozhraní podporovaného jedním nebo více implementačními soubory. (Od Visual Studio 2019 verze 16.2 oddíly ještě nejsou plně implementovány.)

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>Moduly, obory názvů a vyhledávání závislé na argumentech

Pravidla pro obory názvů v modulech jsou stejná jako v jakémkoli jiném kódu. Pokud je exportováno prohlášení v oboru názvů, je implicitně exportován také ohraničující obor názvů (s výjimkou neexportovaných členů). Pokud je obor názvů explicitně exportován, exportují se všechna prohlášení v rámci této definice oboru názvů.

Při provádění vyhledávání v závislosti na argumentu pro řešení přetížení v jednotce importu překladu kompilátor považuje funkce, které jsou deklarovány ve stejné jednotce překladu (včetně rozhraní modulu), jako kde jsou definovány argumenty funkce.

### <a name="module-partitions"></a>Oddíly modulů

> [!NOTE]
> Tato část je k dispozici pro úplnost. Oddíly ještě nejsou implementovány v kompilátoru Microsoft C++.

Modul lze komponentovat do *oddílů*, z nichž každý se skládá ze souboru rozhraní a nula nebo více implementačních souborů. Oddíl modulu je podobný modulu, s tím rozdílem, že sdílí vlastnictví všech deklarací v celém modulu. Všechny názvy, které jsou exportovány soubory rozhraní oddílu jsou importovány a znovu exportovány primárním souborem rozhraní. Název oddílu musí začínat názvem modulu následovaným dvojtečkou. Deklarace v některém z oddílů jsou viditelné v rámci celého modulu. Nejsou nutná žádná zvláštní opatření, aby se zabránilo chybám pravidla jedné definice (ODR). Můžete deklarovat název (funkce, třída, atd.) v jednom oddílu a definovat jej v jiném. Soubor implementace oddílu začíná takto:

```cpp
module Foo:part1
```

a soubor rozhraní oddílu začíná takto:

```cpp
export module Foo:part1
```

Chcete-li získat přístup k deklaracím v jiném oddílu, musí jej oddíl importovat, ale může používat pouze název oddílu, nikoli název modulu:

```cpp
module Foo:part2;
import :part1;
```

Jednotka primárního rozhraní musí importovat a znovu exportovat všechny soubory oddílů rozhraní modulu takto:

```cpp
export import :part1
export import :part2
...
```

Primární jednotka rozhraní může importovat soubory implementace oddílu, ale nemůže je exportovat, protože tyto soubory nemohou exportovat žádné názvy. To umožňuje modulu zachovat podrobnosti implementace interní modulu.

## <a name="modules-and-header-files"></a>Moduly a soubory hlaviček

Soubory hlaviček můžete zahrnout do zdrojového souboru modulu `#include` umístěním směrnice před deklaraci modulu. Tyto soubory jsou považovány za v *fragmentu globálního modulu*. Modul může zobrazit pouze názvy v *fragmentu globálního modulu,* které jsou v záhlaví, které explicitně obsahuje. Fragment globálního modulu obsahuje pouze symboly, které jsou skutečně použity.

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

K řízení importovaných modulů můžete použít tradiční soubor záhlaví:

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>Importované soubory hlaviček

> [!NOTE]
> Tato část je pouze informační. Starší importy ještě nejsou implementovány v kompilátoru Microsoft C++.

Některá záhlaví jsou dostatečně samostatná, aby mohla být uvedena pomocí klíčového slova **import.** Hlavní rozdíl mezi importovou hlavičkou a importovaným modulem spoáži, že všechny definice preprocesoru v hlavičce jsou viditelné v importujícím programu bezprostředně po příkazu importu. (Definice preprocesoru ve všech souborech zahrnutých v této hlavičce *nejsou* viditelné.)

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>Viz také

[modul, import, export](import-export-module.md)
