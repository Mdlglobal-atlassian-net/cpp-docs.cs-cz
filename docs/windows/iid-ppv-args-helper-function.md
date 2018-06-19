---
title: Iid_ppv_args_helper – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
dev_langs:
- C++
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0cef979ae284a303b120df7d14ae71f311498423
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882339"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper – funkce
Ověřuje, zda typ zadaného argumentu odvozuje od `IUnknown` rozhraní.  
  
> [!IMPORTANT]
>  Tato šablona specializace podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu. Použití [IID_PPV_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ argumentu `pp`.  
  
 `pp`  
 Dvakrát nepřímý ukazatel.  
  
## <a name="return-value"></a>Návratová hodnota  
 Argument `pp` přetypovat na ukazatel na ukazatel na `void`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je vygenerována chyba kompilace parametr šablony `T` není odvozena od `IUnknown`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace (knihovna prostředí Windows Runtime)](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)