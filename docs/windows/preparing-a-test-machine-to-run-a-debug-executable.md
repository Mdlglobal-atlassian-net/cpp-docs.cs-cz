---
title: Příprava testovacího počítače ke spuštění ladicího spustitelného souboru
ms.date: 07/02/2019
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
ms.openlocfilehash: 26a92d5efc4bf9f0332a0e81fa2f9c8b2c2a958f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359913"
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>Příprava testovacího počítače ke spuštění ladicího spustitelného souboru

Chcete-li připravit počítač na testování ladicí verze aplikace sestavené aplikací Visual C++, je zapotřebí nasadit ladicí verze knihoven DLL jazyka Visual C++, na kterých aplikace závisí. Chcete-li zjistit, které knihovny DLL mají být nasazeny, postupujte podle kroků v [principu závislostí aplikace Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md). Ladicí verze knihoven DLL jazyka Visual C++ mají obvykle názvy končící písmenem „d“. Například ladicí verze knihovny msvcr100.dll má název msvcr100d.dll.

> [!NOTE]
> Ladicí verze aplikace ani ladicí verze knihoven DLL jazyka Visual C++ nelze distribuovat. Tyto verze je povoleno nasazovat pouze na vlastní počítače, a to pouze za účelem ladění a testování aplikací na počítači, na němž není nainstalována sada Visual Studio. Další informace naleznete [v tématu Redistributing Visual C++ Files](redistributing-visual-cpp-files.md).

Ladicí verze knihoven DLL jazyka Visual C++ lze spolu s ladicí verzí aplikace nasadit třemi různými způsoby.

- Pomocí centrálního nasazení nainstalujte ladicí verzi konkrétní knihovny DLL jazyka Visual C++ do adresáře %windir%\system32\ prostřednictvím Projektu instalace, který obsahuje slučovací moduly pro správnou verzi knihovny a architekturu aplikace. Slučovací moduly se nacházejí v adresáři Program Files nebo Program Files\\(x86) v \Common Files\Merge Modules . Ladicí verze slučovacího modulu obsahuje ve svém názvu řetězec Debug, například Microsoft_VC110_DebugCRT_x86.msm. Příklad tohoto nasazení lze nalézt v [návodu: Nasazení aplikace Visual C++ pomocí instalačního projektu](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

- Pomocí místního nasazení nainstalujte ladicí verzi konkrétní databáze DLL aplikace Visual C++ do instalačního adresáře aplikace pomocí souborů, které jsou \<k dispozici v adresáři Soubory\\programů nebo Soubory programů (x86) v \Microsoft Visual Studio verze>\VC\redist\Debug_NonRedist .

    > [!NOTE]
    >  Pro vzdálené ladění aplikace vytvořené pomocí sady Visual Studio 2005 nebo Visual Studio 2008 v jiném počítači je třeba nasadit ladicí verze knihovny Visual C++ knihovny DLL jako sdílená souběžná sestavení. Odpovídající slučovací moduly lze nainstalovat pomocí Projektu instalace nebo pomocí Instalační služby systému Windows.

- Pomocí možnosti**nasazení** the_ v dialogovém okně **Správce konfigurace** v sadě Visual Studio zkopírujte výstup projektu a další soubory do vzdáleného počítače.

Po nainstalování knihoven DLL jazyka Visual C++ lze ve sdílené síťové složce spustit vzdálený ladicí program. Další informace o vzdáleném ladění naleznete v [tématu Vzdálené ladění](/visualstudio/debugger/remote-debugging).

## <a name="see-also"></a>Viz také

[Nasazení ve Visual C++](deployment-in-visual-cpp.md)<br>
[Možnosti příkazového řádku Instalační služby systému Windows](/windows/win32/Msi/command-line-options)<br>
[Příklady nasazení](deployment-examples.md)<br>
[Vzdálené ladění](/visualstudio/debugger/remote-debugging)
