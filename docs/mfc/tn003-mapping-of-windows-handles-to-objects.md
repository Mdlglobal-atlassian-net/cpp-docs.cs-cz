---
title: 'TN003: Mapování popisovačů Windows na objekty'
ms.date: 11/04/2016
f1_keywords:
- vc.mapping
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
ms.openlocfilehash: 45492963e1b686e03eb59c320fdc3d52d1534f7d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513535"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003: Mapování popisovačů Windows na objekty

Tato poznámka popisuje rutiny knihovny MFC, které podporují mapování popisovačů objektů C++ systému Windows na objekty.

## <a name="the-problem"></a>Problém

Objekty systému Windows jsou obvykle reprezentovány různými objekty [obslužné rutiny](/windows/win32/WinProg/windows-data-types) třídy MFC, které C++ zabalí obslužné rutiny objektů systému Windows s objekty. Funkce zalamování obslužných rutin knihovny knihovny MFC vám umožní najít C++ objekt, který zabalí objekt Windows, který má určitý popisovač. V některých případech však objekt neobsahuje C++ Obálkový objekt a v tomto okamžiku systém vytvoří dočasný objekt, který bude fungovat jako C++ obálka.

Objekty Windows, které používají mapy popisovačů, jsou následující:

- HWND ([CWnd](../mfc/reference/cwnd-class.md) a `CWnd`-odvozené třídy)

- HDC ([CDC](../mfc/reference/cdc-class.md) a `CDC`odvozené třídy)

- HMENU ([CMenu –](../mfc/reference/cmenu-class.md))

- HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))

- HBRUSH (`CGdiObject`)

- HFONT (`CGdiObject`)

- HBITMAP (`CGdiObject`)

- HPALETTE (`CGdiObject`)

- HRGN (`CGdiObject`)

- HIMAGELIST ([atributu CImageList](../mfc/reference/cimagelist-class.md))

- SOKET ([CSocket –](../mfc/reference/csocket-class.md))

S ohledem na popisovač kteréhokoli z těchto objektů, lze najít objekt knihovny MFC, který zabalí popisovač voláním statické metody `FromHandle`. Například s ohledem na HWND s názvem *HWND*, následující řádek vrátí ukazatel na `CWnd` , který zabalí *HWND*:

```
CWnd::FromHandle(hWnd)
```

Pokud *HWND* nemá konkrétní objekt obálky, vytvoří se dočasná `CWnd` pro zabalení *HWND*. Díky tomu je možné získat platný C++ objekt z libovolného popisovače.

Po získání objektu obálky můžete načíst jeho popisovač z veřejné členské proměnné třídy obálky. V případě a `CWnd` *m_hWnd* obsahuje HWND pro daný objekt.

## <a name="attaching-handles-to-mfc-objects"></a>Připojení popisovačů k objektům MFC

Vzhledem k nově vytvořenému objektu s popisovačem a popisovači objektu systému Windows můžete přiřadit dvě voláním `Attach` funkce jako v tomto příkladu:

```
CWnd myWnd;
myWnd.Attach(hWnd);
```

Tím se vytvoří záznam na trvalé mapě, která přidružuje *myWnd* a *HWND*. Volání `CWnd::FromHandle(hWnd)` nyní vrátí ukazatel na *myWnd*. Při odstranění *myWnd* destruktor automaticky odstraní *HWND* voláním funkce Windows [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow) . Pokud to není žádoucí, musí být *HWND* odpojen od *myWnd* před zničením *myWnd* (obvykle při ponechání oboru, ve kterém byl definován *myWnd* ). `Detach` Metoda to dělá.

```
myWnd.Detach();
```

## <a name="more-about-temporary-objects"></a>Další informace o dočasných objektech

Dočasné objekty jsou vytvořeny pokaždé, když `FromHandle` je předána obslužná rutina, která ještě nemá objekt obálky. Tyto dočasné objekty jsou odpojeny od svého popisovače a odstraněny pomocí `DeleteTempMap` funkcí. Ve výchozím nastavení je hodnota [CWinThread:: OnIdle](../mfc/reference/cwinthread-class.md#onidle) automaticky volána `DeleteTempMap` pro každou třídu, která podporuje dočasné mapy popisovačů. To znamená, že nemůžete předpokládat ukazatel na dočasný objekt, bude platný za bodem ukončení od funkce, kde byl ukazatel získán.

## <a name="wrapper-objects-and-multiple-threads"></a>Objekty obálky a více vláken

Dočasné i trvalé objekty jsou uchovávány na základě jednotlivých vláken. To znamená, že jedno vlákno nemůže získat přístup k C++ objektům obálky jiného vlákna bez ohledu na to, zda je dočasné nebo trvalé.

Chcete-li tyto objekty předat z jednoho vlákna do druhého, vždy je odešlete `HANDLE` jako nativní typ. Předání objektu C++ obálky z jednoho vlákna do druhého bude často způsobovat neočekávané výsledky.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
