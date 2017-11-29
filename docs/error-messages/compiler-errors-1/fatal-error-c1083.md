---
title: "Závažná chyba C1083 | Microsoft Docs"
ms.custom: 
ms.date: 09/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1083
dev_langs: C++
helpviewer_keywords: C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bce56a9e90ba8139b55bf013f19af47c587c2472
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1083"></a>Závažná chyba C1083

> Nelze otevřít *typ souboru* souboru: "*soubor*': *zpráv*  
  
Kompilátor generuje C1083 chyba, když nemůže najít soubor, který vyžaduje. Existuje mnoho možných příčin této chyby. Vyhledávání protokolem nesprávný zahrnout cestu nebo chybějící nebo nesprávný název hlavičky soubory jsou nejběžnější příčiny, ale jiné typy souborů a problémy může také způsobit C1083. Tady jsou některé běžné důvody, proč kompilátor vygeneruje tuto chybu.  
  
## <a name="the-specified-file-name-is-wrong"></a>Zadaný název souboru je chybný 
  
Název souboru může být chybně zadán. Například  

`#include <algorithm.h>`  
  
nemusí najít soubor, který chcete. Většina souborů záhlaví standardní knihovna C++ nemají příponu názvu souboru .h. \<Algoritmus > záhlaví nebude nalezen tento `#include` – direktiva. Chcete-li tento problém vyřešit, ověřte, zda je zadán správný název souboru, jako v následujícím příkladu:  

`#include <algorithm>`
  
Některé hlavičky knihovny prostředí runtime jazyka C jsou umístěny v podadresáři standardního adresáře vkládaných souborů. Například pokud chcete zahrnout sys/types.h, musí obsahovat název sys podadresáři v `#include` – direktiva:  
  
`#include <sys/types.h>`  

## <a name="the-file-is-not-included-in-the-include-search-path"></a>Soubor není součástí cesty pro hledání zahrnout  
  
Kompilátor nemůže najít soubor pomocí pravidel vyhledávání, které jsou označeny `#include` nebo `#import` – direktiva. Například pokud název hlavičky souboru uzavřena v uvozovkách,  
  
`#include "myincludefile.h"`  
  
Tato hodnota informuje kompilátoru vyhledat soubor ve stejném adresáři, který obsahuje zdrojový soubor nejdřív, a pak hledejte v jiných umístěních určeného prostředí sestavení. Pokud uvozovky obsahují absolutní cestu, hledá kompilátor soubor pouze na tomto místě. Pokud uvozovky obsahují relativní cestu, hledá kompilátor soubor v adresáři relativním ke zdrojovému adresáři. 

Pokud je název obklopeno lomené závorky  
  
`#include <stdio.h>`  
  
