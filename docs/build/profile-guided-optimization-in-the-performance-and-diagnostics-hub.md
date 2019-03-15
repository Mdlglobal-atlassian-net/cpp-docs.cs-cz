---
title: Optimalizace na základě profilu v centru pro výkon a diagnostiku
ms.date: 11/19/2018
ms.assetid: dc3a1914-dbb6-4401-bc63-10665a8c8943
ms.openlocfilehash: e1aaf64c18ebde29e6ea0d6b4b6bdad66f21a435
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823035"
---
# <a name="profile-guided-optimization-in-the-visual-studio-2013-performance-and-diagnostics-hub"></a>Profilově řízené optimalizace výkon sady Visual Studio 2013 a Centrum diagnostiky

Pokud používáte Visual Studio 2013, zjednodušuje profilově řízené optimalizace pro modul plug-in centru pro výkon a Diagnostika Visual C++ základě profilu optimalizaci prostředí pro vývojáře. Je možné [stáhnout modul plug-in](https://marketplace.visualstudio.com/items?itemName=ProfileGuidedOptimizationTeam.ProfileGuidedOptimizationforVisualC) z webu Visual Studio. Modul plug-in není podporována v novějších verzích sady Visual Studio.

Profil s asistencí řízené optimalizace (PGO) vám pomůže vytvořit sestavení x86 a x64 nativní aplikace, které jsou optimalizovány pro uživatele způsob, jak pracovat s nimi. PGO je vícefázový proces: Vytvoření aplikace sestavení, který je instrumentováno pro profilování a pak proveďte "školení." To znamená spustit instrumentovanou aplikaci prostřednictvím běžných scénářů interakci uživatele. Uložte zaznamenaná data profilování a znovu sestavte aplikaci s použitím výsledky a provede optimalizaci celého programu. I když tyto kroky můžete provést jednotlivě v sadě Visual Studio nebo na příkazovém řádku, modul plug-in PGO centralizuje a zjednodušuje proces. PGO modul plug-in nastaví všechny požadované možnosti, provede vás těmito možnostmi každý krok, ukazuje analýzy a potom výsledky použije ke konfiguraci sestavení pro optimalizaci jednotlivých funkcí pro velikost nebo rychlost. Modul plug-in PGO také umožňuje snadno znovu spustit aplikaci trénování a aktualizovat data sestavení optimalizace, protože po provedení změny kódu.

## <a name="prerequisites"></a>Požadavky

Je nutné [stáhnout modul plug-in PGO](https://marketplace.visualstudio.com/items?itemName=ProfileGuidedOptimizationTeam.ProfileGuidedOptimizationforVisualC) a nainstalujte ho v sadě Visual Studio před použitím v Centrum pro výkon a Diagnostika.

## <a name="walkthrough-using-the-pgo-plug-in-to-optimize-an-app"></a>Návod: Pomocí modulu Plug-in PGO pro optimalizaci aplikace

Nejprve vytvoříte základní aplikaci Win32 klasické pracovní plochy v sadě Visual Studio. Pokud už máte nativní aplikaci, kterou chcete optimalizovat, můžete ji použít a tento krok přeskočit.

### <a name="to-create-an-app"></a>K vytvoření aplikace

1. V panelu nabídky zvolte **souboru**, **nový**, **projektu**.

1. V levém podokně **nový projekt** dialogového okna rozbalte **nainstalováno**, **šablony**, **Visual C++** a pak vyberte  **MFC**.

1. V prostředním podokně vyberte **aplikace knihovny MFC**.

1. Zadejte název projektu – například **SamplePGOProject**– v **název** pole. Zvolte **OK** tlačítko.

1. Na **přehled** stránku **Průvodce aplikací knihovny MFC** dialogového okna zvolte **Dokončit** tlačítko.

Dále nastavte konfiguraci sestavení vaší aplikace na verzi na připraveno pro PGO sestavení a školení kroky.

### <a name="to-set-the-build-configuration"></a>Chcete-li nastavit konfiguraci sestavení

1. V panelu nabídky zvolte **sestavení**, **nástroje Configuration Manager**.

1. V **nástroje Configuration Manager** dialogového okna zvolte **aktivní konfigurace řešení** tlačítko rozevíracího seznamu a vyberte **vydání**. Zvolte **Zavřít** tlačítko.

Otevřete centru pro výkon a Diagnostika – v panelu nabídky zvolte **analyzovat**, **výkon a Diagnostika**. Otevře se stránka relace diagnostiky, obsahující analytické nástroje, které jsou k dispozici pro váš typ projektu.

![PGO v Centrum pro výkon a Diagnostika](media/pgofig0hub.png "PGO v Centrum pro výkon a Diagnostika")

V **dostupných nástrojů**, vyberte **optimalizace na základě profilu** zaškrtávací políčko. Zvolte **Start** tlačítko pro spuštění modulu plug-in PGO.

![Úvodní stránka PGO](media/pgofig1start.png "PGO úvodní stránka")

**Optimalizace na základě profilu** stránka popisuje kroky, které modul plug-in používá ke zlepšení výkonu vaší aplikace. Zvolte **Start** tlačítko.

![Stránka instrumentace PGO](media/pgofig2instrument.png "PGO instrumentace stránky")

V **instrumentace** části použijete **školení je zpočátku povoleno** – možnost zvolit, jestli se mají zahrnout jako součást přípravy fáze spuštění vaší aplikace. Pokud tato možnost není vybraná, trénovacích dat, není zaznamenána v běžící aplikaci instrumentované dokud explicitně povolit školení.

Zvolte **instrumentace** tlačítko k sestavení aplikace s využitím speciální sadu možností kompilátoru. Kompilátor vloží test pokyny v generovaném kódu. Tyto pokyny zaznamenávat data profilace během fáze školení.

![Stránka instrumentované sestavení PGO](media/pgofig3build.PNG "PGO instrumentované sestavení stránky")

Po dokončení instrumentované sestavení vaší aplikace je aplikace spuštěna automaticky.

Pokud během sestavování dojde k nějaké chyby nebo varování, opravte je a klikněte na tlačítko **restartovat sestavení** restartovat instrumentované sestavení.

Při spuštění aplikace, můžete použít **spustit Trénovací** a **pozastavení školení** odkazů v **školení** části k řízení, když se zaznamená profilování informace. Můžete použít **zastavit aplikaci** a **spustit** odkazy na zastavte a restartujte aplikaci.

![Stránka školení PGO](media/pgofig4training.PNG "PGO školení stránky")

Při školení, projděte si vaše uživatelské scénáře k zaznamenání, kterou je potřeba optimalizovat kód modulu plug-in PGO profilování informací. Po dokončení se školení, zavřete vaši aplikaci nebo zvolte **zastavit aplikaci** odkaz. Zvolte **analyzovat** tlačítko pro spuštění analýzy kroku.

Po dokončení analýzy **analýzy** oddíl se zobrazí sestava profilace informací, která se zaznamenala v průběhu fáze školení uživatelský scénář. Tato sestava slouží k prozkoumání, který funguje jako většina a strávený nejvíce času v aplikaci. Modul plug-in PGO používá informace k určení, která aplikace fungovat tak, aby optimalizovat rychlost a které optimalizovat pro velikost. Modul plug-in PGO nakonfiguruje optimalizace sestavení k vytvoření aplikace nejrychlejší, nejmenší pro uživatelské scénáře, které jste si poznamenali během cvičení.

![Stránka analýza PGO](media/pgofig5analyze.png "PGO analýzy stránky")

Pokud školení zachycena očekávaná profilování informace, můžete zvolit **uložit změny** k uložení dat analyzovaný profilu ve vašem projektu a optimalizovat budoucí sestavení. Chcete-li zahodit data profilu a vzdělávání začít od začátku, zvolte **znovu školení**.

Soubor dat profilu je uložen ve vašem projektu v **PGO Trénovacích dat** složky. Tato data slouží k řízení nastavení optimalizace kompilátoru sestavení ve vaší aplikaci.

![PGO datového souboru v Průzkumníku řešení](media/pgofig6data.png "PGO datového souboru v Průzkumníku řešení")

Po dokončení analýzy PGO modul plug-in nastaví možnosti sestavení ve vašem projektu a selektivně optimalizovat aplikaci během kompilace pomocí dat profilu. Můžete nadále upravovat a vytvářet aplikace s využitím stejných dat profilu. Při vytváření aplikace, výstupní sestavení sestavy, jak mnoho funkcí a pokyny se optimalizovalo pomocí dat profilu.

![PGO výstup diagnostiky](media/pgofig7diagnostics.png "PGO výstup diagnostiky")

Pokud provedete změny významné kódu během vývoje, budete muset přeučování vaši aplikaci, abyste získali nejlepší optimalizace. Doporučujeme, abyste přeučování vaší aplikace, když výstup sestavení hlásí, že méně než 80 procent funkcí nebo pokyny se optimalizovalo pomocí dat profilu.