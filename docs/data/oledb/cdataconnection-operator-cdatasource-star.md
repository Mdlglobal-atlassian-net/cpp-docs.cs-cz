---
title: CDataConnection::operator CDataSource * | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
dev_langs:
- C++
helpviewer_keywords:
- CDataSource* operator
- operator * (CDataSource)
ms.assetid: 9118e324-e68d-45c5-a791-03f041d420ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bade9d813fb9804ae353f7c5139f063f278da225
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095336"
---
# <a name="cdataconnectionoperator-cdatasource"></a>CDataConnection::operator CDataSource*
Vrací ukazatel na uzavřeného `CDataSource` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
operator const CDataSource*() throw();  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento operátor vrací ukazatel na uzavřeného `CDataSource` objekt, což umožňuje přenos `CDataConnection` objekt kde `CDataSource` očekává ukazatel.  
  
 V tématu [operátor CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) například využití.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDataConnection – třída](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)