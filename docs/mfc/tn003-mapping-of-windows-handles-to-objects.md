---
title: "TN003: Obslužných rutin Windows na objekty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mapping
dev_langs:
- C++
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e53b2569b0da6bfa63c94adb7bb163e5bcd6b7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003Mapování obslužných rutin Windows na objekty
Tato poznámka se popisuje MFC rutiny, které podporují mapování Windows objekt popisovače C++ objektů.  
  
## <a name="the-problem"></a>Problém  
 Windows objekty jsou obvykle reprezentované pomocí různých [zpracování](http://msdn.microsoft.com/library/windows/desktop/aa383751) objektů MFC – třídy zabalení obslužné rutiny objekt Windows se objekty C++. Popisovač zabalení funkce knihovny tříd MFC umožňují najít C++ objekt, který zahrnuje Windows objekt, který má konkrétní popisovač. Ale někdy objekt nemá objekt obálky C++ a v těchto časech systém vytvoří dočasný objekt tak, aby fungoval jako obálky C++.  
  
 Windows objekty, které používají mapování zpracování jsou následující:  
  
-   HWND ([CWnd](../mfc/reference/cwnd-class.md) a `CWnd`-odvozených tříd)  
  
-   HDC ([CDC](../mfc/reference/cdc-class.md) a `CDC`-odvozených tříd)  
  
-   HMENU ([cmenu –](../mfc/reference/cmenu-class.md))  
  
-   HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))  
  
-   HBRUSH (`CGdiObject`)  
  
-   HFONT (`CGdiObject`)  
  
-   HBITMAP (`CGdiObject`)  
  
-   HPALETTE (`CGdiObject`)  
  
-   HRGN (`CGdiObject`)  
  
-   HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))  
  
-   SOCKET ([CSocket](../mfc/reference/csocket-class.md))  
  
 Zadaný popisovač na některý z těchto objektů, můžete najít MFC objekt, který zabalí popisovač voláním statickou metodu `FromHandle`. Například uděleno popisovačem HWND názvem `hWnd`, vrátí ukazatel na následující řádek `CWnd` který zabalí `hWnd`:  
  
```  
CWnd::FromHandle(hWnd)  
```  
  
 Pokud `hWnd` nemá objekt konkrétní obálku dočasného `CWnd` se vytvoří při zabalení `hWnd`. Díky tomu je možné získat platný objekt C++ od všech popisovač.  
  
 Až budete mít objekt obálky, můžete načíst jeho popisovač z veřejné členské proměnné obálkové třídy. U `CWnd`, `m_hWnd` obsahuje HWND pro tento objekt.  
  
## <a name="attaching-handles-to-mfc-objects"></a>Zpracovává se připojuje k objektům MFC  
 Vzhledem k nově vytvořený popisovač obálku objektu a popisovač na objekt Windows, můžete přidružit dva voláním `Attach` fungovat jako v následujícím příkladu:  
  
```  
CWnd myWnd;  
myWnd.Attach(hWnd);
```  
  
 Díky tomu položku v trvalé mapy přidružení `myWnd` a `hWnd`. Volání metody `CWnd::FromHandle(hWnd)` nyní vrátí ukazatel na `myWnd`. Když `myWnd` je odstranit, destruktoru automaticky zničí `hWnd` voláním Windows [destroywindow –](http://msdn.microsoft.com/library/windows/desktop/ms632682) funkce. Pokud to není žádoucí, `hWnd` musí být odpojit od `myWnd` před `myWnd` zničena (obvykle při opuštění oboru, kdy `myWnd` byl definován). `Detach` Metoda tomu.  
  
```  
myWnd.Detach();
```  
  
## <a name="more-about-temporary-objects"></a>Další informace o dočasné objekty  
 Dočasné objekty vytvářené vždy, když `FromHandle` je zadaný popisovač, který ještě nemá obálku objektu. Tyto dočasné objekty jsou odpojený od jejich popisovač a odstranit, `DeleteTempMap` funkce. Ve výchozím nastavení [CWinThread::OnIdle](../mfc/reference/cwinthread-class.md#onidle) automaticky volá `DeleteTempMap` pro každou třídu, která podporuje mapování dočasné zpracování. To znamená, nelze předpokládat, že ukazatel na dočasný objekt bude platit za bod, ve výstupu z funkce kde byl získán ukazatele.  
  
## <a name="wrapper-objects-and-multiple-threads"></a>Obálka objekty a více vláken  
 Dočasné a trvalé objekty udržované na základě vlákna. To znamená jedno vlákno nemá přístup k jiné vlákno objekty obálku C++, bez ohledu na to, zda je trvalé nebo dočasné.  
  
 Předat tyto objekty z jedno vlákno na jiný, vždycky je odeslat jako jejich nativní `HANDLE` typu. Předání objekt obálky C++ z jednoho vlákna budou často vést k neočekávaným výsledkům.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

