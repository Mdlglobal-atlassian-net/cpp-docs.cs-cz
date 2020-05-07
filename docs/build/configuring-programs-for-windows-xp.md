---
title: Konfigurace programů pro Windows XP
description: Jak nainstalovat a používat sady nástrojů C++ Windows XP v sadě Visual Studio.
ms.date: 03/16/2020
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 92364d7fd25ac617baacc125b279fb0ee9c92f62
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440477"
---
# <a name="configuring-programs-for-windows-xp"></a>Konfigurace programů pro Windows XP

Sada Visual Studio podporuje několik sad nástrojů platformy. To znamená, že je možné cílit na operační systémy a běhové knihovny, které nejsou podporovány výchozí sadou nástrojů. Například přepnutím sady nástrojů platformy můžete použít kompilátor Visual Studio 2017 C++ k vytváření aplikací, které cílí na systémy Windows XP a Windows Server 2003. Můžete také použít starší sady nástrojů platformy k údržbě binárního kódu kompatibilního s binárním prostředím a stále využívat nejnovější funkce integrovaného vývojového prostředí (IDE) sady Visual Studio.

::: moniker range="vs-2019"

Sada nástrojů V142 dodaná v sadě Visual Studio 2019 nezahrnuje podporu pro vytváření kódu pro systém Windows XP. Podpora pro vývoj v systému Windows XP pomocí sady Visual Studio 2017 v141_xp sada nástrojů je k dispozici jako možnost jednotlivé komponenty v Instalační program pro Visual Studio.

::: moniker-end

## <a name="install-the-windows-xp-platform-toolset"></a>Instalace sady nástrojů platformy systému Windows XP

::: moniker range="<=vs-2017"

Chcete-li získat sadu nástrojů a součásti sady Visual Studio 2017 pro cílení na systémy Windows XP a Windows Server 2003, spusťte Instalační program pro Visual Studio. Při úvodní instalaci sady Visual Studio nebo při změně existující instalace se ujistěte, že je vybrána možnost **vývojář pro stolní počítače s C++** . V seznamu volitelných komponent pro tuto úlohu zvolte možnost **Podpora Windows XP pro C++** a pak zvolte možnost **nainstalovat** nebo **Upravit**.

::: moniker-end

::: moniker range="vs-2019"

