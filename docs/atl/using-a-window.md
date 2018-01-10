---
title: "Pomocí okna (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a2be573e10190b385274de9afab498c77a094550
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-a-window"></a>Pomocí okna
Třída [CWindow](../atl/reference/cwindow-class.md) umožňuje použít okno. Po připojení a údržbu za účelem `CWindow` objektu, pak můžete volat `CWindow` metody pro manipulaci s okna. `CWindow`obsahuje také `HWND` operátor převést `CWindow` do objektu `HWND`. Proto můžete předat `CWindow` objekt všechny funkce, která vyžaduje popisovač pro okno. Je možné snadno kombinovat `CWindow` volání metod a volání funkce Win32, aniž by jakékoli dočasné objekty.  
  
 Protože `CWindow` má jenom dvě data člena (popisovač okna a výchozí dimenze), neuplatňuje režijní náklady na kód. Kromě toho řadu `CWindow` metody jednoduše zabalit odpovídající funkce rozhraní API Win32. Pomocí `CWindow`, `HWND` člen je automaticky předá funkci Win32.  
  
 Kromě používání `CWindow` přímo, můžete také odvodit z něj chcete-li přidat data nebo kódu do vaší třídy. ATL samotné odvozena ze tří tříd `CWindow`: [CWindowImpl](../atl/implementing-a-window.md), [CDialogImpl](../atl/implementing-a-dialog-box.md), a [CContainedWindowT](../atl/using-contained-windows.md).  
  
## <a name="see-also"></a>Viz také  
 [Třídy oken](../atl/atl-window-classes.md)

