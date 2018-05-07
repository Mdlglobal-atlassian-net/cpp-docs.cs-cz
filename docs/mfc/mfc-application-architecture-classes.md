---
title: Třídy architektury aplikace MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1174a994f345f4b7733e82603b5a49ed8977651
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-application-architecture-classes"></a>Třídy architektury aplikace MFC
Třídy v této kategorii přispívat k architektuře framework aplikace. Si poskytují funkce, které jsou společné pro většinu aplikací. Vyplňte rozhraní přidat další funkce specifické pro aplikaci. Obvykle je to nové třídy odvozené od třídy architektury a následným přidáním nové členy nebo přepsání existující členské funkce.  
  
 [Průvodci aplikací](../mfc/reference/mfc-application-wizard.md) generovat několik typů aplikací, které všechny používají rozhraní různými způsoby. SDI (rozhraní s jedním dokumentem) a aplikace MDI (rozhraní více dokumentů) plně využívat součástí rozhraní nazývá document/view – architektura. Jiné typy aplikací, jako je například aplikace založené na dialogové okno, založené na formulářích aplikacemi a knihovnami DLL, použijte jenom některé z funkcí document/view – architektura.  
  
 Document/view – aplikace obsahují jednu nebo více sad dokumentů, zobrazení a oken s rámečkem. Objekt šablony dokumentu přidruží třídy pro každou sadu dokument/zobrazení/rámce.  
  
 I když nemáte použít document/view – architektura v aplikaci MFC, existuje několik výhod tak. MFC OLE kontejneru a server podporu je založená na architektuře document/view, jako je podpora tisku a přehled tisku.  
  
 Všechny aplikace MFC mít aspoň dva objekty: objekt aplikace odvozené od [CWinApp](../mfc/reference/cwinapp-class.md)a některé řazení objektu hlavní okno (často nepřímo) odvozené z [CWnd](../mfc/reference/cwnd-class.md). (Nejčastěji hlavní okno je odvozený od [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), nebo [CDialog](../mfc/reference/cdialog-class.md), které jsou odvozeny od `CWnd`.)  
  
 Aplikace, které používají document/view – architektura obsahovat další objekty. Hlavní objekty jsou:  
  
-   Objekt aplikace odvozené od třídy [CWinApp](../mfc/reference/cwinapp-class.md), jak je uvedeno nahoře.  
  
-   Jeden nebo více objektů dokumentu třídy odvozené od třídy [CDocument](../mfc/reference/cdocument-class.md). Objekty třídy dokumentu jsou zodpovědní za interního vyjádření dat s nimi manipulovat, v zobrazení. Mohou být přidruženy datový soubor.  
  
-   Jeden nebo více zobrazení objektů odvozených od třídy [CView](../mfc/reference/cview-class.md). Každé zobrazení je okno, které je připojený k dokumentu a přidružené okně s rámečkem. Zobrazení zobrazit a upravit data obsažená v objektu třídy dokumentu.  
  
 Document/view – aplikace také obsahují okna s rámečkem (odvozený z [CFrameWnd](../mfc/reference/cframewnd-class.md)) a šablony v dokumentu (odvozený z [CDocTemplate](../mfc/reference/cdoctemplate-class.md)).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

