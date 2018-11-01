---
title: MSG – struktura
ms.date: 11/04/2016
f1_keywords:
- MSG
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
ms.openlocfilehash: 1a953f8d0d685e25beedd2d401e227c934414208
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499807"
---
# <a name="msg-structure"></a>MSG – struktura

`MSG` Struktura obsahuje informace o zprávy z fronty zpráv vlákna.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagMSG {     // msg
    HWND hwnd;
    UINT message;
    WPARAM wParam;
    LPARAM lParam;
    DWORD time;
    POINT pt;
} MSG;
```

#### <a name="parameters"></a>Parametry

*hWnd*<br/>
Identifikuje okno, jehož proceduru okna obdrží zprávu.

*message*<br/>
Určuje číslo zprávy.

*wParam*<br/>
Určuje další informace o zprávě. Přesné význam závisí na hodnotě `message` člena.

*lParam*<br/>
Určuje další informace o zprávě. Přesné význam závisí na hodnotě `message` člena.

*čas*<br/>
Určuje dobu, kdy byla publikována zpráva.

*PT*<br/>
Určuje pozici kurzoru v souřadnicovém systému obrazovky, když byla publikována zpráva.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winuser

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

