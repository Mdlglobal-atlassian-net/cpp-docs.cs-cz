---
title: CDynamicAccessor::SetBlobSizeLimit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
dev_langs:
- C++
helpviewer_keywords:
- SetBlobSizeLimit method
ms.assetid: fb8cb85d-f841-408e-a344-37895b10993f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8731857507fa096d500a31f31a7c31ef4f94cfc6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096077"
---
# <a name="cdynamicaccessorsetblobsizelimit"></a>CDynamicAccessor::SetBlobSizeLimit
Nastaví maximální velikost objektu BLOB v bajtech.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      void SetBlobSizeLimit(DBLENGTH nBlobSize);  
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