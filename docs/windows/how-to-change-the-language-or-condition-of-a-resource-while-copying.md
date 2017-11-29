---
title: "Postupy: Změna jazyka nebo podmínky prostředku během kopírování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.resvw.resource.changing
dev_langs: C++
helpviewer_keywords:
- Language property
- condition property of resource
ms.assetid: 8f622ab0-bac2-468f-ae70-78911afc4759
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 966dace3ce94792ca545ea279bafb7ae8587045f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-change-the-language-or-condition-of-a-resource-while-copying"></a>Postupy: Změna jazyka nebo podmínky prostředku během kopírování
Při kopírování v prostředku, můžete změnit jeho vlastnost jazyka nebo podmínky vlastnost nebo obojí.  
  
-   Jazyk prostředku identifikuje právě tedy jazyk pro prostředek. Toto je používáno [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) k identifikaci prostředků, pro kterou se díváte. (Však prostředků může mít rozdíly pro každý jazyk, který nesouvisí se text, například akcelerátorů, které může fungovat jenom na japonské klávesnici nebo rastrového obrázku, který může být pouze vhodné pro čínštinu lokalizované sestavení atd.)  
  
-   Podmínka ve zdroji je definovaný symbol, který identifikuje podmínce, pod kterým má být použita tato konkrétní kopie prostředku.  
  
 Jazyk a podmínky prostředku se zobrazí v závorkách za názvem prostředku v okně pracovního prostoru. V tomto příkladu používá prostředek s názvem IDD_AboutBox finština jako svůj jazyk a jeho podmínka je XX33.  
  
```  
IDD_AboutBox (Finnish - XX33)  
```  
  
### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Kopírovat na existující prostředek a změnit jeho jazyka nebo podmínky  
  
1.  V souboru .rc nebo v [zobrazení prostředků](../windows/resource-view-window.md) okna, klikněte pravým tlačítkem na prostředků, kterou chcete zkopírovat.  
  
2.  Zvolte **vložit kopii** z místní nabídky.  
  
3.  V **vložit kopii** dialogové okno:  
  
    -   Pro **jazyk** vyberte jazyk.  
  
    -   V **podmínku** zadejte podmínku.  
  

  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Postupy: kopírování prostředků](../windows/how-to-copy-resources.md)   
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)