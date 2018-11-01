---
title: TN003Mapování obslužných rutin Windows na objekty
ms.date: 11/04/2016
f1_keywords:
- vc.mapping
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
ms.openlocfilehash: 46421016171f61a199e6a0a04f6b9b81e260496e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677146"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003Mapování obslužných rutin Windows na objekty

Tato poznámka popisuje MFC rutin, které podporují mapování Windows objekt popisovače objektů jazyka C++.

## <a name="the-problem"></a>Problém

Objekty Windows obvykle představují různé [zpracování](/windows/desktop/WinProg/windows-data-types) zabalení objektů tříd MFC Windows manipulačních bodů objektu s objekty jazyka C++. Popisovač funkce třídy knihovny MFC pro zabalení umožňují najít objekt jazyka C++, který zahrnuje Windows objekt, který obsahuje konkrétní popisovač. Ale někdy objekt nemá objekt obálky C++ a systém za těchto okolností vytvoří dočasný objekt, který slouží jako obálky C++.

Windows objekty, které používají mapování zpracování jsou následující:

- HWND ([CWnd](../mfc/reference/cwnd-class.md) a `CWnd`-odvozené třídy)

- HDC ([CDC](../mfc/reference/cdc-class.md) a `CDC`-odvozené třídy)

- HMENU ([cmenu –](../mfc/reference/cmenu-class.md))

- HPEN ([cgdiobject –](../mfc/reference/cgdiobject-class.md))

- HBRUSH (`CGdiObject`)

- HFONT (`CGdiObject`)

- HBITMAP (`CGdiObject`)

- HPALETTE (`CGdiObject`)

- HRGN (`CGdiObject`)

- HIMAGELIST ([atributu CImageList](../mfc/reference/cimagelist-class.md))

- SOKETU ([csocket –](../mfc/reference/csocket-class.md))

Zadaný popisovač na některý z těchto objektů, můžete najít objekt knihovny MFC, která obaluje popisovač zavoláním statické metody `FromHandle`. Mějme například popisovačem HWND volá *hWnd*, vrátí ukazatel na následující řádek `CWnd` tím končí naše *hWnd*:

```
CWnd::FromHandle(hWnd)
```

Pokud *hWnd* nemá objekt konkrétní obálky dočasný `CWnd` se vytvoří při zabalení *hWnd*. Díky tomu je možné získat platný objekt jazyka C++ z jakékoli popisovače.

Jakmile budete mít objekt obálky, můžete načíst jeho popisovač z veřejné členské proměnné této obálkové třídy. V případě třídy `CWnd`, *m_hWnd* HWND pro tento objekt obsahuje.

## <a name="attaching-handles-to-mfc-objects"></a>Zpracovává se připojuje k objektům MFC

Zadaný objekt nově vytvořený popisovač obálky a popisovač na objekt Windows, můžete přidružit dvě voláním `Attach` fungovat jako v následujícím příkladu:

```
CWnd myWnd;
myWnd.Attach(hWnd);
```

Díky tomu položky v mapování trvalé přiřazení *myWnd* a *hWnd*. Volání `CWnd::FromHandle(hWnd)` nyní vrátí ukazatel na *myWnd*. Když *myWnd* je odstraněn, destruktor automaticky zničí *hWnd* voláním Windows [destroywindow –](/windows/desktop/api/winuser/nf-winuser-destroywindow) funkce. Pokud to není žádoucí, *hWnd* musí být odpojen od *myWnd* před *myWnd* zničen (obvykle při ukončení oboru, ve kterém *myWnd*byl definován). `Detach` Metoda to dělá.

```
myWnd.Detach();
```

## <a name="more-about-temporary-objects"></a>Další informace o dočasné objekty

Dočasné objekty jsou vytvořeny vždy, když `FromHandle` je uveden popisovač, který již nemá Obálkový objekt. Tyto dočasné objekty jsou odpojena od své popisovač a odstranit `DeleteTempMap` funkce. Ve výchozím nastavení [CWinThread::OnIdle](../mfc/reference/cwinthread-class.md#onidle) automaticky volá `DeleteTempMap` pro každou třídu, která podporuje mapování dočasné zpracování. To znamená, že nelze předpokládat, že ukazatel na dočasný objekt bude platit za bod výstupu z funkce, kde byl získán ukazatel.

## <a name="wrapper-objects-and-multiple-threads"></a>Obálka objekty a více vláken

Dočasné a trvalé objekty se udržuje na základě vlákna. To znamená jedno vlákno nemůže přistupovat k objektům obálky C++ jiného vlákna, bez ohledu na to, zda jde o dočasné nebo trvalé.

Předat tyto objekty z jednoho vlákna do druhého, vždy je odeslat jako jejich nativním `HANDLE` typu. Předání objektu obálky C++ z jednoho vlákna do druhého se často vést k neočekávaným výsledkům.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

