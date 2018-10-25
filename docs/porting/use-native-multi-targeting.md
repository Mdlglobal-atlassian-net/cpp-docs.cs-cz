---
title: Pomocí nativního cílení na více platforem v sadě Visual Studio sestavení starých projektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c66fe63d97f623011b3dade46266a4a9d8d83b1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064418"
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Pomocí nativního cílení na více platforem v sadě Visual Studio sestavení starých projektů

Za normálních okolností doporučujeme aktualizovat projekty, když instalujete nejnovější verzi sady Visual Studio. Náklady na aktualizaci projekty a kód se obvykle více než posun tak výhod nového integrovaného vývojového prostředí, kompilátor, knihovny a nástroje. Ale víme, že nemusí být schopen aktualizovat některé projekty. Můžete mít binární soubory, které jsou vázané na starší platformy, že z důvodů údržby nelze upgradovat nebo knihovny. Váš kód může použít nestandardní jazykovým konstrukcím, které by přerušit, pokud jste přesunuli na novější kompilátoru. Váš kód může spoléhat na 3. stran knihovny pro konkrétní verzi nástroje Visual C++. Nebo může vytvořit knihovny pro ostatní uživatele, které musí cílit na konkrétní starší verze jazyka Visual C++.

Naštěstí můžete použít Visual Studio 2017 a Visual Studio 2015 k sestavení projektů, které cílový starší sady nástrojů kompilátoru a knihovny. Nemusíte upgradovat Visual Studio 2010, Visual Studio 2012, Visual Studio 2013 nebo projektu sady Visual Studio 2015 využívat nové funkce v integrovaném vývojovém prostředí:

  - Nové funkce refaktoringu jazyka C++ a experimentální funkce editoru
  - Nové nástroje pro diagnostiku ladicího programu a do okna Seznam chyb
  - Přepracované zarážky, okno výjimky a nové tipy pro výkon
  - Nové nástroje navigace a vyhledávání kódu
  - Nové rychlé opravy C++ a rozšíření nástrojů Productivity Power Tools.

Můžete také směrovat projektů Visual Studio 2008, ale nelze je použít beze změny. Podrobnosti najdete v tématu **pokyny, jak Visual Studio 2008** oddílu.

Nejnovější verze sady Visual Studio podporují nativní cílení na více platforem a verzemi projektů. Nativní cílení na více platforem je schopnost nejnovější integrovaného vývojového prostředí pro sestavení pomocí nástrojů, které jsou nainstalované v předchozích verzích sady Visual Studio. Verzemi je schopnost nejnovější IDE načtěte projekty vytvořené v předchozí verzi integrované vývojové prostředí bez jakýchkoli změn do projektu. Pokud nainstalujete nejnovější verzi sady Visual Studio – souběžně se stávající verzi, můžete použít novou verzi rozhraní IDE s kompilátorem a nástroji ze stávající verze k sestavování vašich projektů. Ostatní členové týmu můžete dál používat projekty ve starší verzi sady Visual Studio.

Pokud používáte starší sadu nástrojů, můžete využít výhod řadu nejnovější funkce integrovaného vývojového prostředí, ale ne nejnovější zálohy C++ kompilátor, knihovny a nástroje sestavení. Například nebudou moct použít nová shoda vylepšení jazyka nové ladění a funkce analýzy kódu nebo získat rychlejší propustnost sestavení na nejnovější sadu nástrojů. Existují také některé funkce integrovaného vývojového prostředí, které nejsou kompatibilní s starší sady nástrojů. Například typ informace jsou pravděpodobně chybí v Profiler paměti a operaci refaktoringu **převést na nezpracované řetězcové literály** generuje C ++ 11 kompatibilní kód, který nebude kompilovat při použití sady Visual Studio 2012 nebo starší sady nástrojů.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>Jak používat nativní cílení na více platforem v sadě Visual Studio

Po instalaci sady Visual Studio – souběžně se starší verzí, otevřete existující projekt v nové verzi sady Visual Studio. Při načtení projektu sady Visual Studio vás zeptá, zda chcete upgradovat na nejnovější kompilátor jazyka C++ a knihoven. Vzhledem k tomu, aby se projekt zachovat starší kompilátor a knihovny, zvolte **zrušit** tlačítko.

Visual Studio je trvalé o upgradu projektu. Chcete-li předejít zobrazení upgradu dialogového okna pokaždé, když načtete projekt, můžete definovat následující vlastnosti v projektech, nebo v souborech .props nebo .targets importovat:

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

Pokud chcete provést upgrade vašich projektů, je třeba odebrat tuto vlastnost.

Pokud se rozhodnete neupgradovat, Visual Studio neprovede žádné změny k souborům řešení nebo projektu. Při sestavování projektu generovaný binární soubory jsou plně kompatibilní s těmi, které jste vytvořili pomocí starší verze sady Visual Studio. Je to proto, že Visual Studio používá stejné kompilátor jazyka C++ a propojí stejné knihovny, která jsou součástí vašeho starší prostředí IDE. To je také proč upgradu dialog upozorňuje na starší verze sady Visual Studio nainstalovaný, pokud se rozhodnete udržovat **zrušit**.

