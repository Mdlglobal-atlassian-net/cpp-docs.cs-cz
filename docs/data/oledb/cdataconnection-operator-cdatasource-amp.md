---
title: CDataConnection::operator CDataSource&amp; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
dev_langs:
- C++
helpviewer_keywords:
- CDataSource& operator
- operator & (CDataSource)
ms.assetid: 852faeee-f1b1-4465-9828-b261d1edf022
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8aca05cd83123e2866b8d46e5d5f085b5edd04f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdataconnectionoperator-cdatasourceamp"></a>CDataConnection::operator CDataSource&amp;
Vrátí odkaz na uzavřeného `CDataSource` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
operator const CDataSource&() throw();  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento operátor vrátí odkaz na uzavřeného `CDataSource` objekt, což umožňuje přenos `CDataConnection` objekt kde `CDataSource` namísto očekávaného odkazu.  
  
## <a name="example"></a>Příklad  
 Pokud máte funkci (například `func` níže), která má `CDataSource` odkaz, můžete použít **CDataSource &** předat `CDataConnection` objektu místo.  
  
 [!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDataConnection – třída](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource*](../../data/oledb/cdataconnection-operator-cdatasource-star.md)