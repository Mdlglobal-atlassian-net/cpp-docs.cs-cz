---
title: MessageHandler | Dokumentace Microsoftu
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
ms.openlocfilehash: 74a5e50eae425340bcb0f9a455422b43db0be0b2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207107"
---
# <a name="messagehandler"></a>MessageHandler
`MessageHandler` je název funkce identifikovaný druhý parametr makra MESSAGE_HANDLER do mapy zpráv.  
  
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
 *uMsg*  
 Určuje zprávu.  
  
 *wParam*  
 Další informace specifické pro zprávy.  
  
 *lParam*  
 Další informace specifické pro zprávy.  
  
 *bHandled*  
 Mapování sady zpráv *bHandled* na hodnotu TRUE před `MessageHandler` je volána. Pokud `MessageHandler` plně nezpracovává zprávy, měli nastavit *bHandled* na hodnotu FALSE pro označení je zprávu zapotřebí další zpracování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Výsledek zpracování zprávy. 0 v případě úspěchu.  
  
## <a name="remarks"></a>Poznámky  
 Příklad použití této obslužné rutiny zpráv v mapování zprávy, naleznete v tématu [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).  
  
## <a name="see-also"></a>Viz také  
 [Implementace okna](../atl/implementing-a-window.md)   
 [Mapy zpráv](../atl/message-maps-atl.md)   
 [WM_NOTIFY –](https://msdn.microsoft.com/library/windows/desktop/bb775583)

