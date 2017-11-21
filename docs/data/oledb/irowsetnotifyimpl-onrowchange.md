---
title: IRowsetNotifyImpl::OnRowChange | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
dev_langs: C++
helpviewer_keywords: OnRowChange method
ms.assetid: 148bee03-3707-4bbf-8c51-657efc63645f
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c765561ce1320944888e599fd4d9f7bf1da04976
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetnotifyimplonrowchange"></a>IRowsetNotifyImpl::OnRowChange
Upozorní spotřebitele první změna na řádek nebo všechny změny, která má vliv na celý řádek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STDMETHOD(OnRowChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBCOUNTITEM /* cRows */,  
/* [size_is][in] */ const HROW /* rghRows*/ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) pro popisy parametrů.  
  
## <a name="return-value"></a>Návratová hodnota  
 V tématu [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) pro vrátit hodnotu popisy.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda zabalí [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) metoda. Viz popis dané metody v OLE DB referenční informace pro programátory podrobnosti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetNotifyImpl – třída](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)