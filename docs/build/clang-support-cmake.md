---
title: Podpora Clang/LLVM v projektech Visual Studio CMake
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 46bfe788c13df3a37dd9cba654d16cfe4c3fe177
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323184"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Podpora Clang/LLVM v projektech Visual Studio CMake

::: moniker range="<=vs-2017"

Podpora Clang je k dispozici ve Visual Studiu 2019.

::: moniker-end

::: moniker range="vs-2019"

Pomocí sady Visual Studio s clangmůžete upravovat a ladit c++ CMake projekty, které cílí na Windows nebo Linux.

**Windows**: Visual Studio 2019 verze 16.1 obsahuje podporu pro úpravy, vytváření a ladění s Clang/LLVM v projektech CMake zaměřených na Windows.

**Linux**: Pro linuxové projekty CMake není vyžadována žádná speciální podpora sady Visual Studio. Clang můžete nainstalovat pomocí správce balíčků distro a přidat příslušné příkazy do souboru CMakeLists.txt.

## <a name="install"></a>Instalace

Pro nejlepší podporu IDE v sadě Visual Studio doporučujeme používat nejnovější nástroje kompilátoru Clang pro Windows. Pokud je ještě nemáte, můžete je nainstalovat tak, že otevřete Instalační službu Sady Visual Studio a zvolíte **kompilátor C++ Clang pro Windows** ve vývoji plochy s volitelnými součástmi **c++.** Při použití vlastní instalace Clang zkontrolujte **c++ Clang-cl pro v142 sestavení nástroje** komponenty.

![Instalace komponenty Clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Vytvoření nové konfigurace

Přidání nové konfigurace Clang do projektu CMake:

1. Klepněte pravým tlačítkem myši na soubor CMakeLists.txt v **Průzkumníku řešení** a zvolte **nastavení CMake pro projekt**.

1. V části **Konfigurace**stiskněte tlačítko **Přidat konfiguraci:**

   ![Přidání konfigurace](media/cmake-add-config-icon.png)

1. Zvolte požadovanou konfiguraci Clang (všimněte si, že pro Windows a Linux jsou k dispozici samostatné konfigurace Clang), pak stiskněte **tlačítko Vybrat**:

   ![Konfigurace CMake Clang](media/cmake-clang-configuration.png)

1. Chcete-li provést změny této konfigurace, použijte **Editor nastavení CMake**. Další informace naleznete v [tématu Customize CMake build settings in Visual Studio](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Úprava existující konfigurace pro použití Clang

Chcete-li upravit existující konfiguraci tak, aby používala clang, postupujte takto:

1. Klepněte pravým tlačítkem myši na soubor CMakeLists.txt v **Průzkumníku řešení** a zvolte **nastavení CMake pro projekt**.

1. V části **Obecné** vyberte rozevírací soubor **sady nástrojů** a zvolte požadovanou sadu nástrojů Clang:

   ![Sada nástrojů CMake Clang](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Vlastní umístění clang

Ve výchozím nastavení Visual Studio hledá Clang na dvou místech:

- (Windows) Interně nainstalovaná kopie Clang/LLVM, která je dodávána s instalačním programem sady Visual Studio.
- (Windows a Linux) Proměnná prostředí PATH.

Jiné umístění můžete zadat nastavením proměnných **CMAKE_C_COMPILER** a **CMAKE_CXX_COMPILER** CMake v **nastavení CMake**:

![Sada nástrojů CMake Clang](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Režimy kompatibility clang

Pro konfigurace systému Windows CMake ve výchozím nastavení vyvolá Clang v režimu [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) a odkazy na implementaci Microsoft standardní knihovny. Ve výchozím nastavení je **clang-cl.exe** umístěn v . `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`

Tyto hodnoty můžete upravit v **nastavení CMake** v části **Proměnné CMake a mezipaměť**. Klepněte na tlačítko **Zobrazit rozšířené proměnné**. Posuňte se dolů a **vyhledejte CMAKE_CXX_COMPILER**a potom klepnutím na tlačítko **Procházet** určete jinou cestu kompilátoru.

## <a name="edit-build-and-debug"></a>Úpravy, sestavení a ladění

Po nastavení konfigurace Clang můžete vytvořit a ladit projekt. Visual Studio zjistí, že používáte kompilátor Clang a poskytuje Technologie IntelliSense, zvýraznění, navigaci a další funkce úprav. Chyby a upozornění jsou zobrazeny ve **výstupním okně**.

Při ladění můžete použít zarážky, vizualizaci paměti a dat a většinu dalších funkcí ladění. Některé funkce závislé na kompilátoru, jako je například Upravit a Pokračovat, nejsou k dispozici pro konfigurace Clang.

![CMake Clang ladění](media/clang-debug-visualize.png)

::: moniker-end
