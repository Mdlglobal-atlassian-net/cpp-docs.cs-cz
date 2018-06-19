---
title: Typ aplikace, Průvodce aplikací knihovny MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.apptype
dev_langs:
- C++
helpviewer_keywords:
- static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5708e823c57ecdb8470a398c4192cba1a5b6e411
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353436"
---
# <a name="application-type-mfc-application-wizard"></a>Typ aplikace, Průvodce aplikací knihovny MFC
Pomocí této stránky [Průvodce aplikací knihovny MFC](../../mfc/reference/mfc-application-wizard.md) návrh a přidat do nové aplikace MFC základní funkce.  
  
 **Typ aplikace**  
 Určuje typ podpory dokumentu, který chcete vytvořit ve vaší aplikaci. Typ aplikace, kterou vyberete určuje možnosti uživatelského rozhraní, které jsou dostupné pro vaši aplikaci. V tématu [funkce uživatelského rozhraní, Průvodce aplikací knihovny MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md) Další informace.  
  
 Další informace o typech dokumentů najdete v tématu:  
  
-   [Rozhraní SDI a knihovna MDI](../../mfc/sdi-and-mdi.md)  
  
-   [Okna s rámečkem](../../mfc/frame-windows.md)  
  
-   [Třídy oken s rámečkem](../../mfc/frame-window-classes.md)  
  
-   [Dokumenty, zobrazení a framework](../../mfc/documents-views-and-the-framework.md)  
  
