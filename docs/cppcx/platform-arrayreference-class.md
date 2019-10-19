---
title: 'Platform:: ArrayReference – třída'
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: f7e587902f1c99b294ed79255397aeffccee26b5
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587909"
---
# <a name="platformarrayreference-class"></a>Platform:: ArrayReference – třída

`ArrayReference` je typ optimalizace, který můžete nahradit pro [Platform:: Array ^](../cppcx/platform-array-class.md) ve vstupních parametrech, pokud chcete vyplnit pole ve stylu jazyka C vstupními daty.

## <a name="syntax"></a>Syntaxe

```cpp
class ArrayReference
```

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[ArrayReference::ArrayReference](#ctor)|Inicializuje novou instanci třídy `ArrayReference`.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[ArrayReference:: operator () – operátor](#operator-call)|Převede tento `ArrayReference` na `Platform::Array<T>^*`.|
|[ArrayReference:: operator = – operátor](#operator-assign)|Přiřadí k této instanci obsah jiné `ArrayReference`.|

## <a name="exceptions"></a>Výjimky

### <a name="remarks"></a>Poznámky

Když použijete `ArrayReference` k vyplnění pole ve stylu jazyka C, vyhnete se nadbytečné operaci kopírování, která by byla zahrnuta do kopírování do `Platform::Array` proměnné, a pak do pole ve stylu jazyka C. Při použití `ArrayReference` existuje pouze jedna operace kopírování. Příklad kódu naleznete v tématu [Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Systém Windows 8

**Minimální podporovaný Server:** Windows Server 2012

**Obor názvů:** Platformy

**Záhlaví:** vccorlib. h

## <a name="ctor"></a>ArrayReference:: ArrayReference – konstruktor

Inicializuje novou instanci třídy [Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) .

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
Objekt `ArrayReference`, jehož data budou přesunuta za účelem inicializace nové instance.

### <a name="remarks"></a>Poznámky

## <a name="operator-assign"></a>ArrayReference:: operator = – operátor

Přiřadí zadaný objekt k aktuálnímu objektu [Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) pomocí sémantiky přesunutí.

### <a name="syntax"></a>Syntaxe

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>Parametry

*otherArg*<br/>
Objekt, který je přesunut do aktuálního objektu `ArrayReference`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu `ArrayReference`.

### <a name="remarks"></a>Poznámky

`Platform::ArrayReference` je standardní C++ šablona třídy, nikoli ref class.

## <a name="operator-call"></a>ArrayReference:: operator () – operátor

Převede aktuální objekt [Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) zpět na třídu [Platform:: Array](../cppcx/platform-array-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač objektu typu `Array<TArg>^`

### <a name="remarks"></a>Poznámky

[Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) je standardní C++ šablona třídy a [Platform:: Array](../cppcx/platform-array-class.md) je ref class.

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
