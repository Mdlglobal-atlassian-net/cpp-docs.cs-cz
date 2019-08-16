---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: 16fb330d2da83ddfd013e33a2d4b688b2711103b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492301"
---
# <a name="notifyhandler"></a>NotifyHandler

Název funkce identifikovaný třetím parametrem makra NOTIFY_HANDLER ve vaší mapě zpráv.

## <a name="syntax"></a>Syntaxe

```cpp
LRESULT NotifyHandler(
    int idCtrl,
    LPNMHDR pnmh,
    BOOL& bHandled);
```

#### <a name="parameters"></a>Parametry

*idCtrl*<br/>
Identifikátor ovládacího prvku, který odesílá zprávu

*pnmh*<br/>
Adresa struktury [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) , která obsahuje kód oznámení a další informace. U některých oznamovacích zpráv tento parametr odkazuje na větší strukturu, která má `NMHDR` strukturu jako svůj první člen.

*bHandled*<br/>
Mapa zpráv nastaví *bHandled* na hodnotu true před voláním *NotifyHandler* . Pokud *NotifyHandler* zprávu zcela nezpracovává, měla by nastavit *bHandled* na **false** , aby označovala, že zpráva potřebuje další zpracování.

## <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy 0, pokud bylo úspěšné.

## <a name="remarks"></a>Poznámky

Příklad použití této obslužné rutiny zpráv v mapě zpráv naleznete v tématu [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).

## <a name="see-also"></a>Viz také:

[Implementace okna](../atl/implementing-a-window.md)<br/>
[Mapy zpráv](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
