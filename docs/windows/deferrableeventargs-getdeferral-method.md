---
title: Deferrableeventargs::getdeferral – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: 13cd6b361fccc49de6142a0640ff96dbab3cb92c
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571201"
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral – metoda
Získá odkaz na [odložení](http://go.microsoft.com/fwlink/p/?linkid=526520) objekt, který představuje odložené událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### <a name="parameters"></a>Parametry  
 *výsledek*  
 Ukazatel, který bude odkazovat [odložení](http://go.microsoft.com/fwlink/p/?linkid=526520) objektu po dokončení volání.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.  
  
## <a name="remarks"></a>Poznámky  
 Příklad kódu naleznete v tématu [deferrableeventargs – třída](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [DeferrableEventArgs – třída](../windows/deferrableeventargs-class.md)