---
title: IRowsetChangeImpl::FlushData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
dev_langs: C++
helpviewer_keywords: FlushData method
ms.assetid: fd4bc73b-bc25-4aab-90d5-0bed92670c88
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 31555e1f8305a281955902b71fdc71fbcc5405e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetchangeimplflushdata"></a>IRowsetChangeImpl::FlushData
Overidden poskytovatelem potvrdit data do jeho úložiště.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT FlushData(  
   HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *hRowToFlush*  
 [v] Zpracování na řádky pro data. Typ tento řádek se určí z *RowClass* argumentu šablony `IRowsetImpl` – třída (`CSimpleRow` ve výchozím nastavení).  
  
 *hAccessorToFlush*  
 [v] Popisovač přistupujícího objektu, který obsahuje informace o vazbě a informací o typu v jeho **PROVIDER_MAP** (viz [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetChangeImpl – třída](../../data/oledb/irowsetchangeimpl-class.md)