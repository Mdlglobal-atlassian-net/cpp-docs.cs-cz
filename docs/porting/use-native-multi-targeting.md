---
title: Pomocí nativní cílení na více v sadě Visual Studio staré projekty sestavení | Microsoft Docs
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
ms.openlocfilehash: 2df0bee37a0bcf0e8162fa692be79bd57b16b3cf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Pomocí nativní cílení na více v sadě Visual Studio staré projekty sestavení

Za normálních okolností doporučujeme aktualizovat projekty, při instalaci nejnovější verze sady Visual Studio. Náklady na aktualizaci projekty a kód je obvykle více než posun podle výhod nového IDE, kompilátoru, knihovny a nástroje. Ale víme, že nemusí být možné aktualizovat některé projekty. Můžete mít binární soubory, které jsou svázané s starší knihovny nebo platformy, z důvodů údržby nelze upgradovat. Váš kód mohou používat nestandardní jazykové konstrukty, které by přerušení, pokud se přesune do novější kompilátoru. Váš kód může spoléhají na 3. stran knihovny zkompilovaném pro určitou verzi sady Visual C++. Nebo může vytvořit knihovny pro ostatní, které musí mít jako cíl konkrétní starší verze aplikace Visual C++.

Naštěstí můžete použít Visual Studio 2017 a Visual Studio 2015 k vytvoření projektů, které cíl starší kompilátoru modulové a knihovny. Není nutné upgradovat Visual Studio 2010, Visual Studio 2012, Visual Studio 2013 nebo Visual Studio 2015 projektu využívat výhod nových funkcí v prostředí IDE:

 - Nové možnosti refaktoringu C++ a povolenými experimentálními funkcemi editoru
 - Okno a v okně Seznam chyb ladicího programu nové diagnostické nástroje
 - Renovována zarážky, okno výjimky a nové PerfTips
 - Nové nástroje navigaci a vyhledávání kódu
 - Nové C++ rychlé opravy a kancelářským nástrojům Power rozšíření.

Můžete také vybrat projektů Visual Studio 2008, ale nelze je použít beze změny. Podrobnosti najdete v tématu pokyny pro Visual Studio 2008 oddíl.

Nejnovější verze sady Visual Studio podporují nativní cílení na více a odezvy pro projekty. Nativní cílení na více je schopnost nejnovější IDE sestavení pomocí modulové nainstalován v předchozích verzích sady Visual Studio. Odezvy je schopnost nejnovější IDE načtení projektů vytvořených pomocí předchozí verze IDE bez jakýchkoli změn do projektu. Pokud nainstalujete nejnovější verzi sady Visual Studio – souběžného s vaší stávající verzi, můžete pomocí nástrojů ze stávající verze a kompilátoru novou verzi rozhraní IDE vytvářet projekty. Jiní členové týmu můžete nadále používat projektů ve starší verzi sady Visual Studio.

Pokud používáte starší sada nástrojů, můžete využít výhod řadu nejnovější funkce IDE, ale ne nejnovější zálohy v C++ kompilátoru, knihovny a sestavení nástroje. Například nebudete moci použít nová vylepšení shoda jazyk, nové ladění a code analysis funkce nebo získat rychlejší propustnost sestavení nejnovější sady nástrojů. Existují také některé funkce IDE, které nejsou kompatibilní s starší modulové. Informace o typu může být například chybějící v paměti profileru a operace refaktoringu **převést na nezpracovaná textové literály** generuje C ++ 11 kompatibilní kód, který nebude kompilovat při použití sady Visual Studio 2012 nebo starší modulové.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>Jak používat nativní cílení na více v sadě Visual Studio

Po instalaci sady Visual Studio – souběžného se starší verzí, otevřete existující projekt v nové verzi sady Visual Studio. Při načtení projektu sady Visual Studio zobrazí dotaz, zda chcete ho upgradovat na nejnovější kompilátoru C++ a knihovny. Vzhledem k tomu, že chcete projekt zachovat starší kompilátoru a knihovny, vyberte **zrušit** tlačítko.

Visual Studio je trvalé o upgrade projektu. Nechcete, aby dialog pro upgrade pokaždé, když načtení projektu, můžete definovat následující vlastnosti v projektech, nebo v souborech props nebo .targets importovat:

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

Tato vlastnost je nutné odebrat, pokud chcete provést upgrade vašich projektů.

Pokud si zvolíte neupgradovat, Visual Studio vaše soubory řešení nebo produktu project neprovede žádné změny. Při sestavování projektu vygenerované binární soubory jsou plně kompatibilní se ty, které jste vytvořili pomocí starší verze sady Visual Studio. Je to proto, že Visual Studio používá stejné kompilátoru C++ a propojuje stejné knihovny, které vaše starší IDE součástí. Se také proč dialog pro upgrade vás varuje, chcete-li zachovat starší verze sady Visual Studio, nainstalovat, pokud zvolíte **zrušit**.

## <a name="instructions-for-visual-studio-2008"></a>Pokyny pro Visual Studio 2008  
  
Visual Studio 2008 umožňovaly svůj vlastní systém vyhrazené sestavení C++ názvem VCBuild. Spouštění v sadě Visual Studio 2010, projekty Visual C++ byly změněny na použití nástroje MSBuild. To znamená, že musí projít na aktualizace krok k vytvoření vašich projektů Visual Studio 2008 v nejnovější verzi sady Visual Studio. Aktualizovaný projekt stále generuje binární soubory, které jsou plně kompatibilní se binární soubory, které jsou vytvořené pomocí prostředí Visual Studio 2008 IDE.

