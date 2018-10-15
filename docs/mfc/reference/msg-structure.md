---
title: Msg – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b2f58af3bcf3eef524b95d25579e5bc233f9108
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334442"
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

