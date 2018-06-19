---
title: CUtlProps::SetPropValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
dev_langs:
- C++
helpviewer_keywords:
- SetPropValue method
ms.assetid: 69a703c0-f640-4ca3-8850-0c4e75d52429
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 73f2432a23adf8fe11f759c2caa85d9653040635
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099066"
---
# <a name="cutlpropssetpropvalue"></a>CUtlProps::SetPropValue
Nastaví vlastnost v sadu vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pguidPropSet`  
 [v] Identifikátor GUID sada vlastností.  
  
 `dwPropId`  
 [v] Vlastnost index.  
  
 `pvValue`  
 [v] Ukazatel na hodnotu typu variant, která obsahuje novou hodnotu vlastnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 `Failure` při selhání a `S_OK` v případě úspěchu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [CUtlProps – třída](../../data/oledb/cutlprops-class.md)