---
title: CEnumerator::Open | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
dev_langs: C++
helpviewer_keywords: Open method
ms.assetid: b22821a0-257a-4543-ad0c-2649d4ac092e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cf1205fce9466117a3374ebfd18e21cd034ae229
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cenumeratoropen"></a>CEnumerator::Open
Váže Přezdívka pro enumerátor, pokud jeden zadaný, bude načte sada řádků pro enumerátor voláním [ISourcesRowset::GetSourcesRowset](https://msdn.microsoft.com/en-us/library/ms711200.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT Open(   
   LPMONIKER pMoniker    
) throw( );  
HRESULT Open(   
   const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR    
) throw( );  
HRESULT Open(   
   const CEnumerator& enumerator    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMoniker`  
 [v] Ukazatel na Přezdívka pro enumerátor.  
  
 *pClsid*  
 [v] Ukazatel **CLSID** z enumerátor.  
  
 `enumerator`  
 [v] Odkaz na enumerátor.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CEnumerator – třída](../../data/oledb/cenumerator-class.md)