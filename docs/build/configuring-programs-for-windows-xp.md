---
title: "Konfigurace programů pro systém Windows XP | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff80109c1f3a5e03ecb85406cdaea24804f96783
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="configuring-programs-for-windows-xp"></a>Konfigurace programů pro systém Windows XP
Protože Visual Studio podporuje více modulové platformy, můžete určit cílovou operačních systémů a runtime knihovny, které nepodporují výchozí sady nástrojů. Například přepínání sada nástrojů platformy, můžete pomocí C ++ 11 a C ++ 14, vylepšení C ++ 17 jazyk podporuje – kompilátor Visual C++ v sadě Visual Studio k vytvoření aplikace cílených [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Můžete také použít starší platformy modulové zachovat starší verze kódu binární kompatibilní a nadále využívat výhody nejnovějších funkcí Visual Studio IDE.  
  
> [!NOTE]
>  Pokud používáte [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)], je nutné nainstalovat [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] aktualizace 4 pro přidání podpory sada nástrojů platformy pro [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Ke stažení a instalaci kopii [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] aktualizace 4 najdete [Microsoft Visual Studio Express 2012 for Windows Desktop](http://go.microsoft.com/fwlink/p/?linkid=265464) na webu Microsoft Download Center. Poté nainstalujte [Visual Studio 2012 Update 4](http://go.microsoft.com/fwlink/p/?linkid=335900) získat sada nástrojů platformy v110_xp. Použijte službu Windows Update a získat nejnovější aktualizace softwaru po instalaci.  
  
## <a name="windows-xp-targeting-experience"></a>Cílení na prostředí Windows XP  
 Sada nástrojů platformy systému Windows XP, která je zahrnutá v sadě Visual Studio je verze [!INCLUDE[win7](../build/includes/win7_md.md)] SDK, která byla součástí [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)], ale používá aktuální kompilátoru C++. Nakonfiguruje taky vlastnosti projektu do příslušných výchozích hodnot – například specifikace kompatibilní linkeru pro cílení na nižší úrovni. Pouze Windows aplikace klasické pracovní plochy, které jsou vytvořené pomocí sady nástrojů systému Windows XP spustit na [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], ale tyto aplikace můžete spustit také na novější operační systémy Windows.  
  
#### <a name="to-target-windows-xp"></a>Cíl, Windows XP  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro svůj projekt a potom zvolte **vlastnosti**.  
  
2.  V **stránky vlastností** dialogu pro projekt, v části **vlastnosti konfigurace**, **Obecné**, nastavte **sada nástrojů platformy** Vlastnost požadované sady nástrojů systému Windows XP. Například vyberte **Visual Studio 2015 - Windows XP (PlatformToolset v140_xp)** k vytvoření kódu pro [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] pomocí kompilátoru Microsoft Visual C++ 2015.  
  
### <a name="c-runtime-support"></a>Podpora C++ runtime  
 Sada nástrojů platformy systému Windows XP C Runtime Library (CRT), standardní knihovna C++, Active Template Library (ATL), Concurrency Runtime Library (ConCRT), paralelní vzory knihovna PPL (), Microsoft Foundation Class Library (MFC) a C++ AMP (C++ Accelerated masivní programování) knihovny zahrnují podporu runtime pro [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Pro tyto operační systémy, minimální podporované verze jsou [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 3 (SP3) pro x86, [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 2 (SP2) pro x64, a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Service Pack 2 (SP2) pro x86 a x64.  
  
 Tyto knihovny podporuje modulové platformy nainstalovat Visual Studio, v závislosti na cíl:  
  
|Knihovna|Výchozí platformy nástrojů cílení plochy aplikací pro Windows|Výchozí cílení na sada nástrojů platformy [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikace|Cílení na sada nástrojů platformy systému Windows XP [!INCLUDE[winxp](../build/includes/winxp_md.md)],[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]|  
|-------------|-------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|  
|CRT|X|X|X|  
|Standardní knihovna C++|X|X|X|  
|ATL|X|X|X|  
|ConCRT/PPL|X|X|X|  
|MFC|X||X|  
|C++ AMP|X|X||  
  
> [!NOTE]
>  Aplikace, které jsou napsané v jazyce C + +/ CLI a cílové rozhraní .NET Framework 4 běžet na [!INCLUDE[winxp](../build/includes/winxp_md.md)] a [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)].  
  
### <a name="differences-between-the-toolsets"></a>Rozdíly mezi modulové  
 Vzhledem k rozdílům v podpora platformy a knihovna není vývojového prostředí pro aplikace, které používají sady nástrojů systému Windows XP jako u aplikací, které používají sady nástrojů Visual Studio výchozí jako dokončené.  
  
-   **Funkce jazyka C++**  
  
     Pouze funkcí jazyka C++ implementované v [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] jsou podporovány v aplikacích, které používají sada nástrojů platformy v110_xp. Pouze funkcí jazyka C++ implementované v [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] jsou podporovány v aplikacích, které používají sada nástrojů platformy v120_xp. Visual Studio použije odpovídající kompilátoru k sestavení pomocí starší modulové platformy. Použijte nejnovější sada nástrojů platformy systému Windows XP využívat další funkce jazyka C++ implementovaná v této verzi kompilátoru.  
  
-   **Vzdálené ladění**  
  
     Nástroje pro vzdálenou pro Visual Studio nepodporuje vzdáleného ladění na [!INCLUDE[winxp](../build/includes/winxp_md.md)] nebo [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. K ladění aplikace, když je spuštěn na [!INCLUDE[winxp](../build/includes/winxp_md.md)] nebo [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], ladicí program ze starší verze sady Visual Studio můžete použít k ladění ho místně nebo vzdáleně. To se podobá postupu při ladění aplikace v systému Windows Vista, který je cílem runtime sada nástrojů platformy, ale není vzdáleného ladění cíl.  
  
-   **Statické analýzy**  
  
     Modulové platformy systému Windows XP nepodporují statické analýzy, protože poznámek SAL pro [!INCLUDE[win7](../build/includes/win7_md.md)] SDK a knihovny modulu runtime nejsou kompatibilní. Pokud chcete provádět analýzy statické na aplikaci, která podporuje [!INCLUDE[winxp](../build/includes/winxp_md.md)] nebo [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], můžete dočasně přepnout řešení, jehož cílem je sada nástrojů platformy výchozí k provedení analýzy a pak přejděte zpátky do sady nástrojů systému Windows XP k sestavení aplikace.  
  
-   **Ladění grafiky DirectX**  
  
     Protože ladicího programu grafiky nepodporuje rozhraní API Direct3D – 9, nelze použít k ladění aplikací, které používají Direct3D – na [!INCLUDE[winxp](../build/includes/winxp_md.md)] nebo [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Pokud aplikace implementuje alternativní zobrazovací jednotky, která používá Direct3D – 10 nebo 11 Direct3D – rozhraní API, ladicího programu grafiky můžete použít k diagnostikování problémů s používáním těchto rozhraní API.  
  
-   **Vytváření HLSL**  
  
     Ve výchozím nastavení sady nástrojů systému Windows XP nekompiluje HLSL soubory zdrojového kódu. Ke kompilaci HLSL souborů, stažení a instalaci 2010 června DirectX SDK a potom nastavte projekt je VC adresáře, které chcete zahrnout. Další informace najdete v tématu "DirectX SDK nezaregistruje cesty zahrnutí/knihoven sadou Visual Studio 2010" oddílu [června 2010 stránky pro stažení sady SDK rozhraní DirectX](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).