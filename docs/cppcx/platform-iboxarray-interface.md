---
title: "Rozhraní Platform::IBoxArray | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs:
- C++
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f52f8c95851ec80df41fe9f0838345cf46876227
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray rozhraní
`IBoxArray` obálku pro pole typů hodnot, které jsou předán přes rozhraní binární aplikace (ABI) nebo uložený v kolekcích `Platform::Object^` elementů, jako jsou ty, v ovládacích prvcích XAML.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <typename T>  
interface class IBoxArray  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ zabalené hodnoty v každém poli elementu.  
  
### <a name="remarks"></a>Poznámky  
 `IBoxArray` je C + +/ CX název `Windows::Foundation::IReferenceArray`.  
  
### <a name="members"></a>Členové  
 `IBoxArray` Rozhraní dědí z `IValueType` rozhraní. `IBoxArray` má také tyto členy:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Hodnota](#value)|Vrací nezabalený pole, které byly dříve uloženy v tomto `IBoxArray` instance.|  

## <a name="value"></a> Vlastnost IBoxArray::Value
Vrátí hodnotu, která byla původně uložena v tomto objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property T Value {T get();}  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ zabalené hodnoty.  
  
### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 Vrátí hodnotu, která byla původně uložena v tomto objektu.  
  
### <a name="remarks"></a>Poznámky  
 Příklad, naleznete v části [zabalení](../cppcx/boxing-c-cx.md).  
  
  
## <a name="see-also"></a>Viz také  
 [Pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)