---
title: Podpora clang/LLVM v projektech Visual Studio CMake
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++
ms.openlocfilehash: 6773d9cdb076ef305ba635306f3bc9c6575d2203
ms.sourcegitcommit: b233f05adae607f75815111006a771c432df5a9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67518166"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Podpora clang/LLVM v projektech Visual Studio CMake

::: moniker range="<=vs-2017"

Clang podpora je k dispozici v aplikaci Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Úpravy a ladění můžete použít Visual Studio s Clang C++ projekty CMake tento cíl Windows nebo Linux.

**Windows:** Visual Studio 2019 verze 16.1 zahrnuje podporu pro úpravy, sestavování a ladění pomocí Clang/LLVM v projektech CMake cílení na Windows. 

**Linux:** Pro projekty Linux CMake je nutné žádné speciální podporovat sady Visual Studio. Můžete nainstalovat pomocí Správce balíčků vaší distribuce Clang a přidejte do souboru CMakeLists.txt příslušnými příkazy.

## <a name="install"></a>Instalace

Pro nejlepší podpora integrovaného vývojového prostředí v sadě Visual Studio doporučujeme používat nejnovější kompilačních nástrojů Clang pro Windows. Pokud ještě nemáte ty, instalaci otevřete instalační program sady Visual Studio a zvolíte **Clang kompilátor pro Windows** pod **vývoj desktopových aplikací pomocí C++**  volitelné součásti.

![Instalace součásti clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Vytvořit novou konfiguraci

Chcete-li přidat novou konfiguraci Clang do projektu CMake:

1. Klikněte pravým tlačítkem na soubor CMakeLists.txt v **Průzkumníka řešení** a zvolte **nastavení CMake pro projekt**.

1. V části **konfigurace**, stiskněte **Přidat konfiguraci** tlačítka:

   ![Přidat konfiguraci](media/cmake-add-config-icon.png)

1. Zvolte požadovanou konfiguraci Clang (Všimněte si, že samostatné konfigurace Clang jsou k dispozici pro Windows a Linux), stiskněte klávesu **vyberte**:

   ![CMake, Clang konfigurace](media/cmake-clang-configuration.png)

1. Chcete-li provádět změny této konfigurace, použijte **Editor nastavení CMake**. Další informace najdete v tématu [nastavení v sadě Visual Studio sestavení přizpůsobit CMake](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Změnit existující konfiguraci použít Clang

Pokud chcete upravit existující konfigurace a použití Clang, postupujte takto:

1. Klikněte pravým tlačítkem na soubor CMakeLists.txt v **Průzkumníka řešení** a zvolte **nastavení CMake pro projekt**.

1. V části **Obecné** vyberte **nástrojů** rozevírací seznam a zvolte požadovaný sada nástrojů Clang:

   ![Sada nástrojů CMake Clang](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Vlastní umístění Clang

Ve výchozím nastavení Visual Studio vyhledá Clang na dvou místech:

- (Windows) Interně instalované kopie Clang/LLVM, který je součástí instalačního programu sady Visual Studio.
- (Windows nebo Linuxem) Proměnné prostředí PATH.

Můžete zadat jiné umístění tak, že nastavíte **CMAKE_C_COMPILER** a **CMAKE_CXX_COMPILER** proměnných CMake v **nastavení CMake**:

![Sada nástrojů CMake Clang](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang režimech kompatibility

Pro Windows konfigurací CMake ve výchozím nastavení spustí Clang v [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) režimu a propojení s Microsoft implementace standardní knihovny. Ve výchozím nastavení **clang cl.exe** se nachází v `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

 Můžete změnit tyto hodnoty **nastavení CMake** pod **CMake proměnné a mezipaměti**. Klikněte na tlačítko **zobrazit pokročilé proměnné**. Posuňte se dolů najít **CMAKE_CXX_COMPILER**, klikněte **Procházet** tlačítko a zadejte cestu ke kompilátoru jiný.

## <a name="edit-build-and-debug"></a>Úpravy, vytváření a ladění

Jakmile nastavíte konfigurační Clang, můžete vytvářet a ladit projekt. Sada Visual Studio zjistí, že používáte kompilátoru Clang a poskytuje technologii IntelliSense, navigace a dalších funkcí pro úpravy zvýraznění. V zobrazené chyby a upozornění **okno výstup**.

Při ladění, můžete použít zarážky, paměti a vizualizace dat a většina jiných funkcí ladění. Některé funkce kompilátoru závislé, například upravit a pokračovat nejsou k dispozici pro Clang konfigurace.

![CMake Clang ladění](media/clang-debug-visualize.png)

::: moniker-end
