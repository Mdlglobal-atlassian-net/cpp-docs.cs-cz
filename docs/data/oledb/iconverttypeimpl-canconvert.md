---
title: IConvertTypeImpl::CanConvert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs: C++
helpviewer_keywords: CanConvert method
ms.assetid: bdad6e95-bc0b-4427-9b5e-eea51f09f392
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fcb5870fc1c66fed6657e342c8aea119fa727fcf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iconverttypeimplcanconvert"></a>IConvertTypeImpl::CanConvert
Poskytuje informace o dostupnosti převody typů v příkazu nebo pro sadu řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      STDMETHOD(CanConvert)(   
   DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IConvertType::CanConvert](https://msdn.microsoft.com/en-us/library/ms711224.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="remarks"></a>Poznámky  
 Používá převodu dat OLE DB v `MSADC.DLL`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IConvertTypeImpl – třída](../../data/oledb/iconverttypeimpl-class.md)