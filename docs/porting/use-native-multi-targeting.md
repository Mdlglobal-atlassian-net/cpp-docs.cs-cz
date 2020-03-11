---
title: Sestavení starých projektů v sadě Visual Studio pomocí nativního cílení na více verzí
ms.date: 10/25/2019
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
ms.openlocfilehash: aff21121c181131b04ad22d75f03b7cbb222228a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875868"
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Sestavení starých projektů v sadě Visual Studio pomocí nativního cílení na více verzí

Normálně doporučujeme, abyste projekty aktualizovali při instalaci nejnovější verze sady Visual Studio. Náklady na aktualizaci vašich projektů a kódu jsou obvykle větší než posun díky výhodám nového integrovaného vývojového prostředí (IDE, kompilátoru, knihoven a nástrojů). Víme ale, že možná nebudete moct aktualizovat některé projekty. Můžete mít binární soubory, které jsou svázané se staršími knihovnami nebo platformami, z důvodů údržby nemůžete upgradovat. Váš kód může používat nestandardní jazykové konstrukce, které by byly přerušeny, pokud jste přešli na novější kompilátor. Váš kód může spoléhat na knihovny třetích stran zkompilované pro konkrétní verzi vizuálu C++. Případně můžete vytvořit knihovny pro jiné, které musí cílit na konkrétní starší verzi vizuálu C++.

Naštěstí můžete pomocí sady Visual Studio 2017 a sady Visual Studio 2015 sestavovat projekty, které cílí na starší sady nástrojů a knihovny pro kompilátor. Nemusíte upgradovat projekt sady Visual Studio 2010, Visual Studio 2012, Visual Studio 2013 nebo Visual Studio 2015, aby bylo možné využívat nové funkce v integrovaném vývojovém prostředí (IDE):

  - Nové C++ funkce refaktoringu a experimentální funkce editoru
  - Nové okno ladicího programu nástrojů pro diagnostiku a Seznam chyb okno
  - Přepracované zarážky, okno výjimky a nové tipy pro výkon
  - Nové nástroje pro navigaci v kódu a nástroje pro hledání
  - Nové C++ rychlé opravy a produktivita rozšíření Power Tools.

Můžete také cílit na projekty sady Visual Studio 2008, ale nelze je použít beze změny. Podrobnosti naleznete v části **pokyny pro Visual Studio 2008** .

Nejnovější verze sady Visual Studio podporují nativní cílení na více verzí a kruhové Trip projektů. Nativní cílení na více verzí je schopnost nejnovějšího integrovaného vývojového prostředí (IDE) pro sestavení pomocí sad nástrojů nainstalovaných předchozími verzemi sady Visual Studio. Round-Trip je schopnost nejnovějšího rozhraní IDE načíst projekty vytvořené předchozí verzí IDE bez provedení změn v projektu. Pokud nainstalujete nejnovější verzi sady Visual Studio vedle stávající verze, můžete použít novou verzi rozhraní IDE s kompilátorem a nástroji z existující verze k sestavení projektů. Jiní členové týmu mohou nadále používat projekty ve starší verzi sady Visual Studio.

Použijete-li starší sadu nástrojů, můžete využít mnoho nejnovějších funkcí rozhraní IDE, ale ne poslední pokrok v C++ kompilátoru, knihovnách a nástrojích sestavení. Například nebudete moci používat nová vylepšení v souladu s jazyky, nové funkce ladění a analýzy kódu nebo získat rychlejší sestavení nejnovější sady nástrojů. K dispozici jsou také některé funkce rozhraní IDE, které jsou nekompatibilní se staršími sadami nástrojů. Například informace o typu mohou chybět v profileru paměti a operace refaktoringu **převedené na nezpracované řetězcové literály** generuje kód kompatibilní s jazykem C + +11, který nebude zkompilován při použití sady Visual Studio 2012 nebo starší sady nástrojů.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>Jak používat nativní cílení na více platforem v aplikaci Visual Studio

Jakmile nainstalujete sadu Visual Studio souběžně se starší verzí, otevřete existující projekt v nové verzi sady Visual Studio. Po načtení projektu aplikace Visual Studio zobrazí dotaz, zda chcete upgradovat, aby používala nejnovější C++ kompilátor a knihovny. Vzhledem k tomu, že chcete, aby projekt zachoval starší kompilátor a knihovny, klikněte na tlačítko **Storno** .

Visual Studio je trvalé o upgradu projektu. Chcete-li se vyhnout zobrazení dialogového okna pro upgrade při každém načtení projektu, můžete definovat následující vlastnost v projektech nebo v souborech. props nebo. targets, které importují:

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

Tuto vlastnost je nutné odebrat, pokud chcete upgradovat projekty.

Pokud se rozhodnete neupgradovat, Visual Studio neprovede žádné změny v souborech řešení nebo projektu. Při sestavování projektu jsou vygenerované binární soubory plně kompatibilní s těmi, které jste vytvořili ve starší verzi sady Visual Studio. Je to proto, že Visual Studio používá C++ stejný kompilátor a propojuje stejné knihovny, se kterými bylo vaše staré integrované vývojové prostředí (IDE) dodáváno. To je také důvod, proč dialogové okno pro upgrade vás upozorní, že pokud vyberete **Zrušit**, zůstane nainstalována starší verze sady Visual Studio.

## <a name="instructions-for-visual-studio-2008"></a>Pokyny pro Visual Studio 2008

