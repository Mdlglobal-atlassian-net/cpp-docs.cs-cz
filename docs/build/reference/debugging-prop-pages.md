---
title: C++Ladění stránek vlastností
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 78115a6b-3799-4515-814e-8566b5bdc55d
f1_keywords:
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCLocalDebugPageObject.AmpDefaultAccelerator
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.Environment
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.AmpDefaultAccelerator
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
ms.openlocfilehash: c2190c4406e165cfec1915234b688c598f228777
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169705"
---
# <a name="c-debugging-property-pages"></a>C++Ladění stránek vlastností

Tyto stránky vlastností se nacházejí v části > **vlastností** **projektu** > **Vlastnosti konfigurace** > **ladění**. V rozevíracím seznamu vyberte typ ladicího programu. Další informace o ladění C++ kódu naleznete v tématu [kurz: Naučte se ladit C++ kód pomocí sady Visual Studio](/visualstudio/debugger/getting-started-with-the-debugger-cpp) a ladit [nativní kód](/visualstudio/debugger/debugging-native-code).

## <a name="local-windows-debugger-property-page"></a>Stránka vlastností místního ladicího programu Windows

### <a name="command"></a>Příkaz

Příkaz ladění, který se má provést.

### <a name="command-arguments"></a>Argumenty příkazu

Argumenty příkazového řádku, které se mají předat aplikaci

### <a name="working-directory"></a>Pracovní adresář

Pracovní adresář aplikace Ve výchozím nastavení se jedná o adresář obsahující soubor projektu.

### <a name="attach"></a>Připojit

Určuje, zda se má ladicí program pokusit připojit k existujícímu procesu, když se spustí ladění.

### <a name="debugger-type"></a>Typ ladicího programu

Určuje typ ladicího programu, který se má použít. Při nastavení na hodnotu automaticky se typ ladicího programu vybere na základě obsahu souboru exe.

**Vlastnit**

- **Pouze nativní** – pouze nativní
- Jenom **spravované** jenom spravované
- **Smíšený** smíšený
- **Automaticky** automaticky
- Skript **skriptu**
- **Pouze GPU (C++ amp)** – pouze GPU (C++ amp)

### <a name="environment"></a>Prostředí

Určuje prostředí pro ladění programu nebo proměnné pro sloučení s existujícím prostředím.

### <a name="debugging-accelerator-type"></a>Typ akcelerátoru ladění

Typ akcelerátoru ladění, který se má použít pro ladění kódu GPU. (K dispozici, když je aktivní ladicí program GPU.)

### <a name="gpu-default-breakpoint-behavior"></a>Výchozí chování zarážky GPU

Nastavuje, jak často se má ladicí program GPU přerušuje.

**Vlastnit**

- **Přerušit jednou na pokřivení** – přerušit jednou na pokřivení
- **Přerušení pro každé vlákno (například chování procesoru)** – přerušení pro každé vlákno (například chování CPU)

### <a name="merge-environment"></a>Sloučit prostředí

Začlenit zadané proměnné prostředí s existujícím prostředím.

### <a name="sql-debugging"></a>Ladění SQL

Připojte ladicí program SQL.

### <a name="amp-default-accelerator"></a>Výchozí akcelerátor amp

Přepsat C++ výchozí výběr akcelerátoru amp. Vlastnost se nedá použít při ladění spravovaného kódu.

## <a name="remote-windows-debugger-property-page"></a>Stránka vlastností vzdáleného ladicího programu Windows

Další informace o vzdáleném ladění naleznete v tématu [vzdálené ladění vizuálního C++ projektu v aplikaci Visual Studio](/visualstudio/debugger/remote-debugging-cpp).

### <a name="remote-command"></a>Vzdálený příkaz

Příkaz ladění, který se má provést.

### <a name="remote-command-arguments"></a>Argumenty vzdáleného příkazu

Argumenty příkazového řádku, které se mají předat aplikaci

### <a name="working-directory"></a>Pracovní adresář

Pracovní adresář aplikace Ve výchozím nastavení se jedná o adresář obsahující soubor projektu.

### <a name="remote-server-name"></a>Název vzdáleného serveru

