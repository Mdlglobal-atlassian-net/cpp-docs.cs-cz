---
title: Závažná chyba C1010 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1010
dev_langs:
- C++
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf8af35b28cfa02bd2723ff3c78db04a27cc39ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198492"
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