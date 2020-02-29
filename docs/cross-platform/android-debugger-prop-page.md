---
title: Vlastnosti ladicího programuC++pro Android ()
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 8ff6e539828d697e103c820d05565969f6afb910
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177526"
---
# <a name="android-debugger-properties"></a>Vlastnosti ladicího programu pro Android

Vlastnost | Popis | Vlastnit
--- | ---| ---
Typ ladicího programu | Určuje, který typ kódu se má ladit. | **Pouze nativní**<br>**Pouze Java**<br>
Cíl ladění | Určuje emulátor nebo zařízení, které se má použít pro ladění. Pokud nejsou spuštěné žádné emulátory, spusťte zařízení pomocí příkazu "virtuální zařízení (AVD) Android".
Balíček, který se má spustit | Určuje umístění *. apk* , které se bude ladit. Tato možnost spustí balíček (APK) při ladění aplikace.
Spouštěcí aktivita | Aktivita Androidu, která se má použít pro spuštění aplikace, musí odpovídat hodnotě používané v manifestu. Stisknutím tlačítka použít načtete seznam ze *souboru souboru AndroidManifest. XML* a dynamicky jej nasadíte.
Další cesty pro hledání symbolů | Další cesta hledání pro symboly ladění
Další cesty pro vyhledávání zdrojového kódu Java | Další vyhledávací cesty pro zdrojové soubory Java (Platí pouze v případě, že typ ladicího programu je pouze Java.)
