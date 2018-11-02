---
title: CREATESTRUCT – struktura
ms.date: 11/04/2016
f1_keywords:
- CREATESTRUCT
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
ms.openlocfilehash: 13f715dc914ccc052945790aeaff9c47bd34ed46
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619645"
---
# <a name="createstruct-structure"></a>CREATESTRUCT – struktura

`CREATESTRUCT` Struktury definuje inicializační parametry předány do procedury okna aplikace.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagCREATESTRUCT {
    LPVOID lpCreateParams;
    HANDLE hInstance;
    HMENU hMenu;
    HWND hwndParent;
    int cy;
    int cx;
    int y;
    int x;
    LONG style;
    LPCSTR lpszName;
    LPCSTR lpszClass;
    DWORD dwExStyle;
} CREATESTRUCT;
```

#### <a name="parameters"></a>Parametry

*lpCreateParams*<br/>
Body k datům se použije k vytvoření okna.

*hInstance*<br/>
Identifikuje popisovač instance modulu modulu, který je vlastníkem nové okno.

*hMenu*<br/>
Určuje nabídku pro nové okno. Pokud podřízené okno, obsahuje ID celé číslo.

*hwndParent*<br/>
Identifikuje okně, které vlastní novém okně. Tento člen má hodnotu NULL, pokud se nové okno je okno nejvyšší úrovně.

*CY*<br/>
Určuje výšku nové okno.

*CX*<br/>
Určuje šířku nové okno.

*y*<br/>
Určuje souřadnici y levého horního rohu nové okno. Souřadnice jsou relativní vzhledem k nadřazené okno, pokud je okno nové podřízené okno; v opačném případě souřadnice jsou relativně ke zdroji obrazovky.

*x*<br/>
Určuje souřadnice x levého horního rohu nové okno. Souřadnice jsou relativní vzhledem k nadřazené okno, pokud je okno nové podřízené okno; v opačném případě souřadnice jsou relativně ke zdroji obrazovky.

*Styl*<br/>
Určuje nové okno [styl](../../mfc/reference/styles-used-by-mfc.md).

*lpszName*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje název nového okna.

*lpszClass*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje název třídy nové okno Windows ( [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) struktury; Další informace najdete v tématu Windows SDK).

*dwExStyle*<br/>
Určuje, [rozšířený styl](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) v novém okně.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winuser

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)

