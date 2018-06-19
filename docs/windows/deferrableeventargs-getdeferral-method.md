---
title: Deferrableeventargs::getdeferral – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2442894c5f7bd85eb94262e776294c1e52a19e01
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883538"
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral – metoda
Získá odkaz na [odložení](http://go.microsoft.com/fwlink/p/?linkid=526520) objekt, který reprezentuje odložené události.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### <a name="parameters"></a>Parametry  
 `result`  
 Ukazatele, který bude odkazovat [odložení](http://go.microsoft.com/fwlink/p/?linkid=526520) objektu po dokončení volání.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.  
  
## <a name="remarks"></a>Poznámky  
 Příklad kódu, najdete v části [DeferrableEventArgs – třída](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [DeferrableEventArgs – třída](../windows/deferrableeventargs-class.md)