---
title: "Použití ovládacích prvků posuvník | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4fdab6a7fae25845da81ee7263e045e50951f557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-slider-controls"></a>Použití ovládacích prvků posuvník
Typické použití ovládacího prvku posuvník se následující níže:  
  
-   Ovládací prvek je vytvořen. Pokud ovládací prvek je zadané v poli šablony dialogového okna, je vytvoření automaticky při vytvoření dialogové okno. (Byste měli mít [CSliderCtrl](../mfc/reference/csliderctrl-class.md) člena v vlastní třídy dialogového okna, která odpovídá do ovládacího prvku posuvník.) Alternativně můžete použít [vytvořit](../mfc/reference/csliderctrl-class.md#create) – členská funkce vytvoření ovládacího prvku jako podřízeného okna časového období.  
  
-   Volání různé sady členské funkce pro nastavení hodnot pro ovládací prvek. Změny, které můžete provést zahrnují nastavení minimální a maximální pozice pro posuvník, kreslení osové značky, nastavení výběru rozsahu a přemístění posuvníku. Pro ovládací prvky v dialogovém okně, je vhodná doba na k tomu v dialogovém okně [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkce.  
  
-   Jako uživatel pracuje s ovládacím prvkem, odešle různých zpráv s oznámením. Můžete rozbalit hodnota posuvníku z ovládacího prvku voláním [GetPos](../mfc/reference/csliderctrl-class.md#getpos) – členská funkce.  
  
-   Když jste hotovi s ovládacím prvkem, budete muset zkontrolujte, zda že je správně zničena. Pokud je v ovládacím prvku posuvník v dialogovém okně, jeho a `CSliderCtrl` objektu budou automaticky zničena. Pokud ne, musíte zajistit, aby obě ovládacího prvku a `CSliderCtrl` objekt jsou správně zničena.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

