---
title: "RemoveIUnknown – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::RemoveIUnknown
dev_langs: C++
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4434064e973626fa1274bf620aa6c8cd34dc99d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="removeiunknown-class"></a>RemoveIUnknown – třída
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename T  
>  
struct RemoveIUnknown;  
  
template <  
   typename T  
>  
class RemoveIUnknown : public T;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída.  
  
## <a name="remarks"></a>Poznámky  
 Vytvoří typ, který je ekvivalentní `IUnknown`-založené na typ, ale má nevirtuální `QueryInterface`, `AddRef`, a `Release` členské funkce.  
  
 Ve výchozím nastavení, poskytují virtuální metody modelu COM `QueryInterface`, `AddRef`a verzí metody. Ale `ComPtr` nevyžaduje režii virtuální metody. `RemoveIUnknown`Eliminuje režijní náklady na tento tím, že poskytuje privátní, nevirtuální `QueryInterface`, `AddRef`, a `Release` metody.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`ReturnType`|Synonymum pro typ, který je ekvivalentní pro parametr šablony `T` , ale má nevirtuální IUnknown členy.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `T`  
  
 `RemoveIUnknown`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)