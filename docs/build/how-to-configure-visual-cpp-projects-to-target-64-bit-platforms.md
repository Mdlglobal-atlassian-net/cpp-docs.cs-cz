---
title: 'Postupy: Konfigurace projektů sady C++ Visual Studio pro cílení na 64 platforem x64'
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: 762fd5d6ddbb55713cf2fc5e34cb33fb91b08eb9
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492244"
---
# <a name="how-to-configure-visual-studio-c-projects-to-target-64-bit-x64-platforms"></a>Postupy: Konfigurace projektů sady C++ Visual Studio pro cílení na 64 platforem x64

Můžete použít konfigurace projektu v integrovaném vývojovém prostředí sady Visual Studio k C++ nastavení aplikací pro cílení na 64 platforem x64. Můžete také migrovat nastavení projektu Win32 do 64 konfigurace projektu.

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>Nastavení C++ aplikací pro cílení na 64 platforem

1. Otevřete C++ projekt, který chcete konfigurovat.

1. Otevřete stránky vlastností pro daný projekt. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](working-with-project-properties.md).

   > [!NOTE]
   > V případě projektů .NET se ujistěte, že je vybrán uzel **Vlastnosti konfigurace** nebo některý z jeho podřízených uzlů v  **\<dialogovém okně Vlastnosti ProjectName > stránky vlastností** . v opačném případě tlačítko **Configuration Manager** zůstane znemožnit.

1. Kliknutím na tlačítko **Configuration Manager** otevřete dialogové okno **Configuration Manager** .

1. V rozevíracím seznamu **Aktivní platforma řešení** vyberte  **\<nový... >** možnost otevření dialogového okna **Nová platforma řešení** .

1. V rozevíracím seznamu **typ nebo vyberte Nová platforma** vyberte 64 cílovou platformu.

   > [!NOTE]
   > V dialogovém okně **Nová platforma řešení** můžete pomocí možnosti **Kopírovat nastavení z** zkopírovat existující nastavení projektu do nové 64 konfigurace projektu.

1. Zvolte **OK** tlačítko. Platforma, kterou jste vybrali v předchozím kroku, se zobrazí v části **aktivní řešení platforma** v dialogovém okně **Configuration Manager** .

1. Zvolte tlačítko **Zavřít** v dialogovém okně **Configuration Manager** a pak klikněte na tlačítko   **\<ok v dialogovém okně > stránky vlastností ProjectName** .

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Kopírování nastavení projektu Win32 do 64 konfigurace projektu

- Když je dialogové okno **Nová platforma řešení** otevřené, zatímco nastavíte projekt na cílovou platformu 64, v rozevíracím seznamu **Kopírovat nastavení z** vyberte **Win32**. Tato nastavení projektu se automaticky aktualizují na úrovni projektu:

  - Možnost linkeru [/Machine](reference/machine-specify-target-platform.md) je nastavená na **/Machine: x64**.

  - **Výstup registru** je vypnutý. Další informace najdete v tématu [stránky vlastností linkeru](reference/linker-property-pages.md).

  - **Cílové prostředí** je nastavené na **/ENV x64**. Další informace naleznete v tématu [MIDL – stránky vlastností](reference/midl-property-pages.md).

  - **Ověřte** , že parametry jsou vymazány a obnoveny na výchozí hodnotu. Další informace naleznete v tématu [MIDL – stránky vlastností](reference/midl-property-pages.md).

  - Pokud byl **formát ladicích informací** nastaven na **/Zi** v konfiguraci projektu Win32, pak je v konfiguraci projektu 64 nastavena na **/Zi** . Další informace naleznete v tématu [/Z7,/Zi,/Zi (formát ladicích informací)](reference/z7-zi-zi-debug-information-format.md).

  > [!NOTE]
  > Žádná z těchto vlastností projektu se nezmění, pokud jsou přepsány na úrovni souboru.

## <a name="see-also"></a>Viz také:

[Konfigurace C++ projektů pro 64 cíle platformy x64](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Ladění 64bitových aplikací](/visualstudio/debugger/debug-64-bit-applications)
