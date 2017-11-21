---
title: "Chyba linkerů Lnk1104 | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1104
dev_langs: C++
helpviewer_keywords: LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ebc0b23a7d92c94373b9ae5be01a0ef50476e433
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1104"></a>Chyba linkerů LNK1104
Nelze otevřít soubor "*filename*.  
  
Linkeru nelze otevřít zadaný soubor.  
  
## <a name="possible-causes-and-solutions"></a>Možné příčiny a řešení
  
Této chybě může dojít, když se pokusí otevřít soubor pro čtení nebo zápis linkeru. Nejběžnější příčiny tohoto problému je, že soubor neexistuje, nelze nalézt v jednom adresáři linkeru vyhledá, nebo je používán a uzamčen jiným procesem. Ne tak často můžete mít dostatek místa na disku, soubor je pravděpodobně příliš velký, cesta k souboru může být příliš dlouhý nebo nemusí mít oprávnění k přístupu k souboru.  

Kontrola pro jednu z těchto běžné problémy:  

-   Aplikace je již spuštěn, když zkusíte znovu sestavit. Pokud je soubor, který nelze otevřít spustitelný soubor nebo soubor ladění například pdb, to obvyklou příčinou je. Chcete-li tento problém vyřešit, zastavte program a uvolnit z ladicího programu před vytvořením ho znovu.  
  
-   Soubor *filename* je sestavena řešení, ale ještě neexistuje při linkeru pokusu o přístup. To může dojít v případě, že jeden projektu závisí na jiném projektu k vytvoření tohoto souboru, ale nejsou projektů vytvořen ve správném pořadí. Chcete-li tento problém vyřešit, ujistěte se, odkazy projektu se nastavují v projekt, který používá soubor, takže chybí soubor vychází, než se požaduje. Další informace najdete v tématu [přidání odkazů v projektech Visual C++](../../ide/adding-references-in-visual-cpp-projects.md) a [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).  
  
-   Název souboru nebo na příkazovém řádku nebo v direktivě lib #pragma zadaná cesta je nesprávný, nebo cesta obsahuje specifikace Jednotka není platná. Zkontrolujte zadané informace a ověřte, zda že soubor existuje v zadaném umístění.  
  
-   Pokud používáte Visual Studio IDE pro sestavení projektu, který jste zkopírovali z jiného počítače, může být jiný instalační umístění pro knihovny. Zkontrolujte vlastnost adresáře knihovny na [stránka vlastností adresářů VC ++](../../ide/vcpp-directories-property-page.md) a v případě potřeby ji aktualizujte. Chcete-li zobrazit a upravit aktuální cesty knihoven nastavení v IDE, vyberte ovládací prvek rozevírací seznam pro vlastnost adresáře knihovny a zvolte **upravit**. **Vyhodnotit hodnotu** části dialogového okna adresáře knihovny jsou uvedené aktuální cesty vyhledávat soubory knihovny.  
  
-   Pokud vytváříte projekt, který byl vytvořen pomocí starší verze sady Visual Studio, sada nástrojů platformy a knihovny pro tuto verzi pravděpodobně není nainstalován. Chcete-li tento problém vyřešit, máte dvě možnosti: můžete upgradovat projekt, který používá aktuální sada nástrojů platformy instalaci, nebo můžete nainstalovat starší nástrojů a sestavte projekt beze změny. Další informace najdete v tématu [upgrade projektů z dřívějších verzí nástroje Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) a [pomocí nativní cílení na více v sadě Visual Studio staré projekty sestavení](../../porting/use-native-multi-targeting.md).
  
-   Nejsou nainstalovány knihovny pro aktuální konfigurací projektu nebo sada nástrojů platformy. Ověřte, zda sada nástrojů platformy a sady Windows SDK zadán v [stránku Obecné vlastnosti](../../ide/general-property-page-project.md) jsou nainstalovány pro svůj projekt a ověřte, zda jsou k dispozici v adresáři knihovny pro zadaný v požadované knihovny [ Stránka vlastností adresářů VC ++](../../ide/vcpp-directories-property-page.md) pro nastavení konfigurace. Existují samostatné nastavení pro ladění a prodejní konfigurace, proto pokud jeden sestavení funguje, ale druhá způsobuje chybu, nastavení správné a jsou nainstalovány požadované nástroje a knihovny pro obě konfigurace.  
  
