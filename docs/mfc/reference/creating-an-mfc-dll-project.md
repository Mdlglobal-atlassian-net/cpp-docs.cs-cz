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
ms.openlocfilehash: 6a1718e1f347be46b2f228479d3dbd30027b3160
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077444"
---
# <a name="creating-an-mfc-dll-project"></a>Vytvoření projektu knihovny MFC DLL

Knihovna MFC DLL je binární soubor, který funguje jako sdílená knihovna funkcí, kterou lze použít současně více aplikacemi. Nejjednodušší způsob, jak vytvořit projekt knihovny MFC DLL, je použít Průvodce knihovnou MFC DLL.

> [!NOTE]
>  Vzhled funkcí v integrovaném vývojovém prostředí (IDE) může záviset na vašich aktivních nastaveních nebo edicích a může se lišit od těch popsaných v nápovědě. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Vytvoření projektu knihovny MFC DLL pomocí Průvodce knihovnou MFC DLL

1. Postupujte podle pokynů v tématu nápovědy [Vytvoření aplikace MFC](creating-an-mfc-application.md) , ale zvolte **dynamickou knihovnu MFC** nebo knihovnu **MFC DLL** ze seznamu dostupných šablon.

1. Definujte nastavení aplikace pomocí stránky [nastavení aplikace](../../mfc/reference/application-settings-mfc-dll-wizard.md) v [Průvodci knihovny MFC DLL](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Tento krok přeskočte, pokud chcete zachovat výchozí nastavení průvodce.

1. Kliknutím na tlačítko **Dokončit** zavřete průvodce a otevřete nový projekt v **Průzkumník řešení**.

Po vytvoření projektu můžete zobrazit soubory vytvořené v **Průzkumník řešení**. Další informace o souborech, které průvodce vytvoří pro váš projekt, naleznete v souboru Readme. txt generovaného projektem. Další informace o typech souborů naleznete v tématu [typy souborů vytvořené pro projekty aplikace Visual C++ Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Viz také

[C++typy projektů v aplikaci Visual Studio](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Stránky vlastností](../../build/reference/property-pages-visual-cpp.md)
