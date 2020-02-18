---
title: Podpora Clang/LLVM v projektech sady Visual Studio CMake
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: a71f9dc98f74247788558d1b7dccf3e117f43072
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416025"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Podpora Clang/LLVM v projektech sady Visual Studio CMake

::: moniker range="<=vs-2017"

Podpora Clang je k dispozici v aplikaci Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Pomocí sady Visual Studio s Clang můžete upravovat a ladit C++ projekty CMAK, které cílí na Windows nebo Linux.

**Windows**: Visual Studio 2019 verze 16,1 zahrnuje podporu pro úpravy, sestavování a ladění pomocí CLANG/LLVM v projektech CMAK cílících na Windows.

**Linux**: u projektů Linux cmake není nutná žádná speciální podpora sady Visual Studio. Clang můžete nainstalovat pomocí Správce balíčků distribuce a přidat příslušné příkazy do souboru CMakeLists. txt.

## <a name="install"></a>Instalace

Pro nejlepší podporu IDE v aplikaci Visual Studio doporučujeme použít nejnovější nástroje kompilátoru Clang pro Windows. Pokud je ještě nemáte, můžete je nainstalovat tak, že otevřete instalační program pro Visual Studio a zvolíte  **C++ Clang kompilátor pro Windows** v části **vývoj pro stolní počítače C++ s** volitelnými součástmi. Pokud používáte vlastní instalaci Clang, podívejte se na  **C++ součást Clang-CL pro V142 Build Tools** .

![Instalace součásti Clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Vytvořit novou konfiguraci

Přidání nové konfigurace Clang do projektu CMake:

1. V **Průzkumník řešení** klikněte pravým tlačítkem na CMakeLists. txt a vyberte **Nastavení cmake pro projekt**.

1. V části **Konfigurace**stiskněte tlačítko **Přidat konfiguraci** :

   ![Přidat konfiguraci](media/cmake-add-config-icon.png)

1. Zvolte požadovanou konfiguraci Clang (Všimněte si, že pro Windows a Linux jsou k dispozici samostatné konfigurace Clang) a potom stiskněte **Vybrat**:

   ![Konfigurace CMake Clang](media/cmake-clang-configuration.png)

1. K provedení úprav této konfigurace použijte **Editor nastavení cmake**. Další informace najdete v tématu [přizpůsobení nastavení sestavení cmake v sadě Visual Studio](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Úprava existující konfigurace pro použití Clang

Pokud chcete upravit existující konfiguraci, aby používala Clang, postupujte podle těchto kroků:

1. V **Průzkumník řešení** klikněte pravým tlačítkem na CMakeLists. txt a vyberte **Nastavení cmake pro projekt**.

1. V části **Obecné** vyberte rozevírací seznam sady **nástrojů** a zvolte požadovanou sadu nástrojů Clang:

   ![Sada nástrojů CMake Clang](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Vlastní umístění Clang

Ve výchozím nastavení Visual Studio hledá Clang na dvou místech:

- Systému Interně nainstalovaná kopie Clang/LLVM, která je součástí instalačního programu sady Visual Studio.
- (Windows a Linux) Proměnná prostředí PATH.

Můžete zadat jiné umístění nastavením **CMAKE_C_COMPILER** a **CMAKE_CXX_COMPILER** proměnné cmake v **Nastavení cmake**:

![Sada nástrojů CMake Clang](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Režimy kompatibility Clang

V případě konfigurací systému Windows aplikace CMak ve výchozím nastavení vyvolá Clang v režimu [Clang-CL](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) a odkazy s implementací standardní knihovny od společnosti Microsoft. Ve výchozím nastavení se **Clang-CL. exe** nachází v `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

Tyto hodnoty můžete upravit v **Nastavení cmake** v části **proměnné a mezipaměť pro cmake**. Klikněte na **Zobrazit pokročilé proměnné**. Přejděte dolů k části najít **CMAKE_CXX_COMPILER**a potom klikněte na tlačítko **Procházet** a zadejte jinou cestu kompilátoru.

## <a name="edit-build-and-debug"></a>Úpravy, sestavování a ladění

Po nastavení konfigurace Clang můžete sestavit a ladit projekt. Visual Studio zjistí, že používáte kompilátor Clang a poskytuje IntelliSense, zvýrazňování, navigaci a další funkce pro úpravy. V **okno výstup**se zobrazují chyby a upozornění.

Při ladění můžete používat zarážky, vizualizaci paměti a dat a většinu dalších funkcí ladění. Některé funkce závislé na kompilátoru, jako je například upravit a pokračovat, nejsou pro konfigurace Clang k dispozici.

![Ladění CMake Clang](media/clang-debug-visualize.png)

::: moniker-end