-   Cesta k sadě Windows SDK je zastaralý. Pokud máte nainstalovanou verzi sady Windows SDK, která je novější než vaší verzí sady Visual Studio, ujistěte se, že v zadané cesty [stránka vlastností adresářů VC ++](../../ide/vcpp-directories-property-page.md) jsou aktualizovány tak, aby odpovídaly novou sadu SDK. Pokud pomocí příkazového řádku vývojáře, ujistěte se, že se aktualizuje dávkový soubor, který inicializuje objekt environment variables pro nové cesty SDK.  
  
-   Jiný program může mít soubor otevřít a linkeru nemohou do ní zapisovat. Antivirové programy často dočasně zablokovat přístup k souborům, nově vytvořený. Chcete-li tento problém vyřešit, zkuste vyloučení adresáře sestavení projektu z antivirového programu.  
  
-   Pokud používáte možnost paralelní sestavení, je možné, že tento soubor na jiné vlákno uzamknul Visual Studio. Tento problém vyřešit, ověřte, že jste nevytvářejte stejný objekt kódu nebo knihovny ve více projektech, a použijte závislosti sestavení nebo odkazy na projekt a pokračovat tam integrovaný binární soubory v projektu.  
  
-   Máte nesprávný proměnná prostředí LIB. V sestavení příkazového řádku ověřte, zda proměnná prostředí LIB nastavena a obsahuje všechny adresáře pro knihovny, které používáte. V prostředí IDE, je proměnná LIB nastavena pomocí vlastnosti adresáře knihovny na [stránka vlastností adresářů VC ++](../../ide/vcpp-directories-property-page.md). Zajistěte, aby všechny, které jsou zde uvedeny adresáře, které obsahují knihovny, které potřebujete. Pokud budete muset zadat adresář knihovny, který přepíše adresář standardní knihovny, můžete použít [/Libpath](../../build/reference/libpath-additional-libpath.md)) možnost příkazového řádku nebo vlastnost další knihovny adresáře na stránce vlastností Linkeru pro váš projekt.  
  
-   Při zadávání jednotlivých knihovnách v dialogovém okně stránky vlastností projektu, názvy knihoven musí být oddělené mezerami není čárkami.  
  
-   Cesta pro *filename* zasahuje do více než 260 znaků. Změňte názvy nebo změna uspořádání struktury adresářů v případě potřeby tak, aby zkrátil cesty k požadovaným souborům.  
  
-   Soubor je příliš velký. Knihovny nebo objekt soubory větší než gigabajt velikost může způsobit problémy pro 32-bit linkeru. Možné opravu tohoto problému je použití 64bitovou sadu nástrojů. Další informace o tom, jak to udělat na příkazovém řádku najdete v tématu [postupy: povolení 64bitová verze sady nástrojů Visual C++ v příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Informace o tom, jak to udělat v prostředí IDE najdete v tématu [pomocí nástroje MSBuild s na 64-bit kompilátoru a nástroje pro](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) a tento příspěvek Stack Overflow: [jak použít nativní amd64 nástrojů sady Visual Studio](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).  
  
-   Máte soubor dostatečná oprávnění pro přístup k *filename*. K tomu může dojít, pokud přístup k souborů knihovny do adresáře chráněného systému, nebo použijte soubory zkopírovali od jiných uživatelů, kteří mají oprávnění k nim původní nastavení. Chcete-li tento problém vyřešit, přesunete soubor do adresáře nelze zapisovat projektu. Pokud soubor v adresáři nelze zapisovat, ale má nepřístupný oprávnění, můžete použít příkazový řádek správce a spusťte příkaz takeown.exe převzít vlastnictví souboru.  
  
-   Nemáte dostatek místa na disku. Linkeru používá dočasné soubory v několika případech. I v případě, že máte dostatek místa na disku, můžete velmi velké odkaz vyčerpat by nebo fragmentu dostupné místo na disku. Zvažte použití [/OPT (optimalizace)](../../build/reference/opt-optimizations.md) možnost; to přenositelné sekvence comdat odstranění čtení všechny soubory objekt vícekrát.  
  
-   Pokud *filename* jmenuje LNK*n*, což je název souboru generované linkeru pro dočasného souboru, zadaný v proměnné prostředí TMP adresář neexistuje, nebo má více než jeden adresář je možné zadat proměnné prostředí TMP. Pro proměnnou prostředí TMP by měla být zadána cesta pouze jednomu adresáři.  
  
-   Pokud se zobrazí chybová zpráva pro název knihovny a nedávno přenést soubor .mak z předchozího vývoj systému Microsoft Visual C++, může knihovně již nebude platný. Zkontrolujte, zda je správný název knihovny a stále existuje v zadaném umístění, nebo aktualizovat LIB cestu k bodu do nového umístění.  
