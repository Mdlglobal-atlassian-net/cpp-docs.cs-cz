---
title: "Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: adb4ba4fdcc141438b2eeb87b4e3c9151bb9a5c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-program-or-control-source-and-header-files"></a>Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček
Následující soubory se vytvoří při vytváření projektu knihovny MFC v sadě Visual Studio, v závislosti na možnosti, kterou jste vybrali pro projekt, který vytvoříte. Například projekt obsahuje *Projname*dlg.cpp a *Projname*dlg.h soubory pouze v případě, že vytvoříte třídu nebo na základě dialogovém okně projekt.  
  
 Všechny tyto soubory jsou umístěny v *Projname* adresář a v složky (hlaviček soubory) nebo zdrojové soubory (soubory sada) složky v Průzkumníku řešení.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|*Projname*.h|Hlavní soubor pro program nebo DLL. Obsahuje všechny globální symboly a `#include` pro ostatní soubory hlaviček. Je odvozen `CPrjnameApp` třídy z `CWinApp` a deklaruje `InitInstance` – členská funkce. Pro ovládací prvek `CPrjnameApp` je třída odvozená z `COleControlModule`.|  
|*Projname*sada|Zdrojový soubor hlavní aplikace. Vytvoří jeden objekt třídy `CPrjnameApp`, který je odvozen z `CWinApp`a přepíše `InitInstance` – členská funkce.<br /><br /> Pro spustitelné soubory `CPrjnameApp::InitInstance` provede několik věcí. Zaregistruje šablony dokumentů, které slouží jako propojení mezi dokumenty a zobrazeními; vytvoří okno rámce; a vytvoří prázdného dokumentu (nebo otevře dokument, pokud je zadaná jako argument příkazového řádku do aplikace).<br /><br /> Pro ovládací prvky ActiveX (dříve OLE) a knihoven DLL, `CProjNameApp::InitInstance` zaregistruje objekt factory ovládacího prvku s OLE voláním `COleObjectFactory::RegisterAll` a zavolá `AfxOLEInit`. Kromě toho – členská funkce `CProjNameApp::ExitInstance` slouží k uvolnění z paměti pomocí volání ovládacího prvku **AfxOleTerm**.<br /><br /> Tento soubor také zaregistruje a zrušení registrace ovládacího prvku v databázi registrace Windows implementací `DllRegisterServer` a `DllUnregisterServer` funkce.|  
|*Projname*ctrl.h, *Projname*ctrl.cpp|Deklarace a implementovat `CProjnameCtrl` třídy. `CProjnameCtrl`je odvozený od `COleControl`, a kostru implementace některé členských funkcí inicializovat, kreslení a serializaci, které jsou definovány (načíst a uložte) ovládacího prvku. Rovněž jsou definovány zprávy, události a expediční mapy.|  
|*Projname*dlg.cpp, *Projname*dlg.h|Vytvořit, pokud se rozhodnete dialogové aplikace. Soubory odvozují a implementovat třídu dialogové okno s názvem `CProjnameDlg`a obsahují kostru členů funkcí k inicializaci dialogové okno a provádějí výměna dialogových dat (DDX). Vlastní o třídy dialogového okna je také umístěna v těchto souborech místo v *Projname*sada.|  
|Dlgproxy.cpp Dlgproxy.h|V dialogu založený program, implementaci a hlavičky souboru pro třídu proxy automatizace projektu pro hlavní dialogové okno. Používá se jen pokud jste vybrali podporu automatizace.|  
|*Projname*doc.cpp, *Projname*doc.h|Odvození a implementovat třídu dokument s názvem `CProjnameDoc`a zahrnovat kostru členů funkcí k inicializaci dokumentu, serializaci (uložení a načtení) dokumentu a implementaci ladění diagnostiky.|  
|*Projname*set.h/.cpp|Vytvoří, pokud vytvoříte program, který podporuje databázi a obsahuje třídu sady záznamů.|  
|*Projname*view.cpp, *Projname*view.h|Odvodí a implementuje zobrazení třídy s názvem `CProjnameView`, který se používá k zobrazení a tisku dat dokumentu. `CProjnameView` Třída je odvozena z jedné z následujících tříd MFC:<br /><br /> -   [CEditView](../mfc/reference/ceditview-class.md)<br />-   [Třídy CFormView](../mfc/reference/cformview-class.md)<br />-   [CRecordView](../mfc/reference/crecordview-class.md)<br />-   [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)<br />-   [CTreeView](../mfc/reference/ctreeview-class.md)<br />-   [CListView](../mfc/reference/clistview-class.md)<br />-   [Cricheditview –](../mfc/reference/cricheditview-class.md)<br />-   [CScrollView](../mfc/reference/cscrollview-class.md)<br />-   [CView](../mfc/reference/cview-class.md)<br />-   [CHTMLView](../mfc/reference/chtmlview-class.md)<br />-   [CHTMLEditView](../mfc/reference/chtmleditview-class.md)<br /><br /> Třídy zobrazení projektu obsahuje kostru členů funkcí k vykreslení zobrazení a implementaci ladění diagnostiky. Pokud jste povolili podporu pro tisk, pak map zpráv položky jsou přidány pro tisk, nastavení tisku a příkazy zpráv náhledu tisku. Tyto položky volání odpovídající členské funkce v základní třídě.|  
|*Projname*PropPage.h, *Projname*PropPage.cpp|Deklarace a implementovat `CProjnamePropPage` třídy. `CProjnamePropPage`je odvozený od `COlePropertyPage` a kostry členské funkce, `DoDataExchange`, je určena k implementaci výměny dat a ověřování.|  
|IPframe.cpp IPframe.h|Vytvoří, pokud je vybrána možnost Mini serveru nebo Full-Server v Průvodci aplikace **Možnosti automatizace** (krok 3 6). Soubory odvozují a implementaci třídy oken s rámečkem na místě, s názvem **CInPlaceFrame která v případě**, používá server je v místě aktivován kontejnerem programu.|  
|Mainfrm.cpp Mainfrm.h|Odvození **CMainFrame** třída buď z [CFrameWnd](../mfc/reference/cframewnd-class.md) (pro aplikace SDI) nebo [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) (pro aplikace MDI). **CMainFrame** třída zpracovává vytvoření tlačítka panelu nástrojů a na stavovém řádku, pokud odpovídající možnosti jsou vybrány v Průvodci aplikace **možnosti aplikace** (krok 4 6). Informace o používání **CMainFrame**, najdete v části [třídy oken s rámečkem vytvořené průvodcem aplikací](../mfc/frame-window-classes-created-by-the-application-wizard.md).|  
|Childfrm.cpp Childfrm.h|Odvození **CChildFrame** třídy z [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md). **CChildFrame** třída se používá pro okna s rámečkem MDI dokumentu. Pokud vyberete možnost MDI se vždy vytváří tyto soubory.|  
  
## <a name="see-also"></a>Viz také  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček](../ide/atl-program-or-control-source-and-header-files.md)   
 [CLR – projekty](../ide/files-created-for-clr-projects.md)