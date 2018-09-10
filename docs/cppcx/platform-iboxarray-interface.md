---
title: Platform::iboxarray – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs:
- C++
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66e3ff5a2daf0ddef41ea478b55ca2fc67298c01
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108445"
---
# <a name="platformiboxarray-interface"></a>Platform::iboxarray – rozhraní

`IBoxArray` je obálka pro pole typů hodnot, které jsou předány napříč binárním rozhraním aplikace (ABI) nebo uložena v kolekcích `Platform::Object^` prvky, jako například sítě na ovládací prvky XAML.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
interface class IBoxArray
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ zabalené hodnoty v každém elementu pole.

### <a name="remarks"></a>Poznámky

`IBoxArray` je C + +/ CX název `Windows::Foundation::IReferenceArray`.

### <a name="members"></a>Členové

`IBoxArray` Rozhraní zdědí `IValueType` rozhraní. `IBoxArray` obsahuje také tyto členy:

|Metoda|Popis|
|------------|-----------------|
|[Hodnota](#value)|Vrátí hodnotu, která byla dřív uložená v tomto poli bez unboxingu `IBoxArray` instance.|

## <a name="value"></a> Vlastnost IBoxArray::Value

Vrátí hodnotu, která byla původně uložená v tomto objektu.

### <a name="syntax"></a>Syntaxe

```cpp
property T Value {T get();}
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ zabalené hodnoty.

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

Vrátí hodnotu, která byla původně uložená v tomto objektu.

### <a name="remarks"></a>Poznámky

Příklad najdete v tématu [zabalení](../cppcx/boxing-c-cx.md).

## <a name="see-also"></a>Viz také

[Pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)