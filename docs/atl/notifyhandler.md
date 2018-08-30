---
title: NotifyHandler | Dokumentace Microsoftu
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
ms.openlocfilehash: e39b0b1ac94a759c4a8b30fce8c634ed49be4ff9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209476"
---
# <a name="notifyhandler"></a>NotifyHandler
Název funkce identifikovaný třetí parametr makra NOTIFY_HANDLER do mapy zpráv.  
  
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
 *idCtrl*  
 Identifikátor ovládacího prvku odeslání zprávy.  
  
 *pnmh*  
 Adresa [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) strukturu, která obsahuje kód upozornění a další informace. Pro některé zpráv s oznámením, tento parametr odkazuje na větší struktury, která má `NMHDR` strukturu jako jeho prvním členem.  
  
 *bHandled*  
 Mapování sady zpráv *bHandled* na hodnotu TRUE před *NotifyHandler* je volána. Pokud *NotifyHandler* plně nezpracovává zprávy, měli nastavit *bHandled* k **FALSE** k označení je zprávu zapotřebí další zpracování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Výsledek zpracování zprávy. 0 v případě úspěchu.  
  
## <a name="remarks"></a>Poznámky  
 Příklad použití této obslužné rutiny zpráv v mapování zprávy, naleznete v tématu [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler)).  
  
## <a name="see-also"></a>Viz také  
 [Implementace okna](../atl/implementing-a-window.md)   
 [Mapy zpráv](../atl/message-maps-atl.md)   
 [WM_NOTIFY –](https://msdn.microsoft.com/library/windows/desktop/bb775583)