-   [Dialogová okna](../../mfc/dialog-boxes.md)  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Jednotlivý dokument**|Vytvoří pro aplikaci, kde je na základě třídy zobrazení architekturu (SDI rozhraní) s jedním dokumentem [CView – třída](../../mfc/reference/cview-class.md). Základní třída pro zobrazení v můžete změnit [vygenerované třídy, Průvodce aplikací knihovny MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránce průvodce. Vytvoření aplikace založené na formulářích, například použít [třídy CFormView](../../mfc/reference/cformview-class.md) pro třídu zobrazení.<br /><br /> V tomto typu aplikace okně s rámečkem dokumentu může obsahovat pouze jeden dokument.|  
|**Více dokumentů**|Vytvoří architekturu více dokumentů rozhraní (MDI) pro vaši aplikaci, kde je na základě třídy zobrazení `CView`. Základní třída pro zobrazení v můžete změnit **generované třídy** stránce průvodce. Vytvoření aplikace založené na formulářích, například použít `CFormView` pro třídu zobrazení.<br /><br /> V tomto typu aplikace můžete okně s rámečkem dokumentu obsahovat více podřízených oken.|  
|**Dokumentů s kartami**|Každý dokument umístí na samostatné kartě.|  
|**Na základě dialogové okno**|Vytvoří architektura založená na dialogové okno pro vaši aplikaci, kde je na základě třídy dialogového okna `CDialog`. (Chcete-li vytvořit dialogového okna HTML, zaškrtněte políčko **HTML pomocí dialogu**.)|  
|**Použití dialogového okna HTML**|Dialogové okno pole pouze pro aplikace. Odvozená třída dialogového okna z [CDHtmlDialog třída](../../mfc/reference/cdhtmldialog-class.md) místo [CDialog – třída](../../mfc/reference/cdialog-class.md). Pokud zaškrtnete toto políčko, `CDHtmlDialog` , je uvedena ve **základní třída** pole [vygenerované třídy, Průvodce aplikací knihovny MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránce průvodce.<br /><br /> A `CDHtmlDialog`– dialogové okno odvozené zobrazí dialogové okno HTML, výměnu dat pomocí HTML ovládací prvky a zpracovává události HTML.|  
|**Více dokumentů nejvyšší úrovně**|Vytvoří pro aplikaci, kde je na základě třídy zobrazení architekturu více nejvyšší úrovně `CView`.<br /><br /> V tomto typu aplikace, když uživatel klikne **nový** (nebo **nový snímek**) na **souboru** nabídce aplikace vytvoří okno, jehož nadřazeným prvkem je implicitně plochy. Rámec nového dokumentu se zobrazí na hlavním panelu a není omezena na klientské oblasti okna aplikace.|  
  
 **Document/view – architektura podpory**  
 Určuje, zda mají být zahrnuty document/view – Architektura aplikace pomocí [CDocument – třída](../../mfc/reference/cdocument-class.md) a [CView – třída](../../mfc/reference/cview-class.md) (výchozí). Zaškrtnutí tohoto políčka zrušte, pokud jsou portování mimo MFC aplikace, nebo pokud chcete zmenšit velikost zkompilovaného spustitelného souboru. Ve výchozím nastavení, aplikace bez document/view – architektura je odvozený od [CWinApp – třída](../../mfc/reference/cwinapp-class.md), a nezahrnuje Podpora MFC pro otevření dokumentu ze souboru na disku.  
  
 **Jazyk prostředku**  
 Nastaví jazyk vašich prostředků. Zobrazí se seznam jazyků, které jsou k dispozici v systému, jako nainstalované Visual Studio. Pokud chcete vybrat jiný jazyk než jazyk vašeho systému, musí být nainstalovaný již složce příslušné šablony pro požadovaný jazyk. Další informace o instalaci jazyka prostředků liší od výchozí hodnoty k dispozici v **jazyk prostředku** seznam najdete v tématu [podpora průvodce pro jiné jazyky](../../ide/wizard-support-for-other-languages.md).  
  
 Jazyk, který vyberete, se projeví v **lokalizované řetězce** možnost [řetězce šablony dokumentu, Průvodce aplikací knihovny MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md) stránce průvodce.  
  
 **Použití knihovny Unicode**  
 Určuje, jestli se používá kódování Unicode nebo kódování Unicode verze knihovny MFC.  
  
 **Styl projektu**  
 Označuje, zda má vaše aplikace standardní knihovny MFC, Průzkumníka souborů, Visual Studio, nebo Office architektury a zobrazení. Další informace najdete v tématu [vytváření aplikací MFC ve stylu Průzkumníka souborů](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md).  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Standardní knihovny MFC**|Poskytuje standardní architekturu aplikace knihovny MFC.|  
|**Průzkumníka souborů**|Implementuje soubor stylu Průzkumníka aplikace pomocí okna rozdělovače, kde je v levém podokně [CTreeView – třída](../../mfc/reference/ctreeview-class.md) a je v pravém podokně [CListView – třída](../../mfc/reference/clistview-class.md).|  
|**Visual Studio**|Implementuje aplikace Visual Studio jako, který obsahuje čtyři lze ukotvit podokna (**zobrazení souboru**, **zobrazení tříd**, **vlastnosti**, a **výstup**), které jsou odvozeny od [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) a okno rámce, který je odvozený od [CMDIFrameWndEx Class](../../mfc/reference/cmdiframewndex-class.md) (výchozí).|  
|**Office**|Implementuje Office jako aplikace, která obsahuje pásu karet, který je odvozený od [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md), panel aplikace Outlook, který je odvozený od [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md), záhlaví, které je odvozený od [CMFCCaptionBar Class](../../mfc/reference/cmfccaptionbar-class.md)a hlavního rámce, který je odvozený od [CMDIFrameWndEx Class](../../mfc/reference/cmdiframewndex-class.md).|  
  
 **Vizuálního stylu a barvy**  
 Určuje vizuální styl aplikace. K dispozici jsou následující možnosti:  
  
-   **Nativní nebo výchozí nastavení systému Windows**  
  
-   **Office 2003**  
  
-   **Visual Studio 2005**  
  
-   **Office 2007 (motiv modrý)**  
  
-   **Office 2007 (černý motiv)**  
  
-   **Office 2007 (stříbrný motiv)**  
  
-   **Office 2007 (motiv Aqua)**  
  
 **Povolit přepínání vizuální styl**  
 Určuje, jestli uživatel může změnit vizuální styl aplikace za běhu, obvykle výběrem příslušné vizuální styl z nabídky nebo pásu karet.  
  
 **Použití knihovny MFC**  
 Určuje, jak propojit s knihovnou MFC. Ve výchozím nastavení je MFC propojit jako sdílenou knihovnu DLL.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Použití knihovny MFC ve sdílené knihovny DLL**|Knihovny MFC odkazuje na aplikace jako sdílenou knihovnu DLL. Aplikace volá knihovny MFC za běhu. Tato možnost snižuje požadavky na disk a paměť aplikací, které se skládají z více spustitelné soubory, které používají knihovny MFC. Aplikace Win32 a MFC můžete volat funkce v knihovně DLL (výchozí)|  
|**Použití statické knihovny MFC**|Odkazy aplikace se statickou knihovnou MFC v čase vytvoření buildu.|  
  
## <a name="see-also"></a>Viz také  
 [MFC – Průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)   
 [Typy souborů vytvořených pro projekty Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)

