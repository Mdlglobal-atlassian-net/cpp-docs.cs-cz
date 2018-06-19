---
title: Chyba linkerů Lnk1104 | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1104
dev_langs:
- C++
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2b832d4bceab88fbf3fbe8325a414669d11073c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302809"
---
# <a name="linker-tools-error-lnk1104"></a>Chyba linkerů LNK1104

> Nelze otevřít soubor "*filename*.

Linkeru nelze otevřít zadaný soubor. Nejběžnější příčiny tohoto problému se, že soubor je používán nebo uzamčen jiným procesem, neexistuje, nebyl nalezen v jednom adresáři propojovací prohledává nebo nemáte dostatečná oprávnění k přístupu k souboru. Ne tak často můžete mít dostatek místa na disku, soubor je pravděpodobně příliš velký nebo cesta k souboru může být příliš dlouhý.

## <a name="possible-causes-and-solutions"></a>Možné příčiny a řešení

Této chybě může dojít, když se pokusí otevřít soubor pro čtení nebo zápis linkeru. Můžete zúžit možné příčiny, nejprve zkontrolujte jaký typ souboru je a používat v následujících částech vám pomůžou identifikovat a vyřešit konkrétní problém.

### <a name="cannot-open-your-app-or-its-pdb-file"></a>Nelze otevřít aplikaci nebo soubor PDB

Pokud název souboru je spustitelný soubor sestavení projektu nebo soubor PDB přidružené Nejčastější příčinou je, že vaše aplikace běží již když zkusíte znovu sestavit nebo je načten do ladicí program. Chcete-li tento problém vyřešit, zastavte program a uvolnit z ladicího programu před vytvořením ho znovu. Pokud je aplikace otevřen v jiném programu, například editoru prostředků, zavřete ji. Ve výjimečných případech musíte pomocí Správce úloh ukončit proces, nebo zastavte a restartujte Visual Studio.

Antivirové programy často dočasně blokovat přístup k nově vytvořené soubory, zejména .exe a .dll spustitelné soubory. Chcete-li tento problém vyřešit, zkuste vyloučení adresáře sestavení projektu z antivirového programu.

### <a name="cannot-open-a-microsoft-library-file"></a>Nelze otevřít soubor Microsoft Library

Pokud je soubor, který nelze otevřít jeden ze souborů standardní knihovna od společnosti Microsoft, jako je například kernel32.lib, bude pravděpodobně k chybě konfigurace projektu nebo chybu instalace. Ověřte, zda byla nainstalována sada Windows SDK a pokud váš projekt vyžaduje další knihovny Microsoft, jako je například MFC, ujistěte se, že byly komponent knihovny MFC také nainstalovat pomocí instalačního programu sady Visual Studio. Když spustíte instalační program znovu a kdykoli přidat volitelné součásti. Další informace najdete v tématu [upravit Visual Studio](/visualstudio/install/modify-visual-studio). Na kartě jednotlivých součástí v instalačním programu zvolte konkrétní knihovny a sady SDK.

Pokud vytváříte projekt, který byl vytvořen pomocí starší verze sady Visual Studio, sada nástrojů platformy a knihovny pro tuto verzi se nenainstaluje. Pokud chybová zpráva se zobrazí na název verzí knihovny, například msvcr100.lib, příčinou je pravděpodobně příčinu. Chcete-li tento problém vyřešit, máte dvě možnosti: můžete upgradovat projekt, který používá aktuální sada nástrojů platformy instalaci, nebo můžete nainstalovat starší nástrojů a sestavte projekt beze změny. Další informace najdete v tématu [upgrade projektů z dřívějších verzí nástroje Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) a [pomocí nativní cílení na více v sadě Visual Studio staré projekty sestavení](../../porting/use-native-multi-targeting.md).

Pokud se zobrazí tato chyba, když vytvoříte novou cílovou platformu nebo konfiguraci, knihovny pro tento projekt konfigurace nebo platformu nástrojů se nenainstaluje. Ověřte, zda **sada nástrojů platformy** a **verze systému Windows SDK** zadaný v [stránku Obecné vlastnosti](../../ide/general-property-page-project.md) jsou nainstalovány pro svůj projekt a ověřte, že požadované knihovny jsou k dispozici v **adresáře knihovny** zadaný v [stránka vlastností adresářů VC ++](../../ide/vcpp-directories-property-page.md) pro nastavení konfigurace. Existují samostatné nastavení pro ladění a konfiguracích prodejní, jakož i 32bitové a 64bitové verze konfigurace, tak pokud jeden sestavení funguje, ale jiné způsobuje chybu, zajistěte, aby je nastavení správné a jsou nainstalovány požadované nástroje a knihovny pro každých konfigurace, které vytvoříte.

