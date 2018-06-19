---
title: CArrayRowset::operator | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 755e484f430f47eb072e3c590bfbee8471984bb6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089124"
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