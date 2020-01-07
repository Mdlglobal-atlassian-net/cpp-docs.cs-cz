---
title: Chyba linkerů LNK1104
description: Popisuje chybu linkeru Microsoft C++ C a (MSVC) linker linkerů LNK1104, její příčiny a možná řešení.
ms.date: 12/13/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: 8878db1b0829703b22b2f7863eb7955d17ad3096
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301779"
---
# <a name="linker-tools-error-lnk1104"></a>Chyba linkerů LNK1104

> nejde otevřít soubor*filename*.

Tato chyba je hlášena v případě, že linker nemůže otevřít soubor, a to buď pro čtení, nebo pro zápis. Mezi nejběžnější příčiny problému patří:

- Váš program je již spuštěn nebo je načten v ladicím programu a

- Vaše cesty ke knihovně nejsou správné, nebo nejsou zabaleny do dvojitých uvozovek.

Tato chyba má mnoho dalších možných příčin. Abyste je mohli zúžit, nejdřív zkontrolujte, jaký druh souboru *filename* je. Pak použijte následující části, které vám pomůžou identifikovat a opravit konkrétní problém.

## <a name="cant-open-your-app-or-its-pdb-file"></a>Nedá se otevřít aplikace nebo její soubor. pdb.

### <a name="your-app-is-running-or-its-loaded-in-the-debugger"></a>Vaše aplikace je spuštěná nebo je načtená v ladicím programu.

Pokud je název *souboru* spustitelný soubor nebo přidružený soubor. pdb, zkontrolujte, zda je aplikace již spuštěna. Potom zkontrolujte, zda je načtena v ladicím programu. Chcete-li tento problém vyřešit, zastavte program a uvolněte ho z ladicího programu ještě před tím, než ho znovu sestavíte. Pokud je aplikace otevřená v jiném programu, jako je třeba editor prostředků, zavřete ji. Pokud program nereaguje, může být nutné použít Správce úloh k ukončení procesu. Může být také nutné zavřít a restartovat aplikaci Visual Studio.

### <a name="your-app-is-locked-by-an-antivirus-scan"></a>Vaše aplikace je uzamčená antivirovou kontrolou.

Antivirové programy často dočasně blokují přístup k nově vytvořeným souborům, zejména ke spustitelným souborům exe a. dll. Chcete-li tento problém vyřešit, zkuste vyloučit adresáře pro sestavení projektu z antivirového programu.

## <a name="cant-open-a-microsoft-library-file"></a>Nelze otevřít soubor knihovny Microsoft.

### <a name="windows-libraries-such-as-kernel32lib"></a>Knihovny Windows, například Kernel32. lib

Pokud soubor, který nelze otevřít, je jedním ze standardních souborů knihovny poskytovaných společností Microsoft, například *Kernel32. lib*, může dojít k chybě konfigurace projektu nebo k chybě instalace. Ověřte, že je nainstalovaná Windows SDK. Pokud váš projekt vyžaduje jiné knihovny Microsoftu, jako je například MFC, ujistěte se, že komponenty knihovny MFC byly nainstalovány také instalačním programem sady Visual Studio. Instalační program můžete spustit znovu a kdykoli přidat volitelné součásti. Další informace najdete v tématu [Změna sady Visual Studio](/visualstudio/install/modify-visual-studio). Pomocí karty **jednotlivé komponenty** v instalačním programu vyberte konkrétní knihovny a sady SDK.

### <a name="versioned-vcruntime-libraries"></a>Vcruntime knihovny se správou verzí

Pokud chybová zpráva obsahuje verzi knihovny Microsoftu, jako je *msvcr120. lib*, sada nástrojů platformy pro tuto verzi kompilátoru možná není nainstalovaná. Chcete-li tento problém vyřešit, máte dvě možnosti: Upgradujte projekt tak, aby používal aktuální sadu nástrojů platformy, nebo nainstalujte starší sadu nástrojů a sestavte projekt beze změny. Další informace naleznete v tématu [upgrade projektů z dřívějších verzí vizuálu C++ ](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) a [použití nativního cílení na více verzí v aplikaci Visual Studio k sestavení starých projektů](../../porting/use-native-multi-targeting.md).

### <a name="retail-debug-or-platform-specific-libraries"></a>Knihovny pro maloobchodní prodej, ladění nebo konkrétní platformu

