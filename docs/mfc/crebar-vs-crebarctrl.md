---
title: CReBar vs. Crebarctrl – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CReBar
- CReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6d0b8df40676cc64c97a6bdef013321c404899f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344971"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar vs. CReBarCtrl
Poskytuje dvě třídy Vytvoření tyčová ocel MFC: [CReBar](../mfc/reference/crebar-class.md) a [crebarctrl –](../mfc/reference/crebarctrl-class.md) (který zabalí běžné ovládacího prvku Windows rozhraní API). **CReBar** poskytuje všechny funkce běžné prvku matrice a zpracovává mnoho vyžaduje obecná nastavení ovládacího prvku a struktury za vás.  
  
 `CReBarCtrl` představuje obálkovou třídu ovládacího prvku matrice Win32 a proto může být snazší implementovat, pokud nemáte v úmyslu pro integraci matrice do architektury MFC. Pokud budete chtít použít `CReBarCtrl` a integrovat matrice do architektury MFC, je nutné provést další péči manipulace ovládacího prvku matrice s knihovnou MFC komunikovat. Tato komunikace není složité. je však další práci, kterou je potřeba, když používáte **CReBar**.  
  
 Visual C++ nabízí dva způsoby, jak využít výhod běžného ovládacího prvku matrice.  
  
-   Vytvořte pomocí matrice **CReBar**a pak zavolají [CReBar::GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) získat přístup k `CReBarCtrl` členské funkce.  
  
    > [!NOTE]
    >  `CReBar::GetReBarCtrl` je vložená členské funkce, který vrhá **to** ukazatel matrice objektu. To znamená, že v době běhu volání funkce má žádné režijní náklady.  
  
-   Vytvořte pomocí matrice [crebarctrl –](../mfc/reference/crebarctrl-class.md)pro konstruktor.  
  
 Buď metoda získáte přístup k členské funkce ovládacího prvku matrice. Při volání `CReBar::GetReBarCtrl`, vrátí odkaz na `CReBarCtrl` objekt, můžete použít buď sadu členské funkce. V tématu [CReBar](../mfc/reference/crebar-class.md) informace o vytváření a vytváření matrice pomocí **CReBar**.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

