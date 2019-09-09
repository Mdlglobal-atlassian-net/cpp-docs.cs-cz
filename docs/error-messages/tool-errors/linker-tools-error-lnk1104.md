---
title: Chyba linkerů LNK1104
ms.date: 09/06/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: f3effd9054954a90f69c5b18d8f099e6d705d9a3
ms.sourcegitcommit: 7babce70714242cf498ca811eec3695fad3abd03
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808847"
---
# <a name="linker-tools-error-lnk1104"></a>Chyba linkerů LNK1104

> nejde otevřít soubor*filename*.

Linker nemůže otevřít zadaný soubor. Nejběžnějšími příčinami tohoto problému je, že se soubor používá nebo je uzamčen jiným procesem. Je také možné, že soubor neexistuje nebo nebyl nalezen v jednom adresáři, který hledá linker. Nebo je možné, že nemáte dostatečná oprávnění pro přístup k souboru. Méně často možná dochází místo na disku, soubor může být moc velký nebo cesta k souboru je možná moc dlouhá.

## <a name="possible-causes-and-solutions"></a>Možné příčiny a řešení

K této chybě může dojít, když se linker pokusí otevřít soubor pro čtení nebo pro zápis. Chcete-li zúžit možné příčiny, nejprve zkontrolujte, jaký typ souboru je. Pak použijte následující části, které vám pomůžou identifikovat a opravit konkrétní problém.

### <a name="cant-open-your-app-or-its-pdb-file"></a>Nedá se otevřít aplikace nebo její soubor. pdb.

Pokud název souboru je spustitelný soubor, který je sestavením projektu, nebo přidružený soubor. pdb, Nejběžnější příčinou je, že aplikace je již spuštěna, když se pokusíte ji znovu sestavit nebo když je načtena v ladicím programu. Chcete-li tento problém vyřešit, zastavte program a uvolněte ho z ladicího programu ještě před tím, než ho znovu sestavíte. Pokud je aplikace otevřená v jiném programu, jako je třeba editor prostředků, zavřete ji. V extrémních případech může být nutné použít Správce úloh k ukončení procesu nebo zastavení a restartování sady Visual Studio.

Antivirové programy často dočasně blokují přístup k nově vytvořeným souborům, zejména ke spustitelným souborům exe a. dll. Chcete-li tento problém vyřešit, zkuste vyloučit adresáře pro sestavení projektu z antivirového programu.

### <a name="cant-open-a-microsoft-library-file"></a>Nelze otevřít soubor knihovny Microsoft.

Pokud soubor, který nelze otevřít, je jedním ze standardních souborů knihovny poskytovaných společností Microsoft, například Kernel32. lib, může dojít k chybě konfigurace projektu nebo k chybě instalace. Ověřte, zda byl nainstalován Windows SDK a pokud váš projekt vyžaduje jiné knihovny Microsoftu, jako je například MFC, ujistěte se, že komponenty knihovny MFC byly nainstalovány také instalačním programem sady Visual Studio. Instalační program můžete spustit znovu a kdykoli přidat volitelné součásti. Další informace najdete v tématu [Změna sady Visual Studio](/visualstudio/install/modify-visual-studio). Pomocí karty jednotlivé komponenty v instalačním programu vyberte konkrétní knihovny a sady SDK.

Pro aplikace nebo komponenty Universal Windows (UWP) nejsou k dispozici žádné Spectre knihovny. Pokud zpráva o chybách zmiňuje soubor *vccorlib. lib* , možná jste povolili [/QSPECTRE](../../build/reference/qspectre.md) v projektu UWP. Pokud chcete tento problém vyřešit, zakažte možnost kompilátoru **/Qspectre** . V aplikaci Visual Studio změňte vlastnost **zmírnění rizika Spectre** , která se nachází na **stránce proC++** **generování kódu** v > dialogovém okně **stránky vlastností** projektu.

Pokud vytváříte projekt, který byl vytvořen pomocí starší verze sady Visual Studio, sada nástrojů platformy a knihovny pro tuto verzi pravděpodobně nebudou nainstalovány. Pokud se zobrazí chybová zpráva pro název knihovny s verzí, jako je například msvcr100. lib, může to být způsobeno. Chcete-li tento problém vyřešit, máte dvě možnosti: můžete upgradovat projekt tak, aby používal aktuální sadu nástrojů platformy, kterou jste nainstalovali, nebo můžete nainstalovat starší sadu nástrojů a sestavit projekt beze změny. Další informace naleznete v tématu [upgrade projektů z dřívějších verzí vizuálu C++ ](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) a [použití nativního cílení na více verzí v aplikaci Visual Studio k sestavení starých projektů](../../porting/use-native-multi-targeting.md).

