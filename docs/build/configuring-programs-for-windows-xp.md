---
title: Konfigurace programů pro systém Windows XP | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a846ea5508173ce0e383b1c4b8798b896ae5be0e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="configuring-programs-for-windows-xp"></a>Konfigurace programů pro systém Windows XP

Protože Visual Studio podporuje více modulové platformy, můžete určit cílovou operačních systémů a runtime knihovny, které nepodporují výchozí sady nástrojů. Například přepínání sada nástrojů platformy, můžete pomocí C ++ 11 a C ++ 14, vylepšení C ++ 17 jazyk podporuje – kompilátor Visual C++ v sadě Visual Studio k vytvoření aplikace cílených [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Můžete také použít starší platformy modulové zachovat starší verze kódu binární kompatibilní a nadále využívat výhody nejnovějších funkcí Visual Studio IDE.

## <a name="install-the-windows-xp-platform-toolset"></a>Instalace sady nástrojů systému Windows XP
Sada nástrojů platformy a součásti cíl [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Visual Studio 2017, spusťte instalační program Visual Studio. Po počáteční instalaci sady Visual Studio, nebo když zvolíte **upravit** Pokud chcete upravit existující instalace, ujistěte se, že **vývoj aplikací s jazykem C++** je vybrané úlohy. V seznamu volitelné součásti pro tuto úlohu, vyberte **Windows XP podporu pro jazyk C++** a potom zvolte **nainstalovat** nebo **upravit**.

## <a name="windows-xp-targeting-experience"></a>Cílení na prostředí Windows XP

Sada nástrojů platformy systému Windows XP, která je zahrnutá v sadě Visual Studio je verze [!INCLUDE[win7](../build/includes/win7_md.md)] SDK, ale používá aktuální kompilátoru C++. Nakonfiguruje taky vlastnosti projektu odpovídající výchozí hodnoty, například specifikace kompatibilní linkeru pro cílení na nižší úrovni. Pouze Windows aplikace klasické pracovní plochy, které jsou vytvořené pomocí sady nástrojů systému Windows XP spustit na [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], ale tyto aplikace můžete spustit také na novější operační systémy Windows.

#### <a name="to-target-windows-xp"></a>Cíl, Windows XP

1. V **Průzkumníku řešení**, otevřete místní nabídku pro svůj projekt a potom zvolte **vlastnosti**.

1. V **stránky vlastností** dialogu pro projekt, v části **vlastnosti konfigurace** > **Obecné**, nastavte **sada nástrojů platformy** vlastnost požadované sady nástrojů systému Windows XP. Například vyberte **2017 Visual Studio – Windows XP (v141_xp)** k vytvoření kódu pro [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] pomocí kompilátoru Microsoft Visual C++ 2017.

### <a name="c-runtime-support"></a>Podpora C++ runtime

Sada nástrojů platformy systému Windows XP C Runtime Library (CRT), standardní knihovna C++, Active Template Library (ATL), Concurrency Runtime Library (ConCRT), paralelní vzory knihovna PPL (), Microsoft Foundation Class Library (MFC) a C++ AMP (C++ Accelerated masivní programování) knihovny zahrnují podporu runtime pro [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Pro tyto operační systémy, minimální podporované verze jsou [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 3 (SP3) pro x86, [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 2 (SP2) pro x64, a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Service Pack 2 (SP2) pro x86 a x64.

Tyto knihovny podporuje modulové platformy nainstalovat Visual Studio, v závislosti na cíl:

|Knihovna|Výchozí platformy nástrojů cílení plochy aplikací pro Windows|Výchozí zaměřená na úložiště aplikací sada nástrojů platformy|Cílení na sada nástrojů platformy systému Windows XP [!INCLUDE[winxp](../build/includes/winxp_md.md)], [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]|
|---|---|---|---|
|CRT|X|X|X|
|Standardní knihovna C++|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> Aplikace, které jsou napsané v jazyce C + +/ CLI a cílové rozhraní .NET Framework 4 běžet na [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)].

### <a name="differences-between-the-toolsets"></a>Rozdíly mezi modulové

Vzhledem k rozdílům v podpora platformy a knihovna není vývojového prostředí pro aplikace, které používají sady nástrojů systému Windows XP jako u aplikací, které používají sady nástrojů Visual Studio výchozí jako dokončené.

- **Funkce jazyka C++**

   Jsou podporovány pouze funkcí jazyka C++ v sadě Visual Studio 2012 implementována v aplikacích, které používají v110\_xp sada nástrojů platformy. Jsou podporovány pouze funkcí jazyka C++ v sadě Visual Studio 2013 implementována v aplikacích, které používají v120\_xp sada nástrojů platformy. Jsou podporovány pouze funkcí jazyka C++ v sadě Visual Studio 2015 implementována v aplikacích, které používají v140\_xp sada nástrojů platformy. Visual Studio použije odpovídající kompilátoru k sestavení pomocí starší modulové platformy. Použijte nejnovější sada nástrojů platformy systému Windows XP využívat další funkce jazyka C++ implementovaná v této verzi kompilátoru.

- **Vzdálené ladění**

   Nástroje pro vzdálenou pro Visual Studio nepodporuje vzdáleného ladění na [!INCLUDE[winxp](../build/includes/winxp_md.md)] nebo [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. K ladění aplikace, když je spuštěn na [!INCLUDE[winxp](../build/includes/winxp_md.md)] nebo [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], ladicí program ze starší verze sady Visual Studio můžete použít k ladění ho místně nebo vzdáleně. To se podobá postupu při ladění aplikace v systému Windows Vista, který je cílem runtime sada nástrojů platformy, ale není vzdáleného ladění cíl.

- **Statické analýzy**

   Modulové platformy systému Windows XP nepodporují statické analýzy, protože poznámek SAL pro [!INCLUDE[win7](../build/includes/win7_md.md)] SDK a knihovny modulu runtime nejsou kompatibilní. Pokud chcete provádět analýzy statické na aplikaci, která podporuje [!INCLUDE[winxp](../build/includes/winxp_md.md)] nebo [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], můžete dočasně přepnout řešení, jehož cílem je sada nástrojů platformy výchozí k provedení analýzy a pak přejděte zpátky do sady nástrojů systému Windows XP k sestavení aplikace.

- **Ladění grafiky DirectX**

     Protože ladicího programu grafiky nepodporuje rozhraní API Direct3D – 9, nelze použít k ladění aplikací, které používají Direct3D – na [!INCLUDE[winxp](../build/includes/winxp_md.md)] nebo [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Pokud aplikace implementuje alternativní zobrazovací jednotky, která používá Direct3D – 10 nebo 11 Direct3D – rozhraní API, ladicího programu grafiky můžete použít k diagnostikování problémů s používáním těchto rozhraní API.

- **Vytváření HLSL**

   Ve výchozím nastavení sady nástrojů systému Windows XP nekompiluje HLSL soubory zdrojového kódu. Ke kompilaci HLSL souborů, stažení a instalaci 2010 června DirectX SDK a potom nastavte projekt je VC adresáře, které chcete zahrnout. Další informace najdete v tématu "DirectX SDK nezaregistruje cesty zahrnutí/knihoven sadou Visual Studio 2010" oddílu [června 2010 stránky pro stažení sady SDK rozhraní DirectX](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
