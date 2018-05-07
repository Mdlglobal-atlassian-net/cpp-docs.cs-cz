---
title: CDynamicAccessor::CDynamicAccessor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicAccessor class, constructor
ms.assetid: bf40fe81-2c85-473e-9075-51ad9b060b39
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 80446719ac8e523efc5ef885fe55fb89561509e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorcdynamicaccessor"></a>CDynamicAccessor::CDynamicAccessor
Vytvoří a inicializuje `CDynamicAccessor` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000);  
```  
  
#### <a name="parameters"></a>Parametry  
 `eBlobHandling`  
 Určuje, jak bude zpracovávat data binární rozsáhlý objekt (binární rozsáhlý OBJEKT). Výchozí hodnota je **DBBLOBHANDLING_DEFAULT**. V tématu [setblobhandling –](../../data/oledb/cdynamicaccessor-setblobhandling.md) popis **DBBLOBHANDLINGENUM** hodnoty.  
  
 `nBlobSize`  
 Maximální velikost objektu BLOB v bajtech; sloupec dat přes tato hodnota je zpracovaná jako objekt BLOB. Výchozí hodnota je 8 000. V tématu [setblobsizelimit –](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) podrobnosti.  
  
## <a name="remarks"></a>Poznámky  
 Používáte-li k chybě při inicializaci konstruktoru `CDynamicAccessor` objekt, můžete určit, jak ho vytvoří vazbu objekty BLOB. Objekty BLOB může obsahovat binární data, jako jsou grafiky, zvuk nebo zkompilovaný kód. Výchozí chování je považovat za sloupce maximálně 8 000 bajtů objekty BLOB a pokuste se vytvořit vazbu, aby `ISequentialStream` objektu. Můžete však zadat jinou hodnotu na velikost objektu BLOB.  
  
 Můžete také určit, jak `CDynamicAccessor` zpracovává sloupce dat, která se považují za data objektů BLOB: ji může zpracovat data objektu BLOB způsobem výchozí; můžete přeskočit (nemá vazbu) data objektu BLOB; nebo můžete vázat data objektů BLOB v paměti přidělené zprostředkovatele.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)