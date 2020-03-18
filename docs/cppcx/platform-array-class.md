---
title: 'Platform:: Array – třída'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Array
- VCCORLIB/Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: 7d9fca4de954b5ba9c7cbcb3bdfce0fe3263dbd7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445798"
---
# <a name="platformarray-class"></a>Platform:: Array – třída

Představuje jednorozměrné, upravitelné pole, které lze přijmout a předat přes binární rozhraní aplikace (ABI).

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>Členové

Platform:: Array dědí všechny metody z [třídy Platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) a implementuje vlastnost `Value` [rozhraní Platform:: IBoxArray](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Konstruktory Array](#ctor)|Inicializuje jednorozměrné pole s upravitelnými typy určené parametrem šablony třídy *T*.|

### <a name="methods"></a>Metody

Viz [Třída Platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Vlastnosti

|||
|-|-|
|[Array:: Value](#value)|Načte popisovač k aktuálnímu poli.|

### <a name="remarks"></a>Poznámky

Třída Array je zapečetěná a nelze ji zdědit.

Systém typů prostředí Windows Runtime nepodporuje koncept vícenásobných polí, a proto nelze předat IVector < Platform:: Array\<T > > jako návratovou hodnotu nebo parametr metody. Chcete-li předat vícenásobné pole nebo sekvenci sekvencí v rámci ABI, použijte `IVector<IVector<T>^>`.

Další informace o tom, kdy a jak používat Platform:: Array naleznete v tématu [Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Tato třída je definována v hlavičce vccorlib. h, která je automaticky obsažena v kompilátoru. Je viditelný v technologii IntelliSense, ale ne v Prohlížeč objektů, protože se nejedná o veřejný typ definovaný v objektu Platform. winmd.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: **/ZW**

## <a name="ctor"></a>Konstruktory Array

Inicializuje jednorozměrné pole s upravitelnými typy určené parametrem šablony třídy *T*.

## <a name="syntax"></a>Syntaxe

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Parametr šablony třídy.

*hodnota*<br/>
Počet prvků v poli.

*údajů*<br/>
Ukazatel na pole dat typu `T`, který se používá k inicializaci tohoto objektu Array.

### <a name="remarks"></a>Poznámky

Další informace o vytváření instancí Platform:: Array naleznete v tématu [Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="get"></a>Array:: get – metoda

Načte odkaz na prvek pole v zadaném umístění indexu.

## <a name="syntax"></a>Syntaxe

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Parametry

*indexovacím*<br/>
Index založený na nule, který identifikuje prvek v poli. Minimální index je 0 a maximální index je hodnota zadaná parametrem `size` v [konstruktoru Array](#ctor).

### <a name="return-value"></a>Návratová hodnota

Prvek pole určený parametrem `index`.

## <a name="value"></a>Array:: Value – vlastnost

Načte popisovač k aktuálnímu poli.

## <a name="syntax"></a>Syntaxe

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač k aktuálnímu poli.

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)<br/>
[Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
