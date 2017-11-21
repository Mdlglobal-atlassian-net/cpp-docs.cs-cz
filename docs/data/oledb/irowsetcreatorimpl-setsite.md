---
title: IRowsetCreatorImpl::SetSite | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
dev_langs: C++
helpviewer_keywords: SetSite method
ms.assetid: e92e63d5-93e4-4ee0-9ef7-bb6583cc8091
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e2f01a8e65535599f2b7f79ed6f0cb0b06b0866a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetcreatorimplsetsite"></a>IRowsetCreatorImpl::SetSite
Nastaví lokality, která obsahuje objekt sady řádků. Další informace najdete v tématu [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      STDMETHOD( SetSite )(  
   IUnknown* pCreator   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCreator`  
 [v] Ukazatel **IUnknown** ukazatel rozhraní lokality Správa objektu sady řádků.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Kromě toho `IRowsetCreatorImpl::SetSite` umožňuje OLE DB **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS** vlastnosti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetCreatorImpl – třída](../../data/oledb/irowsetcreatorimpl-class.md)