---
title: CDynamicAccessor::SetBlobSizeLimit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
dev_langs: C++
helpviewer_keywords: SetBlobSizeLimit method
ms.assetid: fb8cb85d-f841-408e-a344-37895b10993f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e5d683c06283c82e6117893e44def41d09300da0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicaccessorsetblobsizelimit"></a>CDynamicAccessor::SetBlobSizeLimit
Nastaví maximální velikost objektu BLOB v bajtech.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      void SetBlobSizeLimit(  
   DBLENGTH nBlobSize   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nBlobSize`  
 Určuje maximální velikost objektu BLOB.  
  
## <a name="remarks"></a>Poznámky  
 Nastaví maximální velikost objektu BLOB v bajtech; sloupce dat, které jsou větší než tato hodnota je zpracovaná jako objekt BLOB. Někteří poskytovatelé poskytují velmi velký velikosti pro sloupce (například 2 GB). Namísto pokusu o přidělení paměti pro sloupec tato velikost by obvykle pokusí navázat tyto sloupce jako objekty BLOB. Tento způsob není nutné přidělit veškerou paměť, ale stále může číst veškerá data bez obav zkrácení. Ale existují případy, ve kterých můžete chtít vynutit `CDynamicAccessor` navázat velké sloupce v jeho nativní datové typy. Chcete-li to provést, volejte `SetBlobSizeLimit` před voláním **otevřete**.  
  
 Metody konstruktoru [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) Nastaví maximální velikost objektu BLOB na výchozí hodnotu 8 000 bajtů.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)