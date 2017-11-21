---
title: "Dialogové okno prostředek zahrnuje | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.resourceincludes
dev_langs: C++
helpviewer_keywords:
- Resource Includes dialog box
- rc files, changing storage
- symbol header files, changing
- compiling source code, including resources
- .rc files, changing storage
- symbol header files, read-only
- symbols, symbol header files
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: be954451335deef88ad459b9de6b865ff45ed909
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="resource-includes-dialog-box"></a>Dialogové okno Prostředek zahrnuje
Můžete použít **prostředek zahrnuje** dialogové okno Upravit v prostředí normální funkční uspořádání ukládání všechny prostředky v souboru projektu .rc a všechny [symboly](../windows/symbols-resource-identifiers.md) v Resource.h.  
  
 Chcete-li otevřít **prostředek zahrnuje** dialogové okno, klikněte pravým tlačítkem na .rc souboru v [zobrazení prostředků](../windows/resource-view-window.md), zvolte **prostředek zahrnuje** z místní nabídky.  
  
 **Soubor hlaviček symbolů**  
 Umožňuje změnit název souboru záhlaví, kde jsou uloženy definice symbolů pro váš soubor prostředků. Další informace najdete v tématu [změna názvy z soubory hlaviček symbolů](../windows/changing-the-names-of-symbol-header-files.md).  
  
 **Směrnice pro symboly jen pro čtení**  
 Umožňuje zahrnout soubory hlaviček, které obsahují znaky, které nesmí být měněny během relace úprav. Například můžete zahrnout soubor symbol, který sdílí několik projektů. Můžete použít také souborů .h MFC. Další informace najdete v tématu [zahrnutí sdílených (jen pro čtení) nebo vypočítat symboly](../windows/including-shared-read-only-or-calculated-symbols.md).  
  
 **Direktivy kompilace**  
 Umožňuje zahrnout soubory prostředků, které jsou vytvořené a upravit samostatně z prostředků v souboru hlavní prostředku, obsahují direktivy kompilaci (jako jsou ty, které podmíněně zahrnují prostředky), nebo obsahují prostředky ve vlastním formátu. Můžete taky pole direktivy kompilace pro zahrnutí standardní zdrojových souborů MFC. Další informace najdete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).  
  
> [!NOTE]
>  Položky do těchto polí se zobrazují v souboru .rc označeny `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, a `TEXTINCLUDE 3` v uvedeném pořadí. Další informace najdete v tématu [TN035: použití více zdrojových souborů a hlavičkových souborů pomocí aplikace Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).  
  
 Po provedení změn pomocí souborů prostředků **prostředek zahrnuje** dialogové okno, je potřeba soubor .rc zavřete a znovu ji změny se projeví. Další informace najdete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).  
  

  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Postupy: určení adresáře souborů k zahrnutí pro prostředky](../windows/how-to-specify-include-directories-for-resources.md)   
 [Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)   
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)