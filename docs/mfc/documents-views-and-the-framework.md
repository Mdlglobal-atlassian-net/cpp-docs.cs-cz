---
title: Dokumenty, zobrazení a framework
ms.date: 11/19/2018
helpviewer_keywords:
- document templates [MFC], template objects
- applications [MFC]
- MFC, application framework
- application objects [MFC], relation to other MFC objects
- documents [MFC]
- MFC, documents
- document objects [MFC], in relation to other MFC objects
- view objects [MFC], relation to other MFC objects
- MFC, views
- document/view architecture [MFC], about document/view architecture
- objects [MFC], MFC applications
- MFC object relationships
- thread objects [MFC]
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
ms.openlocfilehash: e59e8b69dcdf0bf3b22d4286ba4692558a11e096
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175753"
---
# <a name="documents-views-and-the-framework"></a>Dokumenty, zobrazení a framework

V srdci rozhraní MFC jsou pojmy dokumentů a zobrazení. Dokument je datový objekt, se kterým uživatel pracuje v relaci úpravy. Je vytvořena **nový** nebo **otevřít** příkaz **souboru** nabídce a je obvykle uložen v souboru. (Standardní knihovna MFC dokumenty, odvozené od třídy `CDocument`, se liší od aktivní dokumenty a složené dokumenty OLE.) Zobrazení je objekt window, pomocí kterého uživatel pracuje s dokumentem.

Jsou klíčové objekty v běžící aplikaci:

- Dokument nebo dokumenty.

   Dokumentové třídy (odvozený od [CDocument](../mfc/reference/cdocument-class.md)) určuje data vaší aplikace.

   Pokud chcete ve své aplikaci funkce OLE, odvodit vaše dokumentové třídy z [coledocument –](../mfc/reference/coledocument-class.md) nebo jednu z odvozených tříd, v závislosti na typu funkce, které potřebujete.

- Zobrazení nebo zobrazení.

   Zobrazit třídu (odvozený od [CView](../mfc/reference/cview-class.md)) je uživatele "okno na data." Zobrazit třídu řídí, jak uživatel vidí dat váš dokument a s ním pracuje. V některých případech může být vhodné dokument má více zobrazení data.

   Pokud potřebujete posouvání, jsou odvozeny z [cscrollview –](../mfc/reference/cscrollview-class.md). Pokud zobrazení obsahuje uživatelské rozhraní, které se zobrazuje ve prostředku šablony dialogového okna, jsou odvozeny z [CFormView](../mfc/reference/cformview-class.md). Pro jednoduché textových dat, použít nebo odvodit z [CEditView](../mfc/reference/ceditview-class.md). Pro aplikace založené na formulářích – přístup k datům, jako je například program zadávání dat, jsou odvozeny z [CRecordView](../mfc/reference/crecordview-class.md) (pro rozhraní ODBC). K dispozici jsou také třídy [CTreeView](../mfc/reference/ctreeview-class.md), [CListView](../mfc/reference/clistview-class.md), a [cricheditview –](../mfc/reference/cricheditview-class.md).

- Oken s rámečkem

   Zobrazení se zobrazí uvnitř "rámečkem v dokumentu." V aplikaci SDI okna rámce dokumentu je také "hlavní okno rámce" pro aplikaci. V aplikaci MDI okna dokumentu jsou podřízená okna zobrazena uvnitř okna hlavního rámce. Vaše třída odvozená hlavní okno rámce určuje stylů a další vlastnosti, které obsahují zobrazení oken s rámečkem. Pokud je potřeba upravit oken s rámečkem, jsou odvozeny z [CFrameWnd](../mfc/reference/cframewnd-class.md) přizpůsobení dokumentu okno rámce aplikace SDI. Jsou odvozeny z [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) přizpůsobení hlavní okno rámce pro aplikace MDI. Také odvodit třídu z [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) přizpůsobit každý jedinečných druh rámce okna dokumentu MDI, které vaše aplikace podporuje.

- Šablona dokumentu nebo šablony

   Šablona dokumentu orchestruje vytváření dokumenty, zobrazení a oken s rámečkem. Třída konkrétní šablonu dokumentu, odvozená od třídy [CDocTemplate](../mfc/reference/cdoctemplate-class.md), vytváří a spravuje všechny otevřené dokumenty jednoho typu. Aplikace, které podporují více než jeden typ dokumentu mají více šablon dokumentů. Použití třídy [csingledoctemplate –](../mfc/reference/csingledoctemplate-class.md) aplikace SDI nebo použití třídy [cmultidoctemplate –](../mfc/reference/cmultidoctemplate-class.md) pro aplikace MDI.

- Objekt aplikace

   Třída vaší aplikace (odvozený od [CWinApp](../mfc/reference/cwinapp-class.md)) ovládá všechny výše uvedené objekty a určuje chování aplikace, jako je například inicializace a vyčištění. Jedna aplikace a aplikaci pouze objekt vytváří a spravuje šablony dokumentů pro jakýkoliv dokument typy aplikace podporuje.

- Objekty vláken

   Pokud vaše aplikace vytváří samostatného vlákna provádění – například k provádění výpočtů na pozadí – použijete třídy odvozené od [CWinThread](../mfc/reference/cwinthread-class.md). [CWinApp](../mfc/reference/cwinapp-class.md) samotného je odvozen z `CWinThread` a představuje primární vlákno provádění (nebo hlavní proces) ve vaší aplikaci. Můžete také použít knihovnu MFC ve sekundárních vláken.

Ve spuštěné aplikaci tyto objekty kooperativně reagovat na akce uživatele, jsou technologicky propojené, tak, že příkazy a další zprávy. Objekt jednu aplikaci spravuje jeden nebo více šablon dokumentů. Každé šablony dokumentu vytvoří a spravuje jeden nebo více dokumentů (v závislosti na tom, zda je aplikace SDI nebo MDI). Uživatel prohlíží a provádí úpravy dokumentu prostřednictvím zobrazení obsaženo uvnitř okna rámce. Následující obrázek znázorňuje vztahy mezi těmito objekty pro aplikace SDI.

![Objekty v běžící aplikaci SDI](../mfc/media/vc386v1.gif "objekty v běžící aplikaci SDI") <br/>
Objekty v běžící aplikaci SDI

Zbývající část Tato řada článků vysvětluje, jak rozhraní framework nástroje, Průvodce aplikací knihovny MFC a editory prostředků vytvořit tyto objekty, jak spolu fungují a jak využít váš programování v. Dokumenty, zobrazení a oken s rámečkem jsou popsány podrobněji [objekty oken](../mfc/window-objects.md) a [architekturu Document/View](../mfc/document-view-architecture.md).

## <a name="see-also"></a>Viz také

[Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
