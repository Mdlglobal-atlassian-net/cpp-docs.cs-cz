---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageHandler
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: 5d7b1af3f96f34be91c9e4616e0ac3a084689b2a
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693149"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler` je název funkce identifikovaný druhý parametr makra MESSAGE_HANDLER do mapy zpráv.

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
Další informace specifické pro zprávy.

*lParam*<br/>
Další informace specifické pro zprávy.

*bHandled*<br/>
Mapování sady zpráv *bHandled* na hodnotu TRUE před `MessageHandler` je volána. Pokud `MessageHandler` plně nezpracovává zprávy, měli nastavit *bHandled* na hodnotu FALSE pro označení je zprávu zapotřebí další zpracování.

## <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy. 0 v případě úspěchu.

## <a name="remarks"></a>Poznámky

Příklad použití této obslužné rutiny zpráv v mapování zprávy, naleznete v tématu [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).

## <a name="see-also"></a>Viz také

[Implementace okna](../atl/implementing-a-window.md)<br/>
[Mapy zpráv](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY –](/windows/desktop/controls/wm-notify)
