---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 99a95228f6036e5f391395be367cdef39ca3dc3b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492458"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler`je funkce, kterou identifikuje třetí parametr makra COMMAND_HANDLER ve vaší mapě zpráv.

## <a name="syntax"></a>Syntaxe

```cpp
LRESULT CommandHandler(
    WORD wNotifyCode,
    WORD wID,
    HWND hWndCtl,
    BOOL& bHandled);
```

#### <a name="parameters"></a>Parametry

*wNotifyCode*<br/>
Kód oznámení.

*wID*<br/>
Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru

*hWndCtl*<br/>
Popisovač ovládacího prvku okna.

*bHandled*<br/>
Mapa zpráv nastaví *bHandled* na hodnotu true, `CommandHandler` než se zavolá. Pokud `CommandHandler` Tato zpráva nebude plně zpracována, měla by nastavit *bHandled* na hodnotu false, aby bylo indikováno, že zpráva potřebuje další zpracování.

## <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy 0, pokud bylo úspěšné.

## <a name="remarks"></a>Poznámky

Příklad použití této obslužné rutiny zprávy v mapě zpráv naleznete v tématu [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).

## <a name="see-also"></a>Viz také:

[Implementace okna](../atl/implementing-a-window.md)<br/>
[Mapy zpráv](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
