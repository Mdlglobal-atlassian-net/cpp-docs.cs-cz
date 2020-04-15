---
title: Sestavení starých projektů v sadě Visual Studio pomocí nativního cílení na více verzí
ms.date: 10/25/2019
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
ms.openlocfilehash: 70acf3b5b78e0bc58555ef3f1f8e72e8aed74dd5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353268"
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Sestavení starých projektů v sadě Visual Studio pomocí nativního cílení na více verzí

Obvykle doporučujeme aktualizovat projekty při instalaci nejnovější verze sady Visual Studio. Náklady na aktualizaci projektů a kódu jsou obvykle více než kompenzovány výhodami nového rozhraní IDE, kompilátoru, knihoven a nástrojů. Víme však, že některé projekty nemusí být možné aktualizovat. Můžete mít binární soubory, které jsou vázány na starší knihovny nebo platformy, které z důvodu údržby nelze upgradovat. Váš kód může používat nestandardní jazykové konstrukce, které by se přerušily, pokud byste přešli na novější kompilátor. Váš kód může spoléhat na knihovny třetích stran zkompilované pro konkrétní verzi visual c++. Nebo můžete vytvářet knihovny pro ostatní uživatele, které musí cílit na konkrétní starší verzi visual c++.

Naštěstí můžete použít Visual Studio 2017 a Visual Studio 2015 k vytváření projektů, které cílí na starší sady nástrojů kompilátoru a knihovny. Není třeba upgradovat visual studio 2010, Visual Studio 2012, Visual Studio 2013 nebo Visual Studio 2015 projektu využít nové funkce v ide:

- Nové možnosti refaktoringu c++ a experimentální funkce editoru
- Okno ladicího programu nové diagnostické nástroje a okno Seznam chyb
- Přepracované zarážky, okno výjimek a nové perftipy
- Nové nástroje pro navigaci a vyhledávání kódu
- Nové rychlé opravy v C++ a rozšíření o nástroje pro zvýšení produktivity.

Můžete také cílit na projekty sady Visual Studio 2008, ale nelze je použít beze změny. Podrobnosti naleznete v části **Pokyny pro visual studio 2008.**

Nejnovější verze sady Visual Studio podporují nativní vícenásobné cílení a kruhové zakopnutí projektů. Nativní vícenásobné cílení je schopnost nejnovějšího ide vytvářet pomocí sad nástrojů nainstalovaných předchozími verzemi sady Visual Studio. Round-tripping je schopnost nejnovějšího ide načíst projekty vytvořené předchozí verzí ide bez provedení jakýchkoli změn v projektu. Pokud nainstalujete nejnovější verzi sady Visual Studio vedle sebe s vaší stávající verzí, můžete použít novou verzi ide s kompilátorem a nástroje z existující verze k sestavení projektů. Ostatní členové vašeho týmu můžete nadále používat projekty ve starší verzi sady Visual Studio.

Při použití starší sady nástrojů můžete využít mnoho nejnovějších funkcí ide, ale ne nejnovější pokroky v kompilátoru C++, knihovny a nástroje pro sestavení. Například nebudete moci použít nová vylepšení shody jazyka, nové funkce ladění a analýzy kódu nebo získat rychlejší propustnost sestavení nejnovější sady nástrojů. Existují také některé funkce IDE, které nejsou kompatibilní se staršími sadami nástrojů. Například informace o typu může chybět v profileru paměti a refaktoring operace **Převést na raw řetězci literály** generuje C ++ 11 kompatibilní kód, který nebude kompilovat při použití Visual Studio 2012 nebo starší sady nástrojů.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>Použití nativního vícenásobného cílení v sadě Visual Studio

Po instalaci sady Visual Studio vedle sebe se starší verzí otevřete stávající projekt v nové verzi sady Visual Studio. Při načtení projektu visual studio zobrazí dotaz, zda chcete upgradovat na nejnovější kompilátor c++ a knihovny. Vzhledem k tomu, že chcete, aby projekt zachovat starší kompilátor a knihovny, zvolte **tlačítko Storno.**

Visual Studio je trvalé o upgradu projektu. Chcete-li se vyhnout zobrazení dialogového okna upgradu při každém načtení projektu, můžete definovat následující vlastnosti v projektech nebo v souborech .props nebo .targets, které importují:

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

Tuto vlastnost je nutné odebrat, pokud chcete upgradovat projekty.

Pokud se rozhodnete neupgradovat, Visual Studio neprovede žádné změny vašeho řešení nebo soubory projektu. Při vytváření projektu jsou generované binární soubory plně kompatibilní s těmi, které jste vytvořili se starší verzí sady Visual Studio. Důvodem je, že Visual Studio používá stejný kompilátor Jazyka C++ a propojuje stejné knihovny, které vaše starší IDE dodávané s. To je také důvod, proč dialogové okno upgradu vás upozorní, abyste měli mít nainstalovanou starší verzi sady Visual Studio, pokud zvolíte **Zrušit**.

## <a name="instructions-for-visual-studio-2008"></a>Pokyny pro visual studio 2008

