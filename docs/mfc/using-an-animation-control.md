---
title: "Použití ovládacího prvku animace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d06770c13a3150bc291baa296aec225b9ab28e5a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-an-animation-control"></a>Použití ovládacího prvku animace
Typické použití ovládacího prvku animace se následující níže:  
  
-   Ovládací prvek je vytvořen. Pokud ovládací prvek je zadané v poli šablony dialogového okna, je vytvoření automaticky při vytvoření dialogové okno. (Byste měli mít [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) člena v vlastní třídy dialogového okna, která odpovídá do ovládacího prvku animace.) Alternativně můžete použít [vytvořit](../mfc/reference/canimatectrl-class.md#create) – členská funkce vytvoření ovládacího prvku jako podřízeného okna časového období.  
  
-   Načtení souborů AVI klip do ovládacího prvku animace voláním [otevřete](../mfc/reference/canimatectrl-class.md#open) – členská funkce. Pokud vaše animace ovládací prvek v dialogovém okně, je vhodná k tomu ve třídě dialog [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkce.  
  
-   Přehrání klip voláním [přehrání](../mfc/reference/canimatectrl-class.md#play) – členská funkce. Pokud vaše animace ovládací prvek v dialogovém okně, je vhodná k tomu ve třídě dialog **OnInitDialog** funkce. Volání metody **přehrání** není nutné v případě, že se má ovládací prvek animace `ACS_AUTOPLAY` styl sady.  
  
-   Pokud chcete zobrazit části klip nebo může být snímek po snímku, použijte `Seek` – členská funkce. Chcete-li zastavit klip, který je přehrávání, použijte `Stop` – členská funkce.  
  
-   Pokud nechcete po odstranění ovládacího prvku hned, odeberte klip z paměti voláním **Zavřít** – členská funkce.  
  
-   Pokud je ovládacího prvku animace v dialogovém okně, jeho a `CAnimateCtrl` objektu budou automaticky zničena. Pokud ne, musíte zajistit, aby obě ovládacího prvku a `CAnimateCtrl` objekt jsou správně zničena. Zničení ovládacího prvku automaticky zavře klip souborů AVI.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

