---
title: IRowsetImpl::RestartPosition | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
dev_langs:
- C++
helpviewer_keywords:
- RestartPosition method
ms.assetid: 14de66ef-8d2c-4404-adb6-3f6c74ac6cf1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5cfdf198b68b3587146ebc4a666ac2e596d05aba
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimplrestartposition"></a>IRowsetImpl::RestartPosition
Přemístí následující načtenou pozici na výchozí pozici; To znamená vytvořit pozici při první sadu řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="remarks"></a>Poznámky  
 Pozice řádků není definován dokud **objektu GetNextRow** je volána. V můžete přesouvat zpětné rowet voláním `RestartPosition` a načítání nebo zpětné posouvání.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)