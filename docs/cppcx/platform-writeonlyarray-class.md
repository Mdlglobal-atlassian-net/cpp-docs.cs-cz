---
title: Platform::WriteOnlyArray – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
ms.openlocfilehash: d06ed19b7c041f9ae73f862ba521449a206aa321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374646"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray – třída

Představuje jednorozměrné pole, které se používá jako vstupní parametr, když volající předá pole pro metodu vyplnit.

Tato třída ref je deklarována jako soukromá v souboru vccorlib.h; proto není emitován v metadatech a je pouze spotřební doplněk z Jazyka C++. Tato třída je určena pouze pro použití jako vstupní parametr, který přijímá pole, které volající přidělil. Není sestavitelný z uživatelského kódu. Umožňuje metodě Jazyka C++ zapisovat přímo do tohoto pole – vzor, který je známý jako *FillArray* vzor. Další informace naleznete [v tématech Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="syntax"></a>Syntaxe

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Tyto metody mají interní usnadnění přístupu – to znamená, že jsou přístupné pouze v rámci aplikace nebo komponenty jazyka C++.

|Name (Název)|Popis|
|----------|-----------------|
|[WriteOnlyArray::begin](#begin)|Iterátor, který odkazuje na první prvek pole.|
|[WriteOnlyArray::Data](#data)|Ukazatel na vyrovnávací paměť dat.|
|[WriteOnlyArray::end](#end)|Iterátor, který odkazuje na jeden za poslední prvek v poli.|
|[WriteOnlyArray::FastPass](#fastpass)|Označuje, zda pole může používat mechanismus FastPass, což je optimalizace transparentně prováděná systémem. Nepoužívejte to v kódu|
|[WriteOnlyArray::Délka](#length)|Vrátí počet prvků v poli.|
|[WriteOnlyArray::set](#set)|Nastaví zadaný prvek na zadanou hodnotu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`WriteOnlyArray`

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: **/ZW**

**Metadata:** Platform.winmd

**Obor názvů:** Platforma

## <a name="writeonlyarraybegin-method"></a><a name="begin"></a>WriteOnlyArray::metoda begin

Vrátí ukazatel na první prvek v poli.

### <a name="syntax"></a>Syntaxe

```cpp
T* begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první prvek v poli.

### <a name="remarks"></a>Poznámky

Tento iterátor lze použít s algoritmy `std::sort` STL, jako je například pracovat s prvky v poli.

## <a name="writeonlyarraydata-property"></a><a name="data"></a>WriteOnlyArray:vlastnost :Data

Ukazatel na vyrovnávací paměť dat.

### <a name="syntax"></a>Syntaxe

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nezpracované pole bajtů.

## <a name="writeonlyarrayend-method"></a><a name="end"></a>WriteOnlyArray::end Metoda

Vrátí ukazatel na jeden za poslední prvek v poli.

### <a name="syntax"></a>Syntaxe

```cpp
T* end() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel iterátor na jeden za poslední prvek v poli.

### <a name="remarks"></a>Poznámky

Tento iterátor lze použít s algoritmy STL `std::sort` k provádění operací, například na prvky pole.

## <a name="writeonlyarrayfastpass-property"></a><a name="fastpass"></a>WriteOnlyArray::Vlastnost FastPass

Označuje, zda lze provést interní optimalizaci FastPass. Není určeno pro použití podle uživatelského kódu.

### <a name="syntax"></a>Syntaxe

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která označuje, zda je pole FastPass.

## <a name="writeonlyarrayget-method"></a><a name="get"></a>WriteOnlyArray::metoda get

Vrátí prvek v zadaném indexu.

### <a name="syntax"></a>Syntaxe

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>Parametry

*indexArg*<br/>
Index, který chcete použít.

### <a name="return-value"></a>Návratová hodnota

## <a name="writeonlyarraylength-property"></a><a name="length"></a>WriteOnlyArray::Vlastnost Length

Vrátí počet prvků v poli přidělenévolajícím.

### <a name="syntax"></a>Syntaxe

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v poli.

## <a name="writeonlyarrayset-function"></a><a name="set"></a>WriteOnlyArray::nastavená funkce

Nastaví zadanou hodnotu na zadaný index v poli.

### <a name="syntax"></a>Syntaxe

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>Parametry

*indexArg*<br/>
Index prvku nastavit.

*valueArg*<br/>
Hodnota nastavená `indexArg`na .

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek, který byl právě nastaven.

### <a name="remarks"></a>Poznámky

Další informace o interpretaci hodnoty HRESULT naleznete v [tématu Struktura chybových kódů COM](/windows/win32/com/structure-of-com-error-codes).

## <a name="see-also"></a>Viz také

[Obor názvů platformy](platform-namespace-c-cx.md)<br/>
[Vytváření součástí prostředí Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
