---
title: NotifyHandler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- NotifyHandler
dev_langs:
- C++
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74fbdd99c162b4362339d8c1b45ddc281d30eeee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356450"
---
# <a name="notifyhandler"></a>NotifyHandler
Název funkce identifikovaný třetí parametr funkce `NOTIFY_HANDLER` makro mapy zpráv.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 
    LRESULT 
    NotifyHandler 
 (
    int idCtrl,  
    LPNMHDR pnmh,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>Parametry  
 `idCtrl`  
 Identifikátor ovládacího prvku odesílání zprávy.  
  
 *pnmh*  
 Adresa [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) struktura, která obsahuje kód upozornění a další informace. Pro některé zprávy oznámení, tento parametr odkazuje na větší struktury, která má **NMHDR** struktura jako první člena.  
  
 `bHandled`  
 Nastaví mapy zpráv `bHandled` k **TRUE** před *NotifyHandler* je volána. Pokud *NotifyHandler* plně nezpracovává zprávy, je potřeba nastavit `bHandled` k **FALSE** k označení zprávy potřebuje další zpracování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Výsledek zpracování zprávy. 0, pokud bylo úspěšné.  
  
## <a name="remarks"></a>Poznámky  
 Příklad použití tento popisovač zpráv v mapy zpráv naleznete v části [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).  
  
## <a name="see-also"></a>Viz také  
 [Implementace okno](../atl/implementing-a-window.md)   
 [Mapy zpráv](../atl/message-maps-atl.md)   
 [WM_NOTIFY –](http://msdn.microsoft.com/library/windows/desktop/bb775583)

