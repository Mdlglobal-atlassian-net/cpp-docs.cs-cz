---
title: Vytvoření projektu knihovny MFC DLL
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 6367b2a4b85b2c586c5a4420a8be1f80d334b2e4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363965"
---
# <a name="creating-an-mfc-dll-project"></a>Vytvoření projektu knihovny MFC DLL

Knihovna DLL knihovny MFC je binární soubor, který funguje jako sdílená knihovna funkcí, které lze současně používat více aplikací. Nejjednodušší způsob, jak vytvořit projekt Knihovny MFC DLL, je použít Průvodce knihovnou DLL knihovny MFC.

> [!NOTE]
> Vzhled funkcí v prostředí IDE může záviset na aktivním nastavení nebo edici a může se lišit od funkcí popsaných v nápovědě. Chcete-li změnit nastavení, zvolte **Nastavení importu a exportu** v nabídce **Nástroje.** Další informace naleznete [v tématu Přizpůsobení prostředí IDE sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Vytvoření projektu knihovny MFC DLL pomocí Průvodce knihovnou DLL knihovny MFC

1. Postupujte podle pokynů v tématu nápovědy [Vytvoření aplikace knihovny MFC,](creating-an-mfc-application.md) ale ze seznamu dostupných šablon zvolte **knihovnu dynamických odkazů** knihovny MFC nebo **knihovnu DLL knihovny MFC.**

1. Definujte nastavení aplikace pomocí stránky [Nastavení aplikace](../../mfc/reference/application-settings-mfc-dll-wizard.md) [průvodce knihovnou MFC DLL](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Tento krok přeskočte, chcete-li zachovat výchozí nastavení průvodce.

1. Klepnutím na **tlačítko Dokončit** zavřete průvodce a otevřete nový projekt v **Průzkumníku řešení**.

Po vytvoření projektu můžete zobrazit soubory vytvořené v **Průzkumníku řešení**. Další informace o souborech, které průvodce vytvoří pro váš projekt, naleznete v souboru ReadMe.txt generovaném projektem. Další informace o typech souborů naleznete v [tématu Typy souborů vytvořené pro projekty visual studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Viz také

[Typy projektů Jazyka C++ v sadě Visual Studio](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Stránky vlastností](../../build/reference/property-pages-visual-cpp.md)