Chcete-li získat v141_xp sadu nástrojů a součásti platformy pro cílení na systémy Windows XP a Windows Server 2003, spusťte Instalační program pro Visual Studio. Při počáteční instalaci sady Visual Studio nebo při změně existující instalace se ujistěte, že je vybraná možnost **vývoj pro Desktop s C++** . Na kartě **jednotlivé komponenty** v části **kompilátory, nástroje sestavení a moduly runtime**zvolte možnost **podpora C++ Windows XP pro vs 2017 (v141) Tools \[(nepoužívané)** a pak zvolte **nainstalovat** nebo **Upravit**.

::: moniker-end

## <a name="windows-xp-targeting-experience"></a>Prostředí cílení na systém Windows XP

Sada nástrojů platformy Windows XP, která je součástí sady Visual Studio, je verze sady Windows 7 SDK, ale používá kompilátor Visual Studio 2017 C++. Také nakonfiguruje vlastnosti projektu na příslušné výchozí hodnoty, například specifikace kompatibilního linkeru pro cílení na nižší úrovni. V systému Windows XP a Windows Server 2003 lze spustit pouze aplikace klasické pracovní plochy systému Windows, které jsou vytvořeny pomocí sady nástrojů platformy Windows XP. Tyto aplikace můžou běžet taky v novějších operačních systémech Windows.

### <a name="to-target-windows-xp"></a>Cílení na systém Windows XP

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.

1. V dialogovém okně **stránky vlastností** projektu vyberte možnost **vlastnosti** > konfigurace**Obecné**. Nastavte vlastnost **Sada nástrojů platformy** na upřednostňovanou sadu nástrojů pro systém Windows XP. Například vyberte možnost **Visual Studio 2017-Windows XP (v141_xp)** , chcete-li vytvořit kód pro systémy Windows XP a windows Server 2003 pomocí kompilátoru jazyka Microsoft C++ v aplikaci Visual Studio 2017.

### <a name="c-runtime-support"></a>Podpora modulu runtime C++

Společně se sadou nástrojů platformy Windows XP obsahuje několik knihoven i podporu modulu runtime pro systémy Windows XP a Windows Server 2003. Tyto knihovny jsou: knihovna runtime jazyka C (CRT), standardní knihovna C++, knihovna ATL (Active Template Library), knihovna Concurrency Runtime (ConCRT), knihovna paralelních vzorů (PPL), knihovna Microsoft Foundation Class (MFC) a C++ AMP (urychlené programování v jazyce C++). Minimální podporované verze pro tyto operační systémy: Windows XP Service Pack 3 (SP3) pro x86, Windows XP Service Pack 2 (SP2) pro x64 a Windows Server 2003 Service Pack 2 (SP2) pro x86 i x64.

Tyto knihovny jsou podporovány sadami nástrojů platformy nainstalovanými sadou Visual Studio v závislosti na cíli:

|Knihovna|Výchozí sada nástrojů platformy cílící na desktopové aplikace pro Windows|Výchozí sada nástrojů platformy cílící na Store apps|Sada nástrojů platformy Windows XP cílící na systém Windows XP, Windows Server 2003|
|---|---|---|---|
|CRT|×|×|×|
|Standardní knihovna C++|×|×|×|
|ATL|×|×|×|
|ConCRT/PPL|×|×|×|
|MFC|×||×|
|C++ AMP|×|×||

> [!NOTE]
> Aplikace napsané v jazyce C++/CLI a cílí na .NET Framework 4 spuštěné v systémech Windows XP a Windows Server 2003.

### <a name="differences-between-the-toolsets"></a>Rozdíly mezi sadami nástrojů

Kvůli rozdílům v podpoře platforem a knihoven není prostředí pro vývoj aplikací, které používá sadu nástrojů platformy Windows XP, tak kompletní jako u aplikací, které používají výchozí sadu nástrojů platformy sady Visual Studio.

- **Funkce jazyka C++**

   V aplikacích, které používají sadu nástrojů platformy v110\_XP, jsou podporovány pouze funkce jazyka C++ implementované v sadě Visual Studio 2012. V aplikacích, které používají sadu nástrojů platformy v120\_XP, jsou podporovány pouze funkce jazyka C++ implementované v Visual Studio 2013. V aplikacích, které používají sadu nástrojů platformy v140\_XP, jsou podporovány pouze funkce jazyka C++ implementované v sadě Visual Studio 2015. V aplikacích, které používají sadu nástrojů platformy v141\_XP, jsou podporovány pouze funkce jazyka C++ implementované v sadě Visual Studio 2017. Sada Visual Studio používá odpovídající kompilátor při sestavení pomocí starších sad nástrojů platformy. Použijte nejnovější sadu nástrojů platformy Windows XP pro využití dalších funkcí jazyka C++ implementovaných v této verzi kompilátoru.

- **Vzdálené ladění**

   Remote Tools for Visual Studio nepodporuje vzdálené ladění v systému Windows XP nebo Windows Server 2003. Chcete-li ladit aplikaci místně nebo vzdáleně v systému Windows XP nebo Windows Server 2003, použijte ladicí program ze starší verze sady Visual Studio. Je podobný ladění aplikace v systému Windows Vista, která je cílem modulu runtime sady nástrojů platformy, ale ne vzdáleného cíle ladění.

- **Statická analýza**

   Sady nástrojů platformy Windows XP nepodporují statickou analýzu, protože poznámky SAL pro sadu Windows 7 SDK a běhové knihovny jsou nekompatibilní. Statickou analýzu můžete provádět i v aplikaci, která podporuje systém Windows XP nebo Windows Server 2003. Dočasně přepněte řešení, aby se pro tuto analýzu zacíleno na výchozí sadu nástrojů platformy, a pak přepněte zpátky na sadu nástrojů platformy Windows XP a sestavte aplikaci.

- **Ladění grafiky DirectX**

   Vzhledem k tomu, že ladicí program grafiky nepodporuje rozhraní API Direct3D 9, nejde ho použít k ladění aplikací, které používají Direct3D v systému Windows XP nebo Windows Server 2003. Pokud ale aplikace implementuje alternativní zobrazovací jednotku na základě rozhraní API Direct3D 10 nebo Direct3D 11, můžete k diagnostice problémů použít ladicí program grafiky.

- **Sestavování HLSL**

   Sada nástrojů Windows XP nekompiluje ve výchozím nastavení soubory zdrojového kódu HLSL. Chcete-li kompilovat soubory HLSL, Stáhněte a nainstalujte sadu SDK rozhraní DirectX z června 2010 a pak nastavte adresáře VC projektu tak, aby obsahovaly. Další informace najdete v části "sada SDK pro DirectX neregistrují cesty include/Library se sadou Visual Studio 2010" na [stránce pro stažení sady SDK z června 2010 DirectX](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
