---
title: Příprava testovacího počítače ke spuštění ladicího spustitelného souboru
ms.date: 07/02/2019
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
ms.openlocfilehash: ae751b1632473fa316c7965bc751e91b782a89ea
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513666"
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>Příprava testovacího počítače ke spuštění ladicího spustitelného souboru

Chcete-li připravit počítač na testování ladicí verze aplikace sestavené aplikací Visual C++, je zapotřebí nasadit ladicí verze knihoven DLL jazyka Visual C++, na kterých aplikace závisí. Chcete-li zjistit, které knihovny DLL je nutné nasadit, postupujte podle kroků v části [Principy závislostí vizuální C++ aplikace](understanding-the-dependencies-of-a-visual-cpp-application.md). Ladicí verze knihoven DLL jazyka Visual C++ mají obvykle názvy končící písmenem „d“. Například ladicí verze knihovny msvcr100.dll má název msvcr100d.dll.

> [!NOTE]
>  Ladicí verze aplikace ani ladicí verze knihoven DLL jazyka Visual C++ nelze distribuovat. Tyto verze je povoleno nasazovat pouze na vlastní počítače, a to pouze za účelem ladění a testování aplikací na počítači, na němž není nainstalována sada Visual Studio. Další informace najdete v tématu [Redistribuce vizuálních C++ souborů](redistributing-visual-cpp-files.md).

Ladicí verze knihoven DLL jazyka Visual C++ lze spolu s ladicí verzí aplikace nasadit třemi různými způsoby.

- Pomocí centrálního nasazení nainstalujte ladicí verzi konkrétní knihovny DLL jazyka Visual C++ do adresáře %windir%\system32\ prostřednictvím Projektu instalace, který obsahuje slučovací moduly pro správnou verzi knihovny a architekturu aplikace. Slučovací moduly se nacházejí v adresářích Program Files nebo Program Files (x86) v modulech\\\Common Files\Merge. Ladicí verze slučovacího modulu obsahuje ve svém názvu řetězec Debug, například Microsoft_VC110_DebugCRT_x86.msm. Příklad tohoto nasazení lze nalézt v [návodu: Nasazení vizuální C++ aplikace pomocí projektu](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)instalace.

- Použijte místní nasazení pro instalaci ladicí verze konkrétní vizuální C++ knihovny DLL v instalačním adresáři aplikace pomocí souborů, které jsou k dispozici v adresáři Program Files nebo Program Files (x86) v souboru \Microsoft Visual Studio \< verze > \VC\redist\Debug_NonRedist\\.

    > [!NOTE]
    >  Pro vzdálené ladění vaší aplikace sestavené pomocí sady Visual Studio 2005 nebo Visual Studio 2008 na jiném počítači je nutné nasadit ladicí verze knihoven DLL knihovny Visual C++ Library jako sdílená sestavení vedle sebe. Odpovídající slučovací moduly lze nainstalovat pomocí Projektu instalace nebo pomocí Instalační služby systému Windows.

- Použijte možnost**nasazení** the_ v dialogovém okně **Configuration Manager** v aplikaci Visual Studio ke zkopírování výstupu projektu a dalších souborů do vzdáleného počítače.

Po nainstalování knihoven DLL jazyka Visual C++ lze ve sdílené síťové složce spustit vzdálený ladicí program. Další informace o vzdáleném ladění naleznete v tématu [vzdálené ladění](/visualstudio/debugger/remote-debugging).

## <a name="see-also"></a>Viz také:

[Nasazení ve Visual C++](deployment-in-visual-cpp.md)<br>
[Možnosti příkazového řádku Instalační služba systému Windows](/windows/win32/Msi/command-line-options)<br>
[Příklady nasazení](deployment-examples.md)<br>
[Vzdálené ladění](/visualstudio/debugger/remote-debugging)
