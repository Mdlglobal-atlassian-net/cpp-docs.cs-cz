---
title: "Commandhandler – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CommandHandler
dev_langs: C++
helpviewer_keywords: CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c17d9e731eaee9c6e1a1c584e61db6c9826cf8d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="commandhandler"></a>CommandHandler
`CommandHandler`se identifikovanou pomocí třetí parametr funkce `COMMAND_HANDLER` makro mapy zpráv.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 
    LRESULT 
    CommandHandler 
 (
    WORD wNotifyCode,  
    WORD wID,  
    HWND hWndCtl,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>Parametry  
 `wNotifyCode`  
 Kód oznámení.  
  
 *interní databáze Windows*  
 Identifikátor položky nabídky, řízení nebo akcelerátoru.  
  
 *hWndCtl*  
 Obslužná rutina do ovládacího prvku okno.  
  
 `bHandled`  
 Nastaví mapy zpráv `bHandled` k **TRUE** před `CommandHandler` je volána. Pokud `CommandHandler` plně nezpracovává zprávy, je potřeba nastavit `bHandled` k **FALSE** k označení zprávy potřebuje další zpracování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Výsledek zpracování zprávy. 0, pokud bylo úspěšné.  
  
## <a name="remarks"></a>Poznámky  
 Příklad použití tento popisovač zpráv v mapy zpráv naleznete v části [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler).  
  
## <a name="see-also"></a>Viz také  
 [Implementace okno](../atl/implementing-a-window.md)   
 [Mapy zpráv](../atl/message-maps-atl.md)   
 [WM_NOTIFY –](http://msdn.microsoft.com/library/windows/desktop/bb775583)

