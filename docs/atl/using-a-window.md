---
title: Pomocí okna (ATL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44b9988c0ecde4d0aee917fea686ec6511473318
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37847921"
---
# <a name="using-a-window"></a>Použití okna
Třída [cwindow –](../atl/reference/cwindow-class.md) umožňuje použít okno. Jakmile připojíte okno `CWindow` objektu, můžete volat `CWindow` metody pro manipulaci s okna. `CWindow` také obsahuje operátor HWND pro převod `CWindow` objekt popisovačem HWND. Proto můžete předat `CWindow` objekt má všechny funkce, které vyžaduje popisovač okna. Můžete snadno kombinovat `CWindow` volání metod a volání funkce Win32, bez vytvoření všechny dočasné objekty.  
  
 Protože `CWindow` má jenom dvě datový člen (popisovač okna a výchozích dimenzí), nepředstavuje režijní náklady na kód. Kromě toho řadu `CWindow` metody jednoduše zabalit odpovídající funkce rozhraní Win32 API. S použitím `CWindow`, člen HWND automaticky předá funkci Win32.  
  
 Kromě použití `CWindow` přímo, můžete také odvodit z něj přidejte data nebo kód do vaší třídy. ATL samotné odvozuje tři třídy z `CWindow`: [CWindowImpl](../atl/implementing-a-window.md), [CDialogImpl](../atl/implementing-a-dialog-box.md), a [ccontainedwindowt –](../atl/using-contained-windows.md).  
  
## <a name="see-also"></a>Viz také  
 [Třídy oken](../atl/atl-window-classes.md)

