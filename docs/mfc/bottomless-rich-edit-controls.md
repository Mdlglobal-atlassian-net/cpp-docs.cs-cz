---
title: Ovládací prvky Rich Edit neomezené | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f2b08f6c04d345b4ae3ab32c6d0f17a1d8a4647
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="bottomless-rich-edit-controls"></a>Neomezené ovládací prvky pro úpravy s formátováním
Aplikace můžete změnit velikost ovládacího prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) podle potřeby tak, aby se vždy stejnou velikost jako jeho obsah. Ovládacího prvku RichEdit podporuje tato takzvané "neomezené" funkce odesláním jeho nadřazeného okna [EN_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787983) oznámení pokaždé, když se změní velikost jeho obsahu.  
  
 Při zpracování **EN_REQUESTRESIZE** oznámení, aplikace by měl změnit velikost ovládacího prvku do dimenzí v zadané [REQRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787950) struktury. Aplikace může také přesunout všechny informace téměř ovládacího prvku pro přizpůsobení ovládacího prvku změnu na výšku. Chcete-li změnit velikost ovládacího prvku, můžete použít `CWnd` funkce [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).  
  
 Můžete vynutit neomezené bohaté textové pole k odeslání **EN_REQUESTRESIZE** zprávy oznámení pomocí [RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize) – členská funkce. Tato zpráva se může hodit v [OnSize](../mfc/reference/cwnd-class.md#onsize) obslužné rutiny.  
  
 Pro příjem **EN_REQUESTRESIZE** zpráv s oznámením, musíte povolit oznámení pomocí `SetEventMask` – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

