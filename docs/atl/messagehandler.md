---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: aa044ef88ba3c872c2652cd774ac50024e52c68c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492309"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler`je název funkce identifikovaný druhým parametrem makra MESSAGE_HANDLER ve vaší mapě zpráv.

## <a name="syntax"></a>Syntaxe

```
LRESULT MessageHandler(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parametry

*uMsg*<br/>
Určuje zprávu.

*wParam*<br/>
Další informace specifické pro zprávy

*lParam*<br/>
Další informace specifické pro zprávy

*bHandled*<br/>
Mapa zpráv nastaví *bHandled* na hodnotu true, `MessageHandler` než se zavolá. Pokud `MessageHandler` Tato zpráva nebude plně zpracována, měla by nastavit *bHandled* na hodnotu false, aby bylo indikováno, že zpráva potřebuje další zpracování.

## <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy 0, pokud bylo úspěšné.

## <a name="remarks"></a>Poznámky

Příklad použití této obslužné rutiny zprávy v mapě zpráv naleznete v tématu [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).

## <a name="see-also"></a>Viz také:

[Implementace okna](../atl/implementing-a-window.md)<br/>
[Mapy zpráv](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
