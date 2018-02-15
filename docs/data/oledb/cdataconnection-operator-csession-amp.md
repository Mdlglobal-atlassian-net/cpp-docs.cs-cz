---
title: CDataConnection::operator CSession&amp; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
dev_langs:
- C++
helpviewer_keywords:
- operator CSession&
- CSession& operator
ms.assetid: fba1e498-e482-4dda-8e0f-2542163bf627
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1ce7a03d90225457c482c12a4d7df1d6135cd8ac
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cdataconnectionoperator-csessionamp"></a>CDataConnection::operator CSession&amp;
Vrátí odkaz na uzavřeného `CSession` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
operator const CSession&();  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento operátor vrátí odkaz na uzavřeného `CSession` objekt, což umožňuje přenos `CDataConnection` objekt kde `CSession` namísto očekávaného odkazu.  
  
## <a name="example"></a>Příklad  
 Pokud máte funkci (například `func` níže), která má `CSession` odkaz, můžete použít **CSession &** předat `CDataConnection` objektu místo.  
  
 [!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDataConnection – třída](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession*](../../data/oledb/cdataconnection-operator-csession-star.md)