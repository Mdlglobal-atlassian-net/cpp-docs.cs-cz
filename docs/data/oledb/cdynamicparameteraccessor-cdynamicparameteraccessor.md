---
title: CDynamicParameterAccessor::CDynamicParameterAccessor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
dev_langs: C++
helpviewer_keywords:
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
ms.assetid: a1cce5e4-dfb9-43a2-bfb8-0435c653674a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e08c26c7ba9d07c5e845aea3443c824498354b74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicparameteraccessorcdynamicparameteraccessor"></a>CDynamicParameterAccessor::CDynamicParameterAccessor
Konstruktor  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      typedef CDynamicParameterAccessor _ParamClass;  
CDynamicParameterAccessor(   
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000 )   
   : CDynamicAccessor( eBlobHandling, nBlobSize )  
```  
  
#### <a name="parameters"></a>Parametry  
 `eBlobHandling`  
 Určuje, jak bude zpracovávat data objektů BLOB. Výchozí hodnota je **DBBLOBHANDLING_DEFAULT**. V tématu [CDynamicAccessor::SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) popis **DBBLOBHANDLINGENUM** hodnoty.  
  
 `nBlobSize`  
 Maximální velikost objektu BLOB v bajtech; sloupec dat přes tato hodnota je zpracovaná jako objekt BLOB. Výchozí hodnota je 8 000. V tématu [CDynamicAccessor::SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) podrobnosti.  
  
## <a name="remarks"></a>Poznámky  
 Najdete v článku [CDynamicAccessor::CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) konstruktor Další informace o zpracování objektů BLOB.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)