---
title: "Návod: Nasazení programu (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce59dc7b767c8ff8e988ac7a765d3bb5f1cdfffc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-deploying-your-program-c"></a>Návod: Nasazení programu (C++)
Teď, když jste vytvořili vaší aplikace pomocí dříve související názorné postupy, které jsou uvedeny v [pomocí prostředí Visual Studio IDE pro vývoje v jazyce C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md), posledním krokem je vytvoření instalační program tak, aby mohou ostatní uživatelé Nainstalujte aplikaci na svých počítačích. K tomuto účelu přidáte nový projekt do existujícího řešení. Výstup tohoto nového projektu je soubor setup.exe, který bude instalovat aplikaci na jiném počítači.  
  
 Tento návod ukazuje způsob použití Instalační služby systému Windows pro nasazení aplikace. Můžete taky ClickOnce k nasazení aplikace. Další informace najdete v tématu [ClickOnce – nasazení pro aplikace Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md). Další informace o nasazení obecně platí, najdete v části [nasazení aplikací, služeb a komponent](/visualstudio/deployment/deploying-applications-services-and-components).  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Tento návod předpokládá, že rozumíte základy jazyka C++.  
  
-   Také předpokládá, že jste dokončili dříve související návodů, které jsou uvedeny v [pomocí prostředí Visual Studio IDE pro vývoje v jazyce C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
-   Tento názorný postup nemůže být dokončena v edice Express sady Visual Studio.  
  
-   Pokud jste tak již neučinili, stáhněte si InstallShield Limited Edition (MANSKÁ), jak je popsáno v krocích později v tomto článku. MANSKÁ je zdarma pro vývojáře v sadě Visual Studio a nahrazuje funkci instalace a nasazení projektu šablony v dřívějších vydání sady Visual Studio.  
  
### <a name="to-install-the-isle-setup-and-deployment-project-template"></a>Chcete-li nainstalovat ostrov instalace a nasazení v šabloně projektů  
  
1.  Po připojení k Internetu, v řádku nabídek zvolte **soubor**, **nový**, **projektu** otevřete **nový projekt** dialogové okno.  
  
2.  V levém podokně dialogového okna, rozbalte **nainstalovaná**, **šablony**, a **jiné typy projektů** uzly a potom vyberte **instalace a nasazení**. V prostředním podokně vyberte **Povolit InstallShield Limited Edition** a potom zvolte **OK** tlačítko.  
  
3.  Postupujte podle pokynů k instalaci pro Visual Studio (ostrov) InstallShield Limited Edition.  
  
4.  Po stáhnout, nainstalovat a aktivovat ostrov, zavřete Visual Studio a znovu ho otevřete.  
  
5.  Na řádku nabídek zvolte **soubor**, **poslední projekty a řešení**a potom zvolte **herní** řešení, aby ho znovu otevřít.  
  
### <a name="to-create-a-setup-project-and-install-your-program"></a>K vytvoření projektu Instalační program a instalace programu  
  
1.  Změňte konfiguraci aktivního řešení na verzi. Na řádku nabídek zvolte **sestavení**, **nástroje Configuration Manager**. V **nástroje Configuration Manager** v dialogovém **aktivní konfigurace řešení** rozevíracího seznamu vyberte **verze**. Vyberte **Zavřít** tlačítko Uložit konfiguraci.  
  
2.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu** otevřete **nový projekt** dialogové okno.  
  
3.  V levém podokně dialogového okna, rozbalte **nainstalovaná**, **šablony**, a **jiné typy projektů** uzly a potom vyberte **instalace a nasazení**. V prostředním podokně vyberte **projekt InstallShield Limited Edition**.  
  
4.  Zadejte název projektu instalace v **název** pole. V tomto příkladu zadejte **instalační program herní**. V **řešení** rozevíracího seznamu vyberte **přidat do řešení**. Vyberte **OK** tlačítko pro vytvoření projektu instalace. A **projektu Assistant (herní instalační program)** kartě se otevře v okně editoru.  
  
5.  V dolní části **projektu Assistant (herní instalační program)** , zvolte **informace o aplikaci** odkaz.  
  
6.  Na **informace o aplikaci** stránky, zadejte název společnosti, jak se bude zobrazovat v instalačním programu. Můžete použít vlastní název společnosti, nebo v tomto příkladu použijte **Contoso**. Zadejte název aplikace; v tomto příkladu zadejte **herní**. Zadejte webovou adresu společnosti nebo v tomto příkladu použijte **http://www.contoso.com**.  
  
7.  V dolní části **projektu Assistant (herní instalační program)** , zvolte **instalace rozhovoru** odkaz.  
  
8.  Na **instalace rozhovoru** v části **chcete zobrazit dialogové okno licenční smlouvy**, vyberte **ne** tlačítko. V části **chcete vyzvat uživatele k zadání názvu společnosti a uživatelské jméno**, vyberte **ne** tlačítko.  
  
9. V **Průzkumníku řešení**, rozbalte **herní instalační program** projektu, rozbalte položku **uspořádání vaše instalace** uzel a potom otevřete **obecné informace** stránky.  
  
10. Na **obecné informace (herní instalační program)** kartě v okně editor, zadejte **ID značky Creator**, například **regid.2012 12.com.Contoso**.  
  
11. V **Průzkumníku řešení**v části **herní instalační program** projektu, rozbalte **zadejte Data aplikací** uzel a potom otevřete **soubory** stránka.  
  
12. Na **soubory (herní instalační program)** kartě v okně editoru v části **zdrojové soubory počítače**, otevřete místní nabídku pro **primární výstup z herního** a zvolte **Kopie**.  
  
13. Otevřete místní nabídky v prostoru ve skupinovém rámečku **název** sloupec v **soubory v cílovém počítači**a zvolte **vložení**. Nová položka s názvem **Game.Primary výstup** se zobrazí.  
  
14. V **Průzkumníku řešení**v části **zadejte Data aplikací** uzlu, otevřete **Redistributables** stránky.  
  
15. Na **Redistributables (herní instalační program)** v okně editor, vyberte kartu **Visual C++ 11.0 CRT (x86)** zaškrtávací políčko.  
  
16. Na řádku nabídek zvolte **sestavení**, **sestavit řešení** k sestavení herní projekt a projekt herní Instalační služby.  
  
17. Ve složce řešení vyhledejte program setup.exe, který byl vytvořený z projektu herní instalační program a spusťte ho k instalaci herní aplikace ve vašem počítači. Můžete zkopírovat tento soubor k instalaci aplikace a její soubory požadované knihovny na jiném počítači.  
  
18. Mnoho možností můžete nastavit v nastavení projektu podle svých potřeb. Další informace najdete v **Průzkumníku řešení**v části **instalační program herní** projekt, otevřete **Začínáme** stránky a potom zvolte Otevřít knihovnu MANSKÁ nápovědy klávesy F1.  
  
## <a name="next-steps"></a>Další kroky  
 **Předchozí:** [návod: ladění projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)  
 [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)