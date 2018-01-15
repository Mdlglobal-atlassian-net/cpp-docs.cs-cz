---
title: "Dialogové pruhy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3d9d7319f23741f683e31cfd683a8ebd6d25acdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-bars"></a>Dialogové pruhy
Panel dialogového okna je panel nástrojů, typ z [ovládacích pruhů](../mfc/control-bars.md) , může obsahovat jakýkoli typ ovládacího prvku. Protože má charakteristiky nemodální dialogového okna, [CDialogBar](../mfc/reference/cdialogbar-class.md) objekt poskytuje výkonnější panelu nástrojů.  
  
 Existuje několik klíčových rozdílů mezi panelu nástrojů a `CDialogBar` objektu. A `CDialogBar` z prostředku šablony dialogového okna, které můžete vytvořit pomocí editoru dialogových oken Visual C++ a která může obsahovat jakýkoli typ ovládacího prvku systému Windows je vytvořen objekt. Uživatel může kartě z ovládacího prvku na ovládací prvek. A můžete určit zarovnání styl, chcete-li zarovnat dialogového pruhu s libovolnou část nadřazeného rámce okna nebo ponechejte na místě, pokud se změnila velikost nadřazené. Následující obrázek znázorňuje dialogového pruhu s různými ovládacích prvků.  
  
 ![Panel dialogového okna VC](../mfc/media/vc378t1.gif "vc378t1")  
Panel dialogového okna  
  
 V ostatních ohledech práce `CDialogBar` objektu je podobné jako u dialogového okna bez režimu. Použití editoru dialogových oken pro návrh a vytvoření prostředku dialogového okna.  
  
 Jedním z přednosti dialogové pruhy je, že obsahují ovládací prvky než tlačítka.  
  
 I když je normální, že se vlastní dialogové okno odvozovat z `CDialog`, můžete nezískávají obvykle vlastní třída pro panel dialogového okna. Dialogové pruhy, jako jsou rozšíření pro hlavní okno a všechny zprávy oznámení ovládacího prvku panel dialogového okna, **BN_CLICKED** nebo **EN_CHANGE**, budou odeslány do nadřazené dialogového okna panelu Hlavní okno.  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)   
 [Ukázka](../visual-cpp-samples.md)

