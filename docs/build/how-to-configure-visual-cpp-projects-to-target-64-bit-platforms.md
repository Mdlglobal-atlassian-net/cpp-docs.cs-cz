---
title: 'Postupy: Konfigurace projektů Visual C++ pro cílení 64-Bit, x64 platformy'
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: 3df2252e1879fbbcdf6cc950fa8dd637894ba3f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664552"
---
# <a name="how-to-configure-visual-c-projects-to-target-64-bit-x64-platforms"></a>Postupy: Konfigurace projektů Visual C++ pro cílení 64-Bit, x64 platformy

Konfigurace projektu v integrovaném vývojovém prostředí sady Visual Studio můžete použít k nastavení aplikací v jazyce C++ pro cílení 64-bit, x64 platformy. Můžete také migrovat nastavení projektu Win32 do 64-bit projektové konfigurace.

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>K nastavení aplikací v jazyce C++ cílit na 64bitové platformy

1. Otevřete projekt C++, který chcete konfigurovat.

1. Otevření stránek vlastností pro daný projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

   > [!NOTE]
   > Pro projekty .NET, ujistěte se, že **vlastnosti konfigurace** uzlu nebo jeden z jeho podřízených uzlů, je vybrán v  **\<Projectname > stránky vlastností** dialogové okno; v opačném případě  **Nástroj Configuration Manager** tlačítko zůstane k dispozici.

1. Zvolte **nástroje Configuration Manager** tlačítko Otevřít **nástroje Configuration Manager** dialogové okno.

1. V **aktivní platforma řešení** rozevíracího seznamu, vyberte  **\<nový … >** možnost otevření **nová platforma řešení** dialogové okno.

1. V **zadejte nebo vyberte novou platformu** rozevíracího seznamu, vyberte 64bitová verze cílové platformy.

   > [!NOTE]
   > V **nová platforma řešení** dialogové okno, můžete použít **Kopírovat nastavení z:** možnost zkopírovat existující nastavení projektu do nové konfigurace projektu 64-bit.

1. Zvolte **OK** tlačítko. Platforma, která jste vybrali v předchozím kroku se zobrazí v části **aktivní platforma řešení** v **nástroje Configuration Manager** dialogové okno.

1. Zvolte **Zavřít** tlačítko **nástroje Configuration Manager** dialogové okno pole a klikněte na tlačítko **OK** tlačítko  **\<Projectname > Stránky vlastností** dialogové okno.

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Kopírování nastavení projektu Win32 do 64-bit projektové konfigurace

- Když **nová platforma řešení** dialogové okno je otevřený, když nastavíte projekt, aby mířil 64bitové platformě v **Kopírovat nastavení z:** rozevíracího seznamu vyberte **Win32**. Tato nastavení projektu se automaticky aktualizují na úrovni projektu:

   - [/MACHINE](../build/reference/machine-specify-target-platform.md) – možnost linkeru nastavená na **/MACHINE:X 64**.

   - **Registrovat výstup** je vypnuté. Další informace najdete v tématu [stránky vlastností Linkeru](../ide/linker-property-pages.md).

   - **Cílové prostředí** je nastavena na **/env x64**. Další informace najdete v tématu [MIDL – stránky vlastností: Obecné](../ide/midl-property-pages-general.md).

   - **Ověřit parametry** je vymazána a resetovat na výchozí hodnotu. Další informace najdete v tématu [MIDL – stránky vlastností: Upřesnit](../ide/midl-property-pages-advanced.md).

   - Pokud **formát informací o ladění** byl nastaven na **/zi** v konfiguraci projektu Win32, pak bude nastaven **/zi** v konfiguraci projektu 64-bit. Další informace najdete v tématu [/Z7, / zi, /ZI (formát informací o ladění)](../build/reference/z7-zi-zi-debug-information-format.md).

   > [!NOTE]
   > Žádná z těchto vlastností projektu se změní, pokud jsou přepsány na úrovni souboru.

## <a name="see-also"></a>Viz také

[64bitové aplikace rozhraní .NET framework](/dotnet/framework/64-bit-apps)<br/>
[Konfigurace Visual C++ pro 64bitové cíle x64](../build/configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Ladění 64bitových aplikací](/visualstudio/debugger/debug-64-bit-applications)