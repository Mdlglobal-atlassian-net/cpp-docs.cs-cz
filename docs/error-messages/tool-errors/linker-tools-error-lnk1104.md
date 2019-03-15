---
title: Chyba linkerů LNK1104
ms.date: 05/17/2017
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: eadeeb7ac19e3975a37a1364502b33400018cb05
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818268"
---
# <a name="linker-tools-error-lnk1104"></a>Chyba linkerů LNK1104

> Nelze otevřít soubor "*filename*.

Zadaný soubor nelze otevřít, linker. Nejběžnější příčiny tohoto problému je, že soubor je používán nebo uzamčen jiným procesem, neexistuje, nelze nalézt v jednom z adresářů propojovací program vyhledá nebo nemáte dostatečná oprávnění pro přístup k souboru. Ne tak často můžete pravděpodobně vyčerpala volné místo na disku, soubor je pravděpodobně příliš velký nebo cesta k souboru může být příliš dlouhý.

## <a name="possible-causes-and-solutions"></a>Možné příčiny a řešení

Této chybě může dojít, pokud linker se pokusí otevřít soubor pro čtení nebo pro zápis. Abyste omezili možné příčiny, nejprve zkontrolujte druh souboru je a pomocí následujících částí pomáhají identifikovat a vyřešit konkrétní problém.

### <a name="cannot-open-your-app-or-its-pdb-file"></a>Nelze otevřít vaše aplikace nebo její soubor .pdb

Pokud název souboru je spustitelný soubor váš projekt se sestaví nebo přidružený soubor typu .pdb, Nejběžnější příčinou je, že aplikace je již spuštěna při pokusu o její opětovné sestavení, nebo je načten do ladicího programu. Chcete tento problém vyřešit, ukončete program a uvolnit z ladicí program před sestavení znovu. Pokud aplikace je otevřen v jiném programu, jako je například editor prostředků, zavřete ho. V extrémních případech budete muset pomocí Správce úloh ukončit proces, nebo zastavte a restartujte aplikaci Visual Studio.

Antivirové programy často dočasně blokovat přístup k nově vytvořené soubory, zejména .exe a .dll spustitelné soubory. Chcete-li vyřešit tento problém, zkuste projekt adresáře sestavení vyloučíte z antivirového programu.

### <a name="cannot-open-a-microsoft-library-file"></a>Nelze otevřít soubor Microsoft Library

Pokud je soubor, který nelze otevřít jeden ze standardní knihovny souborů od Microsoftu, jako je například kernel32.lib, můžete mít chyby v konfiguraci projektu nebo chybě instalace. Ověřte, že je nainstalovaná sada Windows SDK a pokud váš projekt vyžaduje další knihovny Microsoft, jako je například knihovny MFC, ujistěte se, že komponent knihovny MFC byly také nainstalovat pomocí instalačního programu sady Visual Studio. Můžete spustit instalační program znovu a přidejte volitelné součásti v každém okamžiku. Další informace najdete v tématu [upravit Visual Studio](/visualstudio/install/modify-visual-studio). Na kartě jednotlivé komponenty v instalačním programu k výběru konkrétních knihoven a sad SDK.

Pokud vytváříte projekt, který byl vytvořen ve starší verzi sady Visual Studio, sada nástrojů platformy a knihovny pro tuto verzi se nenainstaluje. Pokud se zobrazí chybová zpráva pro název verzované knihovny, jako je například msvcr100.lib, to je pravděpodobně příčinu. Chcete-li vyřešit tento problém, máte dvě možnosti: můžete upgradovat projekt, který používá aktuální sady nástrojů platformy nainstalujete, nebo můžete nainstalovat na starší sadu nástrojů a sestavte projekt beze změny. Další informace najdete v tématu [upgrade projektů z dřívějších verzí sady Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) a [pomocí nativního cílení na více platforem v sadě Visual Studio sestavení starých projektů](../../porting/use-native-multi-targeting.md).

Pokud tato chyba se zobrazí, když vytvoříte novou cílovou platformu nebo konfiguraci, knihovny pro tuto konfiguraci nebo platformu sady nástrojů projektu se nenainstaluje. Ověřte, že **sada nástrojů platformy** a **verze sady Windows SDK** zadané v poli [stránce obecných vlastností](../../build/reference/general-property-page-project.md) jsou nainstalovány pro váš projekt a ověřte, zda požadovaný knihovny jsou k dispozici v **adresáře knihoven** zadané v poli [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md) nastavení konfigurace. Existují samostatné nastavení pro ladění a konfigurací maloobchodního prodeje, stejně jako 32bitové a 64bitové konfiguraci, tak pokud jednoho sestavení funguje, ale jiné způsobí chybu, ujistěte se, že je nastavení správné a požadované nástroje a knihovny se nainstalují pro všechny konfigurace, které vytváříte.