Pokud používáte Visual Studio IDE pro sestavení projektu, který jste zkopírovali z jiného počítače, může být jiný instalační umístění pro knihovny. Zkontrolujte **adresáře knihovny** vlastnost [stránka vlastností adresářů VC ++](../../ide/vcpp-directories-property-page.md) pro projekt a v případě potřeby ji aktualizujte. Chcete-li zobrazit a upravit aktuální cesty knihoven nastavení v IDE, zvolte pro ovládací prvek rozevírací seznam **adresáře knihovny** vlastnost a zvolte **upravit**. **Vyhodnotit hodnotu** části **adresáře knihovny** dialogové okno zobrazí aktuální cesty vyhledávat soubory knihovny.

Této chybě může dojít také při cestu k sadě Windows SDK je zastaralý. Pokud máte nainstalovanou verzi sady Windows SDK, která je novější než vaší verzí sady Visual Studio, ujistěte se, že v zadané cesty [stránka vlastností adresářů VC ++](../../ide/vcpp-directories-property-page.md) jsou aktualizovány tak, aby odpovídaly novou sadu SDK. Pokud pomocí příkazového řádku vývojáře, ujistěte se, že se aktualizuje dávkový soubor, který inicializuje objekt environment variables pro nové cesty SDK. Tento problém můžete zabránit pomocí instalačního programu sady Visual Studio k instalaci aktualizované sady SDK.

### <a name="cannot-open-a-third-party-library-file"></a>Nelze otevřít soubor knihovny třetích stran

Existuje několik běžných příčin tohoto problému:

- Cesta k souboru knihovny může být nesprávný nebo nemusí zadali jste ho linkeru.

- Můžete nainstalovat 32bitovou verzi knihovny, ale vytváříte pro 64bitovou nebo naopak.

- Knihovny může být závislá na jiné knihovny, které nejsou nainstalované.

Pro cestu problém vyřešit, ověřte, zda proměnná prostředí LIB nastavena a obsahuje všechny adresáře pro knihovny, které můžete použít pro všechny konfigurace, které vytvoříte. V prostředí IDE, proměnnou LIB nastavují **adresáře knihovny** vlastnost [stránka vlastností adresářů VC ++](../../ide/vcpp-directories-property-page.md). Zajistěte, aby všechny adresáře, které obsahují knihovny, které potřebujete jsou zde uvedeny, pro všechny konfigurace, které vytvoříte.

Pokud budete muset zadat adresář knihovny, který přepíše adresář standardní knihovny, můžete použít [/Libpath](../../build/reference/libpath-additional-libpath.md) možnost na příkazovém řádku nebo v prostředí IDE, můžete použít **další adresáře knihovny** Vlastnost **vlastnosti konfigurace > Linkeru > Obecné** stránku vlastností projektu.

Ujistěte se, že jste nainstalovali každou verzi knihovny, které potřebujete pro konfigurace, které vytvoříte. Zvažte použití [vcpkg](../../vcpkg.md) balíček správy nástroj pro automatizaci instalace a nastavení pro mnoho běžných knihoven. Pokud je to možné, doporučujeme vytvářet vlastní kopie knihovny třetích stran, proto se ujistěte, že máte místní závislosti, které vyžadují knihovny, a jsou vytvořeny pro stejné konfigurace jako projektu.

### <a name="cannot-open-a-file-built-by-your-project"></a>Nelze otevřít soubor vytvořené projektu

K této chybě může dojít v případě souboru *filename* je sestavena řešení, ale ještě neexistuje při linkeru pokusu o přístup. To může dojít v případě, že jeden projekt závisí na jiného projektu, ale nejsou projektů vytvořen ve správném pořadí. Chcete-li tento problém vyřešit, ujistěte se, odkazy projektu se nastavují v projekt, který používá soubor, takže chybí soubor vychází, než se požaduje. Další informace najdete v tématu [přidání odkazů v projektech Visual C++](../../ide/adding-references-in-visual-cpp-projects.md) a [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).

### <a name="cannot-open-file-cprogramobj"></a>Nelze otevřít soubor "C:\\Program.obj.

Pokud se zobrazí tato chyba nebo podobné chyby zahrnující soubor neočekávané .obj v kořenové složce jednotky, problém je skoro určitě cestě knihovny, která není uzavřen v uvozovkách.

Chcete-li vyřešit tento problém pro sestavení příkazového řádku, zkontrolujte [/Libpath](../../build/reference/libpath-additional-libpath.md) možnost parametry, určeném v proměnné prostředí LIB cesty a cesty zadat na příkazovém řádku a nezapomeňte použít uvozovky kolem žádné cesty který obsahovat mezery.