Visual Studio 2008 měl vlastní vyhrazený systém sestavení pro C++ s názvem **VCBuild**. Počínaje Visual Studio 2010, Visual Studio C++ projekty byly změněny na použití **MSBuild**. To znamená, že bez ohledu na to, zda inovace trvale nebo více cílení musíte projít krokem aktualizace k vytvoření projektů sady Visual Studio 2008 v nejnovější verzi sady Visual Studio. Aktualizovaný projekt stále generuje binární soubory, které jsou plně kompatibilní s binárními soubory vytvořenými pomocí rozhraní IDE sady Visual Studio 2008.

Nejprve kromě aktuální verze sady Visual Studio je nutné nainstalovat visual studio 2010 do stejného počítače jako Visual Studio 2008. Pouze Visual Studio 2010 nainstaluje skripty **MSBuild,** které jsou nutné k cílení projektů sady Visual Studio 2008.

Dále je nutné aktualizovat řešení sady Visual Studio 2008 a projekty na aktuální verzi sady Visual Studio. Doporučujeme vytvořit zálohu projektů a souborů řešení před upgradem. Chcete-li spustit proces upgradu, otevřete řešení v aktuální verzi sady Visual Studio. Po zobrazení výzvy k upgradu zkontrolujte prezentované informace a pak zvolte **OK** a spusťte upgrade. Pokud máte v řešení více než jeden projekt, je nutné aktualizovat Průvodce vytvoří nové soubory projektu .vcxproj vedle existujících souborů .vcproj. Pokud máte také kopii původního souboru .sln, upgrade nemá žádný jiný vliv na existující projekty sady Visual Studio 2008.

> [!NOTE]
> Následující kroky platí pouze pro scénáře s více cíleními. Pokud máte v úmyslu trvale upgradovat projekt na novější sadu nástrojů, pak dalším krokem je uložení projektu, jeho otevření v sadě Visual Studio 2019 a řešení problémů sestavení, které se tam zobrazují.

Po dokončení upgradu, pokud sestava protokolu obsahuje chyby nebo upozornění pro některý z vašich projektů, pečlivě zkontrolujte. Převod z **VCBuild** na **MSBuild** může způsobit problémy. Ujistěte se, že rozumíte a implementujete všechny položky akcí uvedené v sestavě. Další informace o sestavě protokolu upgradu a problémy, které mohou nastat při převodu **VCBuild** na **MSBuild**, naleznete v tomto [c++ nativní multi-cílení](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) blogu.

Po dokončení upgradu projektu a opravili jste všechny problémy v souboru protokolu, vaše řešení skutečně cílí na nejnovější sadu nástrojů. Jako poslední krok změňte vlastnosti pro každý projekt v řešení použít sadu nástrojů Visual Studio 2008. S řešením načteným v aktuální verzi sady Visual Studio otevřete pro každý projekt v řešení dialogové okno **Stránky vlastností** projektu: Klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a pak vyberte **Vlastnosti**. V dialogovém okně **Stránky vlastností** změňte rozevírací hodnotu **Konfigurace** na **Všechny konfigurace**. Ve **vlastnostech konfigurace**vyberte **možnost Obecné**a potom změňte sadu **nástrojů platformy** na **Visual Studio 2008 (v90).**

Po této změně se kompilátor a knihovny sady Visual Studio 2008 používají ke generování binárních souborů projektu při vytváření řešení v aktuální verzi sady Visual Studio.

## <a name="install-an-older-visual-studio-toolset"></a>Instalace starší sady nástrojů sady nástrojů Sady Visual Studio

Můžete mít starý projekt Visual Studio C++, který nemůžete nebo nechcete upgradovat, ale ne verzi sady nástrojů platformy, která odpovídá vašemu projektu. V takovém případě můžete sadu nástrojů získat, můžete nainstalovat bezplatnou aplikaci Visual Studio Community nebo Express edition verze, kterou potřebujete. Každá verze sady Visual Studio z visual studia 2008 můžete nainstalovat kompilátor, nástroje a knihovny, které potřebujete k cílení na tuto verzi z aktuálnísady Visual Studio. Vyhledejte a stáhněte konkrétní verzi sady Visual Studio v centru pro stahování Microsoft Download Center. Ujistěte se, že jste během instalace zvolili možnosti instalace jazyka C++. Po dokončení instalace spusťte tuto verzi sady Visual Studio a nainstalujte všechny aktualizace. Zkontrolujte také všechny změny služby Windows Update, které mohou být požadovány. Tento proces kontroly aktualizace může být nutné opakovat více než jednou získat každou aktualizaci.

Aktuálně dostupné soubory ke stažení naleznete v [tématu Stažení staršího softwaru sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/).

Po instalaci těchto produktů se automaticky aktualizuje rozevírací výběr vlastností **Sady nástrojů platformy** v dialogovém okně **Stránky vlastností,** aby se zobrazily dostupné sady nástrojů. Nyní můžete použít nejnovější verzi sady Visual Studio k vytváření projektů pro tyto starší verze sady nástrojů bez jejich převodu nebo upgradu.

## <a name="see-also"></a>Viz také

[Inovace projektů z dřívějších verzí visual c++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Vylepšení shody C++ se sadou Visual Studio](../overview/cpp-conformance-improvements.md)
