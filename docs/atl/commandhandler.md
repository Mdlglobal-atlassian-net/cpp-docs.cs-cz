---
title: Commandhandler – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CommandHandler
dev_langs:
- C++
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4799d0b9c36ade8b1e203ca106605db75752b02f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752812"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler` Funkce identifikován třetí parametr makra COMMAND_HANDLER do mapy zpráv.

## <a name="syntax"></a>Syntaxe

```  
LRESULT CommandHandler(
    WORD wNotifyCode,  
    WORD wID,  
    HWND hWndCtl,  
    BOOL& bHandled);
```

#### <a name="parameters"></a>Parametry

*funkci wNotifyCode*  
Kód upozornění.

*wID*  
Identifikátor položky nabídky, ovládací prvek nebo akcelerátoru.

*hWndCtl*  
Popisovač okna ovládacího prvku.

*bHandled*  
Mapování sady zpráv *bHandled* na hodnotu TRUE před `CommandHandler` je volána. Pokud `CommandHandler` plně nezpracovává zprávy, měli nastavit *bHandled* na hodnotu FALSE pro označení je zprávu zapotřebí další zpracování.

## <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy. 0 v případě úspěchu.

## <a name="remarks"></a>Poznámky

Příklad použití této obslužné rutiny zpráv v mapování zprávy, naleznete v tématu [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).

## <a name="see-also"></a>Viz také

[Implementace okna](../atl/implementing-a-window.md)   
[Mapy zpráv](../atl/message-maps-atl.md)   
[WM_NOTIFY –](https://msdn.microsoft.com/library/windows/desktop/bb775583)

