---
title: "Třídy společných dialogů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog classes [MFC]
- dialog boxes [MFC], Windows common dialogs
- common dialog boxes [MFC], common dialog classes
- common dialog classes [MFC]
- MFC dialog boxes [MFC], Windows common dialogs
- Windows common dialogs [MFC]
- dialog classes [MFC], common
- common dialog boxes [MFC]
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 50adbc6faa802802c36e18c614992341def06331
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="common-dialog-classes"></a>Společné třídy dialogových oken
Kromě třída [CDialog](../mfc/reference/cdialog-class.md), MFC poskytuje několik třídy odvozené od třídy `CDialog` zapouzdřují běžně používané dialogových oken, jak je znázorněno v následující tabulce. Dialogová okna zapouzdřené se používá označení "běžné dialogových oken" a jsou součástí Windows běžné dialogové okno knihovny (COMMDLG. KNIHOVNY DLL). Šablony dialogového okna prostředků a kód pro tyto třídy jsou uvedeny v systému Windows běžné dialogových oken, které jsou součástí systému Windows verze 3.1 nebo novější.  
  
### <a name="common-dialog-classes"></a>Společné třídy dialogových oken  
  
|Třídy odvozené dialogového okna|Účel|  
|--------------------------|-------------|  
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Umožňuje uživatele vyberte barvy.|  
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Umožňuje uživateli vybrat filename otevřít nebo uložit.|  
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Umožňuje, aby uživatel zahájit najít nebo nahradit operace v textovém souboru.|  
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Umožní uživateli zadat písmo.|  
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Umožní uživateli zadat informace pro tiskové úlohy.|  
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Tiskové vlastností systému Windows 2000.|  
  
 Další informace o společné třídy dialogových oken, najdete v části názvy jednotlivých tříd v *odkaz knihovny MFC*. MFC také poskytuje řadu standardního dialogového okna třídy používané pro OLE. Informace o těchto tříd naleznete v tématu základní třídy, [COleDialog](../mfc/reference/coledialog-class.md)v *odkaz knihovny MFC*.  
  
 Tří tříd v prostředí MFC mají podobné dialogové okno Vlastnosti. Informace o třídách [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), a [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), najdete v tématu třídy v *odkaz knihovny MFC*. Informace o třídě [CDialogBar](../mfc/reference/cdialogbar-class.md), najdete v části [dialogové pruhy](../mfc/dialog-bars.md).  
  
## <a name="see-also"></a>Viz také  
 [Dialogová okna](../mfc/dialog-boxes.md)   
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)   
 [Dialogová okna v prostředí OLE](../mfc/dialog-boxes-in-ole.md)

