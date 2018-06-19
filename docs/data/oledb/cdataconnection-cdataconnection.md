---
title: CDataConnection::CDataConnection | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class, constructor
ms.assetid: ac25c9a0-44d3-4083-b13f-76c07772e12d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 267341f88886f3ff94a6b828034e8acbaa2dc0c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093321"
---
# <a name="cdataconnectioncdataconnection"></a>CDataConnection::CDataConnection
Vytvoří a inicializuje `CDataConnection` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      CDataConnection();   

CDataConnection(const CDataConnection &ds);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ds`  
 [v] Odkaz na existující datové připojení.  
  
## <a name="remarks"></a>Poznámky  
 Vytvoří novou první přepsání `CDataConnection` objekt s výchozím nastavením.  
  
 Vytvoří novou druhý přepsání `CDataConnection` objekt s nastavením ekvivalentní objekt připojení dat zadáte.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDataConnection – třída](../../data/oledb/cdataconnection-class.md)