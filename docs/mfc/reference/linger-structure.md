---
title: Linger – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LINGER
dev_langs:
- C++
helpviewer_keywords:
- LINGER structure [MFC]
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53601afdd562f29ccd4bce9db76811e610940b7a
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339368"
---
# <a name="linger-structure"></a>LINGER – struktura
`LINGER` Struktura se používá pro manipulaci s možností SO_LINGER a SO_DONTLINGER `CAsyncSocket::GetSockOpt`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct linger {  
    u_short l_onoff;            // option on/off  
    u_short l_linger;           // linger time  
};  
```  
  
## <a name="remarks"></a>Poznámky  
 Nastavení možnosti SO_DONTLINGER brání blokování u členské funkce `Close` při čekání na unsent dat k odeslání. Nastavení této možnosti je ekvivalentní nastavení SO_LINGER s `l_onoff` nastavena na hodnotu 0.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winsock2.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CAsyncSocket::GetSockOpt](../../mfc/reference/casyncsocket-class.md#getsockopt)   
 [CAsyncSocket::SetSockOpt](../../mfc/reference/casyncsocket-class.md#setsockopt)

