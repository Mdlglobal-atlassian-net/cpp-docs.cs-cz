---
title: Přehled modulů v C++
ms.date: 07/23/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: Moduly v C++ 20 poskytují moderní alternativu hlavičkových souborů.
ms.openlocfilehash: 17495aa3e295b26fcfa5c489ff6793bb75d13d68
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273674"
---
# <a name="overview-of-modules-in-c"></a>Přehled modulů v C++

C++ 20 zavádí *moduly*, moderní řešení pro součásti C++ knihoven a programů. Modul je sada souborů zdrojového kódu, které jsou kompilovány nezávisle na [jednotkách překladu](https://wikipedia.org/wiki/Translation_unit_(programming)) , které je importují. Moduly eliminují nebo významně snižují mnohé problémy spojené s používáním hlavičkových souborů a také potenciálně omezují dobu kompilace. Makra, direktivy preprocesoru a neexportované názvy deklarované v modulu nejsou viditelné, takže nemají žádný vliv na kompilaci jednotky překladu, která modul importuje. Moduly můžete importovat v libovolném pořadí bez obav o předefinování maker. Deklarace v importované jednotce překladu se nepodílejí na řešení přetížení ani při vyhledávání názvů v importovaném modulu. Jakmile je modul zkompilován jednou, výsledky jsou uloženy v binárním souboru, který popisuje všechny exportované typy, funkce a šablony. Tento soubor může být zpracován mnohem rychleji než hlavičkový soubor a může být znovu použit kompilátorem každé místo, kde je modul importován v projektu.

Moduly lze použít vedle sebe se soubory hlaviček. C++ Zdrojový soubor může importovat moduly a také #include hlavičkových souborů. V některých případech je možné soubor hlaviček importovat jako modul, nikoli text #included preprocesorem. Doporučujeme, aby nové projekty používaly spíše moduly než soubory hlaviček, které jsou co nejvíc. Pro větší existující projekty v rámci aktivního vývoje doporučujeme experimentovat s převodem starších hlaviček do modulů, abyste zjistili, jestli získáte smysluplné snížení doby kompilace.

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>Povolení modulů v kompilátoru Microsoftu C++

Od verze Visual Studio 2019 verze 16,2 nejsou moduly v kompilátoru Microsoftu C++ plně implementované. Pomocí funkce moduly můžete vytvořit moduly s jedním oddílem a importovat standardní moduly knihovny poskytované společností Microsoft. Pokud chcete povolit podporu pro moduly, zkompilujte s [/Experimental: Module](../build/reference/experimental-module.md) a [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md). V projektu sady Visual Studio klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte **vlastnosti**. V rozevíracím seznamu **Konfigurace** nastavte možnost **všechny konfigurace**a pak zvolte možnost **vlastnosti** > konfigurace moduly povolení >  > **C++** **C++ jazyka C/jazyk ( experimentální)** .

Modul a kód, který ho využívá, musí být kompilovány se stejnými možnostmi kompilátoru.

## <a name="consume-the-c-standard-library-as-modules"></a>Spotřebovat C++ standardní knihovnu jako moduly

I když není určeno standardem C++ 20, společnost Microsoft umožňuje, aby byla C++ vaše implementace standardní knihovny importována jako moduly. Importováním C++ standardní knihovny jako modulů místo jejich #including skrze soubory hlaviček můžete potenciálně zrychlit dobu kompilace v závislosti na velikosti projektu. Knihovna je součástí do následujících modulů:

- STD. Regex poskytuje obsah regulárního výrazu \<Header >
- STD. FileSystem poskytuje obsah systému souborů hlaviček \<>
- STD. Memory poskytuje obsah > hlaviček \<paměti.
- \<std. Threading poskytuje obsah záhlaví atomická >, \<condition_variable >, \<budoucí >, \<mutex >, \<shared_mutex > a \<Thread >
- STD. Core poskytuje vše ostatní ve C++ standardní knihovně.

Chcete-li tyto moduly využívat, stačí přidat příkaz import do horní části souboru zdrojového kódu. Příklad:

```cpp
import std.core;
import std.regex;
```

Chcete-li využívat modul Microsoft Standard Library, je nutné zkompilovat program s možnostmi [/EHsc](../build/reference/eh-exception-handling-model.md) a [/MD](../build/reference/md-mt-ld-use-run-time-library.md) .

## <a name="basic-example"></a>Základní příklad

Následující příklad ukazuje definici jednoduchého modulu ve zdrojovém souboru s názvem **foo. IXX**. Pro soubory rozhraní modulů v aplikaci Visual Studio je vyžadováno rozšíření **. IXX** . V tomto příkladu soubor rozhraní obsahuje definici funkce i deklaraci. Nicméně definice lze také umístit do jednoho nebo více samostatných souborů (jak je znázorněno v pozdějším příkladu). Příkaz **exportovat modul foo** označuje, že tento soubor je primárním rozhraním pro modul s `Foo`názvem. Modifikátor **exportu** na `f()` označuje, že tato funkce bude viditelná, když `Foo` je importována jiným programem nebo modulem. Všimněte si, že modul odkazuje na `Bar`obor názvů.

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

Soubor **MyProgram. cpp** používá příkaz **Import** pro přístup k názvu, který je exportován pomocí `Foo`. Všimněte si, že `Bar` název je viditelný, ale ne všechny jeho členy. Všimněte si také, že `ANSWER` makro není viditelné.

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

Deklarace importu se může vyskytovat jenom v globálním oboru.

## <a name="implementing-modules"></a>Implementace modulů

Můžete vytvořit modul se souborem jediného rozhraní (. IXX), který exportuje názvy a zahrnuje implementace všech funkcí a typů. Implementace můžete také vložit do jednoho nebo více samostatných implementačních souborů, podobně jako se používají soubory. h a. cpp. Klíčové slovo **Export** se používá pouze v souboru rozhraní. Implementační soubor může **importovat** jiný modul, ale nemůže **exportovat** žádné názvy. Implementační soubory mohou být pojmenovány s libovolným rozšířením. Soubor rozhraní a sada implementačních souborů, které jsou v něm umístěny, se považují za speciální druh jednotky překladu označované jako *jednotka modulu*. Název, který je deklarován v jakémkoli implementačním souboru, je automaticky viditelný ve všech ostatních souborech v rámci stejné jednotky modulu.

U větších modulů můžete modul rozdělit do více jednotek modulu s názvem *oddíly*. Každý oddíl obsahuje soubor rozhraní zálohovaný jedním nebo více Implementačními soubory. (Počínaje verzí Visual Studio 2019 verze 16,2, oddíly ještě nejsou plně implementované.)

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>Moduly, obory názvů a vyhledávání závislé na argumentech

Pravidla pro obory názvů v modulech jsou stejná jako v jakémkoli jiném kódu. Pokud je exportována deklarace v rámci oboru názvů, je nadřazený obor názvů (kromě neexportovaných členů) také implicitně exportován. Pokud je obor názvů explicitně exportován, jsou exportovány všechny deklarace v rámci této definice oboru názvů.

Při provádění vyhledávání závislého na argumentu pro rozlišení přetížení v rámci importu jednotky překladu Kompilátor považuje funkce, které jsou deklarovány ve stejné jednotce překladu (včetně rozhraní modulů), jako je typ argumentů funkce. jsou definovány.

### <a name="module-partitions"></a>Oddíly modulů

> [!NOTE]
> Tato část je k dispozici pro úplnost. Oddíly ještě nejsou implementované v kompilátoru Microsoftu C++ .

Modul může být součástí do *oddílů*, z nichž každý obsahuje soubor rozhraní a nula nebo více implementačních souborů. Oddíl modulu je podobný modulu, s tím rozdílem, že sdílí vlastnictví všech deklarací v celém modulu. Všechny názvy, které jsou exportovány soubory rozhraní oddílu, jsou importovány a exportovány souborem primárního rozhraní. Název oddílu musí začínat názvem modulu následovaným dvojtečkou. Deklarace v libovolném z oddílů jsou viditelné v celém modulu. Není potřeba žádná zvláštní opatření, aby se předešlo chybám ODR (One-definition-Rule). Můžete deklarovat název (funkci, třídu atd.) v jednom oddílu a definovat jej v jiném. Soubor implementace oddílu začíná takto:

```cpp
module Foo:part1
```

a soubor rozhraní oddílu začíná takto:

```cpp
export module Foo:part1
```

Chcete-li získat přístup k deklaracím v jiném oddílu, oddíl musí importovat, ale může použít pouze název oddílu, nikoli název modulu:

```cpp
module Foo:part2;
import :part1;
```

Jednotka primárního rozhraní musí naimportovat a znovu exportovat všechny soubory oddílů rozhraní modulu, jako je:

```cpp
export import :part1
export import :part2
...
```

Jednotka primárního rozhraní může importovat soubory implementace oddílu, ale nemůže je exportovat, protože tyto soubory nemají povolený export jakýchkoli názvů. Díky tomu může modul uchovávat podrobnosti o implementaci pro daný modul interní.

## <a name="modules-and-header-files"></a>Moduly a hlavičkové soubory

Soubory hlaviček můžete zahrnout do zdrojového souboru modulu vložením `#include` direktivy před deklarací modulu. Tyto soubory se považují za *fragment globálního modulu*. V modulu se můžou zobrazit jenom názvy v *fragmentu globálních modulů* , které jsou v hlavičkách, které explicitně obsahují. Fragment globálních modulů obsahuje pouze symboly, které jsou skutečně použity.

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

K řízení, které moduly se importují, můžete použít tradiční hlavičkový soubor:

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>Importované hlavičkové soubory

> [!NOTE]
> Tato část je jenom informativní. Starší verze importů ještě nejsou implementované v kompilátoru C++ Microsoftu.

Některá záhlaví jsou dostatečně samostatná, aby bylo možné je uvést pomocí klíčového slova **Import** . Hlavním rozdílem mezi importovanou hlavičkou a importovaným modulem je, že všechny definice preprocesoru v hlavičce jsou viditelné v programu importu ihned po příkazu import. (Definice preprocesoru v žádném ze souborů obsažených v této hlavičce nejsou *viditelné.* )

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>Viz také:

[modul, import, export](import-export-module.md)