Chcete-li tento problém vyřešit v prostředí IDE, zkontrolujte **adresáře knihovny** vlastnost na [vlastnosti konfigurace > adresáře VC ++](../../ide/vcpp-directories-property-page.md) stránka vlastností **další adresáře knihovny** vlastnost v **vlastnosti konfigurace > Linkeru > Obecné** stránku vlastností a **Další závislosti** vlastnost **konfigurace Vlastnosti > Linkeru > vstup** stránku vlastností projektu. Zkontrolujte, zda jsou všechny cesty adresářů, které obsahují knihovny, které potřebujete uzavřen do dvojitých uvozovek, v případě potřeby.

### <a name="other-common-issues"></a>Další běžné problémy

Této chybě může dojít, pokud název souboru knihovny nebo cesta zadána linkeru na příkazovém řádku nebo v [#pragma komentář (lib, "library_name")](../../preprocessor/comment-c-cpp.md) – direktiva je nesprávný, nebo cesta obsahuje specifikace Jednotka není platná. Zkontrolujte pravopis a přípona souboru a ověřte, zda že soubor existuje v zadaném umístění.

Jiný program může mít soubor otevřít a linkeru nemohou do ní zapisovat. Antivirové programy často dočasně zablokovat přístup k souborům, nově vytvořený. Chcete-li tento problém vyřešit, zkuste vyloučení adresáře sestavení projektu z antivirového programu.

Pokud používáte možnost paralelní sestavení, je možné, že tento soubor na jiné vlákno uzamknul Visual Studio. Tento problém vyřešit, ověřte, že jste nevytvářejte stejný objekt kódu nebo knihovny ve více projektech, a použijte závislosti sestavení nebo odkazy na projekt a pokračovat tam integrovaný binární soubory v projektu.

Pokud zadáte v jednotlivých knihovnách **Další závislosti** vlastnost přímo, prostory jednotlivé názvy knihoven, není čárkami nebo středníkem. Pokud použijete **upravit** položku otevřete **Další závislosti** dialogové okno, použijte vložení znaků newline oddělte názvy čárkami není, středníky nebo mezery. Vložení znaků newline použít také při zadání cesty knihoven v **adresáře knihovny** a **další adresáře knihovny** dialogová okna.

Tato chyba se může zobrazit při cesta pro *filename* zasahuje do více než 260 znaků. Změňte názvy nebo změna uspořádání struktury adresářů v případě potřeby tak, aby zkrátil cesty k požadovaným souborům.

Této chybě může dojít, protože soubor je příliš velký. Knihovny nebo objekt soubory větší než gigabajt velikost může způsobit problémy pro 32-bit linkeru. Možné opravu tohoto problému je použití 64bitovou sadu nástrojů. Další informace o tom, jak to udělat na příkazovém řádku najdete v tématu [postupy: povolení 64bitová verze sady nástrojů Visual C++ v příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Informace o tom, jak to udělat v prostředí IDE najdete v tématu [pomocí nástroje MSBuild s na 64-bit kompilátoru a nástroje pro](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) a tento příspěvek Stack Overflow: [jak použít nativní amd64 nástrojů sady Visual Studio](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

Této chybě může dojít, pokud máte dostatek soubor oprávnění pro přístup k *filename*. K tomu může dojít, pokud použijte běžný uživatelský účet a pokus o přístup k souborů knihovny do adresáře chráněného systému, nebo použijte soubory zkopírovali od jiných uživatelů, kteří mají oprávnění k nim původní nastavení. Chcete-li tento problém vyřešit, přesunete soubor do adresáře nelze zapisovat projektu. Pokud soubor v adresáři nelze zapisovat, ale má nepřístupný oprávnění, můžete použít příkazový řádek správce a spusťte příkaz takeown.exe převzít vlastnictví souboru.

Chybě může dojít, pokud nemáte dostatek místa na disku. Linkeru používá dočasné soubory v několika případech. I v případě, že máte dostatek místa na disku, můžete velmi velké odkaz vyčerpat by nebo fragmentu dostupné místo na disku. Zvažte použití [/OPT (optimalizace)](../../build/reference/opt-optimizations.md) možnost; to přenositelné čtení odstranění sekvence COMDAT všechny soubory objekt vícekrát.

Pokud *filename* jmenuje LNK*nnn*, což je název souboru generované linkeru pro dočasného souboru, adresáři určeném v proměnné prostředí TMP neexistuje, nebo může být více než jeden adresář zadat proměnné prostředí TMP. Pro proměnnou prostředí TMP by měla být zadána cesta pouze jednomu adresáři.