## <a name="instructions-for-visual-studio-2008"></a>Pokyny pro sadu Visual Studio 2008

Visual Studio 2008 má svůj vlastní vyhrazený sestavovací systém pro jazyk C++ volá **VCBuild**. Spouští se v sadě Visual Studio 2010, projekty v jazyce Visual C++ byly změněny na použití **MSBuild**. To znamená, že musí přejít až aktualizaci k sestavování projektů Visual Studio 2008 v nejnovější verzi sady Visual Studio. Aktualizovaný projekt stále generuje binární soubory, které jsou plně kompatibilní s binárními soubory vytvořené pomocí integrovaného vývojového prostředí Visual Studio 2008.

Kromě aktuální verze sady Visual Studio, nejprve musíte nainstalovat Visual Studio 2010 ve stejném počítači jako Visual Studio 2008. Nainstaluje pouze Visual Studio 2010 **MSBuild** skripty, které jsou potřeba k projektům cílové sady Visual Studio 2008.

Dále je třeba aktualizovat Visual Studio 2008 řešení a projektů na aktuální verzi sady Visual Studio. Doporučujeme že vytvořit zálohu projekty a soubory řešení před upgradem. Chcete-li zahájit proces upgradu, otevřete řešení v aktuální verzi sady Visual Studio. Když dostanete upgradu řádku, zkontrolujte zobrazené informace a klikněte na tlačítko **OK** spusťte upgrade. Pokud máte více než jeden projekt v řešení, je nutné aktualizovat Průvodce vytvoří novou .vcxproj projektu soubory – souběžně s existujícími soubory .vcproj. Za předpokladu, máte také kopii původního souboru .sln, upgrade nemá žádný vliv na existující projekty Visual Studio 2008.

Po dokončení upgradu, pokud má sestava protokolu chyb a upozornění pro všechny projekty, seznamte se s nimi pečlivě. Převod z **VCBuild** k **MSBuild** může způsobit problémy. Ujistěte se, že pochopit a implementovat všechny akce položky uvedené v sestavě. Další informace o protokolu o upgradu sestavy a problémy, které mohou nastat při převodu **VCBuild** k **MSBuild**, najdete v tomto [cílení na více verzí v nativním C++](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) blogový příspěvek.

Po dokončení upgradu projektu a opravili všechny problémy v souboru protokolu, vaše řešení cílí skutečně nejnovější sadu nástrojů. V posledním kroku změníte vlastnosti pro každý projekt v řešení použít sadu nástrojů Visual Studio 2008. S řešením načten v aktuální verzi sady Visual Studio, pro každý projekt v řešení, otevřete projekt **stránky vlastností** dialogové okno: klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a pak Vyberte **vlastnosti**. V **stránky vlastností** dialogovém okně Změnit **konfigurace** hodnotu rozevíracího seznamu **všechny konfigurace**. V **vlastnosti konfigurace**vyberte **Obecné**a potom změňte **sada nástrojů platformy** k **Visual Studio 2008 (v90)**.

Po této změně Visual Studio 2008 kompilátor a knihovny se používají ke generování binárních souborů projektu při sestavování řešení v aktuální verzi sady Visual Studio.

## <a name="install-an-older-visual-studio-toolset"></a>Instalace starší nástrojů sady Visual Studio

Můžete mít starý projektu Visual C++, který nemůžete nebo nechcete upgradovat, ale ne platformy verzi sady nástrojů, který odpovídá projektu. Získat sadu nástrojů, můžete v tomto případě nainstalovat Visual Studio edice Community zdarma nebo Express edition verze, které potřebujete. Všechny verze sady Visual Studio ze sady Visual Studio 2008 na nainstalovat kompilátoru, nástroje a knihovny, je potřeba cílit na tuto verzi v aktuální sadě Visual Studio. Vyhledejte Microsoft Download Center vyhledejte a stáhněte konkrétní verzi sady Visual Studio. Ujistěte se, že během instalace zvolíte možnosti instalace jazyka C++. Po dokončení instalace, spusťte tuto verzi sady Visual Studio nainstalovat všechny aktualizace. Také zkontrolujte, které mohou vyžadovat změny aktualizací Windows. Tento proces kontroly aktualizací může být nutné opakovat více než jednou. Chcete-li získat všechny aktualizace.

Aktuálně k dispozici ke stažení, najdete v části [starší sadě Visual Studio software ke stažení](https://visualstudio.microsoft.com/vs/older-downloads/).

Při instalaci těchto produktů **sada nástrojů platformy** vlastnost rozevírací seznam v **stránky vlastností** dialogové okno se automaticky aktualizuje a zobrazí dostupné sady nástrojů. Nejnovější verzi sady Visual Studio můžete nyní použít k sestavení projektů pro tyto starší verze sady nástrojů bez převodu nebo upgradu je.

## <a name="see-also"></a>Viz také

[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Vylepšení shody C++ se sadou Visual Studio 2017](../cpp-conformance-improvements-2017.md)