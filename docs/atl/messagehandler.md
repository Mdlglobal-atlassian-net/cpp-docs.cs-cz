---
title: MessageHandler | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MessageHandler
dev_langs: C++
helpviewer_keywords: MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f5a09439cf47c695af0d3b7d6c7724cffcb9ccb4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