Visual Studio 2008 měl vlastní vyhrazený systém sestavení pro C++ s názvem **vcbuild**. Od aplikace Visual Studio 2010 byly projekty sady C++ Visual Studio změněny na použití nástroje **MSBuild**. To znamená, že pokud se má provést upgrade na trvalé nebo na více platforem, musíte projít krok aktualizace a sestavit projekty sady Visual Studio 2008 v nejnovější verzi sady Visual Studio. Aktualizovaný projekt stále generuje binární soubory, které jsou plně kompatibilní s binárními soubory vytvořenými pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio 2008.

Nejprve je třeba nainstalovat sadu Visual Studio 2010 na stejném počítači jako Visual Studio 2008. Pouze Visual Studio 2010 nainstaluje skripty **MSBuild** , které jsou požadovány pro cílení na projekty sady Visual Studio 2008.

Dále je nutné aktualizovat řešení a projekty sady Visual Studio 2008 na aktuální verzi sady Visual Studio. Před upgradem doporučujeme vytvořit zálohu projektů a souborů řešení. Chcete-li spustit proces upgradu, otevřete řešení v aktuální verzi sady Visual Studio. Po zobrazení výzvy k upgradu zkontrolujte zobrazené informace a pak kliknutím na **tlačítko OK** spusťte upgrade. Pokud máte v řešení více než jeden projekt, je nutné aktualizovat Průvodce vytvořením nových souborů projektu vcxproj vedle existujících souborů. vcproj. Pokud máte také kopii původního souboru. sln, upgrade nemá jiný dopad na vaše stávající projekty sady Visual Studio 2008.

> [!NOTE]
> Následující postup se týká pouze scénářů cílení na více platforem. Pokud máte v úmyslu trvale upgradovat projekt na novější sadu nástrojů, pak je dalším krokem uložení projektu, jeho otevření v sadě Visual Studio 2019 a řešení problémů s sestavením, které jsou zde uvedeny.

Pokud se upgrade dokončí, pokud sestava protokolu obsahuje chyby nebo varování pro některý z vašich projektů, pečlivě si je Projděte. Převod z **vcbuild** na **MSBuild** může způsobovat problémy. Ujistěte se, že rozumíte a implementujete všechny položky akcí uvedené v sestavě. Další informace o sestavě protokolu upgradu a problémech, ke kterým může dojít při převodu **vcbuild** na **MSBuild**, najdete v tomto [ C++ nativním](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) blogovém příspěvku cílení na více platforem.

Až se upgrade projektu dokončí a opravíte všechny problémy v souboru protokolu, vaše řešení vlastně cílí na nejnovější sadu nástrojů. V posledním kroku změňte vlastnosti pro každý projekt v řešení tak, aby používal sadu nástrojů sady Visual Studio 2008. Pomocí řešení načteného v aktuální verzi sady Visual Studio, pro každý projekt v řešení, otevřete dialogové okno **stránky vlastností** projektu: klikněte pravým tlačítkem myši na projekt v **Průzkumník řešení** a pak vyberte **vlastnosti**. V dialogovém okně **stránky vlastností** změňte hodnotu rozevíracího seznamu **Konfigurace** na **všechny konfigurace**. V **nastavení vlastnosti konfigurace**vyberte **Obecné**a pak změňte **sadu nástrojů platformy** na **Visual Studio 2008 (V90)** .

Po této změně se kompilátor a knihovny sady Visual Studio 2008 použijí ke generování binárních souborů projektu při sestavení řešení v aktuální verzi sady Visual Studio.

## <a name="install-an-older-visual-studio-toolset"></a>Nainstalovat starší sadu nástrojů sady Visual Studio

Je možné, že máte starý projekt C++ sady Visual Studio, který nemůžete nebo nechcete upgradovat, ale ne verzi sady nástrojů platformy, která odpovídá vašemu projektu. V takovém případě můžete získat sadu nástrojů a nainstalovat bezplatnou verzi sady Visual Studio Community nebo Express, kterou potřebujete. Každá verze sady Visual Studio ze sady Visual Studio 2008 v systému může nainstalovat kompilátor, nástroje a knihovny, které potřebujete k zacílení verze z aktuální sady Visual Studio. Na webu Microsoft Download Center vyhledejte a stáhněte konkrétní verzi sady Visual Studio. Ujistěte se, že během C++ instalace zvolíte možnost instalace. Po dokončení instalace spusťte tuto verzi sady Visual Studio a nainstalujte aktualizace. Také vyhledejte jakékoli web Windows Update změny, které mohou být požadovány. Tento proces kontroly aktualizací může být potřeba zopakovat více než jednou a získat tak každou aktualizaci.

Informace o aktuálně dostupných souborech ke stažení najdete v tématu [stažení staršího softwaru sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/).

Po instalaci těchto produktů se v dialogovém okně **stránky vlastností** automaticky aktualizuje rozevírací seznam vlastnosti sady **nástrojů platformy** , aby se zobrazily dostupné sady nástrojů. Nyní můžete použít nejnovější verzi sady Visual Studio k sestavení projektů pro tyto starší verze sady nástrojů bez jejich převádění nebo upgradu.

## <a name="see-also"></a>Viz také

[Upgrade projektů z dřívějších verzí sady VisualC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Vylepšení shody C++ se sadou Visual Studio](../overview/cpp-conformance-improvements.md)
