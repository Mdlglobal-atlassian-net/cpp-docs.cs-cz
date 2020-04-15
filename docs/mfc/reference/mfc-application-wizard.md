---
title: MFC – průvodce aplikací
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: 6949f136890e8274f225a49496b2eb1b8f78b6fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351837"
---
# <a name="mfc-application-wizard"></a>MFC – průvodce aplikací

Průvodce aplikací knihovny MFC generuje aplikaci, která při kompilaci implementuje základní funkce spustitelné aplikace systému Windows (.exe). Počáteční aplikace knihovny MFC obsahuje soubory zdroje C++(.cpp), soubory prostředků (.rc), soubory záhlaví (.h) a soubor projektu (.vcxproj). Kód, který je generován v těchto počátečních souborech je založen na knihovně MFC.

> [!NOTE]
> V závislosti na vybraných možnostech průvodce vytvoří další soubory v projektu. Pokud například vyberete **kontextovou nápovědu** na stránce [Rozšířené funkce,](../../mfc/reference/advanced-features-mfc-application-wizard.md) průvodce vytvoří soubory, které jsou nezbytné pro kompilaci souborů nápovědy projektu. Další informace o souborech, které průvodce vytvoří, naleznete [v tématu Typy souborů vytvořené pro projekty visual ateliéru C++](../../build/reference/file-types-created-for-visual-cpp-projects.md)a v souboru Readme.txt v projektu.

## <a name="overview"></a>Přehled

Tato stránka průvodce popisuje aktuální nastavení aplikace pro vytvářenou aplikaci knihovny MFC. Ve výchozím nastavení průvodce vytvoří projekt následujícím způsobem:

- [Typ aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md)

  - Projekt je vytvořen s podporou rozhraní MDI (s kartami). Další informace naleznete v [tématech SDI a MDI](../../mfc/sdi-and-mdi.md).

  - Projekt používá [architekturu dokumentu/zobrazení](../../mfc/document-view-architecture.md).

  - Projekt používá knihovny Unicode.

  - Projekt je vytvořen pomocí stylu projektu sady Visual Studio a umožňuje přepínání vizuálních stylů.

  - Projekt používá knihovnu MFC ve sdílené knihovně DLL. Další informace naleznete v [tématu Vytvoření knihoven DLL c/C++ v sadě Visual Studio](../../build/dlls-in-visual-cpp.md).

- [Podpora složených dokumentů, Průvodce aplikací MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

  - Projekt neposkytuje žádnou podporu pro složené dokumenty.

- [Řetězce šablon dokumentů, Průvodce aplikací MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

  - Projekt používá název projektu pro výchozí řetězce šablony dokumentu.

- [Podpora databáze, Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md)

  - Projekt neposkytuje žádnou podporu pro databáze.

- [Funkce uživatelského rozhraní, Průvodce aplikací MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

  - Projekt implementuje standardní funkce uživatelského rozhraní systému Windows, jako je například systémová nabídka, stavový řádek, maximalizace a minimalizace polí, pole **O,** standardní panel nabídek a ukotvení panelu nástrojů a podřízené rámce.

- [Pokročilé funkce, Průvodce aplikací MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)

  - Projekt podporuje tisk a náhled.

  - Projekt podporuje ovládací prvky ActiveX. Další informace naleznete [v tématu Sequence of Operations for Creating ActiveX Controls](../../mfc/sequence-of-operations-for-creating-activex-controls.md).

  - Projekt neposkytuje žádnou podporu pro [automatizaci](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows Sockets](../../mfc/windows-sockets-in-mfc.md)nebo Aktivní přístupnost.

  - Projekt podporuje dokovací podokno **Průzkumníka,** **dokovací** podokno Výstup a dokovací podokno **Vlastnosti.**

- [Generované třídy, Průvodce aplikací MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)

  - Třída zobrazení projektu je odvozena z [třídy CView](../../mfc/reference/cview-class.md).

  - Třída aplikace projektu je odvozena z [třídy CWinAppEx](../../mfc/reference/cwinappex-class.md).

  - Třída dokumentu projektu je odvozena z [třídy CDocument](../../mfc/reference/cdocument-class.md).

  - Třída hlavního rámce projektu je odvozena z [třídy CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md).

  - Třída podřízeného rámce projektu je odvozena z [třídy CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md).

Chcete-li tato výchozí nastavení změnit, klepněte na příslušný název karty v levém sloupci průvodce a proveďte změny na stránce, která se zobrazí.

Po vytvoření projektu aplikace knihovny MFC můžete do projektu přidat objekty nebo ovládací prvky pomocí [průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)jazyka Visual C++ .

## <a name="see-also"></a>Viz také

[Vytvoření aplikace MFC](../../mfc/reference/creating-an-mfc-application.md)<br/>
[Desktopové aplikace knihovny MFC](../../mfc/mfc-desktop-applications.md)<br/>
[Použití tříd pro psaní aplikací pro Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
