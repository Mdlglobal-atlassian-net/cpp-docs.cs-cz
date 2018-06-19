---
title: CDataConnection::operator CSession * | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
dev_langs:
- C++
helpviewer_keywords:
- operator CSession*
- CSession* operator
ms.assetid: 0b0feede-5c3e-4835-be5b-03651597014d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 97219418f18220cde84c80cb9052f17552a3a45d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094466"
---
# <a name="cdataconnectionoperator-csession"></a>CDataConnection::operator CSession*
Vrací ukazatel na uzavřeného `CSession` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
operator const CSession*() throw();  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento operátor vrací ukazatel na uzavřeného `CSession` objekt, což umožňuje přenos `CDataConnection` objekt kde `CSession` očekává ukazatel.  
  
## <a name="example"></a>Příklad  
 V tématu [operátor CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md) například využití.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDataConnection – třída](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md)