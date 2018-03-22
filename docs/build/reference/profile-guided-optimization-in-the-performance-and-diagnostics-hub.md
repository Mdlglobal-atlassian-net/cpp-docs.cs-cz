---
title: Optimalizace výkonu a Centrum diagnostiky na základě profilu | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: article
dev_langs:
- C++
ms.assetid: dc3a1914-dbb6-4401-bc63-10665a8c8943
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 98933630a2cc8b5dfb5c4d1d7b24ceac3ec2937b
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="profile-guided-optimization-in-the-visual-studio-2013-performance-and-diagnostics-hub"></a>Optimalizace v nástroji Visual Studio 2013 výkon a diagnostiku na základě profilu

Pokud používáte Visual Studio 2013, optimalizace na základě profilu pro Visual C++ v výkon a diagnostiku modulu plug-in zjednodušuje možnosti optimalizace na základě profilu pro vývojáře. Můžete [stáhnout modul plug-in](http://go.microsoft.com/fwlink/p/?LinkId=327915) z webu sady Visual Studio. Modul plug-in není podporována v novějších verzích sady Visual Studio.

Profil na základě optimalizace (PGO) vám pomůže vytvořit sestavení x86 a x64 nativní aplikace, které jsou optimalizované pro způsobem uživatelé komunikovat s nimi. PGO je vícekrokový proces: vytvoření sestavení aplikace, která je instrumentována pro profilaci, a pak provedete "školení." To znamená spusťte instrumentovaného aplikaci prostřednictvím běžné scénáře interakci uživatele. Uložit zaznamenaná data profilování a pak je znovu vytvořte vaší aplikace pomocí výsledky do Průvodce optimalizace celého programu. I když tyto kroky můžete provést jednotlivě v sadě Visual Studio nebo na příkazovém řádku, modul plug-in PGO centralizuje a zjednodušuje proces. Modul plug-in PGO nastaví všechny požadované možnosti, vás provede každý krok, analýzy se dozvíte a pak použije výsledky konfigurace sestavení za účelem optimalizace jednotlivé funkce pro velikost a rychlost. Modul plug-in PGO také snadno znovu školení vaší aplikace a aktualizovat data sestavení optimalizace, když změníte kód.

## <a name="prerequisites"></a>Požadavky

Je nutné [stáhnout modul plug-in PGO](http://go.microsoft.com/fwlink/p/?LinkId=327915) a nainstalujte ho v sadě Visual Studio, abyste mohli používat v výkon a diagnostiku.

## <a name="walkthrough-using-the-pgo-plug-in-to-optimize-an-app"></a>Návod: Použití modulu Plug-in PGO za účelem optimalizace aplikace

Nejdřív vytvoříte základní desktopové aplikaci Win32 v sadě Visual Studio. Pokud již máte nativní aplikaci, kterou chcete optimalizovat, můžete ho použít a tento krok přeskočit.

### <a name="to-create-an-app"></a>K vytvoření aplikace

1. Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.

1. V levém podokně **nový projekt** dialogové okno, rozbalte seznam **nainstalovaná**, **šablony**, **Visual C++**a potom vyberte  **MFC**.

1. V prostředním podokně vyberte **aplikace knihovny MFC**.

1. Zadejte název projektu – například **SamplePGOProject**– v **název** pole. Vyberte **OK** tlačítko.

1. Na **přehled** stránky **Průvodce aplikací knihovny MFC** dialogovém okně vyberte **Dokončit** tlačítko.

Dále nastavte konfiguraci sestavení vaší aplikace na verzi připravte PGO sestavení a školení kroky.

### <a name="to-set-the-build-configuration"></a>Chcete-li nastavit konfiguraci sestavení

1. Na řádku nabídek zvolte **sestavení**, **nástroje Configuration Manager**.

1. V **nástroje Configuration Manager** dialogovém okně vyberte **aktivní konfigurace řešení** tlačítko rozevíracího seznamu a vyberte **verze**. Vyberte **Zavřít** tlačítko.

Otevřete Centrum diagnostiky a výkonu – v řádku nabídek zvolte **analyzovat**, **výkonu a Diagnostika**. Otevře se stránka diagnostiky relace, který má analytické nástroje, které jsou k dispozici pro typ vašeho projektu.

![PGO v výkon a diagnostiku](../../build/reference/media/pgofig0hub.png "PGOFig0Hub")

V **nástroje**, vyberte **optimalizace na základě profilu** zaškrtávací políčko. Vyberte **spustit** tlačítko Spustit PGO modulu plug-in.

![Úvodní stránka PGO](../../build/reference/media/pgofig1start.png "PGOFig1Start")

**Optimalizace na základě profilu** stránka popisuje kroky, které modul plug-in používá ke zlepšení výkonu vaší aplikace. Vyberte **spustit** tlačítko.

![Stránka instrumentace PGO](../../build/reference/media/pgofig2instrument.png "PGOFig2Instrument")

V **instrumentace** části použijete **školení původně zapnutá** možnost vyberte, zda má být zahrnut jako součást přípravy fázi spuštění vaší aplikace. Pokud tuto možnost nevyberete, není ve spuštěné aplikaci instrumentovaného zaznamená Cvičná data, dokud je explicitně povolit školení.

Vyberte **nástrojem** tlačítko k sestavení aplikace pomocí speciální sadu možností kompilátoru. Kompilátor vloží testu pokyny v generovaného kódu. Tyto pokyny záznam data profilování během fáze školení.

![Stránka instrumentovaného sestavení PGO](../../build/reference/media/pgofig3build.PNG "PGOFig3Build")

Po dokončení instrumentovaného sestavení aplikace po spuštění automaticky.

Dojde-li žádné chyby nebo upozornění během sestavení, opravte je a potom zvolte **restartujte sestavení** restartovat instrumentovaného sestavení.

Při spuštění aplikace můžete použít **spustit školení** a **pozastavení školení** odkazů v **školení** části řídit, kdy se zaznamenává profilace informace. Můžete použít **zastavení aplikace** a **spustit aplikaci** odkazy na zastavte a restartujte aplikaci.

![Stránka školení PGO](../../build/reference/media/pgofig4training.PNG "PGOFig4Training")

Během cvičení, projděte vaše uživatelské scénáře pro zachycení profilování informace, které modul plug-in PGO musí optimalizovat kód. Pokud jste vyplnili školení, zavřete aplikaci nebo zvolte **zastavení aplikace** odkaz. Vyberte **analyzovat** tlačítko Spustit krok analýzy.

Po dokončení analýzy **Analysis** část ukazuje sestavu profilování informace, které byla zaznamenána během fáze školení uživatelský scénář. Tato sestava slouží k prozkoumání, který funguje jako většina a strávený nejvíce času v aplikaci. Modul plug-in PGO používá informace k určení, které aplikace funkce na optimalizovat pro rychlost a který za účelem optimalizace pro velikost. Modul plug-in PGO nakonfiguruje optimalizace sestavení vytvoření nejmenší, nejrychlejší aplikace pro uživatelské scénáře, které jste si poznamenali během cvičení.

![Stránka analýza PGO](../../build/reference/media/pgofig5analyze.png "PGOFig5Analyze")

Pokud se školení zaznamenat očekávané profilování informace, můžete zvolit **uložit změny** k uložení dat analyzovaných profilu ve vašem projektu a optimalizovat budoucí sestavení. Zahodit data profilu a školení, začít znovu od začátku, zvolte **vrátit školení**.

Soubor dat profilu je uložen v projektu v **PGO Cvičná Data** složky. Tato data se používají pro řízení nastavení optimalizace kompilátoru sestavení v aplikaci.

![PGO datový soubor v Průzkumníku řešení](../../build/reference/media/pgofig6data.png "PGOFig6Data")

Po dokončení analýzy modul plug-in PGO nastaví možnosti sestavení v projektu pro použití data profilu selektivně optimalizace aplikace během kompilace. Můžete upravit a vytvoření aplikace se stejnými daty profilu. Když je integrovaná aplikace, jeho výstup sestavy, kolik funkce a pokyny byly optimalizovány s použitím data profilu.

![PGO výstup diagnostiky](../../build/reference/media/pgofig7diagnostics.png "PGOFig7Diagnostics")

Pokud provedete změny významné kódu během vývoje, budete muset přeučování aplikaci, kterou chcete získat nejlepší optimalizace. Doporučujeme, abyste přeučování vaší aplikace, když výstupu sestavení hlásí, že byly menší než 80 procent funkce nebo pokyny optimalizované pomocí data profilu.