Určuje název vzdáleného serveru.

### <a name="connection"></a>Připojení

Určuje typ připojení.

**Vlastnit**

- **Vzdálené s ověřováním systému Windows** – vzdálené s [ověřováním systému Windows](/windows-server/security/windows-authentication/windows-authentication-overview).
- **Vzdálené bez ověřování** – vzdálené bez ověřování.

### <a name="debugger-type"></a>Typ ladicího programu

Určuje typ ladicího programu, který se má použít. Při nastavení na hodnotu automaticky se typ ladicího programu vybere na základě obsahu souboru exe.

**Vlastnit**

- **Pouze nativní** – pouze nativní
- Jenom **spravované** jenom spravované
- **Smíšený** smíšený
- **Automaticky** automaticky
- Skript **skriptu**
- **Pouze GPU (C++ amp)** – pouze GPU (C++ amp)

### <a name="environment"></a>Prostředí

Určuje prostředí pro ladění programu nebo proměnné pro sloučení s existujícím prostředím.

### <a name="debugging-accelerator-type"></a>Typ akcelerátoru ladění

Typ akcelerátoru ladění, který se má použít pro ladění kódu GPU. (K dispozici, když je aktivní ladicí program GPU.)

### <a name="gpu-default-breakpoint-behavior"></a>Výchozí chování zarážky GPU

Nastavuje, jak často se má ladicí program GPU přerušuje.

**Vlastnit**

- **Přerušit jednou na pokřivení** – přerušit jednou na pokřivení
- **Přerušení pro každé vlákno (například chování procesoru)** – přerušení pro každé vlákno (například chování CPU)

### <a name="attach"></a>Připojit

Určuje, zda se má ladicí program pokusit připojit k existujícímu procesu, když se spustí ladění.

### <a name="sql-debugging"></a>Ladění SQL

Připojte ladicí program SQL.

### <a name="deployment-directory"></a>Adresář nasazení

Pokud chcete při ladění na vzdáleném počítači zkopírovat obsah výstupu projektu (kromě souborů PDB) na vzdálený počítač, zadejte cestu zde.

### <a name="additional-files-to-deploy"></a>Další soubory k nasazení

Při ladění na vzdáleném počítači se tady uvedené soubory a adresáře (kromě výstupu projektu) zkopírují do adresáře nasazení, pokud je zadaný.

### <a name="deploy-visual-c-debug-runtime-libraries"></a>Nasadit knihovny C++ běhového modulu Visual Debug

Určuje, jestli se mají nasadit běhové knihovny ladicího programu pro aktivní platformu (Win32, x64 nebo ARM).

### <a name="amp-default-accelerator"></a>Výchozí akcelerátor amp

Přepsat C++ výchozí výběr akcelerátoru amp. Vlastnost se nedá použít při ladění spravovaného kódu.

## <a name="web-browser-debugger-property-page"></a>Stránka vlastností ladicího programu webového prohlížeče

### <a name="http-url"></a>ADRESA URL HTTP

Určuje adresu URL projektu.

### <a name="debugger-type"></a>Typ ladicího programu

Určuje typ ladicího programu, který se má použít. Při nastavení na hodnotu automaticky se typ ladicího programu vybere na základě obsahu souboru exe.

**Vlastnit**

- **Pouze nativní** – pouze nativní
- Jenom **spravované** jenom spravované
- **Smíšený** smíšený
- **Automaticky** automaticky
- Skript **skriptu**

## <a name="web-service-debugger-property-page"></a>Stránka vlastností ladicího programu webové služby

### <a name="http-url"></a>ADRESA URL HTTP

Určuje adresu URL projektu.

### <a name="debugger-type"></a>Typ ladicího programu

Určuje typ ladicího programu, který se má použít. Při nastavení na hodnotu automaticky se typ ladicího programu vybere na základě obsahu souboru exe.

**Vlastnit**

- **Pouze nativní** – pouze nativní
- Jenom **spravované** jenom spravované
- **Smíšený** smíšený
- **Automaticky** automaticky
- Skript **skriptu**

### <a name="sql-debugging"></a>Ladění SQL

Připojte ladicí program SQL.