Kromě aktuální verze sady Visual Studio, Nejdřív musíte nainstalovat Visual Studio 2010 ve stejném počítači jako Visual Studio 2008. Pouze Visual Studio 2010 nainstaluje nástroje MSBuild skripty, které jsou nutné pro projekty Visual Studio 2008. 

Dále je nutné aktualizovat Visual Studio 2008 řešení a projektů na aktuální verzi sady Visual Studio. Doporučujeme že vytvořit zálohu své projekty a řešení soubory před upgradem. Chcete-li zahájit proces upgradu, otevřete řešení v aktuální verzi sady Visual Studio. Když získáte řádku upgradu, projděte si informace uvedené a potom vyberte **OK** spusťte upgrade. Pokud máte více než jeden projekt v řešení, je nutné aktualizovat Průvodce vytvoří novou VCXPROJ projektu soubory-souběžného s existujícími soubory .vcproj. Tak dlouho, dokud máte také kopii původní soubor .sln, upgrade nemá žádné další vliv na existující projekty Visual Studio 2008.

Po dokončení upgradu, pokud zpráva protokolu obsahuje chyby nebo upozornění pro některé z vašich projektů, zkontrolujte je pečlivě. Převod VCBuild MSBuild může způsobit problémy. Zajistěte, aby pochopit a implementovat všechny položky akce uvedené v této sestavě. Další informace o upgradu protokolu sestavy a problémy, které mohou nastat při převodu VCBuild na MSBuild najdete [cílení na více nativní C++](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) příspěvku na blogu.

Pokud je dokončen upgrade projektu a opravili všechny problémy v souboru protokolu, vaše řešení ve skutečnosti cíle nejnovější sady nástrojů. Jako poslední krok změňte vlastnosti pro každý projekt v řešení, aby používalo sady nástrojů Visual Studio 2008. S řešením načíst v aktuální verzi sady Visual Studio pro každý projekt v řešení, otevřete projekt **stránky vlastností** dialogové okno: klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a potom Vyberte **vlastnosti**. V **stránky vlastností** dialogové okno, změny **konfigurace** hodnotu rozevíracího seznamu **všechny konfigurace**. V **vlastnosti konfigurace**, vyberte **Obecné**a poté změňte **sada nástrojů platformy** k **Visual Studio 2008 (v90)**.

Po této změně kompilátoru Visual Studio 2008 a knihovny se používají ke generování binárních souborů projektu při sestavování řešení v aktuální verzi sady Visual Studio.

## <a name="install-an-older-visual-studio-toolset"></a>Instalace starší sady nástrojů Visual Studio

Můžete mít staré projektu Visual C++, které nemůžete nebo nechcete použít k upgradu, ale není sada nástrojů verze platformy, která odpovídá projektu. V takovém případě sada nástrojů získáte instalací volné Visual Studio Community nebo edice Express verze, které potřebujete. Každá verze sady Visual Studio ze sady Visual Studio 2008 na můžete nainstalovat kompilátoru, nástroje a knihovny, musíte pro tuto verzi z aktuální sady Visual Studio. Vyhledejte Microsoft Download Center vyhledat a stáhnout na konkrétní verzi sady Visual Studio. Ujistěte se, že vyberete možnosti instalace C++ během instalace. Po dokončení instalace spusťte danou verzi sady Visual Studio instalaci žádných aktualizací. Také zkontrolujte změny služby Windows Update, které mohou být požadovány. Tento proces aktualizace zkontrolujte možná muset opakovat více než jednou. Chcete-li získat každá aktualizace.

Tady jsou některé soubory ke stažení sady Visual Studio, které byste měli:

  - [Microsoft Visual Studio Community 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48146)  
  - [Sadu Microsoft Visual Studio Express 2013 pro Windows Desktop s aktualizací 5](https://www.microsoft.com/en-us/download/details.aspx?id=48131)  
  - [Sadu Microsoft Visual Studio Express 2012 for Windows Desktop](https://www.microsoft.com/en-us/download/details.aspx?id=34673)  
  - [Visual Studio 2012 Update 5](https://www.microsoft.com/en-us/download/details.aspx?id=34673)  
  - [Microsoft Visual C++ 2010 Express (Webová instalační služba)](https://download.microsoft.com/download/1/D/9/1D9A6C0E-FC89-43EE-9658-B9F0E3A76983/vc_web.exe)  
  - [Microsoft Visual Studio 2010 Service Pack 1](https://www.microsoft.com/en-us/download/details.aspx?id=23691)  
  - [Microsoft Visual C++ 2008 Express s aktualizací SP1 (webový instalační program)](https://go.microsoft.com/?linkid=7729279)  

Pokud jsou nainstalovány tyto produkty, **sada nástrojů platformy** vlastnost rozevírací seznam v **stránky vlastností** dialogové okno se automaticky aktualizuje a zobrazí dostupná modulové. Nyní můžete nejnovější verze sady Visual Studio k vytvoření projektů pro tyto starší verze sady nástrojů bez převádění nebo jejich aktualizace.

## <a name="see-also"></a>Viz také

[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Vylepšení shody C++ se sadou Visual Studio 2017](../cpp-conformance-improvements-2017.md)  
