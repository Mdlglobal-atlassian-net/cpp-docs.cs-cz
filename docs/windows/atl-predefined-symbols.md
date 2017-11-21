---
title: "Předdefinované symboly ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- symbols, ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: daa70cb5bc1bcb1fef77930a9955f7afbd618f67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atl-predefined-symbols"></a>Předdefinované symboly ATL
Tyto symboly jsou definovány v ATL hlavičkových souborů, ale podporují standardní funkce aplikací systému Windows a akce. Tyto symboly jsou používány především s dialogová okna. Pokud pracujete s dialogů a ovládacích prvků v [editoru dialogového okna](../windows/dialog-editor.md), tyto symboly se zobrazí v okně vlastnosti přidružené k běžné ovládací prvky. Například pokud vašem dialogovém okně tlačítko Zrušit, tento příkaz bude spojený s symbol IDCANCEL v [vlastnosti – okno](/visualstudio/ide/reference/properties-window).  
  
|||  
|-|-|  
|IDABORT|Řízení: Tlačítko dialogovém přerušení|  
|IDC_STATIC|Řízení: Statické ovládací prvek|  
|IDCANCEL|Ovládacího prvku: Tlačítko Zrušit pole dialogové okno|  
|IDIGNORE|Řízení: Tlačítko dialogovém ignorovat|  
|IDNO|Ovládací prvek: Žádné tlačítko dialogu|  
|IDOK|Ovládacího prvku: Tlačítko pole OK dialogové okno|  
|IDR_ACCELERATOR1|Prostředků: Tabulka akcelerátoru|  
|IDRETRY|Řízení: Tlačítko dialogovém opakování|  
|IDS_PROJNAME|Řetězec: Název aktuální aplikace|  
|IDYES|Ovládací prvek: Dialogové okno Ano tlačítko.|  
  
## <a name="requirements"></a>Požadavky  
 ATL  
  
## <a name="see-also"></a>Viz také  
 [ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)   
 [Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)