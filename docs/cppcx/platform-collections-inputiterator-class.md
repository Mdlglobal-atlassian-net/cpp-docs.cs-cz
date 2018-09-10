---
title: 'Platform::Collections:: inputiterator – třída | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
dev_langs:
- C++
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67376497f3c0be84c0e24e403eaa3129ec38b255
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110776"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections:: inputiterator – třída

Poskytuje standardní knihovny InputIterator šablony pro kolekce odvozené z modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename X>
class InputIterator;
```

#### <a name="parameters"></a>Parametry

*X*<br/>
Vlastnost typename třídy InputIterator šablony.

### <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`difference_type`|Rozdíl ukazatelů (ptrdiff_t).|
|`iterator_category`|Kategorie vstupní iterátor (:: std::input_iterator_tag).|
|`pointer`|Ukazatel `const X`|
|`reference`|Odkaz na `const X`|
|`value_type`|`X` Typename.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[InputIterator::InputIterator](#ctor)|Inicializuje novou instanci třídy InputIterator.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[InputIterator::operator! = – operátor](#operator-inequality)|Určuje, zda aktuální InputIterator není roven zadané InputIterator.|
|[InputIterator::operator * – operátor](#operator-decrement)|Získá odkaz na prvek určeném aktuálním InputIterator.|
|[InputIterator::operator ++ – operátor](#operator-increment)|Aktuální InputIterator zvýší.|
|[InputIterator::operator == – operátor](#operator-equality)|Určuje, zda aktuální InputIterator rovná zadané InputIterator.|
|[InputIterator::operator -> – operátor](#operator-arrow)|Načte adresu elementu, který odkazuje aktuální InputIterator.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InputIterator`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections –

## <a name="ctor"></a>  InputIterator::InputIterator konstruktor

Inicializuje novou instanci třídy InputIterator.

### <a name="syntax"></a>Syntaxe

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iter);
```

### <a name="parameters"></a>Parametry

*ITER*<br/>
Objekt iterátoru.

## <a name="operator-arrow"></a>  InputIterator::operator -&gt; – operátor

Načte adresu určeném aktuálním InputIterator elementu.

### <a name="syntax"></a>Syntaxe

```
pointer operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa prvku určeném aktuálním InputIterator.

## <a name="operator-dereference"></a>  InputIterator::operator\* – operátor

Získá odkaz na prvek určeném aktuálním InputIterator.

### <a name="syntax"></a>Syntaxe

```
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Element určeném aktuálním InputIterator.

## <a name="operator-equality"></a>  InputIterator::operator == – operátor

Určuje, zda aktuální InputIterator rovná zadané InputIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné InputIterator.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud se rovná aktuální InputIterator `other`; v opačném případě `false`.

## <a name="operator-increment"></a>  InputIterator::operator ++ – operátor

Aktuální InputIterator zvýší.

### <a name="syntax"></a>Syntaxe

```
InputIterator& operator++();
InputIterator operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První syntaxe zvýší hodnotu a vrátí aktuální InputIterator. Druhá syntaxe vrátí kopii objektu aktuální InputIterator a potom zvýší aktuální InputIterator.

### <a name="remarks"></a>Poznámky

První syntaxe InputIterator předem zvýší aktuální InputIterator.

Druhá syntaxe po zvýší aktuální InputIterator. `int` v druhé syntaxi označuje operaci po přírůstku není skutečný celočíselný operand.

## <a name="operator-inequality"></a>  InputIterator::operator! = – operátor

Určuje, zda aktuální InputIterator není roven zadané InputIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné InputIterator.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud aktuální InputIterator není roven `other`; v opačném případě `false`.

## <a name="see-also"></a>Viz také

[Platforma Namespace](platform-namespace-c-cx.md)