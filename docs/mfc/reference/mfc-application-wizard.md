---
title: MFC – Průvodce aplikací | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4cbdc5e6db53fd4eacf9154bc356a1a64c77391
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-application-wizard"></a>MFC – průvodce aplikací
Průvodce aplikací MFC generuje aplikaci, když kompilovat, implementuje základní funkce spustitelný soubor (.exe) aplikace systému Windows. Výchozí aplikace knihovny MFC zahrnuje C++ zdrojové (sada) soubory, soubory prostředků (RC), soubory hlavičky () a soubor projektu (VCXPROJ). Kód, který je generovaný v těchto souborech starter vychází MFC.  
  
> [!NOTE]
>  V závislosti na možnostech, které jste vybrali Průvodce vytvoří další soubory v projektu. Například, pokud vyberete **Kontextová nápověda** na [upřesňující funkce](../../mfc/reference/advanced-features-mfc-application-wizard.md) stránce průvodce vytvoří soubory, které jsou nezbytné pro kompilaci soubory nápovědy projektu. Další informace o souborech, které průvodce vytvoří najdete v tématu [typy souborů vytvořené pro projekty Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)a naleznete v souboru Readme.txt v projektu.  
  
## <a name="overview"></a>Přehled  
 Tato stránka průvodce popisuje aktuální nastavení aplikace pro aplikace MFC, kterou vytváříte. Ve výchozím nastavení Průvodce vytvoří projekt takto:  
  
-   [Typ aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md)  
  
    -   Vytvoření projektu s podporou záložkách rozhraní více dokumentů (MDI). Další informace najdete v tématu [SDI a MDI](../../mfc/sdi-and-mdi.md).  
  
    -   Projekt využívá [Document/View – architektura](../../mfc/document-view-architecture.md).  
  
    -   Projekt využívá knihovny kódování Unicode.  
  
    -   Projekt je vytvořený pomocí styl projektu sady Visual Studio a umožňuje přepínání vizuálního stylu.  
  
    -   Projekt využívá MFC v sdílenou knihovnu DLL. Další informace najdete v tématu [knihovny DLL v jazyce Visual C++](../../build/dlls-in-visual-cpp.md).  
  
-   [Podpora složených dokumentů, Průvodce aplikací MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)  
  
    -   Projekt nepodporuje složené dokumenty.  
  
-   [Řetězce šablon dokumentů, Průvodce aplikací MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)  
  
    -   Projekt využívá název projektu pro výchozích řetězce šablony dokumentu.  
  
-   [Podpora databáze, Průvodce aplikací MFC](../../mfc/reference/database-support-mfc-application-wizard.md)  
  
    -   Projekt poskytuje žádná podpora pro databáze.  
  
-   [Funkce uživatelského rozhraní, Průvodce aplikací MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)  
  
    -   Projekt implementuje standardní Windows uživatelské rozhraní funkce, jako je system nabídku, stavového řádku, maximalizovat a minimalizovat polí **o** pole, standardní řádek nabídek a ukotvení panelu nástrojů a podřízené rámce.  
  
-   [Pokročilé funkce, Průvodce aplikací MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)  
  
    -   Projekt podporuje tisku a přehled tisku.  
  
    -   Projekt podporuje ovládací prvky ActiveX. Další informace najdete v tématu [pořadí operací při vytváření ovládacích prvků ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).  
  
    -   Projekt nepodporuje [automatizace](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows Sockets](../../mfc/windows-sockets-in-mfc.md), nebo Active Accessibility.  
  
    -   Projekt podporuje **Explorer** ukotvení podokně **výstup** ukotvení podokně a **vlastnosti** ukotvení podokně.  
  
-   [Generované třídy, Průvodce aplikací MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)  
  
    -   Třídy zobrazení projektu je odvozený od [CView – třída](../../mfc/reference/cview-class.md).  
  
    -   Třída aplikace projektu je odvozený od [CWinAppEx Class](../../mfc/reference/cwinappex-class.md).  
  
    -   Třída dokumentu projektu je odvozený od [CDocument – třída](../../mfc/reference/cdocument-class.md).  
  
    -   Třída hlavního rámce projektu je odvozený od [CMDIFrameWndEx Class](../../mfc/reference/cmdiframewndex-class.md).  
  
    -   Třída podřízeného rámce projektu je odvozený od [CMDIChildWndEx Class](../../mfc/reference/cmdichildwndex-class.md).  
  
 Chcete-li změnit toto výchozí nastavení, klikněte na příslušnou kartu název v levém sloupci průvodce a proveďte změny na stránku, která se zobrazí.  
  
 Po vytvoření projektu aplikace MFC, můžete přidat objekty nebo ovládacích prvků do projektu Visual C++ pomocí [code průvodců](../../ide/adding-functionality-with-code-wizards-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytváření aplikací MFC](../../mfc/reference/creating-an-mfc-application.md)   
 [Běžné aplikace knihovny MFC](../../mfc/mfc-desktop-applications.md)   
 [Použití tříd pro psaní aplikací pro Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
