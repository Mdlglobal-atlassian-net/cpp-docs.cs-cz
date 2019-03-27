---
title: Konfigurace CMake ladicími relacemi v sadě Visual Studio
ms.date: 03/21/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 712728247c439c38d5e640118fc153cf89647c80
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356163"
---
# <a name="configure-cmake-debugging-sessions"></a>Konfigurace CMake ladicími relacemi

Všechny spustitelné cílů CMake jsou uvedeny v **položku při spuštění** rozevírací seznam v **Obecné** nástrojů. Spuštění ladicí relace, vyberte jeden a spuštění ladicího programu.

![Rozevírací seznam položky po spuštění CMake](media/cmake-startup-item-dropdown.png "CMake spouštěcí položka rozevíracího seznamu")

Můžete také spustit relaci ladění z nabídky CMake.

## <a name="customize-debugger-settings"></a>Přizpůsobení nastavení ladicího programu

Chcete-li přizpůsobit nastavení ladicího programu pro libovolný spustitelný cíl CMake ve vašem projektu, klikněte pravým tlačítkem na konkrétní soubor CMakeLists.txt a vyberte **nastavení ladění a spouštění**. (Nebo vyberte cílovou třídu v **zobrazení cílů** v **Průzkumníka řešení**.) Při výběru cílové CMake v podnabídce soubor s názvem **souboru launch.vs.json** se vytvoří. Tento soubor se předem načtou informace o cílové CMake, které jste vybrali a můžete zadat další parametry jako argumenty programu nebo typ ladicího programu. Odkazovat v libovolné klávesy **CMakeSettings.json** soubor, adresa s `cmake.` v **souboru launch.vs.json**. Následující příklad ukazuje jednoduchý **souboru launch.vs.json** soubor, který si vyžádá hodnotu `remoteCopySources` klíče v **CMakeSettings.json** souboru pro aktuálně vybranou konfiguraci:

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

Po uložení **souboru launch.vs.json** souboru, bude vytvořena položka ve **položku při spuštění** rozevírací seznam s novým názvem. Úpravou **souboru launch.vs.json** soubor, můžete vytvořit mnoho konfiguraci ladění, kolik potřebujete pro libovolný počet cílů CMake.

## <a name="support-for-cmakesettings-variables"></a>Podpora pro proměnné cmakesettings na pozici

 **Launch.vs.JSON** podporuje proměnné, které jsou deklarovány v **CMakeSettings.json** (viz níže) a, která se vztahují na aktuálně vybrané konfigurace. Je také klíč s názvem `currentDir`, který nastaví aktuální adresář spouštění aplikace:

```json
{
  "type": "default",
  "project": "CMakeLists.txt",
  "projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Při spuštění aplikace, hodnota `currentDir` je podobný

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```
## <a name="see-also"></a>Viz také:

[Projekty CMake v sadě Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)<br/>
[Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Vlastní nastavení sestavení CMake](customize-cmake-settings.md)<br/>
[Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referenční dokumentace ke konfiguraci CMake předdefinované](cmake-predefined-configuration-reference.md)<br/>