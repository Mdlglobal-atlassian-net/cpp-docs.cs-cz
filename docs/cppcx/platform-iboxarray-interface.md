---
title: 'Platform:: IBoxArray – rozhraní'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IBoxArray
- VCCORLIB/Platform::IBoxArray::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: 493770cab092c2bb719d47e5d3a9d6a9f0646489
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444154"
---
# <a name="platformiboxarray-interface"></a>Platform:: IBoxArray – rozhraní

`IBoxArray` je obálka pro pole typů hodnot, které jsou předávány napříč binárním rozhraním aplikace (ABI) nebo uloženy v kolekcích `Platform::Object^` prvků, jako jsou například v ovládacích prvcích XAML.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
interface class IBoxArray
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Typ zabalené hodnoty v každém elementu pole.

### <a name="remarks"></a>Poznámky

`IBoxArray` je název C++/cx pro `Windows::Foundation::IReferenceArray`.

### <a name="members"></a>Členové

Rozhraní `IBoxArray` dědí z rozhraní `IValueType`. `IBoxArray` mají také tyto členy:

|Metoda|Popis|
|------------|-----------------|
|[Hodnota](#value)|Vrátí nezabalené pole, které bylo dříve Uloženo v této instanci `IBoxArray`.|

## <a name="value"></a>IBoxArray:: Value – vlastnost

Vrátí hodnotu, která byla původně uložena v tomto objektu.

### <a name="syntax"></a>Syntaxe

```cpp
property T Value {T get();}
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ zabalené hodnoty.

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

Vrátí hodnotu, která byla původně uložena v tomto objektu.

### <a name="remarks"></a>Poznámky

Příklad naleznete v tématu [zabalení](../cppcx/boxing-c-cx.md).

## <a name="see-also"></a>Viz také

[Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
