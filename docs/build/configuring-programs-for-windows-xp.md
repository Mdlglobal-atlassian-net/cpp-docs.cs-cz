---
title: Konfigurace programů pro Windows XP
ms.date: 02/02/2018
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 989a4e2c7e91c05498902bf1c5cb9d838ee47c3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273799"
---
# <a name="configuring-programs-for-windows-xp"></a>Konfigurace programů pro Windows XP

Vzhledem k tomu, že Visual Studio podporuje více sad nástrojů platformy, můžete směrovat operačních systémů a knihovny runtime, které nejsou podporované výchozí sady nástrojů. Například přepnutím sada nástrojů platformy vám pomůže C ++ 11, C ++ 14 a C ++ 17 jazyka vylepšení a kompilátorem MSVC v sadě Visual Studio podporuje vytváření aplikací určených pro Windows XP a Windows Server 2003. Můžete také použít starší sad nástrojů platformy zachovat starší verze kódu binárně kompatibilní a stále využívat nejnovější funkce integrovaného vývojového prostředí sady Visual Studio.

## <a name="install-the-windows-xp-platform-toolset"></a>Nainstalovat sadu nástrojů platformy Windows XP

Pokud chcete získat sadu nástrojů platformy a komponenty na cíl Windows XP a Windows Server 2003 v sadě Visual Studio 2017, spusťte instalační program sady Visual Studio. Při počáteční instalaci sady Visual Studio, nebo když zvolíte **změnit** k úpravě stávající instalace, ujistěte se, že **vývoj desktopových aplikací pomocí C++** vybrané úlohy. V seznamu volitelných součástí pro danou úlohu, vyberte **podpora Windows XP pro C++** a klikněte na tlačítko **nainstalovat** nebo **změnit**.

## <a name="windows-xp-targeting-experience"></a>Windows XP cílení

Sada nástrojů platformy Windows XP, který je součástí sady Visual Studio je verze sady Windows 7 SDK, ale používá aktuální kompilátoru C++. Také nakonfiguruje vlastnosti projektu vhodné výchozí hodnoty, například specifikace kompatibilní linkeru pro cílení na nižší úrovni. Jenom aplikace klasické pracovní plochy Windows, které jsou vytvořeny pomocí nástrojů pro platformy Windows XP běží na Windows XP a Windows Server 2003, ale tyto aplikace můžete spustit také na novější operační systémy Windows.

#### <a name="to-target-windows-xp"></a>Na cíl Windows XP

1. V **Průzkumníka řešení**, otevřete místní nabídku pro váš projekt a klikněte na tlačítko **vlastnosti**.

1. V **stránky vlastností** dialogové okno pro projekt, v části **vlastnosti konfigurace** > **Obecné**, nastavte **Sadanástrojůplatformy** vlastnost k požadované sadě nástrojů Windows XP. Například zvolte **Visual Studio 2017 – Windows XP (v141_xp)** vytvořit kód pro Windows XP a Windows Server 2003 pomocí Microsoft Visual C++ kompilátoru 2017.

### <a name="c-runtime-support"></a>Podpora modulu CLR C++

Společně se sada nástrojů platformy Windows XP, knihovny Runtime jazyka C (CRT), standardní knihovna C++, aktivní šablony knihovny (ATL), knihovna prostředí Runtime souběžnosti (ConCRT), knihovna paralelních vzorů (PPL), třída knihovny MFC (Microsoft Foundation) a C++ AMP (C++ Accelerated Massive programování) knihovny zahrnují podporu runtime pro Windows XP a Windows Server 2003. Minimální podporované verze jsou pro tyto operační systémy Windows XP Service Pack 3 (SP3) pro x86, Windows XP Service Pack 2 (SP2) pro x64 a Windows Server 2003 Service Pack 2 (SP2) pro x86 i x64.

Tyto knihovny jsou podporovány sad nástrojů platformy, které instaluje sada Visual Studio, v závislosti na cíl:

|Knihovna|Výchozí sada nástrojů cílení Windows desktopové aplikace pro platformu|Výchozí aplikace Store cílení sadu nástrojů platformy|Sada nástrojů platformy Windows XP, které cílí na Windows XP, Windows Server 2003|
|---|---|---|---|
|CRT|X|X|X|
|Standardní knihovna C++|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> Aplikace, které jsou napsané v C++/rozhraní příkazového řádku a cílové rozhraní .NET Framework 4 běží na Windows XP a Windows Server 2003.

### <a name="differences-between-the-toolsets"></a>Rozdíly mezi sady nástrojů

Vývojové prostředí pro aplikace, které používají sadu nástrojů platformy Windows XP není tak úplné jako u aplikací, které používají výchozí sady nástrojů platformy Visual Studio, z důvodu rozdílů v podpora platformy a knihovny.

- **Funkce jazyka C++**

   Jsou podporovány pouze funkcí jazyka C++ implementovány v aplikaci Visual Studio 2012 v aplikacích, které používají v110\_xp sada nástrojů platformy. Jsou podporovány pouze funkcí jazyka C++ implementovány v sadě Visual Studio 2013 v aplikacích, které používají v120\_xp sada nástrojů platformy. Pouze funkcí jazyka C++ implementovány v sadě Visual Studio 2015 jsou podporovány v aplikacích, které používají v140\_xp sada nástrojů platformy. Visual Studio používá odpovídající kompilátoru k sestavení pomocí starší sad nástrojů platformy. Můžete využít výhod dalších funkcí jazyka C++ implementovány v této verzi kompilátoru nejnovější sada nástrojů platformy Windows XP.

- **Vzdálené ladění**

   Nástroje Remote Tools for Visual Studio nepodporuje vzdálené ladění na Windows XP nebo Windows Server 2003. Chcete-li ladit aplikaci, když je spuštěná na Windows XP nebo Windows Server 2003, vám pomůže ladicího programu ze starší verze sady Visual Studio místně nebo vzdáleně ho ladit. To se podobá prostředí ladění aplikace v systému Windows Vista, což je cílový modul runtime sady nástrojů platformy, ale ne cíl vzdáleného ladění.

- **Statické analýzy**

   Sad nástrojů platformy Windows XP nepodporují statickou analýzu, protože poznámky SAL pro Windows 7 SDK a knihoven modulu runtime nejsou kompatibilní. Pokud chcete provést Statická analýza v aplikaci, která podporuje Windows XP nebo Windows Server 2003, můžete dočasně přepněte řešení pro cílení na platformy výchozí sadu nástrojů k provedení analýzy a pak přepněte zpět do sady nástrojů platformy Windows XP k sestavení aplikace.

- **Ladění grafiky DirectX**

   Protože ladicí program grafiky nepodporuje rozhraní API Direct3D 9, nelze použít k ladění aplikace, které používají rozhraní Direct3D na Windows XP nebo Windows Server 2003. Pokud aplikace implementuje alternativní renderer, který používá rozhraní Direct3D 10 nebo rozhraní Direct3D 11 API, ladicí program grafiky můžete použít k diagnostice problémů s použitím těchto rozhraní API.

- **Vytváření HLSL**

   Ve výchozím nastavení sada nástrojů Windows XP nezkompiluje HLSL souborů se zdrojovým kódem. Pro kompilaci souborů HLSL, stáhněte a nainstalujte červen 2010 je rozhraní DirectX SDK a pak nastavte projekt VC adresáře ho. Další informace najdete v tématu "rozhraní DirectX SDK nezaregistruje cesty zahrnutí nebo knihovnu, sadou Visual Studio 2010" část [červen 2010 stránku pro stažení rozhraní DirectX SDK](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
