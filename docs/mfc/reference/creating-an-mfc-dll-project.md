---
title: Vytvoření projektu knihovny MFC DLL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcdll.project
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5c560fecdaed6ea74442596aab685a08300b3fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374052"
---
# <a name="creating-an-mfc-dll-project"></a>Vytvoření projektu knihovny MFC DLL
Knihovna MFC DLL je binární soubor, který funguje jako sdílenou knihovnu funkcí, které je možné využívat současně více aplikacemi. Nejjednodušší způsob, jak vytvořit projektu MFC DLL je použití Průvodce MFC DLL.  
  
> [!NOTE]
>  Vzhled funkcí v prostředí IDE, může záviset na aktivním nastavení nebo edici a může lišit od těch popsaných v nápovědě. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Vytvoření projektu knihovny MFC DLL pomocí Průvodce MFC DLL  
  
1.  Postupujte podle pokynů v tématu nápovědy [vytvoření projektu pomocí Průvodce aplikací Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
 **Poznámka:** v **nový projekt** dialogové okno, vyberte `MFC DLL` ikona v podokně šablon pro spuštění Průvodce MFC DLL.  
  
1.  Určete nastavení aplikace pomocí [nastavení aplikace](../../mfc/reference/application-settings-mfc-dll-wizard.md) stránky [MFC DLL – průvodce](../../mfc/reference/mfc-dll-wizard.md).  
  
    > [!NOTE]
    >  Přeskočit tento krok průvodce zachovat výchozí nastavení.  
  
2.  Klikněte na tlačítko **Dokončit** zavřete průvodce a otevřete nový projekt v **Průzkumníku řešení**.  
  
 Po vytvoření projektu, můžete zobrazit soubory vytvořené v Průzkumníku řešení. Další informace o souborech Průvodce vytvoří pro váš projekt, naleznete v souboru projektu vygenerované souboru ReadMe.txt. Další informace o typech souborů najdete v tématu [typy souborů vytvořené pro projekty Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).  
  
## <a name="see-also"></a>Viz také  
 [Typy projektů Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)   
 [Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Stránky vlastností](../../ide/property-pages-visual-cpp.md)   
 [Nasazení aplikací](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)

