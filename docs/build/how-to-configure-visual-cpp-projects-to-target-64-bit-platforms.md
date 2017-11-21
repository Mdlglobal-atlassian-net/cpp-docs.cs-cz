---
title: "Postupy: Konfigurace projektů Visual C++ pro 64bitové, x64 platformy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 97e128d7e940420698d57ccca5cc2afc01d27b02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-configure-visual-c-projects-to-target-64-bit-x64-platforms"></a>Postupy: Konfigurace projektů Visual C++ pro 64bitové, x64 platformy

Konfigurace projektu v integrovaném vývojovém prostředí sady Visual Studio můžete použít k nastavení aplikace C++ pro 64bitové, x64 platformy. Můžete také migrovat nastavení projektu Win32 do konfigurace 64bitového projektu.  
  
### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>Nastavení aplikace C++ pro 64bitové platformy  
  
1.  Otevřete projekt C++, který chcete nakonfigurovat.  
  
2.  Otevření stránek vlastností pro tento projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
    > [!NOTE]
    >  Pro projekty rozhraní .NET, ujistěte se, že **vlastnosti konfigurace** je vybrán uzel nebo jeden z jeho podřízených uzlů v  **\<název projektu > stránky vlastností** dialogové okno, jinak hodnota  **Nástroj Configuration Manager** tlačítko zůstává k dispozici.  
  
3.  Vyberte **nástroje Configuration Manager** tlačítko Otevřít **nástroje Configuration Manager** dialogové okno.  
  
4.  V **Active platforma řešení** rozevíracího seznamu, vyberte  **\<nová... >** možnost otevření **nová platforma řešení** dialogové okno.  
  
5.  V **zadejte nebo vyberte nové platformě** rozevíracího seznamu, vyberte 64bitového cílové platformy.  
  
    > [!NOTE]
    >  V **nová platforma řešení** dialogové okno, můžete použít **Kopírovat nastavení z** možnost kopírování existující nastavení projektu do nové konfigurace projektu 64-bit.  
  
6.  Vyberte **OK** tlačítko. Platforma, která jste vybrali v předchozím kroku se zobrazí pod **Active platforma řešení** v **nástroje Configuration Manager** dialogové okno.  
  
7.  Vyberte **Zavřít** tlačítka na **nástroje Configuration Manager** dialogové okno pole a potom vyberte **OK** tlačítka na  **\<název projektu > Stránky vlastností** dialogové okno.  
  
### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Chcete zkopírovat do projektu 64-bit konfigurace nastavení projektu Win32  
  
-   Když **nová platforma řešení** dialogové okno je otevřené během nastavení projektu pro 64bitové platformě v **Kopírovat nastavení z** rozevíracího seznamu vyberte **Win32**. Tato nastavení projektu se automaticky aktualizují na úrovni projektu:  
  
    -   [/MACHINE](../build/reference/machine-specify-target-platform.md) – možnost linkeru nastavena na **/MACHINE:X 64**.  
  
    -   **Zaregistrujte výstupní** je byl VYPNUT. Další informace najdete v tématu [stránky vlastností Linkeru](../ide/linker-property-pages.md).  
  
    -   **Cílové prostředí** je nastaven na **/env x64**. Další informace najdete v tématu [MIDL – stránky vlastností: Obecné](../ide/midl-property-pages-general.md).  
  
    -   **Ověření parametrů** je vymazána a resetovat na výchozí hodnotu. Další informace najdete v tématu [MIDL – stránky vlastností: Upřesnit](../ide/midl-property-pages-advanced.md).  
  
    -   Pokud **Debug Information Format** byla nastavena na **/ZI** v konfiguraci projektu Win32, pak je nastavený na **/Zi** v konfiguraci 64bitového projektu. Další informace najdete v tématu [/Z7, / zi, /ZI (formát informace ladění)](../build/reference/z7-zi-zi-debug-information-format.md).  
  
    > [!NOTE]
    >  Žádná z těchto vlastností projektu jsou změnit, pokud je přepsána na úrovni souborů.  
  
## <a name="see-also"></a>Viz také  

[64bitové aplikace rozhraní .NET framework](/dotnet/framework/64-bit-apps)   
[Konfigurace Visual C++ pro 64bitové, x64 cíle](../build/configuring-programs-for-64-bit-visual-cpp.md)   
[Ladění 64bitových aplikací](/visualstudio/debugger/debug-64-bit-applications)