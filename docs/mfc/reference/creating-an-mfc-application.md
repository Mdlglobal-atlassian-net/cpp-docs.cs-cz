---
title: Vytvoření aplikace MFC
ms.date: 07/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 454a994da6db2841317d41ea1cdacfd36b0705e4
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606483"
---
# <a name="creating-an-mfc-application"></a>Vytvoření aplikace MFC

Aplikace MFC je spustitelná aplikace pro systém Windows, která je založena na knihovně MFC (Microsoft Foundation Class). Nejjednodušší způsob, jak vytvořit aplikaci knihovny MFC, je použití Průvodce aplikací knihovny MFC (**projekt MFC aplikace** v aplikaci Visual Studio 2019). Chcete-li vytvořit konzolovou aplikaci knihovny MFC, použijte Průvodce desktopovou aplikací systému Windows a zvolte možnost okna **Konzolová aplikace** a **záhlaví knihovny MFC** .

> [!IMPORTANT]
>  Projekty knihovny MFC nejsou podporovány v edicích Visual Studio Express.

Spustitelné soubory knihovny MFC obecně spadají do pěti typů: standardní aplikace systému Windows, dialogová okna, aplikace založené na formulářích, aplikace stylu Průzkumníka a aplikace ve stylu webového prohlížeče. Další informace naleznete v tématu:

- [Použití tříd pro psaní aplikací pro Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Vytváření a zobrazování dialogových oken](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Vytvoření aplikace MFC založené na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Vytvoření aplikace MFC ve stylu Průzkumníka souborů](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Vytvoření aplikace MFC ve stylu webového prohlížeče](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

Průvodce aplikací knihovny MFC vygeneruje příslušné třídy a soubory pro některý z těchto typů aplikací v závislosti na možnostech, které jste vybrali v průvodci.

### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>Vytvoření aplikace MFC pomocí Průvodce aplikací knihovny MFC

1. Postupujte podle pokynů v tématu nápovědy [vytvoření C++ projektu konzolové aplikace](../../get-started/tutorial-console-cpp.md).

1. V dialogovém okně **Nový projekt** vyberte v podokně šablony možnost **aplikace MFC** a otevřete průvodce.

1. Definujte nastavení aplikace pomocí [Průvodce aplikací knihovny MFC](../../mfc/reference/mfc-application-wizard.md).

    > [!NOTE]
    >  Tento krok přeskočte, pokud chcete zachovat výchozí nastavení průvodce.

1. Kliknutím na tlačítko **Dokončit** zavřete průvodce a otevřete nový projekt ve vývojovém prostředí.

Po vytvoření projektu můžete zobrazit soubory vytvořené v **Průzkumník řešení**. Další informace o souborech, které průvodce vytvoří pro váš projekt, naleznete v souboru Readme. txt generovaného projektem. Další informace o typech souborů naleznete v tématu [typy souborů vytvořené pro projekty aplikace Visual C++ Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Viz také:

[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Stránky vlastností](../../build/reference/property-pages-visual-cpp.md)

