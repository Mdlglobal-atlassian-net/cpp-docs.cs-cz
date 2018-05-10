---
title: Předdefinované symboly ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c00487b2bb7c7a67dfb81ffb638f5a46fc611bc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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