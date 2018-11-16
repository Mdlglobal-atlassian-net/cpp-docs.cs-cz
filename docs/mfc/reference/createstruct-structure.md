---
title: CREATESTRUCT – struktura
ms.date: 11/04/2016
f1_keywords:
- CREATESTRUCT
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
ms.openlocfilehash: 1de42ba3e26f7a06918a69358083e68f142836cc
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694696"
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
Odkazuje na řetězec zakončený hodnotou null, který určuje název třídy nové okno Windows ( [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) struktury; Další informace najdete v tématu Windows SDK).

*dwExStyle*<br/>
Určuje, [rozšířený styl](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) v novém okně.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winuser

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)

