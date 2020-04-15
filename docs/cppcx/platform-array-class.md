---
title: Platforma::Třída pole
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Array
- VCCORLIB/Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: d625d80df67a3c8207467ad629afd4c2bf88db18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318660"
---
# <a name="platformarray-class"></a>Platforma::Třída pole

Představuje jednorozměrné, upravitelné pole, které lze přijímat a předávána přes binární rozhraní aplikace (ABI).

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>Členové

Platforma::Array zdědí všechny své metody z [platformy::WriteOnlyArray Class](../cppcx/platform-writeonlyarray-class.md) a implementuje `Value` vlastnost rozhraní [Platform::IBoxArray .](../cppcx/platform-iboxarray-interface.md)

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Konstruktory polí](#ctor)|Inicializuje jednorozměrné, upravitelné pole typů určených parametrem šablony třídy *T*.|

### <a name="methods"></a>Metody

Viz [Platform::WriteOnlyArray Class](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Vlastnosti

|||
|-|-|
|[Pole::Hodnota](#value)|Načte popisovač do aktuálního pole.|

### <a name="remarks"></a>Poznámky

Třída Array je zapečetěna a nelze ji zdědit.

Systém typu Prostředí Windows Runtime nepodporuje koncept zubatých polí, a proto nelze\<předat platformu IVector<::Array T>> jako parametr návratové hodnoty nebo metody. Chcete-li předat zubaté pole nebo posloupnost `IVector<IVector<T>^>`sekvencí přes ABI, použijte .

Další informace o tom, kdy a jak používat platformu::Array, naleznete [v tématech Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Tato třída je definována v záhlaví vccorlib.h, která je automaticky zahrnuta kompilátorem. Je viditelná v IntelliSense, ale ne v prohlížeči objektů, protože se nejedná o veřejný typ definovaný v platform.winmd.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: **/ZW**

## <a name="array-constructors"></a><a name="ctor"></a>Konstruktory polí

Inicializuje jednorozměrné, upravitelné pole typů určených parametrem šablony třídy *T*.

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

*Dat*<br/>
Ukazatel na pole dat typu, `T` které se používá k inicializaci tohoto objektu Array.

### <a name="remarks"></a>Poznámky

Další informace o vytváření instancí platformy Platform::Array naleznete v [tématech Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="arrayget-method"></a><a name="get"></a>Pole::metoda get

Načte odkaz na prvek pole v zadaném umístění indexu.

## <a name="syntax"></a>Syntaxe

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Parametry

*Index*<br/>
Index založený na nule, který identifikuje prvek v poli. Minimální index je 0 a maximální index je `size` hodnota určená parametrem v [konstruktoru Array](#ctor).

### <a name="return-value"></a>Návratová hodnota

Prvek pole určený `index` parametrem.

## <a name="arrayvalue-property"></a><a name="value"></a>Pole::Vlastnost Value

Načte popisovač do aktuálního pole.

## <a name="syntax"></a>Syntaxe

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač aktuálního pole.

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)<br/>
[Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
