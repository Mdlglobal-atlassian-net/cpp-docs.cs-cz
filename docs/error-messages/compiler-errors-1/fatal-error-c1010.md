---
title: "Závažná chyba C1010 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1010
dev_langs:
- C++
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b2123118be2a8a382f6b718499c5af16f88d111
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1010"></a>Závažná chyba C1010
Neočekávaný konec souboru při hledání předkompilovaných hlaviček. Nezapomněli jste přidat ' #include se ke zdroji?  
  
 Vložené soubory zadaným [/Yu](../../build/reference/yu-use-precompiled-header-file.md) není uveden ve zdrojovém souboru.  Tato možnost je povolená ve výchozím nastavení většina typy projektů Visual C++ a "stdafx.h" je výchozí zahrnout soubor určený touto tuto možnost.  
  
 V prostředí Visual Studio použijte jednu z následujících metod Chcete-li vyřešit tuto chybu:  
  
-   Pokud nepoužijete předkompilovaných hlaviček v projektu, nastavte **vytvoření/použití předkompilovaných hlaviček** vlastnost zdrojové soubory k **není použití předkompilovaných hlaviček**. Pokud chcete nastavit tuto možnost kompilátoru, postupujte takto:  
  
    1.  V podokně Průzkumník řešení projektu klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti**.  
  
    2.  V levém podokně klikněte **C/C++** složky.  
  
    3.  Klikněte **předkompilovaných hlaviček** uzlu.  
  
    4.  V pravém podokně klikněte na **vytvoření nebo použití předkompilovaných hlaviček**a potom klikněte na **není použití předkompilovaných hlaviček**.  
  
-   Ujistěte se, že máte není nechtěně odstranit, přejmenovat nebo odebrat záhlaví souboru (ve výchozím nastavení, stdafx.h) z aktuálního projektu. Tento soubor také musí být součástí před jakýkoli jiný kód ve zdrojových souborech pomocí **#include "stdafx.h"**. (Tento soubor hlaviček je zadán jako **vytvořit nebo použít PCH prostřednictvím soubor** vlastnosti projektu)