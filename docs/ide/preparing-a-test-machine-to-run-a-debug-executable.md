---
title: Příprava testovacího počítače ke spuštění ladicího spustitelného souboru
ms.date: 11/04/2016
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
ms.openlocfilehash: 9ae5e0007105cfda233f808bf52d2d81068524be
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744856"
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>Příprava testovacího počítače ke spuštění ladicího spustitelného souboru

Chcete-li připravit počítač na testování ladicí verze aplikace sestavené aplikací Visual C++, je zapotřebí nasadit ladicí verze knihoven DLL jazyka Visual C++, na kterých aplikace závisí. Pokud chcete zjistit, které mají být nasazeny knihovny DLL, postupujte podle kroků v [Principy závislostí v aplikacích Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Ladicí verze knihoven DLL jazyka Visual C++ mají obvykle názvy končící písmenem „d“. Například ladicí verze knihovny msvcr100.dll má název msvcr100d.dll.

> [!NOTE]
>  Ladicí verze aplikace ani ladicí verze knihoven DLL jazyka Visual C++ nelze distribuovat. Tyto verze je povoleno nasazovat pouze na vlastní počítače, a to pouze za účelem ladění a testování aplikací na počítači, na němž není nainstalována sada Visual Studio. Další informace najdete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).

Ladicí verze knihoven DLL jazyka Visual C++ lze spolu s ladicí verzí aplikace nasadit třemi různými způsoby.

- Pomocí centrálního nasazení nainstalujte ladicí verzi konkrétní knihovny DLL jazyka Visual C++ do adresáře %windir%\system32\ prostřednictvím Projektu instalace, který obsahuje slučovací moduly pro správnou verzi knihovny a architekturu aplikace. Slučovací moduly se nacházejí ve složce Program Files nebo Program Files (x86) adresáře v \Common moduly\\. Ladicí verze slučovacího modulu obsahuje ve svém názvu řetězec Debug, například Microsoft_VC110_DebugCRT_x86.msm. Příklad tohoto nasazení lze nalézt v [názorný postup: Nasazení aplikace v jazyce Visual C++ pomocí projektu instalace](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

- Pomocí místního nasazení nainstalujte ladicí verzi konkrétní knihovny DLL jazyka Visual C++ v adresáři instalace aplikace pomocí souborů, které jsou k dispozici ve složce Program Files nebo Program Files (x86) adresáře v \Microsoft Visual Studio \<verze > \VC\redist\Debug_NonRedist\\.

    > [!NOTE]
    >  Chcete-li vzdáleně ladit aplikaci sestavenou aplikací Visual C++ 2005 nebo Visual C++ 2008 na jiném počítači, je zapotřebí nasadit ladicí verze knihoven DLL jazyka Visual C++ jako sdílená sestavení vedle sebe. Odpovídající slučovací moduly lze nainstalovat pomocí Projektu instalace nebo pomocí Instalační služby systému Windows.

- Pomocí možnosti**nasadit** možnost **nástroje Configuration Manager** dialogové okno v sadě Visual Studio Zkopírujte výstup projektu a další soubory do vzdáleného počítače.

Po nainstalování knihoven DLL jazyka Visual C++ lze ve sdílené síťové složce spustit vzdálený ladicí program. Další informace o vzdáleném ladění naleznete v tématu [vzdálené ladění](/visualstudio/debugger/remote-debugging.md).

## <a name="see-also"></a>Viz také:

[Nasazení ve Visual C++](../ide/deployment-in-visual-cpp.md)<br>
[Možnosti Windows Installer příkazového řádku](/windows/desktop/Msi/command-line-options)<br>
[Příklady nasazení](../ide/deployment-examples.md)<br>
[Vzdálené ladění](/visualstudio/debugger/remote-debugging.md)
