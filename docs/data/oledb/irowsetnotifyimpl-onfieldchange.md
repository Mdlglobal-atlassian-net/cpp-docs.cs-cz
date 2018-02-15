---
title: IRowsetNotifyImpl::OnFieldChange | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
dev_langs:
- C++
helpviewer_keywords:
- OnFieldChange method
ms.assetid: f26b492c-c86e-423b-9374-175e510a2860
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6dcee73e08a4dbd4cfe117bd7ecf8d96b56052db
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetnotifyimplonfieldchange"></a>IRowsetNotifyImpl::OnFieldChange
Upozorní příjemce všechny změny na hodnotu sloupce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(OnFieldChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ HROW /* hRow */,  
/* [in] */ DBORDINAL /* cColumns */,  
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx) pro popisy parametrů.  
  
## <a name="return-value"></a>Návratová hodnota  
 V tématu [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx) pro vrátit hodnotu popisy.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda zabalí [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx) metoda. Viz popis dané metody v OLE DB referenční informace pro programátory podrobnosti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetNotifyImpl – třída](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx)