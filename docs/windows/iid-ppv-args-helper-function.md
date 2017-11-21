---
title: "Iid_ppv_args_helper – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/IID_PPV_ARGS_Helper
dev_langs: C++
helpviewer_keywords: IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 705f1ee7f1b471491b6df5953cf92b12f6edc13c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper – funkce
Ověřuje, zda typ zadaného argumentu odvozuje od `IUnknown` rozhraní.  
  
> [!IMPORTANT]
>  Tato šablona specializace podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu. Použití [IID_PPV_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename T  
>  
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