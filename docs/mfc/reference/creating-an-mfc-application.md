---
title: Vytvoření aplikace MFC
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 0f16fe577f1dc02dc9a2fc0cffb5899b16ad8cca
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708237"
---
# <a name="creating-an-mfc-application"></a>Vytvoření aplikace MFC

Aplikace knihovny MFC je spustitelná aplikace pro Windows, který je založen na knihovny Microsoft Foundation Class (MFC). Nejjednodušším způsobem vytvoření aplikace knihovny MFC je použití Průvodce aplikací knihovny MFC.

> [!IMPORTANT]
>  Projekty MFC nejsou podporovány v edici Visual Studio Express.

Spustitelné soubory knihovny MFC se obecně dělí do pěti typů: standardní aplikace Windows, dialogová okna, aplikace založené na formulářích, aplikace stylu Průzkumník a webové aplikace ve stylu prohlížeče. Další informace naleznete v tématu:

- [Použití tříd pro psaní aplikací pro Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Vytváření a zobrazování dialogových oken](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Vytvoření aplikace MFC založené na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Vytvoření aplikace MFC ve stylu Průzkumníka souborů](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Vytvoření aplikace MFC ve stylu webového prohlížeče](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

Průvodce aplikací knihovny MFC generuje příslušné třídy a soubory pro všechny typy aplikací, v závislosti na možnostech, které vyberete v průvodci.

### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>Vytvoření aplikace knihovny MFC pomocí Průvodce aplikací MFC

1. Postupujte podle pokynů v tématu nápovědy [vytvoření projektu aplikace konzoly C++](../../get-started/tutorial-console-cpp.md).

1. V **nový projekt** dialogu **aplikace knihovny MFC** v podokně šablon a spusťte průvodce.

1. Definujte nastavení aplikace pomocí [Průvodce aplikací knihovny MFC](../../mfc/reference/mfc-application-wizard.md).

    > [!NOTE]
    >  Přeskočení tohoto kroku zachová průvodce výchozí nastavení.

1. Klikněte na tlačítko **Dokončit** zavřete průvodce a otevření nového projektu ve vývojovém prostředí.

Po vytvoření projektu lze zobrazit vytvořené soubory v **Průzkumníka řešení**. Další informace o souborech Průvodce vytvoří pro váš projekt, naleznete v generovaném souboru ReadMe.txt. Další informace o typech souborů naleznete v tématu [typy souborů vytvořené pro Visual Studio C++ projekty](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Viz také:

[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Stránky vlastností](../../build/reference/property-pages-visual-cpp.md)

