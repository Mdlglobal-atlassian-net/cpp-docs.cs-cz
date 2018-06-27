---
title: Použití ovládacího prvku animace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d6b6b07040fbece5fae24fb2ca6be8985695eb0
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950534"
---
# <a name="using-an-animation-control"></a>Použití ovládacího prvku animace
Typické použití ovládacího prvku animace se následující níže:  
  
-   Ovládací prvek je vytvořen. Pokud ovládací prvek je zadané v poli šablony dialogového okna, je vytvoření automaticky při vytvoření dialogové okno. (Byste měli mít [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) člena v vlastní třídy dialogového okna, která odpovídá do ovládacího prvku animace.) Alternativně můžete použít [vytvořit](../mfc/reference/canimatectrl-class.md#create) – členská funkce vytvoření ovládacího prvku jako podřízeného okna časového období.  
  
-   Načtení souborů AVI klip do ovládacího prvku animace voláním [otevřete](../mfc/reference/canimatectrl-class.md#open) – členská funkce. Pokud vaše animace ovládací prvek v dialogovém okně, je vhodná k tomu ve třídě dialog [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkce.  
  
-   Přehrání klip voláním [přehrání](../mfc/reference/canimatectrl-class.md#play) – členská funkce. Pokud vaše animace ovládací prvek v dialogovém okně, je vhodná k tomu ve třídě dialog `OnInitDialog` funkce. Volání metody `Play` není nutné, pokud má nastaven styl ACS_AUTOPLAY ovládacího prvku animace.  
  
-   Pokud chcete zobrazit části klip nebo může být snímek po snímku, použijte `Seek` – členská funkce. Chcete-li zastavit klip, který je přehrávání, použijte `Stop` – členská funkce.  
  
-   Pokud nechcete po odstranění ovládacího prvku hned, odeberte klip z paměti voláním `Close` – členská funkce.  
  
-   Pokud je ovládacího prvku animace v dialogovém okně, jeho a `CAnimateCtrl` objektu budou automaticky zničena. Pokud ne, musíte zajistit, aby obě ovládacího prvku a `CAnimateCtrl` objekt jsou správně zničena. Zničení ovládacího prvku automaticky zavře klip souborů AVI.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

