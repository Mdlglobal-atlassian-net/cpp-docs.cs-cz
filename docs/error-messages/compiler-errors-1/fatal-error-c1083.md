---
title: Závažná chyba C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: 522bc4a36be59d4e2c9425e50b1238eb9f4aba61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368055"
---
# <a name="fatal-error-c1083"></a>Závažná chyba C1083

> Nelze otevřít *filetype* souboru: "*souboru*': *zprávy*

Kompilátor vygeneruje chybu C1083, pokud nemůže najít soubor, který vyžaduje. Existuje mnoho možných příčin této chyby. Vyhledávání protokolem nesprávné zahrnout cestu nebo chybějící nebo nesprávný název hlavičkové soubory jsou nejčastější příčiny, ale ostatní typy souborů a problémy mohou být způsobeny také C1083. Tady jsou některé běžné důvody, proč kompilátor tuto chybu vygeneruje.

## <a name="the-specified-file-name-is-wrong"></a>Zadaný název souboru je chybný

Název souboru může být chybně zadán. Například

`#include <algorithm.h>`

nemusí najít soubor, který chcete. Většina souborech hlaviček standardní knihovny C++ nemají příponu názvu souboru hlaviček. \<Algoritmus > by je nenašla záhlaví to `#include` směrnice. Chcete-li vyřešit tento problém, ověřte, že je zadán správný název souboru, jako v následujícím příkladu:

`#include <algorithm>`

Některé hlavičky knihovny prostředí runtime jazyka C jsou umístěny v podadresáři standardního adresáře vkládaných souborů. Například pokud chcete zahrnout sys/types.h, musí obsahovat název podadresáře sys v `#include` – direktiva:

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>Soubor není zahrnutý v cestu vyhledávání

Kompilátor nemůže soubor najít pomocí pravidel vyhledávání, které jsou označeny `#include` nebo `#import` směrnice. Například, pokud je název souboru hlaviček uzavřen v uvozovkách,

`#include "myincludefile.h"`

říká kompilátoru, vyhledejte soubor ve stejném adresáři, který obsahuje zdrojový soubor nejprve, a pak vyhledejte jiných místech určených sestavovacím prostředím. Pokud uvozovky obsahují absolutní cestu, hledá kompilátor soubor pouze na tomto místě. Pokud uvozovky obsahují relativní cestu, hledá kompilátor soubor v adresáři relativním ke zdrojovému adresáři.

Pokud název je uzavřen do lomených závorek

`#include <stdio.h>`

