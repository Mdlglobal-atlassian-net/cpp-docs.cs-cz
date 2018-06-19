---
title: MessageHandler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- MessageHandler
dev_langs:
- C++
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec0fd88def88f7d31fce078fec0c860f4f21f51c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356364"
---
# <a name="messagehandler"></a>MessageHandler
**MessageHandler** je název funkce identifikovaný druhý parametr `MESSAGE_HANDLER` makro mapy zpráv.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 
    LRESULT 
    MessageHandler 
 (
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>Parametry  
 `uMsg`  
 Určuje zprávu.  
  
 `wParam`  
 Další informace specifické pro zprávy.  
  
 `lParam`  
 Další informace specifické pro zprávy.  
  
 `bHandled`  
 Nastaví mapy zpráv `bHandled` k **TRUE** před `MessageHandler` je volána. Pokud `MessageHandler` plně nezpracovává zprávy, je potřeba nastavit `bHandled` k **FALSE** k označení zprávy potřebuje další zpracování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Výsledek zpracování zprávy. 0, pokud bylo úspěšné.  
  
## <a name="remarks"></a>Poznámky  
 Příklad použití tento popisovač zpráv v mapy zpráv naleznete v části [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).  
  
## <a name="see-also"></a>Viz také  
 [Implementace okno](../atl/implementing-a-window.md)   
 [Mapy zpráv](../atl/message-maps-atl.md)   
 [WM_NOTIFY –](http://msdn.microsoft.com/library/windows/desktop/bb775583)

