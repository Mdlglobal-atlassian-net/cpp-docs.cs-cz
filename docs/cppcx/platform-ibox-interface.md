---
title: Rozhraní Platform::IBox | Microsoft Docs
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7894eceb2f345303400eec9b0490db58b3c3583f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="platformibox-interface"></a>Platform::IBox rozhraní
[Platform::IBox](../cppcx/platform-ibox-interface.md) rozhraní je název C++ `Windows::Foundation::IReference` rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <typename T>  
interface class IBox  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ zabalené hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 `IBox<T>` Rozhraní je primárně interně představují typy hodnot s povolenou hodnotou Null, jak je popsáno v [hodnota třídy a struktury (C + +/ CX)](../cppcx/value-classes-and-structs-c-cx.md). Rozhraní se používá i k pole typů hodnot, které se budou předávat C++ metod, které berou parametrů typu `Object^`. Můžete explicitně deklarovat jako vstupní parametr `IBox<SomeValueType>`. Příklad, naleznete v části [zabalení](../cppcx/boxing-c-cx.md).  
  
### <a name="requirements"></a>Požadavky  
  
### <a name="members"></a>Členové  
 `Platform::IBox` Rozhraní dědí z [Platform::IValueType](../cppcx/platform-ivaluetype-interface.md) rozhraní. `IBox` má tyto členy:  
  
 **Vlastnosti**  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Hodnota](#value)|Vrátí hodnota které byly dříve uloženy v tomto `IBox` instance.|  

## <a name="value"></a> Vlastnost IBox::Value
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
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)