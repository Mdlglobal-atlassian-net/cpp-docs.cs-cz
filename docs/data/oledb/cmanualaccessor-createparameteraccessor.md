---
title: CManualAccessor::CreateParameterAccessor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
dev_langs: C++
helpviewer_keywords: CreateParameterAccessor method
ms.assetid: d0a2095b-b37c-4472-accc-45ef365a18c8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 94fbe6e0a7e44e861c3a0cb0039860e47a27ad3e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmanualaccessorcreateparameteraccessor"></a>CManualAccessor::CreateParameterAccessor
Přidělí paměť pro parametr vazby struktury a inicializuje parametry datových členů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT CreateParameterAccessor(   
   int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `nBindEntries`  
 [v] Počet sloupců.  
  
 `pBuffer`  
 [v] Ukazatel do vyrovnávací paměti, kde jsou uloženy vstupní sloupce.  
  
 `nBufferSize`  
 [v] Velikost vyrovnávací paměti v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Musí volat tuto funkci před voláním [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)   
 [CManualAccessor::CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)   
 [CManualAccessor::AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)