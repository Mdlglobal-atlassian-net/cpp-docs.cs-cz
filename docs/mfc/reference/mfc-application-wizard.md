---
title: MFC – průvodce aplikací
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: f69f0a19cdcd3526d8afac2e1492da806c2dffd3
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448488"
---
# <a name="mfc-application-wizard"></a>MFC – průvodce aplikací

Průvodce aplikací knihovny MFC generuje aplikaci, která při kompilaci, implementuje základní funkce spustitelný soubor (.exe) aplikace Windows. Startovní aplikace knihovny MFC zahrnuje C++ (CPP) zdrojové soubory, soubory prostředků (.rc), soubory hlaviček (.h) a soubor projektu (.vcxproj). Kód, který je vygenerován v těchto souborech starter je založena na knihovně MFC.

> [!NOTE]
>  V závislosti na možnostech, které jste vybrali Průvodce vytvoří další soubory v projektu. Pokud vyberete třeba **kontextové nápovědy** na [rozšířené funkce](../../mfc/reference/advanced-features-mfc-application-wizard.md) stránce průvodce vytvoří soubory, které jsou nezbytné pro kompilaci soubory nápovědy projektu. Další informace o souborech vytvořených průvodcem najdete v tématu [typy souborů vytvořené pro vizuál C++ projekty](../../build/reference/file-types-created-for-visual-cpp-projects.md)a najdete v souboru Readme.txt v projektu.

## <a name="overview"></a>Přehled

Tato stránka průvodce popisuje aktuální nastavení aplikace pro aplikaci knihovny MFC, kterou vytváříte. Ve výchozím nastavení Průvodce vytvoří projekt následujícím způsobem:

- [Typ aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md)

   - Projekt je vytvořen s podporou rozhraní s kartami více dokumentů (MDI). Další informace najdete v tématu [SDI a knihovna MDI](../../mfc/sdi-and-mdi.md).

   - Projekt používá [architekturu Document/View](../../mfc/document-view-architecture.md).

   - Projekt používá kódování Unicode knihovny.

   - Projekt je vytvořený pomocí sady Visual Studio styl projektu a umožňuje přepínání vizuálního stylu.

   - Projekt nepoužívá knihovnu MFC ve sdílené knihovně DLL. Další informace najdete v tématu [vytvořit C /C++ knihovny DLL v sadě Visual Studio](../../build/dlls-in-visual-cpp.md).

- [Podpora složených dokumentů, Průvodce aplikací MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

   - Projekt nepodporuje složených dokumentů.

- [Řetězce šablon dokumentů, Průvodce aplikací MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

   - Projekt používá název projektu pro výchozí řetězce šablony dokumentu.

- [Podpora databáze, Průvodce aplikací MFC](../../mfc/reference/database-support-mfc-application-wizard.md)

   - Projekt nepodporuje databází.

- [Funkce uživatelského rozhraní, Průvodce aplikací MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

   - Projekt implementuje standardní uživatelské rozhraní funkce, jako jsou systémové nabídky stavového řádku, maximalizovat a minimalizovat polí Windows **o** pole, standardní nabídek a ukotvení panelu nástrojů a podřízených rámců.

- [Pokročilé funkce, Průvodce aplikací MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)

   - Projekt podporuje tisku a tiskového náhledu.

   - Projekt podporuje ovládací prvky ActiveX. Další informace najdete v tématu [pořadí operací při vytváření ovládacích prvků ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).

   - Projekt nepodporuje [automatizace](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [rozhraní Windows Sockets](../../mfc/windows-sockets-in-mfc.md), nebo Active Accessibility.

   - Projekt podporuje **Explorer** ukotvené podokno, **výstup** ukotvené podokno a **vlastnosti** ukotvené podokno.

- [Generované třídy, Průvodce aplikací MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)

   - Zobrazit třídu v projektu je odvozen z [CView Class](../../mfc/reference/cview-class.md).

   - Třídy v projektu aplikace pochází z [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md).

   - Třída dokumentu projektu je odvozen z [CDocument – třída](../../mfc/reference/cdocument-class.md).

   - V projektu hlavního rámce třídy je odvozen z [CMDIFrameWndEx – třída](../../mfc/reference/cmdiframewndex-class.md).

   - Třída podřízeného rámce projektu je odvozen z [CMDIChildWndEx – třída](../../mfc/reference/cmdichildwndex-class.md).

Chcete-li změnit toto výchozí nastavení, klikněte na název příslušnou kartu v levém sloupci průvodce a proveďte změny na stránce, která se zobrazí.

Po vytvoření projektu aplikace knihovny MFC lze přidat objekty nebo ovládací prvky k projektu Visual C++ pomocí [průvodců kódu](../../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="see-also"></a>Viz také:

[Vytvoření aplikace MFC](../../mfc/reference/creating-an-mfc-application.md)<br/>
[Desktopové aplikace knihovny MFC](../../mfc/mfc-desktop-applications.md)<br/>
[Použití tříd pro psaní aplikací pro Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
