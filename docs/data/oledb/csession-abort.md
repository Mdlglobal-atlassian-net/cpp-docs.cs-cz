---
title: CSession::Abort | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
dev_langs: C++
helpviewer_keywords: Abort method
ms.assetid: 02413b20-c486-451f-b4d7-73a6e8065df8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 50a359b2197179ee14661c659b814ffc6af64245
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="csessionabort"></a>CSession::Abort
Ukončí transakce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT Abort(   
   BOID* pboidReason = NULL,   
   BOOL bRetaining = FALSE,   
   BOOL bAsync = FALSE    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [ITransaction::Abort](https://msdn.microsoft.com/en-us/library/ms709833.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CSession – třída](../../data/oledb/csession-class.md)