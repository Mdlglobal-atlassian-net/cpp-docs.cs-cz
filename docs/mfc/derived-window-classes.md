---
title: Odvozené třídy oken | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eddc6c59190856d09eae75c6f4314c902740092f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351490"
---
# <a name="derived-window-classes"></a>Odvozené třídy oken
Můžete vytvořit windows přímo z [CWnd](../mfc/reference/cwnd-class.md), nebo odvozovat nové okno z `CWnd`. Toto je, jak obvykle vytvoříte vlastní vlastní windows. Většina windows používá v rámci programu jsou však místo toho vytvářeny z jednoho z `CWnd`-odvozené třídy oken s rámečkem poskytl MFC.  
  
## <a name="frame-window-classes"></a>Třídy oken s rámečkem  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 Použít pro okna s rámečkem SDI, které rámce jednotlivý dokument a jeho zobrazení. Okně s rámečkem se hlavního rámce okna pro aplikace a okně s rámečkem v aktuálním dokumentu.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 Použít jako hlavní okno rámce pro aplikace MDI. Hlavní okno rámce je kontejner pro všechny oken MDI dokumentu a sdílí jeho řádku nabídek s nimi. Rámec okna MDI je okno nejvyšší úrovně, který se zobrazí na ploše.  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 Použít pro jednotlivé dokumenty v hlavního rámce okna MDI otevřít. Každý dokument a jeho zobrazení se rámcová podle rámce okna MDI podřízené obsažený v hlavního rámce okna MDI. Podřízená okna MDI mnohem vypadá typické rámce okna, ale je obsažený v rámci okna aplikace MDI místo uložený na ploše. Podřízeného okna MDI však chybí řádku nabídek své vlastní a musejí sdílet panelu nabídek okna MDI rámce, který jej obsahuje.  
  
 Další informace najdete v tématu [okna s rámečkem](../mfc/frame-windows.md).  
  
## <a name="other-window-classes-derived-from-cwnd"></a>Další okno třídy odvozené od CWnd  
 Kromě okna s rámečkem, několik dalších hlavních kategorií systému windows jsou odvozeny od `CWnd`:  
  
 *Zobrazení*  
 Zobrazení jsou vytvořené pomocí `CWnd`-odvozené třídy [CView](../mfc/reference/cview-class.md) (nebo jeden z jejich odvozené třídy). Zobrazení je připojena k dokumentu a funguje jako zprostředkovatel mezi dokumentu a uživatele. Zobrazení je obvykle vyplní celé okno s rámečkem SDI nebo podřízené rámce okna MDI (nebo část se nevztahuje panelu nástrojů nebo stavového řádku klientské oblasti) klientské oblasti podřízeného okna (ne podřízeného MDI).  
  
 *Dialogová okna*  
 Dialogová okna jsou vytvořené pomocí `CWnd`-odvozené třídy [CDialog](../mfc/reference/cdialog-class.md).  
  
 *Formuláře*  
 Zobrazení formulářů na základě šablony dialogového okna prostředků, jako je například dialogových oken, jsou vytvořené pomocí třídy [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), nebo [CDaoRecordView](../mfc/reference/cdaorecordview-class.md).  
  
 *Ovládací prvky*  
 Ovládací prvky, např. tlačítka, seznamy a pole se seznamem jsou vytvořené pomocí jiných třídy odvozené od třídy `CWnd`. V tématu [řízení témata](../mfc/controls-mfc.md).  
  
 *Ovládací pruhy*  
 Podřízená okna, které obsahují ovládací prvky. Mezi příklady patří panely nástrojů a stavové řádky. V tématu [ovládací pruhy](../mfc/control-bars.md).  
  
## <a name="window-class-hierarchy"></a>Hierarchie tříd oken  
 Odkazovat [graf hierarchie MFC](../mfc/hierarchy-chart.md) v *odkaz knihovny MFC*. Zobrazení jsou vysvětlené v [Document/View – architektura](../mfc/document-view-architecture.md). Dialogová okna jsou vysvětlené v [dialogová okna](../mfc/dialog-boxes.md).  
  
## <a name="creating-your-own-special-purpose-window-classes"></a>Vytvoření vlastní třídy speciální oken  
 Kromě třídy oken, poskytuje knihovna tříd může být nutné speciální podřízená okna. K vytvoření takového okna, vytvořit vlastní [CWnd](../mfc/reference/cwnd-class.md)-odvozené třídy a nastavit jej jako podřízeného okna rámečkem nebo zobrazení. Berte v úvahu, že rozhraní spravuje rozsah klientské oblasti rámce okna dokumentu. Většina klientské oblasti spravuje zobrazení, ale jiné windows, jako je třeba Správa řádky nebo vlastními vlastní windows, může sdílet prostor s zobrazení. Budete muset interakci s mechanismy ve třídách [CView](../mfc/reference/cview-class.md) a [ccontrolbar –](../mfc/reference/ccontrolbar-class.md) pro umístění podřízená okna v okně s rámečkem klientské oblasti.  
  
 [Vytváření oken](../mfc/creating-windows.md) popisuje vytvoření okna objektů a jejich správa systému windows.  
  
## <a name="see-also"></a>Viz také  
 [Objekty oken](../mfc/window-objects.md)

