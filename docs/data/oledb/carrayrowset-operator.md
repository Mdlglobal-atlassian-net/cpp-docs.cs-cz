---
title: CArrayRowset::operator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CArrayRowset::operator[]
- CArrayRowset.operator[]
dev_langs:
- C++
helpviewer_keywords:
- operator [], arrays
- '[] operator'
- operator[], arrays
ms.assetid: 3bb8c310-cc1e-46e8-9711-9b565488acaa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0921ad4c574c496656ec616d1d569158c596c5ad
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="carrayrowsetoperator"></a>CArrayRowset::operator
Poskytuje syntaxe pro pole pro přístup k řádku v sadě řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      TAccessor  
      & operator[](int nrow);  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Použitím šablon parametr, který určuje typ přistupujícího objektu uložené v dané sadě řádků.  
  
 `nRow`  
 [v] Počet řádků (pole element) chcete získat přístup.  
  
## <a name="return-value"></a>Návratová hodnota  
 Obsah požadovaný řádek.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `nRow` překračuje maximální počet řádků v dané sadě řádků, je vyvolána výjimka.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CArrayRowset – třída](../../data/oledb/carrayrowset-class.md)