Pokud používáte Visual Studio IDE pro sestavení projektu, který byl zkopírován z jiného počítače, může být jiný instalační umístění pro knihovny. Zkontrolujte **adresáře knihoven** vlastnost [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md) pro projekt a v případě potřeby ji aktualizujte. Chcete-li zobrazit a upravit aktuální cesty knihoven, nastavte v integrovaném vývojovém prostředí, zvolte ovládací prvek rozevírací seznam pro **adresáře knihoven** vlastnosti a zvolte **upravit**. **Vyhodnotit hodnotu** část **adresáře knihoven** dialogové okno uvádí aktuální cesty hledat soubory knihovny.

K této chybě může dojít také při cestu k sadě Windows SDK není aktuální. Pokud máte nainstalovanou verzi sady Windows SDK, která je novější než vaše verze sady Visual Studio, ujistěte se, že cesty zadané v [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md) jsou aktualizovány tak, aby odpovídala nové sady SDK. Pokud používáte příkazový řádek pro vývojáře, ujistěte se, že dávkový soubor, který inicializuje proměnné prostředí je aktualizováno pro nové cesty sady SDK. Tento problém můžete vyhnout použitím instalačního programu sady Visual Studio k instalaci aktualizované sady SDK.

### <a name="cannot-open-a-third-party-library-file"></a>Nelze otevřít soubor knihovny třetí strany

Existuje několik běžných příčin pro tento problém:

- Cesta k souboru knihovny může být nesprávný, nebo nemusí zadali jste ho do propojovacího programu.

- Je nainstalovaná 32bitová verze knihovny, ale vytváříte 64 bitů, nebo naopak.

- Knihovny mohou mít závislosti na dalších knihoven, které nejsou nainstalované.

Chcete-li vyřešit problém cestu, ověřte, zda proměnné prostředí LIB je nastavena a obsahuje všechny adresáře pro knihovny, který používáte pro každou konfiguraci, kterou vytvoříte. V integrovaném vývojovém prostředí, je proměnná LIB nastavil **adresáře knihoven** vlastnost [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md). Zajistěte, aby všechny adresáře, které obsahují potřebné knihovny, které potřebujete jsou zde uvedeny, pro každou konfiguraci, kterou vytváříte.

Pokud je třeba zadat adresář knihovny, která přepíše adresář standardní knihovny, můžete použít [/Libpath](../../build/reference/libpath-additional-libpath.md) možnost na příkazovém řádku nebo v integrovaném vývojovém prostředí, můžete použít **další adresáře knihoven** Vlastnost **vlastnosti konfigurace > Linker > Obecné** stránku vlastností pro váš projekt.

Ujistěte se, že máte nainstalované všechny verze knihovny, které potřebujete pro konfigurace, které vytváříte. Zvažte použití [vcpkg](../../vcpkg.md) balíček nástroj pro správu k automatizaci instalace a nastavení pro mnoho běžných knihoven. Pokud je to možné, doporučujeme vytvářet vlastní kopie knihovny třetích stran, takže máte jistotu, že mají všechny místní závislosti, které vyžadují knihovny a jsou vytvořené pro stejnou konfiguraci jako váš projekt.

### <a name="cannot-open-a-file-built-by-your-project"></a>Nelze otevřít soubor vytvořen vaším projektem

Tato chyba může zobrazit, pokud soubor *filename* je vytvořených vaším řešením, ale dosud neexistuje propojovací program se pokusí k němu přistupovat. To může nastat při jednom projektu závisí na jiný projekt, ale projektů nejsou vytvořená ve správném pořadí. Chcete-li vyřešit tento problém, ujistěte se, že odkazy projektu jsou nastaveny v projektu, který používá soubor tak, že chybí soubor je sestaveny předtím, než je povinný. Další informace najdete v tématu [přidávání odkazů v projektech Visual C++](../../build/adding-references-in-visual-cpp-projects.md) a [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).

### <a name="cannot-open-file-cprogramobj"></a>Nelze otevřít soubor "C:\\Program.obj.

Pokud se zobrazí tato chyba nebo podobné chyby týkající se soubor .obj neočekávané v kořenové složce jednotky, problém se téměř jistě cestu ke knihovně, která není zabalena do dvojitých uvozovek.

Chcete-li vyřešit tento problém pro sestavení příkazového řádku, zkontrolujte [/Libpath](../../build/reference/libpath-additional-libpath.md) možnost parametry cesty zadané v proměnné prostředí LIB a cesty zadané v příkazovém řádku a je třeba použít dvojité uvozovky kolem žádné cesty který obsahuje mezery.

