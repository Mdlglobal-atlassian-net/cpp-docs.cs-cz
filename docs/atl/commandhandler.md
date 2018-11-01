---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandHandler
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: fe0871f9778d7a1f74bf74af6030d7f8162d3b79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611845"
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

*funkci wNotifyCode*<br/>
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

## <a name="see-also"></a>Viz také

[Implementace okna](../atl/implementing-a-window.md)<br/>
[Mapy zpráv](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY –](https://msdn.microsoft.com/library/windows/desktop/bb775583)

