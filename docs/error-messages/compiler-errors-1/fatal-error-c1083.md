---
title: Závažná chyba C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: b982c3adf59789f6c48e7e0f54ed4e71539692ad
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630777"
---
# <a name="fatal-error-c1083"></a>Závažná chyba C1083

> Nejde otevřít soubor *typ_souboru* :*File*: *Message* .

Kompilátor vygeneruje chybu C1083, když nemůže najít soubor, který vyžaduje. Tato chyba má mnoho možných příčin. Nejběžnějšími příčinami jsou nesprávná cesta hledání include nebo chybějící nebo špatně pojmenované soubory hlaviček, ale jiné typy souborů a problémy mohou také způsobovat C1083. Zde jsou některé z běžných příčin, proč kompilátor tuto chybu vygeneruje.

## <a name="the-specified-file-name-is-wrong"></a>Zadaný název souboru je chybný

Název souboru může být chybně zadán. Například

`#include <algorithm.h>`

nemusí najít soubor, který chcete. Většina C++ standardních hlavičkových souborů knihovny nemá příponu názvu souboru. h. \< Tato`#include` direktiva nenalezne hlavičku > algoritmu. Chcete-li tento problém vyřešit, ověřte, zda je zadán správný název souboru, jako v tomto příkladu:

`#include <algorithm>`

Některé hlavičky knihovny prostředí runtime jazyka C jsou umístěny v podadresáři standardního adresáře vkládaných souborů. Například pokud chcete zahrnout sys/Types. h, musíte do `#include` direktivy zahrnout název podadresáře sys:

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>Soubor není zahrnutý do cesty pro hledání vložených souborů.

Kompilátor nemůže najít soubor pomocí pravidel hledání, která jsou uvedena `#include` v direktivě nebo. `#import` Například pokud je název hlavičkového souboru uzavřený v uvozovkách,

`#include "myincludefile.h"`

Tento příkaz instruuje kompilátor, aby vyhledal soubor ve stejném adresáři, který obsahuje zdrojový soubor jako první, a pak se podívejte na jiná umístění určená prostředím sestavení. Pokud uvozovky obsahují absolutní cestu, hledá kompilátor soubor pouze na tomto místě. Pokud uvozovky obsahují relativní cestu, hledá kompilátor soubor v adresáři relativním ke zdrojovému adresáři.

Pokud je název uzavřený lomenými závorkami,

`#include <stdio.h>`