Chcete-li opravit tento problém v integrovaném vývojovém prostředí, zkontrolujte **adresáře knihoven** vlastnost [vlastnosti konfigurace > adresáře VC ++](../../build/reference/vcpp-directories-property-page.md) stránku vlastností **další adresáře knihoven** vlastnost v **vlastnosti konfigurace > Linker > Obecné** stránku vlastností a **Další závislosti** vlastnost v **konfigurace Vlastnosti > Linker > vstup** stránku vlastností pro váš projekt. Ujistěte se, že všechny cesty adresáře, které obsahují potřebné knihovny jsou zabaleny v uvozovkách, v případě potřeby.

### <a name="other-common-issues"></a>Další běžné problémy

Této chybě může dojít, pokud je název souboru knihovny nebo cesta zadaná propojovací program na příkazovém řádku nebo v [#pragma comment (lib, "library_name")](../../preprocessor/comment-c-cpp.md) – direktiva je nesprávný, nebo má specifikaci jednotka není platná cesta. Zkontrolujte pravopis a přípona souboru a ověřte, zda že soubor existuje na zadaném umístění.

Jiný program může mít soubor otevřete a linker nemůže zapisovat do něj. Antivirové programy často dočasně zablokovat přístup k nově vytvořené soubory. Chcete-li vyřešit tento problém, zkuste projekt adresáře sestavení vyloučíte z antivirového programu.

Pokud použijete možnost paralelního sestavení, je možné, že Visual Studio uzamknul souboru v jiném vlákně. Chcete-li vyřešit tento problém, ověřte, že není sestavení na stejný objekt kódu nebo knihovnu ve více projektech a aby se získaly sestavené binární soubory v projektu použít závislosti sestavení nebo odkazy na projekt.

Pokud zadáte jednotlivé knihovny **Další závislosti** vlastnost přímo, pomocí prostorů jednotlivé názvy knihoven, není čárkami nebo středníkem. Pokud používáte **upravit** otevřete položku nabídky **Další závislosti** dialogové okno, vložení znaků newline použít k oddělení názvů, ne čárkami, středníky nebo mezery. Vložení znaků newline použít také při zadání cesty knihoven v **adresáře knihoven** a **další adresáře knihoven** dialogových oknech.

Tato chyba může zobrazit při cesta pro *filename* rozšiřuje na více než 260 znaků. Změňte názvy nebo změně uspořádání adresářovou strukturu v případě potřeby ke zkrácení cesty k požadovaným souborům.

Této chybě může dojít, protože soubor je příliš velký. Knihovny nebo objekt soubory větší než gigabajty velikost může způsobit potíže 32bitovému linkeru. Je to možné opravu tohoto problému je použít 64bitové sady nástrojů. Další informace o tom, jak to provést na příkazovém řádku naleznete v tématu [jak: Povolit 64bitové sady nástrojů Visual C++ v příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Informace o tom, jak to provést v prostředí IDE najdete v tématu [pomocí nástroje MSBuild s 64bitovým kompilátorem a nástroji](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) a tento příspěvek na webu Stack Overflow: [Jak sada Visual Studio pomocí sady nástrojů nativní amd64](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

K této chybě může dojít, pokud máte soubor dostatečná oprávnění pro přístup k *filename*. To může dojít, pokud můžete použít běžný uživatelský účet a pokus o přístup k souborům knihovny v adresářích chráněného systému, nebo použít soubory zkopírovány z jiných uživatelů, kteří mají oprávnění k nim původní nastavení. Chcete-li vyřešit tento problém, přesuňte soubor na adresář zapisovatelný projektu. Pokud soubor je do zapisovatelného adresáře, ale je nedostupný oprávnění, můžete použít příkazový řádek správce a spusťte příkaz takeown.exe převzít vlastnictví souboru.

Této chybě může dojít, pokud nemáte dostatek místa na disku. Propojovací program použije dočasných souborů v několika případech. I v případě, že máte dostatek místa na disku, můžete velmi velké odkaz poškozují nebo fragment dostupné místo na disku. Zvažte použití [/OPT (optimalizace)](../../build/reference/opt-optimizations.md) možnost; to tranzitivní čtení sekvencí COMDAT odstranění všech souborů objektů více než jednou.

Pokud *filename* jmenuje LNK*nnn*, což je název souboru, který je vygenerován linkerem pro dočasný soubor, neexistuje v adresáři uvedeném na proměnnou prostředí TMP, nebo může být více než jeden adresář zadat proměnné prostředí TMP. Pro proměnnou prostředí TMP by měla být zadána cesta pouze jednomu adresáři.
