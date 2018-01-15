---
title: "Sockaddr – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SOCKADDR
dev_langs: C++
helpviewer_keywords: SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 55b310ec83aae35c7386d61849663752811651d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="sockaddr-structure"></a>SOCKADDR – struktura
Struktura `SOCKADDR` se používá k uchování adresy protokolu IP pro počítače podílející se na komunikaci prostřednictvím rozhraní Windows Sockets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct sockaddr {  
    unsigned short sa_family;  
    char sa_data[14];  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 *sa_family*  
 Skupina adres soketu.  
  
 *sa_data*  
 Maximální velikost všech různých struktur adres soketu.  
  
## <a name="remarks"></a>Poznámky  
 Sada Microsoft TCP/IP Sockets Developer's Kit podporuje pouze domény internetových adres. Pro skutečné vyplnění hodnot všech částí adresy se používá datová struktura `SOCKADDR_IN`, která je upravena výslovně pro tento formát adresy. Datové struktury `SOCKADDR` a `SOCKADDR_IN` mají stejnou velikost. Přecházet mezi těmito dvěma typy struktur lze pouhým přetypováním.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winsock2.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Sockaddr_in – struktura](../../mfc/reference/sockaddr-in-structure.md)   
 [CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)   
 [CSocket::Create](../../mfc/reference/csocket-class.md#create)

