---
title: "Sockaddr_in – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SOCKADDR_IN
dev_langs: C++
helpviewer_keywords: SOCKADDR_IN structure [MFC]
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8b7ed601ba01bb006d156015e3c126d1eda1aec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sockaddrin-structure"></a>SOCKADDR_IN – struktura
V rodina adres Internet `SOCKADDR_IN` struktura používá rozhraní Windows Sockets k zadejte adresu místního nebo vzdáleného koncového bodu, ke kterému chcete připojit k soketu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct sockaddr_in{  
    short sin_family;  
    unsigned short sin_port;  
struct in_addr sin_addr;  
    char sin_zero[8];  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 *sin_family*  
 Rodina adres (musí být **AF_INET**).  
  
 *sin_port*  
 IP a portu.  
  
 *sin_addr*  
 IP adresa.  
  
 *Sin_Zero*  
 Odsazení aby struktura stejnou velikost jako `SOCKADDR`.  
  
## <a name="remarks"></a>Poznámky  
 Toto je formu `SOCKADDR` struktury specifické pro rodina adres Internet a můžete převést na `SOCKADDR`.  
  
 IP adresa součástí tato struktura je typu **IN_ADDR**. **IN_ADDR** struktura je definována v záhlaví souboru Windows Sockets rozhraní WINSOCK. H následujícím způsobem:  
  
```  
struct in_addr {
    union {
        struct {  
            unsigned char s_b1, s_b2, s_b3, s_b4;  
        } S_un_b;  
        struct {  
            unsigned short s_w1, s_w2;
        } S_un_w;
        unsigned long S_addr;
    } S_un;  
};  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winsock2.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Sockaddr – struktura](../../mfc/reference/sockaddr-structure.md)