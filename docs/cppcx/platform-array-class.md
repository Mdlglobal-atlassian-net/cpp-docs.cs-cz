---
title: Platform::Array – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Array Constructors
- VCCORLIB/Namespace not found::Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: 597f8e32e2da95370169cdbfe2ccd209296322cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161657"
---
# <a name="platformarray-class"></a>Platform::Array – třída

Představuje jednorozměrné, upravitelná pole, která může být přijata a předané napříč binárním rozhraním aplikace (ABI).

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>Členové

Platform::Array dědí všechny metody z [Platform::writeonlyarray – třída](../cppcx/platform-writeonlyarray-class.md) a implementuje `Value` vlastnost [Platform::iboxarray – rozhraní](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Pole konstruktory](#ctor)|Inicializuje jednorozměrné upravitelná pole s typy zadanými parametrem šablony třídy *T*.|

### <a name="methods"></a>Metody

Zobrazit [Platform::writeonlyarray – třída](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Vlastnosti

|||
|-|-|
|[Array::Value](#value)|Načte popisovač pro daného pole.|

### <a name="remarks"></a>Poznámky

Třídy pole je zapečetěná a nelze ji zdědit.

Systém typů prostředí Windows Runtime nepodporuje konceptu Vícenásobná pole a proto nelze předat IVector < Platform::Array\<T >> jako návratovou hodnotu nebo metoda parametr. Vícenásobné pole nebo sekvence sekvencí předejte ABI, použijte `IVector<IVector<T>^>`.

Další informace o kdy a jak používat Platform::Array najdete v tématu [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Systém typů prostředí Windows Runtime nepodporuje konceptu Vícenásobná pole a proto nelze předat IVector < Platform::Array\<T >> jako návratovou hodnotu nebo metoda parametr. Vícenásobné pole nebo sekvence sekvencí předejte ABI, použijte `IVector<IVector<T>^>`.

Tato třída je definována v hlavičce vccorlib.h, který je automaticky zahrnut v kompilátoru. Je viditelný v technologii IntelliSense, ale ne v prohlížeči objektů, protože není veřejným typem definovaným v platform.winmd.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: **/ZW**

## <a name="ctor"></a>  Pole konstruktory

Inicializuje jednorozměrné upravitelná pole s typy zadanými parametrem šablony třídy *T*.

## <a name="syntax"></a>Syntaxe

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Parametr šablony třídy.

*Velikost*<br/>
Počet prvků v poli.

*data*<br/>
Ukazatel na pole datového typu `T` , který slouží k inicializaci objektu tohoto pole.

### <a name="remarks"></a>Poznámky

Další informace o tom, jak vytvořit instance Platform::Array najdete v tématu [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="get"></a>  Array::Get – metoda

Získá odkaz na element pole na zadané umístění indexu.

## <a name="syntax"></a>Syntaxe

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Parametry

*index*<br/>
Index založený na nule, který určuje element v poli. Minimální index 0 a maximální index hodnoty určené `size` parametr [konstruktor pole](#ctor).

### <a name="return-value"></a>Návratová hodnota

Prvek pole, které jsou určené `index` parametru.

## <a name="value"></a>  Vlastnost Array::Value

Načte popisovač pro daného pole.

## <a name="syntax"></a>Syntaxe

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač na aktuální pole.

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)<br/>
[Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
