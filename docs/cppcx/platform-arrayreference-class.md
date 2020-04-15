---
title: Platform::ArrayReference – třída
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: e9dd16ad6c3f53c5562b0419197a582c06fbc642
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354789"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference – třída

`ArrayReference`je typ optimalizace, který můžete nahradit [platformou::Array^](../cppcx/platform-array-class.md) ve vstupních parametrech, pokud chcete vyplnit pole ve stylu C vstupními daty.

## <a name="syntax"></a>Syntaxe

```cpp
class ArrayReference
```

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[ArrayReference::ArrayReference](#ctor)|Inicializuje novou instanci třídy. `ArrayReference`|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[ArrayReference::operátor() Operátor](#operator-call)|Převede `ArrayReference` to `Platform::Array<T>^*`na .|
|[ArrayReference::operátor= Operátor](#operator-assign)|Přiřadí obsah jiné `ArrayReference` instance této instanci.|

## <a name="exceptions"></a>Výjimky

### <a name="remarks"></a>Poznámky

Pomocí `ArrayReference` vyplnit pole ve stylu C, vyhnete další operace kopírování, `Platform::Array` které by se podílejí na kopírování nejprve do proměnné a potom do pole stylu C. Při použití `ArrayReference`, je pouze jedna operace kopírování. Příklad kódu naleznete v tématech [Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Windows 8

**Minimální podporovaný server:** Windows Server 2012

**Obor názvů:** Platforma

**Záhlaví:** vccorlib.h

## <a name="arrayreferencearrayreference-constructor"></a><a name="ctor"></a>ArrayReference::Konstruktor ArrayReference

Inicializuje novou instanci třídy [Platform::ArrayReference.](../cppcx/platform-arrayreference-class.md)

### <a name="syntax"></a>Syntaxe

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>Parametry

*dataArg*<br/>
Ukazatel na data pole.

*sizeArg*<br/>
Počet prvků ve zdrojovém poli.

*otherArg*<br/>
Objekt, `ArrayReference` jehož data budou přesunuta k inicializaci nové instance.

### <a name="remarks"></a>Poznámky

## <a name="arrayreferenceoperator-operator"></a><a name="operator-assign"></a>ArrayReference::operátor= Operátor

Přiřadí zadaný objekt aktuálnímu objektu [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) pomocí sémantiky move.

### <a name="syntax"></a>Syntaxe

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>Parametry

*otherArg*<br/>
Objekt, který je přesunut `ArrayReference` do aktuálního objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu `ArrayReference`.

### <a name="remarks"></a>Poznámky

`Platform::ArrayReference`je standardní šablona třídy Jazyka C++, nikoli třída ref.

## <a name="arrayreferenceoperator-operator"></a><a name="operator-call"></a>ArrayReference::operátor() Operátor

Převede aktuální objekt [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) zpět na třídu [Platform::Array.](../cppcx/platform-array-class.md)

### <a name="syntax"></a>Syntaxe

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>Návratová hodnota

Typ typu z úchytu k objektu`Array<TArg>^`

### <a name="remarks"></a>Poznámky

[Platforma::ArrayReference](../cppcx/platform-arrayreference-class.md) je standardní šablona třídy C++ a [Platform::Array](../cppcx/platform-array-class.md) je třída ref.

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
