---
title: 'Postupy: Změna cílové architektury a sady nástrojů'
ms.custom: conceptual
ms.date: 07/24/2019
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
ms.openlocfilehash: c5e7172fea06f6b455422fb023a0b6462b5c4103
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964902"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>Postupy: Změna cílové architektury a sady nástrojů

Můžete upravit soubor projektu sady Visual C++ Studio pro cílení na různé verze sady C++ nástrojů platformy, Windows SDK a .NET Framework (C++pouze projekty/CLI). Ve výchozím nastavení používá projektový systém verzi .NET Framework a verzi sady nástrojů, která odpovídá verzi sady Visual Studio, kterou používáte k vytvoření projektu. Můžete upravit všechny tyto hodnoty v souboru. vcxproj tak, abyste mohli použít stejný základ kódu pro každý cíl kompilace.

## <a name="platform-toolset"></a>Sada nástrojů platformy

Sada nástrojů platformy se skládá z C++ kompilátoru (CL. exe) a Linker (Link. exe) společně s knihovnami C/C++ Standard. Vzhledem k tomu, že sada Visual Studio 2015, hlavní verze sady nástrojů zůstala v rozmezí 14, což znamená, že projekty zkompilované se sadou Visual Studio 2019 nebo Visual Studio 2017 jsou s projekty kompilovanými se sadou Visual Studio 2015 kompatibilní. Dílčí verze se aktualizovala o 1 pro každou verzi od Visual Studia 2015:

- Visual Studio 2015: v140
- Visual Studio 2017: v141
- Visual Studio 2019: V142

Tyto sady nástrojů podporují .NET Framework 4,5 a novější.

Visual Studio také podporuje více cílů pro C++ projekty. Pomocí integrovaného vývojového prostředí sady Visual Studio můžete upravovat a sestavovat projekty, které byly vytvořeny pomocí starších verzí sady Visual Studio, aniž by bylo nutné je upgradovat, aby používaly novou verzi sady nástrojů. V počítači musíte mít nainstalované starší sady nástrojů. Další informace najdete v tématu [Jak používat nativní cílení na více platforem v aplikaci Visual Studio](../porting/use-native-multi-targeting.md). Například v sadě Visual Studio 2015 můžete *cílit* .NET Framework 2,0, ale je nutné použít starší sadu nástrojů, která ji podporuje.

## <a name="target-framework-ccli-project-only"></a>Cílová architektura (C++jenom projekt/CLI)

Když změníte cílovou architekturu, změňte také sadu nástrojů platformy na verzi, která rozhraní podporuje. Chcete-li například cílit na .NET Framework 4,5, je nutné použít sadu nástrojů kompatibilní platformy, jako je například Visual Studio 2015 (v140), Visual Studio 2013 (v120) nebo Visual Studio 2012 (v110). Sadu nástrojů platformy [Windows 7,1 SDK](https://www.microsoft.com/download/details.aspx?id=8279) můžete použít k cílení na .NET Framework 2,0, 3,0, 3,5 a 4 a platformy x86/x64.

Cílovou platformu můžete rozšířit ještě tak, že vytvoříte vlastní sadu nástrojů platformy. Další informace najdete v tématu [ C++ nativní cílení na více](https://devblogs.microsoft.com/cppblog/c-native-multi-targeting/) platforem na C++ blogu vizuálu.

### <a name="to-change-the-target-framework"></a>Změna cílového rozhraní .NET Framework

1. V aplikaci Visual Studio v **Průzkumník řešení**vyberte svůj projekt. V panelu nabídek otevřete nabídku **projekt** a vyberte možnost **Uvolnit projekt**. Tím se uvolní soubor projektu (. vcxproj) pro váš projekt.

   > [!NOTE]
   >  Během C++ úprav souboru projektu v aplikaci Visual Studio nelze načíst projekt. Můžete však použít jiný editor, například Poznámkový blok, pro úpravu souboru projektu, když je projekt načten v aplikaci Visual Studio. Visual Studio zjistí, že se soubor projektu změnil, a zobrazí výzvu k opětovnému načtení projektu.

1. Na panelu nabídek vyberte **soubor**, **otevřít**, **soubor**. V dialogovém okně **otevřít soubor** přejděte do složky projektu a pak otevřete soubor projektu (. vcxproj).

1. V souboru projektu vyhledejte položku pro cílovou verzi rozhraní .NET Framework. Například pokud je váš projekt navržen pro použití .NET Framework 4,5, vyhledejte `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` v prvku `<PropertyGroup Label="Globals">` elementu `<Project>`. Pokud `<TargetFrameworkVersion>` prvek není k dispozici, projekt nepoužívá .NET Framework a není vyžadována žádná změna.

1. Změňte hodnotu na požadovanou verzi rozhraní, například v 3.5 nebo v 4.6.

1. Uložte změny a zavřete Editor.

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a pak zvolte možnost **znovu načíst projekt**.

1. Chcete-li ověřit změnu, v **Průzkumník řešení**klikněte pravým tlačítkem myši a otevřete místní nabídku pro projekt (ne pro vaše řešení) a poté zvolte možnost **vlastnosti** , čímž otevřete dialogové okno **stránky vlastností** projektu. V levém podokně dialogového okna rozbalte položku **Vlastnosti konfigurace** a pak vyberte možnost **Obecné**. Ověřte, zda **verze rozhraní .NET Target Framework** zobrazuje novou verzi rozhraní .NET Framework.

### <a name="to-change-the-platform-toolset"></a>Změna sady nástrojů platformy

1. V aplikaci Visual Studio v **Průzkumník řešení**otevřete místní nabídku pro váš projekt (ne pro vaše řešení) a pak zvolte **vlastnosti** . otevře se dialogové okno **stránky vlastností** projektu.

1. V dialogovém okně **stránky vlastností** otevřete rozevírací seznam **Konfigurace** a vyberte možnost **všechny konfigurace**.

1. V levém podokně dialogového okna rozbalte položku **Vlastnosti konfigurace** a pak vyberte možnost **Obecné**.

1. V pravém podokně vyberte **sadu nástrojů platformy** a v rozevíracím seznamu vyberte požadovanou sadu nástrojů. Pokud jste například nainstalovali sadu nástrojů sady Visual Studio 2010, vyberte sadu **Visual studio 2010 (V100)** a použijte ji pro svůj projekt.

1. Klikněte na tlačítko **OK** .

## <a name="see-also"></a>Viz také:

[MSBuild na příkazovém řádku –C++](msbuild-visual-cpp.md)