sleduje kompilátor vyhledávací cestu, která je definována sestavovacím prostředím, **/I** – možnost kompilátoru, **/X** – možnost kompilátoru a **zahrnout** proměnné prostředí. Další informace, včetně podrobností o pořadí hledání používá k nalezení souboru, naleznete v tématu [#include – direktiva (C/C++)](../../preprocessor/hash-include-directive-c-cpp.md) a [#import Directive](../../preprocessor/hash-import-directive-cpp.md).

Pokud jsou zahrnuté soubory v jiném adresáři relativně vzhledem k adresáři zdroje a použít relativní cestu ve vaší direktiv, je nutné použít dvojité uvozovky místo lomených závorek. Například pokud vaše myheader.h soubor záhlaví je v podadresáři zdroje projektu s názvem záhlaví, pak v tomto příkladu se nepodaří najít soubor a způsobí, že C1083:

`#include <headers\myheader.h>`

ale tento příklad funguje:

`#include "headers\myheader.h"`

Relativní cesty lze použít také s adresáři na cestě pro vyhledávání zahrnout. Pokud chcete přidat adresář do **zahrnout** proměnné prostředí nebo na vaše **adresáře souborů k zahrnutí** cestu v sadě Visual Studio také nepřidávejte část cesty pro direktivy include. Například, pokud se nachází na \path\example\headers\myheader.h záhlaví a přidat \path\example\headers\ do vaší **adresáře souborů k zahrnutí** cestu v sadě Visual Studio, ale vaše `#include` – direktiva odkazuje na soubor jako

`#include <headers\myheader.h>`

pak soubor nebyl nalezen. Použijte správnou cestu relativní vzhledem k adresáři uvedeném na cestu vyhledávání. V tomto příkladu můžete změnit cesty hledání zahrnutí \path\example\, nebo odeberte segment cesty headers\ z `#include` směrnice.

## <a name="third-party-library-issues-and-vcpkg"></a>Problémy knihovny třetí strany a Vcpkg

Pokud tato chyba se zobrazí, když se pokoušíte nakonfigurovat knihovny třetích stran jako součást vašeho sestavení, zvažte použití [Vcpkg](../../vcpkg.md), Visual C++ balíček správce k instalaci a vytvoření knihovny. Vcpkg podporuje jejichž [seznam knihoven třetích stran](https://github.com/Microsoft/vcpkg/tree/master/ports)a nastaví vlastnosti konfigurace a závislosti, které vyžaduje pro úspěšné sestavení jako součást vašeho projektu. Další informace najdete v tématu související [blogu Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) příspěvku.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>Soubor je v projektu, ale ne cestu vyhledávání

I, když jsou hlavičkové soubory uvedeny v **Průzkumníku řešení** v rámci projektu se soubory najít pouze kompilátor při jsou označovány pomocí `#include` nebo `#import` směrnice ve zdroji souborů a jsou umístěny v Zahrňte cestu vyhledávání. Různé druhy sestavení mohou používat různé vyhledávací cesty. **/X** – možnost kompilátoru je možné vyloučit adresáře z cesty hledání zahrnutí. To umožňuje, aby různá sestavení používala odlišné vkládané soubory, které mají stejný název, ale jsou uloženy v různých adresářích. Jedná se o alternativu k podmíněné kompilaci pomocí příkazů preprocesoru. Další informace o **/X** – možnost kompilátoru, naleznete v tématu [/X (Ignore Standard Include Paths)](../../build/reference/x-ignore-standard-include-paths.md).

Chcete-li tento problém vyřešit, opravte cestu, kterou kompilátor používá k hledání vkládaného nebo importovaného souboru. Nový projekt používá výchozí vyhledávací cesty zahrnutí. Budete muset změnit cestu vyhledávání přidat adresář projektu. Pokud kompilujete na příkazovém řádku, přidejte cestu k **zahrnout** proměnné prostředí nebo **/I** – možnost kompilátoru chcete zadat cestu k souboru.

Chcete-li nastavit cestu k adresáři vkládaných v sadě Visual Studio, otevřete v projektu **stránky vlastností** dialogové okno. Vyberte **adresáře VC ++** pod **vlastnosti konfigurace** v levém podokně a pak upravit **adresáře souborů k zahrnutí** vlastnost. Další informace o uživatelských a projektových adresářích prohledávat pomocí kompilátoru v sadě Visual Studio najdete v tématu [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md). Další informace o **/I** – možnost kompilátoru, naleznete v tématu [/I (další vložené adresáře)](../../build/reference/i-additional-include-directories.md).

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>Není nastaven na příkazovém řádku zahrnout nebo prostředí LIB

Při vyvolání kompilátoru z příkazového řádku se k určení vyhledávací cesty často používají proměnné prostředí. Pokud vyhledávací cesta popsaná **zahrnout** nebo **LIB** proměnná prostředí není nastavená správně, je možné generovat chybu C1083. Důrazně doporučujeme použití zástupce příkazového řádku pro vývojáře k nastavení základní prostředí pro příkazový řádek sestavení. Další informace najdete v tématu [sestavení C/C++ v příkazovém řádku](../../build/building-on-the-command-line.md). Další informace o tom, jak použít proměnné prostředí najdete v tématu [jak: Použití proměnných prostředí v sestavení](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build).

## <a name="the-file-may-be-locked-or-in-use"></a>Soubor může být uzamčen nebo používá

Pokud používáte jiný program pro úpravy nebo přístup k souboru, může mít soubor uzamčen. Zavřete soubor v jiné aplikaci. Druhý program někdy může být Visual Studio jako takové, pokud použijete možnosti souběžné kompilace. Pokud vypnutí možnosti paralelního buildu provede chybu odstranit, a to je problém. Tento problém může mít také jiné systémy paralelní sestavení. Buďte opatrní při nastavení závislostí souboru a projektu, tedy správné pořadí sestavení. V některých případech zvažte vytvoření zprostředkující projektu k vynucení pořadí závislosti sestavení pro běžné souborů, které můžou vytvářet více projektů. Někdy antivirové programy dočasně uzamčení nejnověji změněných souborů ke skenování. Pokud je to možné zvažte možnost vyloučit adresáře sestavení projektu z antivirového programu.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>Je vložena chybná verze souboru

Chyba C1083 může také označovat, že je vložena chybná verze souboru. Sestavení může obsahovat třeba chybná verze souboru, který má `#include` směrnice pro soubor hlaviček, který není určený pro toto sestavení. Například některé soubory může platit pouze pro x86 sestavení, nebo k sestavení pro ladění. Pokud hlavičkový soubor není nalezen, vygeneruje kompilátor chybu C1083. Tento problém vyřešíte použitím správného souboru, nikoli přidáním hlavičkového souboru nebo adresáře do sestavení.

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>Předkompilované hlavičky ještě nejsou předkompilovány

Pokud se v projektu používají předkompilované hlavičky, musí být vytvořeny relevantní soubory .pch, aby bylo možné zkompilovat soubory, které používají obsah těchto hlaviček. Například soubor stdafx.cpp se automaticky vytvoří v adresáři projektu pro nové projekty. Tento soubor zkompilujte jako první, abyste vytvořili předkompilované hlavičkové soubory. V typickém návrhu procesu sestavení je to automaticky. Další informace najdete v tématu [vytváření předkompilovaných hlavičkových souborů](../../build/creating-precompiled-header-files.md).

## <a name="additional-causes"></a>Další příčiny

- Jste nainstalovali sadu SDK nebo knihovny třetí strany, ale nebyly otevřít nové okno příkazového řádku pro vývojáře po sady SDK nebo knihovna je nainstalována. Pokud sada SDK nebo knihovny přidá soubory **zahrnout** cestu, je nutné otevřít nové okno příkazového řádku pro vývojáře ke sbírání tyto změny proměnné prostředí.

- Soubor používá spravovaný kód, ale možnost kompilátoru **/CLR** není zadán. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

- Soubor je zkompilován pomocí jiného **/ analyze** nastavení parametru kompilátoru, než jaký se použil k předkompilaci hlaviček. Pokud jsou hlavičky projektu předkompilovány, měly by všechny používat stejné **/ analyze** nastavení. Další informace najdete v tématu [/ analyze (Analýza kódu)](../../build/reference/analyze-code-analysis.md).

- Soubor nebo adresář byl vytvořen v subsystému Windows pro Linux, rozlišování velikosti písmen pro každý adresář je povoleno a zadaný případ cesty nebo souboru se neshoduje s případ cesty nebo souboru na disku.

- Soubor, adresář nebo disk je určen jen pro čtení.

- Visual Studio nebo nástroje příkazového řádku nemají dostatečná oprávnění ke čtení souboru nebo adresáři. To může nastat například při soubory projektu mají různé vlastnictví než proces, který běží Visual Studio nebo nástroje příkazového řádku. Někdy může být tento problém vyřešen pomocí sady Visual Studio nebo příkazového řádku pro vývojáře jako správce.

- Není k dispozici dostatek popisovačů souborů. Ukončete některé aplikace a opakujte kompilaci. Tento stav je za typických okolností neobvyklý. Může se však vyskytnout při sestavování rozsáhlých projektů na počítači s omezenou fyzickou pamětí.

## <a name="example"></a>Příklad

Následující příklad vygeneruje chybu C1083 při hlavičkový soubor `"test.h"` neexistuje ve zdrojovém adresáři nebo na cestu vyhledávání.

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

Informace o tom, jak vytvářet projekty C/C++ v integrovaném vývojovém prostředí nebo na příkazovém řádku a informace o nastavení proměnných prostředí, najdete v části [projekty a sestavení systémy](../../build/projects-and-build-systems-cpp.md).

## <a name="see-also"></a>Viz také:

- [Vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties)
