---
title: Typ aplikace, Průvodce aplikací knihovny MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.apptype
helpviewer_keywords:
- static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
ms.openlocfilehash: de23c59fdb59f6f40e256589c5450a8118bb8e5c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281249"
---
# <a name="application-type-mfc-application-wizard"></a>Typ aplikace, Průvodce aplikací knihovny MFC

Pomocí této stránky [Průvodce aplikací knihovny MFC](../../mfc/reference/mfc-application-wizard.md) k navrhování a přidat základní funkce do nové aplikace knihovny MFC.

- **Typ aplikace**

  Určuje typ podpory dokumentu, který chcete vytvořit ve vaší aplikaci. Určuje typ aplikace, kterou jste vybrali možnosti uživatelského rozhraní, které jsou k dispozici pro vaši aplikaci. Zobrazit [funkce uživatelského rozhraní, Průvodce aplikací knihovny MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md) Další informace.

   Další informace o typech dokumentů najdete v tématu:

  - [Rozhraní SDI a knihovna MDI](../../mfc/sdi-and-mdi.md)

  - [Okna s rámečkem](../../mfc/frame-windows.md)

  - [Třídy oken s rámečkem](../../mfc/frame-window-classes.md)

  - [Dokumenty, zobrazení a framework](../../mfc/documents-views-and-the-framework.md)

  - [Dialogová okna](../../mfc/dialog-boxes.md)

  |Možnost|Popis|
  |------------|-----------------|
  |**Jednoho dokumentu**|Vytvoří architekturu rozhraní (SDI) jeden dokument pro vaši aplikaci, ve kterém je třída zobrazení na základě [CView Class](../../mfc/reference/cview-class.md). Základní třída pro zobrazení můžete změnit [vygenerované třídy, Průvodce aplikací knihovny MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránky průvodce. Vytvoření aplikace založené na formulářích, například použít [třídy CFormView](../../mfc/reference/cformview-class.md) pro danou třídu zobrazení.<br /><br /> V tomto typu aplikace okna rámce dokumentu může obsahovat pouze jeden dokument.|
  |**Více dokumentů**|Vytvoří více architekturu rozhraní (MDI) dokument pro vaši aplikaci, ve kterém je třída zobrazení na základě `CView`. Základní třída pro zobrazení můžete změnit **třídy generované v** stránky průvodce. Vytvoření aplikace založené na formulářích, například použít `CFormView` pro danou třídu zobrazení.<br /><br /> V tomto typu aplikace můžete okna rámce dokumentu obsahovat více podřízených oken.|
  |**Dokumenty s kartami**|Každý dokument umístí na samostatné kartě.|
  |**Na bázi dialogu**|Vytvoří architekturu založených na dialogovém okně pro vaši aplikaci, kde je na základě třídy dialogového okna `CDialog`. (Chcete-li vytvořit dialogového okna HTML, zaškrtněte políčko **HTML pomocí dialogového okna**.)|
  |**Použít HTML dialog**|Dialogové okno pole pouze pro aplikace. Odvozená třída dialogu z [CDHtmlDialog – třída](../../mfc/reference/cdhtmldialog-class.md) místo [CDialog – třída](../../mfc/reference/cdialog-class.md). Pokud zaškrtnete toto políčko `CDHtmlDialog` je uveden v **základní třída** pole [vygenerované třídy, Průvodce aplikací knihovny MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránky průvodce.<br /><br /> A `CDHtmlDialog`– dialogové okno odvozené zobrazí dialogová okna založeného na HTML, ovládací prvky vyměňuje data s kódem HTML a zpracovává události HTML.|
  |**Více dokumentů na nejvyšší úrovni**|Vytvoří více architekturou nejvyšší úrovně pro vaši aplikaci, ve kterém je třída zobrazení na základě `CView`.<br /><br /> V tomto typu aplikace, když uživatel klikne **nový** (nebo **nový rámec**) na **souboru** nabídky, aplikace vytvoří okno, jejíž nadřazený prvek je implicitně plochy. Nový rámec dokumentu se zobrazí na hlavním panelu a není omezen na klientskou oblast okna aplikace.|

- **Podpora architektury dokument/zobrazení**

  Určuje, zda mají být zahrnuty document/view – Architektura aplikace s použitím [CDocument – třída](../../mfc/reference/cdocument-class.md) a [CView Class](../../mfc/reference/cview-class.md) (výchozí). Pokud se přenos non-MFC aplikace nebo pokud budete chtít snížit velikost zkompilované spustitelný soubor, zrušte zaškrtnutí tohoto políčka. Ve výchozím nastavení, aplikace bez architekturu document/view pochází z [CWinApp – třída](../../mfc/reference/cwinapp-class.md), a neobsahuje podporu knihovny MFC pro otevření dokumentu ze souboru na disku.

- **Jazyk prostředku**

  Nastaví jazyk vašich prostředků. Po instalaci sady Visual Studio se v seznamu zobrazí dostupné jazyky ve vašem systému. Pokud chcete vybrat jiný jazyk než jazyku systému, musí být již nainstalován složku příslušnou šablonu pro daný jazyk.

  Jazyk, který jste vybrali, se projeví v **lokalizované řetězce** možnost [řetězce šablony dokumentu, Průvodce aplikací knihovny MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md) stránky průvodce.

- **Použití knihovny Unicode**

  Určuje, zda se používá kódování Unicode nebo jiným kódováním než Unicode verze knihovny MFC.

- **Styl projektu**

  Označuje, zda má vaše aplikace standardní knihovny MFC, Průzkumníka souborů, Visual Studio, nebo architektura systému Office a zobrazení. Další informace najdete v tématu [vytvoření aplikace MFC ve stylu Průzkumníka souborů](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md).

  |Možnost|Popis|
  |------------|-----------------|
  |**Standardní knihovny MFC**|Poskytuje standardní architekturu aplikace knihovny MFC.|
  |**Průzkumník souborů**|Implementuje soubor jako v Průzkumníku aplikace s použitím okno s rozdělovačem. Pokud je v levém podokně [CTreeView – třída](../../mfc/reference/ctreeview-class.md) a je v pravém podokně [CListView – třída](../../mfc/reference/clistview-class.md).|
  |**Visual Studio**|Implementuje Visual Studio jako aplikace, která obsahuje čtyři ukotvitelné podokna (**zobrazení souboru**, **zobrazení tříd**, **vlastnosti**, a **výstup**), které jsou odvozeny z [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md) a okna hlavního rámce, který je odvozen z [CMDIFrameWndEx – třída](../../mfc/reference/cmdiframewndex-class.md) (výchozí).|
  |**Office**|Implementuje obsahující pás karet, který je odvozen z aplikace Office jako [CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md), panel aplikace Outlook, který je odvozen z [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md), záhlaví, která je odvozena z [CMFCCaptionBar – třída](../../mfc/reference/cmfccaptionbar-class.md)a hlavního rámce, který je odvozen z [CMDIFrameWndEx – třída](../../mfc/reference/cmdiframewndex-class.md).|

- **Vizuální styl a barvy**

  Určuje styl visual aplikace. Jsou k dispozici následující možnosti:

  - **Nativní Windows/výchozí**

  - **Office 2003**

  - **Visual Studio 2005**

  - **Office 2007 (modrý motiv)**

  - **Office 2007 (černý motiv)**

  - **Office 2007 (stříbrná motiv)**

  - **Office 2007 (azurová motiv)**

- **Povolit přepínání vizuálního stylu**

  Určuje, zda uživatel může změnit vzhled aplikace za běhu, obvykle tak, že vyberete vhodné vizuální styl nabídce nebo na pásu karet.

- **Použití knihovny MFC**

  Určuje, jak propojit knihovnu MFC. Ve výchozím nastavení se propojí MFC jako sdílenou knihovnu DLL.

  |Možnost|Popis|
  |------------|-----------------|
  |**Použít knihovnu MFC ve sdílené knihovně DLL**|Odkazy na aplikace jako sdílenou knihovnu DLL knihovny MFC. Aplikace provádí volání na knihovně MFC v době běhu. Tato možnost snižuje požadavky na disku a paměti aplikací, které se skládají z několika spustitelnými soubory, které používají knihovnu MFC. Aplikace Win32 a knihovny MFC můžete volat funkce v knihovně DLL (výchozí)|
  |**Použít knihovnu MFC ve statické knihovně**|Propojení aplikace se statickou knihovnou MFC v okamžiku sestavení.|

## <a name="see-also"></a>Viz také:

[MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)<br/>
[Typy souborů vytvořených pro projekty Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)
