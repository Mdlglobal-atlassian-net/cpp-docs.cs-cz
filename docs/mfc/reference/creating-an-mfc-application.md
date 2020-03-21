---
title: Vytvoření aplikace MFC
ms.date: 08/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 16dbbc4a3b2e8927643d3612bec034f9f5da8d9c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077519"
---
# <a name="creating-an-mfc-application"></a>Vytvoření aplikace MFC

Aplikace MFC je spustitelná aplikace pro systém Windows, která je založena na knihovně MFC (Microsoft Foundation Class). Spustitelné soubory knihovny MFC obecně spadají do pěti typů: standardní aplikace systému Windows, dialogová okna, aplikace založené na formulářích, aplikace stylu Průzkumníka a aplikace ve stylu webového prohlížeče. Další informace naleznete v tématu:

- [Použití tříd pro psaní aplikací pro Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Vytváření a zobrazování dialogových oken](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Vytvoření aplikace MFC založené na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Vytvoření aplikace MFC ve stylu Průzkumníka souborů](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Vytvoření aplikace MFC ve stylu webového prohlížeče](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

Průvodce aplikací knihovny MFC vygeneruje příslušné třídy a soubory pro některý z těchto typů aplikací v závislosti na možnostech, které jste vybrali v průvodci.

Nejjednodušší způsob, jak vytvořit aplikaci knihovny MFC, je použití Průvodce aplikací knihovny MFC (**projekt MFC aplikace** v aplikaci Visual Studio 2019). Chcete-li vytvořit konzolovou aplikaci knihovny MFC (program příkazového řádku, který používá knihovny MFC, ale běží v okně konzoly), použijte Průvodce desktopovou aplikací systému Windows a zvolte možnost **záhlaví knihovny MFC** **aplikace** a okna.

::: moniker range=">=vs-2019"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Vytvoření formulářů knihovny MFC nebo aplikace založené na dialogu

1. V hlavní nabídce vyberte možnost **soubor** > **Nový** > **projekt**.
1. Do vyhledávacího pole zadejte "MFC" a pak zvolte možnost **aplikace MFC** ze seznamu výsledků.
1. Podle potřeby upravte výchozí hodnoty a potom stisknutím tlačítka **vytvořit** spusťte **Průvodce aplikací knihovny MFC**.
1. Podle potřeby upravte konfigurační hodnoty a pak stiskněte tlačítko **Dokončit**.

Další informace naleznete v tématu [vytváření aplikací MFC založených na formulářích](creating-a-forms-based-mfc-application.md).

![MFC – průvodce aplikací](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>Vytvoření konzolové aplikace MFC

Konzolová aplikace MFC je program příkazového řádku, který používá knihovny MFC, ale běží v okně konzoly.

1. V hlavní nabídce vyberte možnost **soubor** > **Nový** > **projekt**.
1. Do vyhledávacího pole zadejte "Desktop" a v seznamu výsledků klikněte na **desktopový průvodce Windows** .
1. Podle potřeby upravte název projektu a pak stisknutím klávesy **Next** otevřete Průvodce pro **plochu Windows**.
1. Zaškrtněte pole **hlavičky knihovny MFC** a podle potřeby nastavte další hodnoty a potom stiskněte **Dokončit**.

![MFC – průvodce aplikací](media/windows-desktop-wizard.png)

::: moniker-end

::: moniker range="=vs-2017"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Vytvoření formulářů knihovny MFC nebo aplikace založené na dialogu

1. V hlavní nabídce vyberte možnost **soubor** > **Nový** > **projekt**.
1. V části **nainstalované** šablony zvolte možnost **Visual C++**  > **MFC/ATL**. Pokud je nevidíte, přidejte je pomocí Instalační program pro Visual Studio.
1. V prostředním podokně zvolte **aplikace MFC** .
1. Podle potřeby upravte konfigurační hodnoty a pak stiskněte tlačítko **Dokončit**.

Další informace naleznete v tématu [vytváření aplikací MFC založených na formulářích](creating-a-forms-based-mfc-application.md).

![MFC – průvodce aplikací](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>Vytvoření konzolové aplikace MFC

Konzolová aplikace MFC je program příkazového řádku, který používá knihovny MFC, ale běží v okně konzoly.

1. V hlavní nabídce vyberte možnost **soubor** > **Nový** > **projekt**.
1. V části **nainstalované** šablony vyberte **Visual C++**  > **plocha Windows**.
1. V prostředním podokně vyberte **Průvodce desktopovou plochou systému Windows** .
1. Podle potřeby upravte název projektu a potom kliknutím na tlačítko **OK** otevřete **Průvodce pro plochu systému Windows**.
1. Zaškrtněte pole **hlavičky knihovny MFC** a podle potřeby nastavte další hodnoty a potom stiskněte **Dokončit**.

![MFC – průvodce aplikací](media/windows-desktop-wizard-2017.png)

::: moniker-end

::: moniker range="=vs-2015"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Vytvoření formulářů knihovny MFC nebo aplikace založené na dialogu

1. V hlavní nabídce vyberte možnost **soubor** > **Nový** > **projekt**.
1. V části **nainstalované** šablony zvolte možnost **Visual C++**  > **MFC**.
1. V prostředním podokně zvolte **aplikace MFC** .
1. Kliknutím na tlačítko **Další** spusťte **Průvodce aplikací knihovny MFC**.

Další informace naleznete v tématu [vytváření aplikací MFC založených na formulářích](creating-a-forms-based-mfc-application.md).

![MFC – průvodce aplikací](media/mfc-app-wizard-2015.png)

## <a name="to-create-an-mfc-console-application"></a>Vytvoření konzolové aplikace MFC

Konzolová aplikace MFC je program příkazového řádku, který používá knihovny MFC, ale běží v okně konzoly.

1. V hlavní nabídce vyberte možnost **soubor** > **Nový** > **projekt**.
1. V části **nainstalované** šablony vyberte **Visual C++**  > **Win32**.
1. V prostředním podokně vyberte **Konzolová aplikace Win32** .
1. Podle potřeby upravte název projektu a pak stiskněte **OK**.
1. Na druhé stránce průvodce zaškrtněte políčko **Přidat společné hlavičky pro knihovnu MFC** a nastavte další hodnoty podle potřeby a potom stiskněte **Dokončit**.

::: moniker-end

Po vytvoření projektu můžete zobrazit soubory vytvořené v **Průzkumník řešení**. Další informace o souborech, které průvodce vytvoří pro váš projekt, naleznete v souboru Readme. txt generovaného projektem. Další informace o typech souborů naleznete v tématu [typy souborů vytvořené pro projekty aplikace Visual C++ Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Viz také

[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Stránky vlastností](../../build/reference/property-pages-visual-cpp.md)