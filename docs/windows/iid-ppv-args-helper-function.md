---
title: Iid_ppv_args_helper – funkce | Dokumentace Microsoftu
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
ms.openlocfilehash: 351e0755f786e69da1dea6a925b7afc7cb6d6bf1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011637"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper – funkce
Ověřuje, že typ zadaného argumentu je odvozen od `IUnknown` rozhraní.  
  
> [!IMPORTANT]
>  Tato specializace šablony podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo v kódu. Použití [IID_PPV_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename T>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ argumentu *pp*.  
  
 *str*  
 Dvakrát nepřímé ukazatel.  
  
## <a name="return-value"></a>Návratová hodnota  
 Argument *pp* přetypovat na ukazatel na ukazatel na **void**.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je vygenerována chyba kompilace parametr šablony *T* není odvozen od `IUnknown`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace (knihovna Windows Runtime)](http://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)