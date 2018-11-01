---
title: Vytvoření projektu knihovny MFC DLL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 6a24fb136570d1b5984582cab3593a29d843a54c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608114"
---
# <a name="creating-an-mfc-dll-project"></a>Vytvoření projektu knihovny MFC DLL

Knihovna MFC DLL je binární soubor, který funguje jako sdílená knihovna funkcí, které je možné využívat současně více aplikacemi. Nejjednodušším způsobem vytvoření projektu knihovny MFC je použití Průvodce MFC DLL.

> [!NOTE]
>  Vzhled funkcí v rozhraní IDE může záviset na aktivních nastaveních nebo edici a mohou lišit od těch popsaných v nápovědě. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Vytvoření projektu knihovny DLL MFC pomocí Průvodce MFC DLL

1. Postupujte podle pokynů v tématu nápovědy [vytvoření projektu pomocí Průvodce aplikací jazyka Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).

**Poznámka:** v **nový projekt** dialogové okno, vyberte `MFC DLL` ikonu v podokně šablon a spusťte Průvodce MFC DLL.

1. Definujte nastavení aplikace pomocí [nastavení aplikace](../../mfc/reference/application-settings-mfc-dll-wizard.md) stránku [Průvodce MFC DLL](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Přeskočení tohoto kroku zachová průvodce výchozí nastavení.

1. Klikněte na tlačítko **Dokončit** zavřete průvodce a otevřete nově vytvořený projekt v **Průzkumníka řešení**.

Po vytvoření projektu lze zobrazit vytvořené soubory v **Průzkumníka řešení**. Další informace o souborech Průvodce vytvoří pro váš projekt, naleznete v generovaném souboru ReadMe.txt. Další informace o typech souborů naleznete v tématu [typy souborů vytvořené pro projekty Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Viz také

[Typy projektů Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Stránky vlastností](../../ide/property-pages-visual-cpp.md)

