---
title: Vlastnosti ladicího programu Android (C++)
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 23fd871f030593607cf374870b96e09d8bc2da7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374201"
---
# <a name="android-debugger-properties"></a>Vlastnosti ladicího programu Android

| Vlastnost | Popis | Choices |
|--|--|--|
| Typ ladicího programu | Určuje, který typ kódu se má ladit. | **Pouze nativní**<br /><br />**Pouze Java** |
| Cíl ladění | Určuje emulátor nebo zařízení, které se má použít pro ladění. Pokud nejsou spuštěny žádné emulátory, pak použijte 'Android Virtual Device (AVD) Manager' pro spuštění zařízení. |
| Balíček ke spuštění | Určuje umístění sady *APK,* která bude laděna. Tato možnost spustí balíček (APK) při odladění aplikace. |
| Aktivita spuštění | Android aktivity použít ke spuštění aplikace, musí odpovídat ten, který se používá v manifestu. Stisknutím klávesy Použít načtěte seznam z *souboru AndroidManifest.xml* a dynamicky jej naplňte. |
| Další cesty hledání symbolů | Další vyhledávací cesta pro ladicí symboly. |
| Další cesty pro vyhledávání zdrojů Java | Další vyhledávací cesty pro zdrojové soubory Java. (Platí pouze v případě, že typ ladicího programu je pouze java.) |
