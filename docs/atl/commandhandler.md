---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 743be3e0bc9cc96fc6b22d0806d399ab5e160a3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235061"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler` Funkce identifikován třetí parametr makra COMMAND_HANDLER do mapy zpráv.

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
Kód upozornění.

*wID*<br/>
Identifikátor položky nabídky, ovládací prvek nebo akcelerátoru.

*hWndCtl*<br/>
Popisovač okna ovládacího prvku.

*bHandled*<br/>
Mapování sady zpráv *bHandled* na hodnotu TRUE před `CommandHandler` je volána. Pokud `CommandHandler` plně nezpracovává zprávy, měli nastavit *bHandled* na hodnotu FALSE pro označení je zprávu zapotřebí další zpracování.

## <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy. 0 v případě úspěchu.

## <a name="remarks"></a>Poznámky

Příklad použití této obslužné rutiny zpráv v mapování zprávy, naleznete v tématu [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).

## <a name="see-also"></a>Viz také:

[Implementace okna](../atl/implementing-a-window.md)<br/>
[Mapy zpráv](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
