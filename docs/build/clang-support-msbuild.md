---
title: Podpora Clang/LLVM v projektech Visual studia Visual studia
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
# <a name="clangllvm-support-in-visual-studio-projects"></a>Podpora Clang/LLVM v projektech Visual studia

::: moniker range="<=vs-2017"

Podpora Clang pro projekty CMake a MSBuild je k dispozici v sadě Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Pomocí sady Visual Studio 2019 verze 16,2 s Clang můžete upravovat, sestavovat a ladit projekty Visual studia C++ (MSBuild), které cílí na Windows nebo Linux.

## <a name="install"></a>Instalace

Pro nejlepší podporu IDE v aplikaci Visual Studio doporučujeme použít nejnovější nástroje kompilátoru Clang pro Windows. Pokud je ještě nemáte, můžete je nainstalovat tak, že otevřete Instalační program pro Visual Studio a zvolíte možnost **C++ Clang Tools for Windows** v části **vývoj pro stolní počítače pomocí** volitelných komponent c++. Pokud dáváte přednost použití existující instalace Clang na vašem počítači, vyberte **Nástroje pro sestavení V142 v jazyce C++ Clang-CL.** volitelná součást. Standardní knihovna Microsoft C++ aktuálně vyžaduje aspoň Clang 8.0.0; sada Instalovaná verze Clang se automaticky aktualizuje, aby byla aktuální s aktualizacemi v implementaci standardní knihovny od Microsoftu.

![Instalace součásti Clang](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Konfigurace projektu Windows pro použití nástrojů Clang

Chcete-li nakonfigurovat projekt sady Visual Studio tak, aby používal Clang, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **vlastnosti**. Obvykle byste nejdřív měli zvolit **všechny konfigurace** v horní části dialogového okna. Pak v části **Obecná** > **Sada nástrojů platformy**zvolte **LLVM (Clang-CL)** a pak klikněte na **OK**.

![Instalace součásti Clang](media/clang-msbuild-prop-page.png)

Pokud používáte nástroje Clang, které jsou součástí sady Visual Studio, nejsou nutné žádné další kroky. V případě projektů Windows aplikace Visual Studio ve výchozím nastavení vyvolá Clang v režimu [Clang-CL](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) a odkazy s implementací standardní knihovny od společnosti Microsoft. Ve výchozím nastavení se **Clang-CL. exe** nachází v `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

Pokud používáte vlastní instalaci Clang, můžete buď upravit**vlastnosti** >  **projektu** > **VC + + adresáře** > **vlastnosti** > konfigurace**spustitelné adresáře** přidáním vlastního kořenového adresáře instalace Clang jako prvního adresáře, nebo změnit hodnotu `LLVMInstallDir` vlastnosti. Další informace najdete v tématu [nastavení vlastního umístění LLVM](#custom_llvm_location) .

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Konfigurace projektu se systémem Linux pro použití nástrojů Clang

Pro projekty se systémem Linux používá Visual Studio front-end kompatibilní s Clang RSZ. Vlastnosti projektu a skoro všechny příznaky kompilátoru jsou identické.

Konfigurace projektu sady Visual Studio pro systém Linux pro použití Clang:

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte **vlastnosti**.
1. Obvykle byste nejdřív měli zvolit **všechny konfigurace** v horní části dialogového okna.
1. V části **Obecná** > **Sada nástrojů platformy**vyberte možnost **WSL_Clang_1_0** , pokud používáte podsystém Windows pro Linux, nebo **Remote_Clang_1_0** Pokud používáte vzdálený počítač nebo virtuální počítač.
1. Stiskněte **OK**.

![Instalace součásti Clang](media/clang-msbuild-prop-page.png)

V systému Linux používá Visual Studio ve výchozím nastavení první umístění Clang, ke kterému dojde ve vlastnosti prostředí PATH. Pokud používáte vlastní instalaci Clang, musíte `LLVMInstallDir` změnit hodnotu vlastnosti nebo jinak dosadit cestu v části**vlastnosti** >  **projektu** > **VC + + adresáře** > **vlastnosti** > konfigurace**spustitelné adresáře**. Další informace najdete v tématu [nastavení vlastního umístění LLVM](#custom_llvm_location) .

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a>Nastavení vlastního umístění LLVM

Můžete nastavit vlastní cestu pro LLVM pro jeden nebo více projektů vytvořením souboru *Directory. Build. props* a přidáním tohoto souboru do kořenové složky libovolného projektu. Můžete ji přidat do kořenové složky řešení a použít ji pro všechny projekty v řešení. Soubor by měl vypadat nějak takto (ale nahraďte svou vlastní cestu):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>Nastavení dalších vlastností, úpravy, sestavení a ladění

Po nastavení konfigurace Clang klikněte znovu pravým tlačítkem myši na uzel projektu a vyberte možnost **znovu načíst projekt**. Nyní můžete sestavit a ladit projekt pomocí nástrojů Clang. Visual Studio zjistí, že používáte kompilátor Clang a poskytuje IntelliSense, zvýrazňování, navigaci a další funkce pro úpravy. V **okno výstup**se zobrazují chyby a upozornění. Stránky vlastností projektu pro konfiguraci Clang jsou velmi podobné těm pro MSVC, i když některé funkce závislé na kompilátoru, jako je například upravit a pokračovat, nejsou k dispozici pro konfigurace Clang. Chcete-li nastavit kompilátor Clang nebo možnost linkeru, která není k dispozici na stránkách vlastností, můžete ji přidat ručně na stránce vlastností v části **vlastnosti** > konfigurace**C/C++ (nebo linker)** > .**Další možnosti**naleznete v**příkazovém řádku** > .

Při ladění můžete používat zarážky, vizualizaci paměti a dat a většinu dalších funkcí ladění.  

![Clang ladění](media/clang-debug-msbuild.png)

::: moniker-end
