---
title: Platform::ibox – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs:
- C++
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d83afb854aaa400a02f9de95e269f85cfeba1a96
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761509"
---
# <a name="platformibox-interface"></a>Platform::ibox – rozhraní
[Platform::ibox –](../cppcx/platform-ibox-interface.md) rozhraní je název C++ `Windows::Foundation::IReference` rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <typename T>  
interface class IBox  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ zabalené hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 `IBox<T>` Rozhraní je primárně interně používá k reprezentaci typy s možnou hodnotou Null, jak je popsáno v [hodnotové třídy a struktury (C + +/ CX)](../cppcx/value-classes-and-structs-c-cx.md). Rozhraní se také používá pro typy hodnot pole, které jsou předány do metody jazyka C++, které přijímají parametry typu `Object^`. Můžete explicitně deklarovat jako vstupní parametr `IBox<SomeValueType>`. Příklad najdete v tématu [zabalení](../cppcx/boxing-c-cx.md).  
  
### <a name="requirements"></a>Požadavky  
  
### <a name="members"></a>Členové  
 `Platform::IBox` Rozhraní zdědí [Platform::ivaluetype –](../cppcx/platform-ivaluetype-interface.md) rozhraní. `IBox` má tyto členy:  
  
 **Vlastnosti**  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Hodnota](#value)|Vrátí hodnota, která byla dřív uložená v tomto `IBox` instance.|  

## <a name="value"></a> Vlastnost IBox::Value
Vrátí hodnotu, která byla původně uložená v tomto objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property T Value {T get();}  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ zabalené hodnoty.  
  
### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 Vrátí hodnotu, která byla původně uložená v tomto objektu.  
  
### <a name="remarks"></a>Poznámky  
 Příklad najdete v tématu [zabalení](../cppcx/boxing-c-cx.md).  
  
  
## <a name="see-also"></a>Viz také  
 [Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)