kompilátor následuje cesta pro hledání, která je definována prostředím pro sestavení, parametrem kompilátoru **/i** , možností kompilátoru **/x** a proměnnou prostředí **include** . Další informace, včetně konkrétních údajů o pořadí hledání, který se používá k vyhledání souboru, najdete v tématu direktiva [#includeC++(C/)](../../preprocessor/hash-include-directive-c-cpp.md) a [direktiva #import](../../preprocessor/hash-import-directive-cpp.md).

Pokud jsou soubory zahrnutí v jiném adresáři vzhledem ke zdrojovému adresáři a v direktivách include použijete relativní cestu, musíte místo lomených závorek použít dvojité uvozovky. Například pokud se soubor hlaviček MyHeader. h nachází v podadresáři zdrojů projektu s názvem Headers, pak tento příklad nenalezne soubor a způsobí C1083:

`#include <headers\myheader.h>`

Tento příklad funguje:

`#include "headers\myheader.h"`

Relativní cesty lze také použít s adresáři v cestě hledání include. Pokud přidáte adresář do proměnné prostředí **include** nebo cestu k **adresářům include** v aplikaci Visual Studio, nepřidávejte také část cesty k direktivám include. Například pokud je vaše hlavička umístěna na \path\example\headers\myheader.h a přidáte \path\example\headers\ do cesty k **adresářům include** v aplikaci Visual Studio, ale vaše `#include` direktiva odkazuje na soubor jako

`#include <headers\myheader.h>`

soubor se pak nenajde. Použijte správnou cestu relativní k adresáři určenému v cestě hledání include. V tomto příkladu můžete změnit cestu pro hledání include na \path\example\, nebo odebrat segment Headers \ Path z této `#include` direktivy.

## <a name="third-party-library-issues-and-vcpkg"></a>Problémy s knihovnou třetích stran a Vcpkg

Pokud se tato chyba zobrazí při pokusu o konfiguraci knihovny třetí strany v rámci sestavení, zvažte použití [Vcpkg](../../vcpkg.md), správce balíčků Visual C++ , k instalaci a sestavení knihovny. Vcpkg podporuje velký a rostoucí [seznam knihoven třetích stran](https://github.com/Microsoft/vcpkg/tree/master/ports)a nastavuje všechny vlastnosti konfigurace a závislosti vyžadované pro úspěšná sestavení v rámci projektu. Další informace najdete v souvisejícím [ C++ blogovém](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) příspěvku.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>Soubor je ve vašem projektu, ale ne cesta pro hledání include.

I když jsou hlavičkové soubory uvedeny v **Průzkumník řešení** jako součást projektu, jsou soubory nalezeny pouze kompilátorem, pokud jsou odkazovány `#include` direktivou nebo `#import` ve zdrojovém souboru a jsou umístěny v cestě hledání include. Různé druhy sestavení mohou používat různé vyhledávací cesty. Možnost kompilátoru **/x** se dá použít k vyloučení adresářů z cesty pro hledání vložených souborů. To umožňuje, aby různá sestavení používala odlišné vkládané soubory, které mají stejný název, ale jsou uloženy v různých adresářích. Jedná se o alternativu k podmíněné kompilaci pomocí příkazů preprocesoru. Další informace o možnosti kompilátoru **/x** naleznete v tématu [/x (ignorování standardních cest zahrnutí)](../../build/reference/x-ignore-standard-include-paths.md).

Chcete-li tento problém vyřešit, opravte cestu, kterou kompilátor používá k hledání vkládaného nebo importovaného souboru. Nový projekt používá výchozí cesty hledání include. Je možné, že budete muset změnit cestu pro vyhledávání zahrnutí a přidat adresář pro váš projekt. Pokud kompilujete na příkazovém řádku, přidejte cestu k proměnné prostředí **include** nebo **/i** možnost kompilátoru pro určení cesty k souboru.

Chcete-li nastavit cestu k adresáři include v aplikaci Visual Studio, otevřete dialogové okno **stránky vlastností** projektu. V levém podokně v části **Vlastnosti konfigurace** vyberte **adresáře VC + +** a pak upravte vlastnost **Zahrnout adresáře** . Další informace o adresářích pro jednotlivé uživatele a projekty vyhledaných kompilátorem v aplikaci Visual Studio naleznete na [stránce vlastností adresářů VC + +](../../build/reference/vcpp-directories-property-page.md). Další informace o možnosti kompilátoru **/i** naleznete v tématu [/I (další adresáře k zahrnutí)](../../build/reference/i-additional-include-directories.md).

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>Prostředí příkazového řádku INCLUDE nebo LIB není nastavené.

Při vyvolání kompilátoru z příkazového řádku se k určení vyhledávací cesty často používají proměnné prostředí. Pokud není správně nastavena cesta vyhledávání popsaná proměnnou prostředí **include** nebo **lib** , může být vygenerována chyba C1083. Důrazně doporučujeme použít zástupce příkazového řádku pro vývojáře k nastavení základního prostředí pro sestavení příkazového řádku. Další informace naleznete v tématu [sestavení C/C++ na příkazovém řádku](../../build/building-on-the-command-line.md). Další informace o použití proměnných prostředí naleznete v tématu [How to: Použijte proměnné prostředí v sestavení](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build).

## <a name="the-file-may-be-locked-or-in-use"></a>Soubor může být uzamčený nebo používaný.

Pokud k úpravám nebo přístupu k souboru používáte jiný program, soubor může být zamčený. Zkuste soubor zavřít v druhém programu. V některých případech může být jiný program Visual Studio, pokud používáte možnosti paralelní kompilace. Pokud vypnete možnost paralelního sestavení, dojde k chybě, takže se jedná o problém. K těmto potížím může mít i další paralelní sestavovací systémy. Buďte opatrní při nastavování závislostí souborů a projektů, aby bylo pořadí sestavení správné. V některých případech zvažte vytvoření zprostředkujícího projektu pro vynucení pořadí závislosti sestavení pro společný soubor, který může být sestaven více projekty. Někdy antivirové programy dočasně mění nedávno změněné soubory ke skenování. Pokud je to možné, zvažte možnost vyloučit adresáře pro sestavení projektu z antivirového programu.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>Je vložena chybná verze souboru

Chyba C1083 může také označovat, že je vložena chybná verze souboru. Sestavení může například obsahovat chybnou verzi souboru, který obsahuje `#include` direktivu pro hlavičkový soubor, který není určen pro toto sestavení. Například některé soubory mohou být použity pouze pro sestavení x86 nebo pro ladění sestavení. Pokud hlavičkový soubor není nalezen, vygeneruje kompilátor chybu C1083. Tento problém vyřešíte použitím správného souboru, nikoli přidáním hlavičkového souboru nebo adresáře do sestavení.

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>Předkompilované hlavičky ještě nejsou předkompilovány

Pokud se v projektu používají předkompilované hlavičky, musí být vytvořeny relevantní soubory .pch, aby bylo možné zkompilovat soubory, které používají obsah těchto hlaviček. Například soubor *PCH. cpp* (*stdafx. cpp* v aplikaci Visual Studio 2017 a starší) je automaticky vytvořen v adresáři projektu pro nové projekty. Tento soubor zkompilujte jako první, abyste vytvořili předkompilované hlavičkové soubory. V typickém návrhu procesu sestavení je to provedeno automaticky. Další informace naleznete v tématu [vytváření předkompilovaných hlavičkových souborů](../../build/creating-precompiled-header-files.md).

## <a name="additional-causes"></a>Další příčiny

- Nainstalovali jste sadu SDK nebo knihovnu třetích stran, ale po instalaci sady SDK nebo knihovny jste neotevřeli nové okno příkazového řádku pro vývojáře. Pokud sada SDK nebo knihovna přidá soubory do cesty **include** , může být nutné otevřít nové okno příkazového řádku pro vývojáře, aby bylo možné tyto změny proměnných prostředí vybrat.

- Soubor používá spravovaný kód, ale možnost kompilátoru **/CLR** není zadána. Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

- Soubor je zkompilován pomocí jiného nastavení možnosti kompilátoru **/analyze** , než je použito pro předkompilování hlaviček. Pokud jsou hlavičky projektu předkompilovány, všechny by měly používat stejné nastavení **/analyze** . Další informace naleznete v tématu [/analyze (analýza kódu)](../../build/reference/analyze-code-analysis.md).

- Soubor nebo adresář byl vytvořen v subsystému Windows pro Linux, citlivost na velká a malá písmena v adresáři je povolena a zadaný případ cesty nebo souboru neodpovídá velikosti písmen nebo souboru na disku.

- Soubor, adresář nebo disk je určen jen pro čtení.

- Sady Visual Studio nebo nástroje příkazového řádku nemají dostatečná oprávnění ke čtení souboru nebo adresáře. K tomu může dojít například v případě, že soubory projektu mají jiné vlastnictví než proces, na kterém běží aplikace Visual Studio nebo nástroje příkazového řádku. Tento problém je někdy možné vyřešit spuštěním sady Visual Studio nebo příkazového řádku pro vývojáře jako správce.

- Není k dispozici dostatek popisovačů souborů. Ukončete některé aplikace a opakujte kompilaci. Tento stav je za typických okolností neobvyklý. Může se však vyskytnout při sestavování rozsáhlých projektů na počítači s omezenou fyzickou pamětí.

## <a name="example"></a>Příklad

Následující příklad vygeneruje chybu C1083 v případě, že soubor `"test.h"` hlaviček neexistuje ve zdrojovém adresáři nebo v cestě pro hledání include.

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

Informace o tom, jak sestavit C/C++ projekty v integrovaném vývojovém prostředí (IDE) nebo na příkazovém řádku a informace o nastavení proměnných prostředí naleznete v tématu [projekty a systémy sestavení](../../build/projects-and-build-systems-cpp.md).

## <a name="see-also"></a>Viz také:

- [Vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties)