Pokud se tato chyba zobrazí při sestavování pro novou cílovou platformu nebo konfiguraci, nemusíte mít nainstalované knihovny pro tuto konfiguraci projektu nebo sadu nástrojů platformy. Ověřte, zda je nainstalována **Sada nástrojů platformy** a **verze Windows SDK** na [stránce vlastností Obecné](../../build/reference/general-property-page-project.md) pro váš projekt, a ověřte, zda jsou požadované knihovny k dispozici v **adresářích knihoven** určených v [Stránka vlastností adresářů VC + +](../../build/reference/vcpp-directories-property-page.md) pro nastavení konfigurace. Existují samostatná nastavení pro ladění a maloobchodní konfiguraci a také 32 a 64 konfigurace, takže pokud jedno sestavení funguje, ale jiná chyba způsobí chybu, ujistěte se, že je nastavení správné a že jsou nainstalované požadované nástroje a knihovny pro každé konfigurace, kterou sestavíte.

Pokud používáte Visual Studio IDE k sestavení projektu, který byl zkopírován z jiného počítače, instalační umístění pro knihovny se mohou lišit. Na [stránce vlastností adresářů VC + +](../../build/reference/vcpp-directories-property-page.md) pro projekt ověřte vlastnost **adresáře knihovny** a v případě potřeby ho aktualizujte. Chcete-li zobrazit a upravit aktuální cesty knihoven nastavené v integrovaném vývojovém prostředí, vyberte rozevírací seznam pro vlastnost **adresáře knihovny** a klikněte na tlačítko **Upravit**. Oddíl **vyhodnocená hodnota** v dialogovém okně **adresáře knihoven** obsahuje seznam aktuálních cest prohledávaných pro soubory knihovny.

K této chybě může dojít také v případě, že cesta k Windows SDK je zastaralá. Pokud jste nainstalovali verzi Windows SDK, která je novější než vaše verze sady Visual Studio, ujistěte se, že cesty zadané na [stránce vlastností adresáře VC + +](../../build/reference/vcpp-directories-property-page.md) jsou aktualizovány tak, aby odpovídaly nové sadě SDK. Pokud používáte Developer Command Prompt, ujistěte se, že dávkový soubor, který inicializuje proměnné prostředí, je aktualizovaný pro nové cesty sady SDK. K tomuto problému se můžete vyhnout pomocí instalačního programu sady Visual Studio k instalaci aktualizovaných sad SDK.

### <a name="cannot-open-a-third-party-library-file"></a>Soubor knihovny třetí strany se nedá otevřít.

Tento problém má několik běžných příčin:

- Cesta k souboru knihovny je pravděpodobně nesprávná nebo jste ji pravděpodobně neurčili pro linker.

- Je možné, že máte nainstalovanou 32ovou verzi knihovny, ale sestavíte ji na 64-bitů nebo naopak.

- Knihovna může mít závislosti na jiných knihovnách, které nejsou nainstalovány.

Chcete-li opravit problém s cestou, ověřte, zda je nastavena proměnná prostředí LIB a zda obsahuje všechny adresáře pro knihovny, které používáte, pro každou konfiguraci, kterou sestavíte. V integrovaném vývojovém prostředí je proměnná LIB nastavena vlastností **adresáře knihovny** na [stránce vlastností adresáře VC + +](../../build/reference/vcpp-directories-property-page.md). Ujistěte se, že jsou tady uvedené všechny adresáře obsahující knihovny, které potřebujete, a to pro každou konfiguraci, kterou sestavíte.

Pokud potřebujete zadat adresář knihovny, který Přepisuje standardní adresář knihovny, můžete použít možnost [/LIBPATH](../../build/reference/libpath-additional-libpath.md) na příkazovém řádku nebo v integrovaném vývojovém prostředí (IDE), můžete použít vlastnost **Další adresáře knihovny** ve **vlastnostech konfigurace. > Linker > Obecná** stránka vlastností projektu.

Ujistěte se, že máte nainstalovanou každou verzi knihovny, kterou potřebujete pro vámi sestavené konfigurace. Zvažte použití nástroje pro správu balíčků [vcpkg](../../vcpkg.md) k automatizaci instalace a nastavení pro mnoho běžných knihoven. Když můžete, je nejlepší vytvořit vlastní kopie knihoven třetích stran, abyste měli jistotu, že budete mít všechny místní závislosti, které knihovny vyžadují, a jsou sestavené pro stejné konfigurace jako váš projekt.

### <a name="cannot-open-a-file-built-by-your-project"></a>Nejde otevřít soubor sestavený vaším projektem.

Tato chyba se může zobrazit, pokud soubor *filename* je sestavený vaším řešením, ale ještě neexistuje, když se linker pokusí k němu přistoupit. K tomu může dojít, když jeden projekt závisí na jiném projektu, ale projekty nejsou sestaveny ve správném pořadí. Chcete-li tento problém vyřešit, zajistěte, aby byly odkazy na projekt nastaveny v projektu, který používá soubor, aby byl chybějící soubor vytvořen před jeho požadováním. Další informace naleznete v tématu [Přidání odkazů v projektech sady C++ Visual Studio](../../build/adding-references-in-visual-cpp-projects.md) a [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).

### <a name="cannot-open-file-cprogramobj"></a>Nejde otevřít soubor C:\\program. obj.

Pokud se zobrazí tato chyba nebo podobná chyba, která se týká neočekávaného souboru. obj v kořenovém adresáři jednotky, je problém téměř určitě cesta knihovny, která není zabalena do dvojitých uvozovek.