K této chybě může dojít při prvním sestavení pro novou cílovou platformu nebo konfiguraci, jako je například Retail nebo ARM64. V rozhraní IDE ověřte, zda je nainstalována **Sada nástrojů platformy** a **verze Windows SDK** zadaná na [stránce vlastností Obecné](../../build/reference/general-property-page-project.md) . Ověřte také, že požadované knihovny jsou k dispozici v **adresářích knihoven** zadaných na [stránce vlastností adresáře VC + +](../../build/reference/vcpp-directories-property-page.md). Ověřte vlastnosti každé konfigurace, jako je například ladění, maloobchod, x86 nebo ARM64. Pokud jedno sestavení funguje, ale ještě jiné, porovnejte nastavení pro obojí. Nainstalujte všechny chybějící požadované nástroje a knihovny.

### <a name="the-vccorliblib-library"></a>Knihovna vccorlib. lib

Pro aplikace nebo komponenty Universal Windows (UWP) nejsou k dispozici žádné Spectre knihovny. Pokud chybová zpráva zahrnuje *vccorlib. lib*, možná jste povolili [/QSPECTRE](../../build/reference/qspectre.md) v projektu UWP. Pokud chcete tento problém vyřešit, zakažte možnost kompilátoru **/Qspectre** . V aplikaci Visual Studio změňte vlastnost **zmírnění rizika Spectre** . Nachází se na stránce **generování kódu** **jazykaC++ C/**  > dialogového okna **stránky vlastností** projektu.

### <a name="libraries-in-projects-from-online-or-other-sources"></a>Knihovny v projektech z online nebo jiných zdrojů

Pokud sestavíte projekt zkopírovaný z jiného počítače, umístění instalace knihovny se mohou lišit. Pro sestavení příkazového řádku ověřte, zda je proměnná prostředí LIB a cesty ke knihovně nastavena správně pro sestavení. V sadě Visual Studio můžete zobrazit a upravit aktuální cesty knihoven nastavené na stránkách vlastností projektu. Na stránce **adresáře VC + +** vyberte rozevírací seznam pro vlastnost **adresáře knihovny** a pak zvolte možnost **Upravit**. Oddíl **vyhodnocená hodnota** v dialogovém okně **adresáře knihoven** obsahuje seznam aktuálních cest prohledávaných pro soubory knihovny. Aktualizujte tyto cesty tak, aby odkazovaly na místní knihovny.

### <a name="updated-windows-sdk-libraries"></a>Aktualizované knihovny Windows SDK

K této chybě může dojít, pokud je cesta sady Visual Studio k Windows SDK zastaralá. K tomu může dojít, pokud nainstalujete novější Windows SDK nezávisle na instalačním programu sady Visual Studio. Pokud ho chcete opravit v integrovaném vývojovém prostředí, aktualizujte cesty zadané na [stránce vlastností adresáře VC + +](../../build/reference/vcpp-directories-property-page.md). Nastavte verzi v cestě tak, aby odpovídala nové sadě SDK. Pokud použijete Developer Command Prompt, aktualizujte dávkový soubor, který inicializuje proměnné prostředí s použitím nových cest k sadě SDK. K tomuto problému se můžete vyhnout pomocí instalačního programu sady Visual Studio k instalaci aktualizovaných sad SDK.

## <a name="cant-open-a-third-party-library-file"></a>Soubor knihovny třetí strany se nedá otevřít.

Tento problém má několik běžných příčin:

- Cesta k souboru knihovny je pravděpodobně nesprávná nebo není zabalena do dvojitých uvozovek. Nebo je možné, že jste ho neurčili linkeru.

- Je možné, že máte nainstalovanou 32ovou verzi knihovny, ale sestavíte ji na 64 bitů nebo na jiný způsob.

- Knihovna může mít závislosti na jiných knihovnách, které nejsou nainstalovány.

Chcete-li opravit problém s cestou pro sestavení příkazového řádku, ověřte, zda je nastavena proměnná prostředí LIB. Ujistěte se, že obsahuje cesty pro všechny knihovny, které používáte, a pro každou konfiguraci, kterou sestavíte. V integrovaném vývojovém prostředí se cesty ke knihovnám nastavují pomocí **adresářů VC + +**  > **složky knihovny** . Ujistěte se, že jsou tady uvedené všechny adresáře obsahující knihovny, které potřebujete, a to pro každou konfiguraci, kterou sestavíte.

Je možné, že budete muset dodat adresář knihovny, který přepíše standardní adresář knihovny. Na příkazovém řádku použijte možnost [/LIBPATH](../../build/reference/libpath-additional-libpath.md) . V integrovaném vývojovém prostředí použijte vlastnost **Další adresáře knihovny** ve **vlastnostech konfigurace > stránce vlastností Obecné > linkeru** pro váš projekt.

Ujistěte se, že jste nainstalovali všechny verze knihovny, které potřebujete pro vámi sestavené konfigurace. Zvažte použití nástroje pro správu balíčků [vcpkg](../../vcpkg.md) k automatizaci instalace a nastavení pro mnoho běžných knihoven. Když můžete, je nejlepší vytvořit vlastní kopie knihoven třetích stran. Pak jste si jisti, že všechny místní závislosti knihoven jsou sestavené pro stejné konfigurace jako váš projekt.

## <a name="cant-open-a-file-built-by-your-project"></a>Nejde otevřít soubor sestavený vaším projektem.

Tato chyba se může zobrazit, pokud *název souboru* ještě neexistuje, když se linker pokusí o přístup. K tomu může dojít, když jeden projekt závisí na jiném v řešení, ale projekty se sestavují v nesprávném pořadí. Chcete-li tento problém vyřešit, zajistěte, aby byly v projektu, který používá soubor, nastaveny odkazy na projekt. Pak se chybějící soubor sestaví ještě předtím, než se bude vyžadovat. Další informace naleznete v tématu [Přidání odkazů v projektech sady C++ Visual Studio](../../build/adding-references-in-visual-cpp-projects.md) a [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).

## <a name="cannot-open-file-cprogramobj"></a>Nejde otevřít soubor C:\\program. obj.

Pokud se v chybové zprávě zobrazí název souboru *C:\\program. obj* , zabalte cesty knihovny do dvojitých uvozovek. K této chybě dochází, je-li do linkeru předána nezabalená cesta začínající řetězcem *C:\\Program Files* . Nezabalené cesty můžou způsobovat i podobné chyby. Obvykle zobrazují neočekávaný soubor. obj v kořenovém adresáři disku.

Chcete-li tento problém vyřešit pro sestavení příkazového řádku, podívejte se na parametry možnosti [/LIBPATH](../../build/reference/libpath-additional-libpath.md) . Také ověřte cesty zadané v proměnné prostředí LIB a cesty zadané v příkazovém řádku. Nezapomeňte použít dvojité uvozovky kolem všech cest, které obsahují mezery.

Chcete-li tento problém vyřešit v integrovaném vývojovém prostředí, přidejte dvojité uvozovky podle potřeby do následujících vlastností projektu:

- Vlastnost **adresáře knihovny** na stránce [vlastností konfigurace > adresářů VC + +](../../build/reference/vcpp-directories-property-page.md) ,

- Vlastnost **Další adresáře knihovny** ve **vlastnostech konfigurace > stránce vlastností Obecné > linkeru** ,

- Vlastnost **Další závislosti** ve **vlastnostech konfigurace > stránce vlastností linker > Input** .

## <a name="other-common-issues"></a>Další běžné problémy

### <a name="path-or-filename-issues"></a>Problémy s cestou nebo názvem souboru

K této chybě může dojít, pokud je název souboru nebo cesta k linkeru zadán nesprávně. Nebo, pokud má cesta neplatnou specifikaci jednotky. Vyhledejte problémy v příkazovém řádku nebo ve všech direktivách [#pragma Comment (LIB, "library_name")](../../preprocessor/comment-c-cpp.md) . Zkontrolujte správnost a příponu souboru a ověřte, zda soubor existuje v zadaném umístění.

### <a name="parallel-build-synchronization"></a>Synchronizace paralelních sestavení

Pokud používáte možnost paralelního sestavení, může Visual Studio uzamknout soubor v jiném vlákně. Chcete-li tento problém vyřešit, ověřte, zda stejný objekt kódu nebo knihovna není sestavena v několika projektech. Pomocí závislostí sestavení nebo odkazů na projekt můžete ze svého projektu vybrat sestavené binární soubory.

### <a name="additional-dependencies-specified-in-the-ide"></a>Další závislosti zadané v integrovaném vývojovém prostředí

Když zadáte jednotlivé knihovny do vlastnosti **Další závislosti** přímo, použijte mezery k oddělení názvů knihoven. Nepoužívejte čárky ani středníky. Použijete-li položku nabídky **Upravit** k otevření dialogového okna **Další závislosti** , oddělte názvy čárkami, středníkem nebo mezerami pomocí newlines. Při zadání cest knihovny v **adresářích knihovny** a v dialogových oknech **Další adresáře knihoven** použijte také newlines.

### <a name="paths-that-are-too-long"></a>Příliš dlouhé cesty

Tato chyba se může zobrazit, pokud se cesta k *názvu souboru* rozbalí na více než 260 znaků. V případě potřeby přeuspořádejte svou adresářovou strukturu nebo Zkraťte název složky a souboru, aby se zkrátily cesty.

### <a name="files-that-are-too-large"></a>Soubory, které jsou příliš velké

K této chybě může dojít, protože soubor je příliš velký. Knihovny nebo soubory objektů větší než gigabajt v velikosti mohou způsobovat problémy pro 32 linker. Možnou příčinou opravy tohoto problému je použití sady nástrojů 64-bit. Další informace o tom, jak použít 64-bitovou sadu nástrojů v příkazovém řádku, naleznete v tématu [How to: Enable a 64- C++ bit Visual sada nástrojů na příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Informace o tom, jak používat 64-bitovou sadu nástrojů v rozhraní IDE, najdete v tématu [použití nástroje MSBuild s 64 kompilátorem a nástroji](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project). Viz také tento Stack Overflow příspěvek: [Jak používat Visual Studio Native amd64 sada nástrojů](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

### <a name="incorrect-file-permissions"></a>Nesprávná oprávnění souboru

K této chybě může dojít, pokud nemáte dostatečná oprávnění pro přístup k *názvu*souboru. K tomu může dojít, pokud použijete běžný uživatelský účet pro přístup k souborům knihoven v chráněných systémových adresářích. Nebo, pokud používáte soubory zkopírované z jiných uživatelů, kteří mají stále nastavená původní oprávnění. Chcete-li tento problém vyřešit, přesuňte soubor do zapisovatelného adresáře projektu. Pokud má přesunutý soubor oprávnění k dispozici, spusťte příkaz takeown. exe v okně příkazového řádku správce a převezměte vlastnictví souboru.

### <a name="insufficient-disk-space"></a>Nedostatek místa na disku

K této chybě může dojít, pokud nemáte dostatek místa na disku. Linker používá dočasné soubory v několika případech. I v případě, že máte dostatek místa na disku, může velký odkaz vyčerpat nebo fragmentovat dostupné místo na disku. Zvažte použití možnosti [/opt (optimalizace)](../../build/reference/opt-optimizations.md) ; přenositelný COMDAT eliminuje čtení všech souborů objektů několikrát.

### <a name="problems-in-the-tmp-environment-variable"></a>Problémy v proměnné prostředí TMP

Pokud *název souboru* má název LNK*NNN*, jedná se o název souboru vygenerovaný linkerem pro dočasný soubor. Adresář zadaný v proměnné prostředí TMP možná neexistuje. Nebo lze pro proměnnou prostředí TMP zadat více než jeden adresář. Pro proměnnou prostředí TMP by měla být zadána pouze jedna cesta k adresáři.

## <a name="help-my-issue-isnt-listed-here"></a>V této nápovědě se tady problém neuvádí.

Pokud zde není žádný z uvedených problémů, můžete použít nástroje pro zpětnou vazbu v aplikaci Visual Studio pro nápovědu. V integrovaném vývojovém prostředí přejděte do řádku nabídek a vyberte možnost **Help > Odeslat názor > nahlásit problém**. Případně můžete odeslat návrh pomocí **> pomoci Odeslat názor > Odeslat návrh**. Můžete také použít web Visual Studio C++ [Developer Community](https://developercommunity.visualstudio.com/spaces/62/index.html)). Použijte ho k hledání odpovědí na otázky a požádejte o pomoc. Další informace najdete v tématu [postup nahlášení problému s vizuální C++ sadou nástrojů nebo dokumentací](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Pokud jste zjistili nový způsob, jak tento problém vyřešit, měli bychom do tohoto článku přidat. Dejte nám prosím jistotu. Můžete nám poslat zpětnou vazbu pomocí tlačítka níže pro **tuto stránku**. Použijte ho k vytvoření nového problému v [ C++ dokumentaci k GitHubu v dokumentaci](https://github.com/MicrosoftDocs/cpp-docs/issues). Děkujeme.
