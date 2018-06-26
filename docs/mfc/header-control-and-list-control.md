---
title: Ovládací prvky záhlaví a seznam | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acee0508243f468f41c645a0cde825ca7c828657
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931591"
---
# <a name="header-control-and-list-control"></a>Ovládací prvky záhlaví a seznam
Ve většině případů budete používat ovládací prvek záhlaví, který je součástí [CListCtrl](../mfc/reference/clistctrl-class.md) nebo [CListView](../mfc/reference/clistview-class.md) objektu. Existují však případech, kdy je žádoucí, jako je například manipulace s daty, uspořádané do sloupců nebo řádků, objekt ovládacího prvku záhlaví samostatné [CView](../mfc/reference/cview-class.md)-odvozené objektu. V takových případech musíte větší kontrolu nad vzhledem a výchozí chování ovládacího prvku záhlaví embedded.  
  
 V případě běžné, že chcete ovládacím prvkem záhlaví zajistit standard, výchozí chování, můžete chtít použít [CListCtrl](../mfc/reference/clistctrl-class.md) nebo [CListView](../mfc/reference/clistview-class.md) místo. Použití `CListCtrl` když chcete, aby funkce ovládacího prvku záhlaví výchozí vložených v ovládacím prvku běžné zobrazení seznamu. Použití [CListView](../mfc/reference/clistview-class.md) když chcete, aby funkce ovládacího prvku záhlaví výchozí vložených v zobrazení objektu.  
  
> [!NOTE]
>  Tyto ovládací prvky obsahovat ovládacím prvkem záhlaví předdefinované jenom, pokud zobrazení ovládacího prvku seznam je vytvořený pomocí **LVS_REPORT** stylu.  
  
 Ve většině případů lze upravit vzhled ovládacího prvku záhlaví embedded změnou styly nadřazeného ovládacího prvku zobrazení seznamu. Kromě toho je možné získat informace o ovládacím prvku záhlaví prostřednictvím členských funkcí nadřazeného ovládacího prvku zobrazení seznamu. Pro úplnou kontrolu a přístupu, atributy a styly ovládacího prvku embedded záhlaví, ale doporučujeme získat ukazatel na objekt ovládacího prvku záhlaví.  
  
 Objekt ovládacího prvku záhlaví embedded lze přistupovat z buď `CListCtrl` nebo `CListView` pomocí volání do příslušné třídy `GetHeaderCtrl` – členská funkce. Následující kód ukazuje toto:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Použití seznamů obrázků s ovládacími prvky záhlaví](../mfc/using-image-lists-with-header-controls.md)  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