Chcete-li tento problém vyřešit pro sestavení příkazového řádku, zaškrtněte parametry možnosti [/LIBPATH](../../build/reference/libpath-additional-libpath.md) , cesty zadané v proměnné prostředí LIB a cesty zadané v příkazovém řádku a nezapomeňte použít dvojité uvozovky kolem všech cest, které obsahují mezery.

Chcete-li tento problém vyřešit v integrovaném vývojovém prostředí, ověřte vlastnost **adresáře knihovny** na stránce vlastností [Konfigurace > adresář VC + +](../../build/reference/vcpp-directories-property-page.md) , vlastnost **Další adresáře knihovny** ve **vlastnostech konfigurace > linkeru > Obecná** stránka vlastností a vlastnost **Další závislosti** v části **vlastnosti konfigurace > linker > vstupní** vlastnosti pro váš projekt. Ujistěte se, že všechny cesty k adresářům, které obsahují knihovny, které potřebujete, jsou v případě potřeby zabaleny do dvojitých uvozovek.

### <a name="other-common-issues"></a>Další běžné problémy

K této chybě může dojít, pokud je název souboru nebo cesta ke knihovně zadané linkeru na příkazovém řádku nebo v direktivě [#pragma Comment (LIB, "library_name)](../../preprocessor/comment-c-cpp.md) " nesprávný "nebo má cesta neplatnou specifikaci jednotky. Zkontrolujte správnost a příponu souboru a ověřte, zda soubor existuje v zadaném umístění.

Soubor může mít otevřený jiný program a linker do něj nemůže zapisovat. Antivirové programy často dočasně zablokují přístup k nově vytvořeným souborům. Chcete-li tento problém vyřešit, zkuste vyloučit adresáře pro sestavení projektu z antivirového programu.

Používáte-li možnost paralelního sestavení, je možné, že aplikace Visual Studio uzamkl soubor v jiném vlákně. Chcete-li tento problém vyřešit, ověřte, zda sestavíte stejný objekt kódu nebo knihovnu ve více projektech a zda používáte závislosti sestavení nebo odkazy na projekt pro výběr sestavených binárních souborů v projektu.

Když zadáte jednotlivé knihovny do vlastnosti **Další závislosti** přímo, použijte mezery k oddělení názvů knihoven, nikoli čárek nebo středníků. Použijete-li položku nabídky **Upravit** k otevření dialogového okna **Další závislosti** , oddělte názvy čárkami, středníkem nebo mezerami pomocí newlines. Při zadání cest knihovny v **adresářích knihovny** a v dialogových oknech **Další adresáře knihoven** použijte také newlines.

Tato chyba se může zobrazit, pokud se cesta k *názvu souboru* rozbalí na více než 260 znaků. Pokud potřebujete zkrátit cesty k požadovaným souborům, změňte názvy nebo změňte uspořádání adresářové struktury.

K této chybě může dojít, protože soubor je příliš velký. Knihovny nebo soubory objektů větší než gigabajt v velikosti mohou způsobovat problémy pro 32 linker. Možnou příčinou opravy tohoto problému je použití sady nástrojů 64-bit. Další informace o tom, jak to provést na příkazovém řádku, najdete v [tématu How to: Povolte 64 vizuální C++ sadu nástrojů na příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Informace o tom, jak to provést v integrovaném vývojovém prostředí, najdete v tématu [použití nástroje MSBuild s 64 kompilátorem a nástroji](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) a tohoto Stack Overflow příspěvku: [Jak používat Visual Studio nativní amd64 sada nástrojů](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

K této chybě může dojít, pokud nemáte dostatečná oprávnění pro přístup k *názvu*souboru. K tomu může dojít, pokud použijete běžný uživatelský účet a pokusíte se o přístup k souborům knihoven v chráněných systémových adresářích nebo použijete soubory zkopírované z jiných uživatelů, kteří mají nastavená původní oprávnění. Chcete-li tento problém vyřešit, přesuňte soubor do zapisovatelného adresáře projektu. Pokud je soubor v zapisovatelném adresáři, ale má nepřístupná oprávnění, můžete k převzetí vlastnictví souboru použít příkazový řádek správce a spustit příkaz takeown. exe.

K této chybě může dojít, pokud nemáte dostatek místa na disku. Linker používá dočasné soubory v několika případech. I v případě, že máte dostatek místa na disku, může velmi velký odkaz vyčerpat nebo fragmentovat dostupné místo na disku. Zvažte použití možnosti [/opt (optimalizace)](../../build/reference/opt-optimizations.md) ; přenositelný COMDAT eliminuje čtení všech souborů objektů několikrát.

Pokud *název souboru* má název LNK*NNN*, což je název souboru generovaný linkerem pro dočasný soubor, adresář zadaný v proměnné prostředí TMP možná neexistuje nebo pro proměnnou prostředí TMP se dá zadat víc než jeden adresář. Pro proměnnou prostředí TMP by měla být zadána pouze jedna cesta k adresáři.
