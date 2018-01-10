---
title: "Třídy ovládacích pruhů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.control
dev_langs: C++
helpviewer_keywords: control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44fcecbf1d7ddb6c46469f25349d972c8b317809
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="control-bar-classes"></a>Třídy ovládacích pruhů
Ovládací pruhy jsou připojené k okně s rámečkem. Obsahují tlačítka, stav podokna nebo šablony dialogového okna. Plovoucí ovládací pruhy, označované taky jako nástroj palety, jsou implementované připojení, aby [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) objektu.  
  
## <a name="framework-control-bars"></a>Framework ovládací pruhy  
 Tyto ovládací pruhy jsou nedílnou součástí rozhraní MFC framework. Jsou snadněji používat a výkonnější než Windows řízení řádky, protože jsou integrované s rozhraní. Většina aplikací MFC použijte tyto ovládací pruhy, ne ovládací pruhy systému Windows.  
  
 [Ccontrolbar –](../mfc/reference/ccontrolbar-class.md)  
 Základní třída pro MFC – ovládací pruhy uvedené v této části. Ovládací prvek panelu je okno zarovnání na hranu okně s rámečkem. Ovládací prvek panelu obsahuje buď `HWND`– na základě podřízené ovládací prvky nebo ovládací prvky nejsou založené na `HWND`, jako jsou tlačítka panelu nástrojů.  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 Ovládací prvek panel, který je založený na šabloně dialogové okno pole.  
  
 [CReBar](../mfc/reference/crebar-class.md)  
 Podporuje panel nástrojů, který může obsahovat další podřízené windows ve formuláři ovládací prvky.  
  
 [Ctoolbar –](../mfc/reference/ctoolbar-class.md)  
 Na základě windows ovládací prvek panelu nástrojů, které obsahují příkazová tlačítka rastrového obrázku není `HWND`. Tato třída slouží většinu aplikací MFC místo `CToolBarCtrl`.  
  
 [Cstatusbar –](../mfc/reference/cstatusbar-class.md)  
 Základní třída pro ovládací prvek windows stavového řádku. Tato třída slouží většinu aplikací MFC místo `CStatusBarCtrl`.  
  
## <a name="windows-control-bars"></a>Windows ovládací pruhy  
 Tyto ovládací pruhy jsou dynamické obálek pro odpovídající ovládací prvky Windows. Vzhledem k tomu, že jejich nejsou integraci rozhraní, jsou obtížnější než ovládací pruhy dříve uvedené. Většina aplikací MFC použijte ovládací pruhy dříve uvedené.  
  
 [Crebarctrl –](../mfc/reference/crebarctrl-class.md)  
 Implementuje interního řízení `CRebar` objektu.  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 Vodorovné okno obvykle rozdělené do podokna, ve kterých se aplikace můžete zobrazit informace o stavu.  
  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 Poskytuje funkci Windows běžné ovládací prvek panelu nástrojů.  
  
## <a name="related-classes"></a>Související třídy  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 Malé místní okno, které zobrazuje jeden řádek textu popisující účel nástroj v aplikaci.  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 Zpracovává trvalé úložiště dat o stavu pro ovládací pruhy ukotvení.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

