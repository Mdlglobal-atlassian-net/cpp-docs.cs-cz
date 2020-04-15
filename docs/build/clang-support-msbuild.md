---
title: Podpora clang/LLVM v projektech Visual Studia Visual Studio
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 8d7d7fec979d3e7b8f665e56094ee1c309e3b686
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323119"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Podpora Clang/LLVM v projektech sady Visual Studio

::: moniker range="<=vs-2017"

Podpora clang pro projekty CMake a MSBuild je k dispozici v sadě Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 verze 16.2 s Clang můžete upravit, sestavit a ladit projekty C++ Visual Studio (MSBuild), které cílí na Windows nebo Linux.

## <a name="install"></a>Instalace

Pro nejlepší podporu IDE v sadě Visual Studio doporučujeme používat nejnovější nástroje kompilátoru Clang pro Windows. Pokud je ještě nemáte, můžete je nainstalovat tak, že otevřete Instalační službu Sady Visual Studio a vyberete **nástroje C++ Clang pro Windows** ve vývoji plochy s volitelnými součástmi **c++.** Pokud dáváte přednost použití existující instalace Clang v počítači, zvolte **C++ Clang-cl pro nástroje sestavení v142.** volitelnou součást. Standardní knihovna Microsoft C++ aktuálně vyžaduje alespoň Clang 8.0.0; přiložená verze clangu bude automaticky aktualizována, aby zůstala aktuální s aktualizacemi v implementaci standardní knihovny společností Microsoft.

![Instalace komponenty Clang](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Konfigurace projektu systému Windows pro použití nástrojů Clang

Chcete-li nakonfigurovat projekt sady Visual Studio tak, aby používal clang, klepněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a zvolte **Vlastnosti**. Obvykle byste měli nejprve zvolit **všechny konfigurace** v horní části dialogového okna. Potom v části **Obecná** > **sada nástrojů platformy**zvolte **LLVM (clang-cl)** a pak **OK**.

![Instalace komponenty Clang](media/clang-msbuild-prop-page.png)

Pokud používáte nástroje Clang, které jsou dodávány s Visual Studio, žádné další kroky jsou požadovány. U projektů systému Windows visual studio ve výchozím nastavení vyvolá Clang v režimu [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) a odkazy na implementaci Microsoft standardní knihovny. Ve výchozím nastavení je **clang-cl.exe** umístěn v . `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`

Pokud používáte vlastní instalaci Clang, můžete buď upravit**vlastnosti** >  **projektu** > **VC++ DIrectories** > **Vlastnosti** > **konfigurace spustitelné adresáře** přidáním vlastní `LLVMInstallDir` kořen instalace Clang jako první adresář tam, nebo změnit hodnotu vlastnosti. Další informace naleznete [v tématu Nastavení vlastního umístění LLVM.](#custom_llvm_location)

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Konfigurace projektu Linuxu pro použití nástrojů Clang

Pro linuxové projekty visual studio používá front-end kompatibilní s Clang GCC. Vlastnosti projektu a téměř všechny příznaky kompilátoru jsou identické.

Konfigurace projektu Visual Studia Linux pro použití clangu:

1. Klikněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a zvolte **Vlastnosti**.
1. Obvykle byste měli nejprve zvolit **všechny konfigurace** v horní části dialogového okna.
1. V části **Obecná** > **sada nástrojů platformy**zvolte **WSL_Clang_1_0** pokud používáte podsystém Windows pro Linux, nebo **Remote_Clang_1_0,** pokud používáte vzdálený počítač nebo virtuální počítač.
1. Stiskněte **OK**.

![Instalace komponenty Clang](media/clang-msbuild-prop-page.png)

V systému Linux visual studio ve výchozím nastavení používá první umístění Clang, které narazí v prostředí PATH vlastnost. Pokud používáte vlastní instalaci Clang, musíte `LLVMInstallDir` změnit hodnotu vlastnosti nebo jinak nahradit cestu v části**Vlastnosti** >  **projektu** > **VC++ DIrectories** > **Vlastnosti konfigurace** > **spustitelné adresáře**. Další informace naleznete [v tématu Nastavení vlastního umístění LLVM.](#custom_llvm_location)

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a>Nastavení vlastního umístění LLVM

Vlastní cestu pro llvm pro jeden nebo více projektů můžete nastavit vytvořením souboru *Directory.build.props* a přidáním tohoto souboru do kořenové složky libovolného projektu. Můžete jej přidat do kořenové složky řešení a použít ji na všechny projekty v řešení. Soubor by měl vypadat takto (ale nahradit skutečnou cestu):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>Nastavení dalších vlastností, úpravy, sestavení a ladění

Po nastavení konfigurace Clang znovu klepněte pravým tlačítkem myši na uzel projektu a zvolte **Znovu načíst projekt**. Nyní můžete vytvořit a ladit projekt pomocí clang nástroje. Visual Studio zjistí, že používáte kompilátor Clang a poskytuje Technologie IntelliSense, zvýraznění, navigaci a další funkce úprav. Chyby a upozornění jsou zobrazeny ve **výstupním okně**. Stránky vlastností projektu pro konfiguraci Clang jsou velmi podobné těm pro MSVC, ačkoli některé funkce závislé na kompilátoru, jako je například Upravit a Pokračovat, nejsou k dispozici pro konfigurace Clang. Chcete-li nastavit možnost kompilátoru clang nebo linkeru, která není k dispozici na stránkách vlastností, můžete ji přidat ručně na stránkách vlastností v části Další**možnosti****příkazového řádku** >  **Vlastnosti** > konfigurace**C/C++ (nebo Linker).** > 

Při ladění můžete použít zarážky, vizualizaci paměti a dat a většinu dalších funkcí ladění.  

![Clang ladění](media/clang-debug-msbuild.png)

::: moniker-end
