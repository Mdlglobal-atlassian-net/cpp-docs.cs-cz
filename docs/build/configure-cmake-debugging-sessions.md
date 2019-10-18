---
title: Konfigurace relací ladění CMake v sadě Visual Studio
ms.date: 03/21/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 41f53c0c3ea46a8a1aa11215968aaee6c13c2dea
ms.sourcegitcommit: e33126222c418daf977533ea9e2819d99e0d7b8d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72534101"
---
# <a name="configure-cmake-debugging-sessions"></a>Konfigurace ladicích relací CMake

Všechny spustitelné cíle CMake se zobrazí v rozevíracím seznamu **spouštěcí položka** na panelu nástrojů **Obecné** . Chcete-li spustit relaci ladění, stačí vybrat jednu a spustit ladicí program.

![Rozevírací seznam pro položku po spuštění CMake](media/cmake-startup-item-dropdown.png "Rozevírací seznam pro položku po spuštění CMake")

Můžete také spustit relaci ladění z Průzkumník řešení. Nejprve přepněte na **zobrazení cíle cmake** v okně **Průzkumník řešení** .

![Tlačítko zobrazení cílů CMake](media/cmake-targets-view.png  "Položka nabídky zobrazení cílů CMake")

Potom klikněte pravým tlačítkem na jakýkoli spustitelný soubor a vyberte **ladit** nebo **ladit a spustit nastavení**. **Ladění** automaticky spustí ladění vybraného cíle na základě aktivní konfigurace. **Nastavení ladění a spouštění** otevře soubor *Launch. vs. JSON* a přidá novou konfiguraci ladění pro vybraný cíl.

## <a name="customize-debugger-settings"></a>Přizpůsobení nastavení ladicího programu

Chcete-li přizpůsobit nastavení ladicího programu pro kterýkoli spustitelný cíl CMake v projektu, klikněte pravým tlačítkem na konkrétní soubor CMakeLists. txt a vyberte **nastavení ladění a spuštění**. (Nebo vyberte cíl v **zobrazení cíle** v **Průzkumník řešení**.) Když v podnabídce vyberete cíl CMake, vytvoří se soubor s názvem **Launch. vs. JSON** . Tento soubor se předem naplní informacemi o vybraném cíli CMake a umožňuje zadat další parametry, jako jsou argumenty programu nebo typ ladicího programu. Chcete-li odkazovat na libovolný klíč v souboru **CMakeSettings. JSON** , před ním `cmake.` v souboru **Launch. vs. JSON**. Následující příklad ukazuje jednoduchý soubor **Launch. vs. JSON** , který se načte do hodnoty `remoteCopySources` klíč v souboru **CMakeSettings. JSON** pro aktuálně vybranou konfiguraci:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

Po uložení souboru **Launch. vs. JSON** se v rozevíracím seznamu **položka po spuštění** vytvoří položka s novým názvem. Úpravou souboru **Launch. vs. JSON** můžete vytvořit tolik konfigurací ladění, kolik chcete pro libovolný počet cílů cmake.

## <a name="support-for-cmakesettings-variables"></a>Podpora pro proměnné CMakeSettings

 **Launch. vs. JSON** podporuje proměnné deklarované v **CMakeSettings. JSON** (viz níže) a ty, které se vztahují k aktuálně vybrané konfiguraci. Má také klíč s názvem `currentDir`, který nastaví aktuální adresář aplikace pro spuštění pro místní projekt:

```json
{
  "type": "default",
  "project": "CMakeLists.txt",
  "projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Když aplikaci spustíte, hodnota `currentDir` je podobná

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```

Klíč "CWD" nastaví aktuální adresář spouštějící aplikace pro vzdálený projekt. Výchozí hodnota je $ {debugInfo. defaultWorkingDirectory}, která se vyhodnotí jako. 

```cmd
/var/tmp/src/bfc6f7f4-4f0f-8b35-80d7-9198fa973fb9/Linux-Debug
```

## <a name="see-also"></a>Viz také:

[Projekty CMake v sadě Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)<br/>
[Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Vlastní nastavení sestavení CMake](customize-cmake-settings.md)<br/>
[Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Odkaz na předdefinovaný konfigurační odkaz CMake](cmake-predefined-configuration-reference.md)<br/>
