---
title: "Úvod do tříd oken ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 636fe8aa87b6880f5cda77fb46fc481d99d78a81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="introduction-to-atl-window-classes"></a>Úvod do tříd oken ATL
Následující třídy ATL jsou určené k implementaci a manipulaci s windows:  
  
-   [CWindow](../atl/reference/cwindow-class.md) umožňuje připojit popisovač okna pro `CWindow` objektu. Potom zavolejte `CWindow` metody pro manipulaci s okna.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) umožňuje implementovat nové okno a zpracování zpráv s mapy zpráv. Můžete vytvořit okno podle novou třídu, supertřídě existující třídy nebo podtřídou Windows existujícího okna.  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) umožňuje implementovat modální nebo dialogového okna bez režimu pole a proces zprávy s mapy zpráv.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) je předem třída, která implementuje časového období, jejichž mapy zpráv se nachází v jiné třídy. Pomocí `CContainedWindowT` umožňuje centralizovat zpracování zprávy do jedné třídy.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) umožňuje implementovat, dialogové okno (modální nebo nemodální), který hostuje ovládací prvky ActiveX.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) umožňuje implementovat modální dialogové okno s základních funkcí.  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) umožňuje implementovat okno, který je hostitelem ovládacího prvku ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) umožňuje implementovat okno, který je hostitelem licencované ovládací prvek ActiveX.  
  
 Kromě konkrétní okno třídy ATL poskytuje několik tříd, které jsou navržené tak, aby usnadňují implementace objektu knihovny ATL okno. Jsou to tyto:  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) spravuje informace novou třídu okna.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) a [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) nabízejí jednoduchý způsob standardizace vlastnosti objektu ATL okno.  
  
## <a name="see-also"></a>Viz také  
 [Třídy oken](../atl/atl-window-classes.md)

