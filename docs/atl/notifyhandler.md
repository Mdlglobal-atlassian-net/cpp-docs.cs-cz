---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: 292a1c6606585dc0694ee678ba8bc9b5fbc42681
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808219"
---
# <a name="notifyhandler"></a>NotifyHandler

Název funkce identifikovaný třetí parametr makra NOTIFY_HANDLER do mapy zpráv.

## <a name="syntax"></a>Syntaxe

```cpp
LRESULT NotifyHandler(
    int idCtrl,
    LPNMHDR pnmh,
    BOOL& bHandled);
```

#### <a name="parameters"></a>Parametry

*idCtrl*<br/>
Identifikátor ovládacího prvku odeslání zprávy.

*pnmh*<br/>
Adresa [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) strukturu, která obsahuje kód upozornění a další informace. Pro některé zpráv s oznámením, tento parametr odkazuje na větší struktury, která má `NMHDR` strukturu jako jeho prvním členem.

*bHandled*<br/>
Mapování sady zpráv *bHandled* na hodnotu TRUE před *NotifyHandler* je volána. Pokud *NotifyHandler* plně nezpracovává zprávy, měli nastavit *bHandled* k **FALSE** k označení je zprávu zapotřebí další zpracování.

## <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy. 0 v případě úspěchu.

## <a name="remarks"></a>Poznámky

Příklad použití této obslužné rutiny zpráv v mapování zprávy, naleznete v tématu [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).

## <a name="see-also"></a>Viz také:

[Implementace okna](../atl/implementing-a-window.md)<br/>
[Mapy zpráv](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
