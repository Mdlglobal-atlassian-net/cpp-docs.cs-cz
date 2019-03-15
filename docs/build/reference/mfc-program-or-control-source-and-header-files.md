---
title: Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
ms.openlocfilehash: a46fedc9f9bbc888e9b59d2ed313eaf7146394ff
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823060"
---
# <a name="mfc-program-or-control-source-and-header-files"></a>Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček

Následující soubory jsou vytvořeny při vytvoření projektu knihovny MFC v sadě Visual Studio, v závislosti na možnostech, které vyberete pro projekt, který vytvoříte. Například váš projekt obsahuje *název_projektu*dlg.cpp a *název_projektu*dlg.h soubory pouze v případě, že vytvoříte projekt založený na dialogové okno nebo třídy.

Všechny tyto soubory jsou umístěny v *název_projektu* adresář a soubory hlaviček (.h souborů), složku nebo zdrojové soubory (.cpp) složku v Průzkumníku řešení.

|Název souboru|Popis|
|---------------|-----------------|
|*Název_projektu*.h|Hlavní zahrnout soubor pro program nebo knihovnu DLL. Obsahuje všechny globální symboly a `#include` direktivy pro další hlavičkové soubory. Se odvozuje `CPrjnameApp` třídy z `CWinApp` a deklaruje `InitInstance` členskou funkci. Pro ovládací prvek `CPrjnameApp` je třída odvozena z `COleControlModule`.|
|*Projname*.cpp|Zdrojový soubor hlavního programu. Vytvoří jeden objekt třídy `CPrjnameApp`, který je odvozen z `CWinApp`a přepíše `InitInstance` členskou funkci.<br /><br /> Pro spustitelné soubory `CPrjnameApp::InitInstance` provádí několik operací. Registruje šablony dokumentů, které slouží jako propojení mezi dokumenty a zobrazeními; vytvoří hlavní okno rámce; Vytvoří prázdný dokument (nebo otevře dokument, pokud je zadaná jako argument příkazového řádku pro aplikaci).<br /><br /> Pro ovládací prvky ActiveX (dříve OLE) a knihoven DLL, `CProjNameApp::InitInstance` zaregistruje objekt factory ovládacího prvku OLE voláním `COleObjectFactory::RegisterAll` a zavolá `AfxOLEInit`. Kromě toho má členská funkce `CProjNameApp::ExitInstance` slouží k uvolnění z paměti pomocí volání do ovládacího prvku **AfxOleTerm**.<br /><br /> Tento soubor také zaregistruje a zruší registraci ovládacího prvku v registrační databázi Windows pomocí implementace `DllRegisterServer` a `DllUnregisterServer` funkce.|
|*Název_projektu*ctrl.h, *název_projektu*ctrl.cpp|Deklaruje a implementuje `CProjnameCtrl` třídy. `CProjnameCtrl` je odvozen z `COleControl`, a kostru implementace z některých členských funkcí inicializovat, kreslit a serializaci, které jsou definovány (načtení a uložení) ovládacího prvku. Také jsou definovány zprávy, události a expediční mapy.|
|*Název_projektu*dlg.cpp, *název_projektu*dlg.h|Vytvoří, pokud se rozhodnete aplikaci založené na dialogu. Soubory odvodit a implementovat dialogové třídy s názvem `CProjnameDlg`a zahrnovat kostru členské funkce pro inicializaci dialogového okna a provádět výměna dat dialogových oken (DDX). Vlastní o třídy dialogového okna je také umístěná v těchto souborech místo v *název_projektu*.cpp.|
|Dlgproxy.cpp, Dlgproxy.h|Do založené na dialogu program, provádění a záhlaví souboru projektu klientská automatizační třída proxy server pro hlavní dialog. Používá se pouze pokud jste vybrali podporu automatizace.|
|*Projname*doc.cpp, *Projname*doc.h|Odvodit a implementovat třídu dokumentu s názvem `CProjnameDoc`a zahrnovat kostru členské funkce, chcete-li inicializovat dokument, serializaci (Uložit a načíst) dokumentu a implementovat ladění a Diagnostika.|
|*Název_projektu*set.h/.cpp|Vytvoří, pokud vytvoříte program, který podporuje databázi a obsahuje třídy sady záznamů.|
|*Název_projektu*view.cpp, *název_projektu*view.h|Odvodit a implementovat třídu zobrazení s názvem `CProjnameView`, který se používá k zobrazení a tisku data dokumentu. `CProjnameView` Třídy je odvozen z jednoho z následujících tříd knihovny MFC:<br /><br />- [CEditView](../../mfc/reference/ceditview-class.md)<br />- [CFormView](../../mfc/reference/cformview-class.md)<br />- [CRecordView](../../mfc/reference/crecordview-class.md)<br />- [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)<br />- [CTreeView](../../mfc/reference/ctreeview-class.md)<br />- [CListView](../../mfc/reference/clistview-class.md)<br />- [CRichEditView](../../mfc/reference/cricheditview-class.md)<br />- [CScrollView](../../mfc/reference/cscrollview-class.md)<br />- [CView](../../mfc/reference/cview-class.md)<br />- [CHTMLView](../../mfc/reference/chtmlview-class.md)<br />- [CHTMLEditView](../../mfc/reference/chtmleditview-class.md)<br /><br /> Zobrazit třídu v projektu obsahuje kostru členské funkce k vykreslení zobrazení a implementaci, ladění a Diagnostika. Pokud je povolena podpora pro tisk, pak položky mapování zpráv jsou přidány pro tisk, nastavení tisku a Tisk zprávy příkazů ve verzi preview. Tyto položky volat odpovídající člen funkce v základní třídě.|
|*Název_projektu*PropPage.h, *název_projektu*PropPage.cpp|Deklaruje a implementuje `CProjnamePropPage` třídy. `CProjnamePropPage` je odvozen z `COlePropertyPage` a kostru členskou funkci, `DoDataExchange`, je k dispozici k implementaci výměny dat a ověřování.|
|IPframe.cpp, IPframe.h|Pokud je vybrána možnost Mini serveru nebo úplný Server v Průvodci aplikací **Možnosti automatizace** stránky (krok 3 ze 6). Soubory odvodit a implementovat třídu okna rámečkem na místě, s názvem **CInPlaceFrame která v případě**, používá server je na místě aktivoval program kontejneru.|
|Mainfrm.cpp, Mainfrm.h|Odvodit **CMainFrame** třídy buď z [CFrameWnd](../../mfc/reference/cframewnd-class.md) (pro aplikace SDI) nebo [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md) (pro aplikace MDI). **CMainFrame** třída zpracovává vytváření tlačítek panelu nástrojů a stavový řádek, pokud se vybere odpovídající možnosti v Průvodci aplikací **možnosti aplikace** stránky (krok 4 6). Informace o používání **CMainFrame**, naleznete v tématu [třídy oken s rámečkem vytvořené průvodcem aplikací](../../mfc/frame-window-classes-created-by-the-application-wizard.md).|
|Childfrm.cpp, Childfrm.h|Odvodit **CChildFrame** třídy z [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md). **CChildFrame** třída se používá pro oken s rámečkem v dokumentu MDI. Tyto soubory jsou vytvořeny vždy, pokud vyberete možnost MDI.|

## <a name="see-also"></a>Viz také:

[Typy souborů vytvořených pro projekty Visual C++](file-types-created-for-visual-cpp-projects.md)<br>
[Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček](atl-program-or-control-source-and-header-files.md)<br>
[Projekty CLR](files-created-for-clr-projects.md)