Kompilátor následuje cesta hledání, který je definován v prostředí sestavení, **/I** – možnost kompilátoru, **/X** – možnost kompilátoru a **zahrnout** proměnné prostředí. Další informace, včetně konkrétní podrobnosti o pořadí hledání použít k vyhledání souboru, najdete v části [#include – direktiva (C/C++)](../../preprocessor/hash-include-directive-c-cpp.md) a [#import – direktiva](../../preprocessor/hash-import-directive-cpp.md).

Pokud jsou vaše zahrnout soubory v jiném adresáři relativně k zdrojový adresář a použít relativní cestu do vaší zahrnují direktivy, je nutné použít uvozovky místo lomené závorky. Například pokud vaše myheader.h záhlaví souboru je v podadresáři vašich zdrojů projektu s názvem hlavičky, pak tento příklad nepodaří najít soubor a způsobí, že C1083:

`#include <headers\myheader.h>`

ale funguje v tomto příkladu:

`#include "headers\myheader.h"`

Relativní cesty můžete použít taky s adresáře v cestě hledání zahrnout. Pokud přidáte adresáře **zahrnout** proměnné prostředí nebo vaše **adresáře Include** cestu v sadě Visual Studio, taky nepřidávejte část cesty do direktivy zahrnout. Například pokud vaše záhlaví se nachází v \path\example\headers\myheader.h a přidejte \path\example\headers\ k vaší **adresáře Include** cestu v sadě Visual Studio, ale vaše `#include` – direktiva odkazuje na soubor jako
  
`#include <headers\myheader.h>`  

potom soubor nebyl nalezen. Pomocí správné cesty relativní k adresáři zadaná v cestě pro vyhledávání zahrnout. V tomto příkladu můžete změnit cesta hledání zahrnout \path\example\, nebo odeberte segment cesty headers\ z `#include` – direktiva.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>Soubor je v projektu, ale ne cesta hledání zahrnout

I když uvedené hlavičkových souborů v **Průzkumníku řešení** v rámci projektu, se soubory pouze nacházejí kompilátorem při jsou označovány pomocí `#include` nebo `#import` direktivy ve zdroji souborů a jsou umístěny v Zahrňte cesty pro hledání. Různé druhy sestavení mohou používat různé vyhledávací cesty. **/X** – možnost kompilátoru lze použít k vyloučení adresářů z cesty pro hledání zahrnout. To umožňuje, aby různá sestavení používala odlišné vkládané soubory, které mají stejný název, ale jsou uloženy v různých adresářích. Jedná se o alternativu k podmíněné kompilaci pomocí příkazů preprocesoru. Další informace o **/X** – možnost kompilátoru, najdete v části [/X (Ignorovat standardní cesty zahrnutí)](../../build/reference/x-ignore-standard-include-paths.md).  
  
Chcete-li tento problém vyřešit, opravte cestu, kterou kompilátor používá k hledání vkládaného nebo importovaného souboru. Hledání cesty zahrnutí nové používá výchozí projekt. Možná budete muset upravit cesta hledání zahrnout přidat adresář pro váš projekt. Pokud jste se kompilování na příkazovém řádku, přidejte cestu k **zahrnout** proměnné prostředí nebo **/I** – možnost kompilátoru pro zadání cesty k souboru. 

Pokud chcete nastavit cestu k adresáři include v sadě Visual Studio, otevřete projektu **stránky vlastností** dialogové okno. Vyberte **adresáře VC ++** pod **vlastnosti konfigurace** v levém podokně a upravte **adresáře Include** vlastnost. Další informace o adresářích na uživatele a každý projekt, vyhledávat kompilátorem v sadě Visual Studio najdete v tématu [stránka vlastností adresářů VC ++](../../ide/vcpp-directories-property-page.md). Další informace o **/I** – možnost kompilátoru, najdete v části [/I (Další adresáře Include)](../../build/reference/i-additional-include-directories.md).  
  
## <a name="the-command-line-include-environment-is-not-set"></a>Není nastaven zahrnout prostředí příkazového řádku

Při vyvolání kompilátoru z příkazového řádku se k určení vyhledávací cesty často používají proměnné prostředí. Pokud cesta hledání popsaného **zahrnout** proměnnou prostředí není správně nastaven, lze vygenerovat C1083 chyby. Důrazně doporučujeme nastavit základní prostředí pro příkazový řádek pomocí zástupce příkazového řádku vývojáře sestavení. Další informace najdete v tématu najdete v části [sestavení C/C++ v příkazovém řádku](../../build/building-on-the-command-line.md). Další informace o tom, jak použít proměnné prostředí, najdete v tématu [postupy: použití proměnných prostředí v sestavení](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build).  

## <a name="the-file-may-be-locked-or-in-use"></a>Soubor je pravděpodobně uzamčen nebo používat

Pokud používáte jiný program upravit nebo získat přístup k souboru, může mít soubor uzamčen. Zavřete soubor v jiné aplikaci. Druhý program někdy může být Visual Studio, samostatně, pokud použijete možnosti Paralelní kompilace. Pokud vypnutí možnost paralelní sestavení provede chyba zmizí, pak se jedná o problém. Tento problém může mít také jiné systémy paralelní sestavení. Pečlivě nastavit soubor a projekt závislosti pořadí sestavení je správný. V některých případech zvažte vytvoření projektu zprostředkující vynutit pořadí závislostí sestavení pro běžné soubor, který může být vytvořené více projektů. Někdy antivirové programy dočasně uzamčení naposledy změněné soubory pro skenování. Pokud je to možné zvažte vyloučení adresáře sestavení projektu z antivirového programu.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>Je vložena chybná verze souboru  
  
Chyba C1083 může také označovat, že je vložena chybná verze souboru. Sestavení může obsahovat třeba chybná verze souboru, který má `#include` direktivy pro soubor hlaviček, která není určená pro toto sestavení. Například určitých souborů může platit pouze pro x86 sestavení, nebo k sestavení pro ladění. Pokud hlavičkový soubor není nalezen, vygeneruje kompilátor chybu C1083. Tento problém vyřešíte použitím správného souboru, nikoli přidáním hlavičkového souboru nebo adresáře do sestavení.  
  
## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>Předkompilované hlavičky ještě nejsou předkompilovány  
  
Pokud se v projektu používají předkompilované hlavičky, musí být vytvořeny relevantní soubory .pch, aby bylo možné zkompilovat soubory, které používají obsah těchto hlaviček. Například soubor stdafx.cpp se automaticky vytvoří v adresáři projektu pro nové projekty. Tento soubor zkompilujte jako první, abyste vytvořili předkompilované hlavičkové soubory. V procesu návrhu typické sestavení udělá se to automaticky. Další informace najdete v tématu [vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md).  
  
## <a name="additional-causes"></a>Další příčiny  
  
- Instalaci sady SDK nebo knihovna třetích stran, ale nebyly otevřít nové okno příkazového řádku vývojáře po sady SDK nebo knihovna je nainstalována. Pokud sada SDK nebo knihovny přidá soubory **zahrnout** cestu, budete muset otevřete nové okno příkazového řádku vývojáře k vyzvedne, až tyto změny proměnné prostředí.

- Soubor, který používá spravovaného kódu, ale možnost kompilátoru **/CLR** není zadán. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
- Kompiluje soubor pomocí jiné **/ analyze** nastavení kompilátoru možnosti, než se používá k předkompilovat hlavičky. Když jsou předkompilované hlavičky pro projekt, všechny musí používat stejné **/ analyze** nastavení. Další informace najdete v tématu [/ analyze (Analýza kódu)](../../build/reference/analyze-code-analysis.md).  
  
- Soubor, adresář nebo disk je určen jen pro čtení.  
  
- Visual Studio nebo nástroje příkazového řádku nemají dostatečná oprávnění ke čtení soubor nebo adresář. To může nastat, například při soubory projektu mají různé vlastnictví než procesu spuštění sady Visual Studio nebo nástroje příkazového řádku. Někdy lze tento problém opravit spuštěním Visual Studio nebo příkazového řádku vývojáře jako správce.  
  
- Není k dispozici dostatek popisovačů souborů. Ukončete některé aplikace a opakujte kompilaci. Tento stav je za typických okolností neobvyklý. Může se však vyskytnout při sestavování rozsáhlých projektů na počítači s omezenou fyzickou pamětí.  
  
## <a name="example"></a>Příklad

Následující příklad generuje chyby C1083 při soubor hlaviček `"test.h"` ze zdrojového adresáře nebo na cesta hledání zahrnout neexistuje.  
  
```  
// C1083.cpp  
// compile with: /c  
#include "test.h"   // C1083 test.h does not exist  
#include "stdio.h"  // OK  
```  
  
Informace o tom, jak vytvářet projekty C/C++ v prostředí IDE nebo na příkazovém řádku a informace o nastavení proměnných prostředí najdete v tématu [sestavení C/C++ programů](../../build/building-c-cpp-programs.md).
 
## <a name="see-also"></a>Viz také

[Vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties)