---
title: Platform::iboxarray – rozhraní
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: a35a8b7d9f23bcb624755353e27e52de4b873c5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497015"
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