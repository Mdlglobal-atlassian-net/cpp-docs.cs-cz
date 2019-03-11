---
title: Platform::weakreference – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- Platform::WeakReference
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
ms.openlocfilehash: cadafcc227347bc2f55c8600ae63a5c0996aefae
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742078"
---
# <a name="platformweakreference-class"></a>Platform::weakreference – třída

Představuje Slabý odkaz na instanci třídy ref class.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakReference
```

#### <a name="parameters"></a>Parametry

### <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Člen|Popis|
|------------|-----------------|
|[Weakreference::weakreference –](#ctor)|Inicializuje novou instanci třídy WeakReference.|

### <a name="methods"></a>Metody

|Člen|Popis|
|------------|-----------------|
|[Weakreference::Resolve –](#resolve)|Vrátí popisovač do základní třídy ref class nebo nullptr, pokud objekt již existuje.|

### <a name="operators"></a>Operátory

|Člen|Popis|
|------------|-----------------|
|[WeakReference::operator =](#operator-assign)|WeakReference objektu přiřadí novou hodnotu.|
|[WeakReference::operator BoolType](#booltype)|Implementuje vzor bezpečné bool.|

### <a name="remarks"></a>Poznámky

Vlastní třídy WeakReference není třídy ref class a proto není odvozena od Platform::Object ^ a nelze jej použít v podpisu veřejné metody.

## <a name="operator-assign"></a> WeakReference::operator =

Přiřadí hodnotu WeakReference.

### <a name="syntax"></a>Syntaxe

```cpp
WeakReference& operator=(decltype(__nullptr));
WeakReference& operator=(const WeakReference& otherArg);
WeakReference& operator=(WeakReference&& otherArg);
WeakReference& operator=(const volatile ::Platform::Object^ const otherArg);
```

### <a name="remarks"></a>Poznámky

Poslední přetížení v seznamu výše umožňuje přiřadit proměnné WeakReference třídy ref class. V tomto případě je třída ref class přetypovat dolů na [Platform::Object](../cppcx/platform-object-class.md)^. Později obnovit původní typ tak, že zadáte jako argument pro parametr typu v [weakreference::Resolve –\<T >](#resolve) členskou funkci.

## <a name="booltype"></a> WeakReference::operator BoolType

Implementuje vzor bezpečné bool třídy WeakReference. Nesmí být explicitně volat z vašeho kódu.

### <a name="syntax"></a>Syntaxe

```cpp
BoolType BoolType();
```

## <a name="resolve"></a> Weakreference::Resolve – metoda (obor názvů Platform)

Vrátí popisovač do původní třídy ref nebo `nullptr` Pokud objekt již existuje.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
T^ Resolve() const;
```

### <a name="parameters"></a>Parametry

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

Popisovač třídy ref class, která byla dříve přidružená weakreference – objekt nebo nullptr.

### <a name="example"></a>Příklad

```cpp
Bar^ bar = ref new Bar();
//use bar...

if (bar != nullptr)
{
    WeakReference wr(bar);
    Bar^ newReference = wr.Resolve<Bar>();
}
```

Všimněte si, že je parametr typu T, T není ^.

## <a name="ctor"></a> Weakreference::weakreference – konstruktor

Poskytuje různé způsoby, jak vytvořit WeakReference.

### <a name="syntax"></a>Syntaxe

```cpp
WeakReference();
WeakReference(decltype(__nullptr));
WeakReference(const WeakReference& otherArg);
WeakReference(WeakReference&& otherArg);
explicit WeakReference(const volatile ::Platform::Object^ const otherArg);
```

### <a name="example"></a>Příklad

```cpp
MyClass^ mc = ref new MyClass();
WeakReference wr(mc);
MyClass^ copy2 = wr.Resolve<MyClass>();
```

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
