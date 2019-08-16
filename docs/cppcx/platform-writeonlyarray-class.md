---
title: 'Platform:: WriteOnlyArray – třída'
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
ms.openlocfilehash: 5652123d4866262515f804dba790af51610eb426
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500525"
---
# <a name="platformwriteonlyarray-class"></a>Platform:: WriteOnlyArray – třída

Představuje jednorozměrné pole, které se používá jako vstupní parametr, když volající předává pole pro metodu, která má být vyplněna.

Tato referenční třída je deklarována jako soukromá v vccorlib. h; Proto nejsou vygenerovány v metadatech a jsou použitelné pouze z C++. Tato třída je určena pouze pro použití jako vstupní parametr, který přijímá pole, které volající přidělil. Není constructible z uživatelského kódu. Umožňuje C++ metodě zapisovat přímo do tohoto pole – vzor, který je známý jako *metodě FillArray* vzor. Další informace najdete v tématu [Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="syntax"></a>Syntaxe

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Tyto metody mají interní přístupnost – to znamená, že jsou přístupné pouze v rámci C++ aplikace nebo komponenty.

|Name|Popis|
|----------|-----------------|
|[WriteOnlyArray:: begin](#begin)|Iterátor, který odkazuje na první prvek pole.|
|[WriteOnlyArray::D ATA](#data)|Ukazatel na vyrovnávací paměť dat.|
|[WriteOnlyArray:: end](#end)|Iterátor, který odkazuje na jeden za poslední prvek v poli.|
|[WriteOnlyArray:: FastPass](#fastpass)|Označuje, zda může pole používat mechanismus FastPass, což je optimalizace, kterou systém provádí transparentně. Nepoužívejte ho ve svém kódu.|
|[WriteOnlyArray:: Length](#length)|Vrátí počet prvků v poli.|
|[WriteOnlyArray:: set](#set)|Nastaví zadaný element na zadanou hodnotu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`WriteOnlyArray`

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: **/ZW**

**Metadata:** Platform.winmd

**Hosting** Platforma

## <a name="begin"></a>WriteOnlyArray:: begin – metoda

Vrátí ukazatel na první prvek v poli.

### <a name="syntax"></a>Syntaxe

```cpp
T* begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první prvek v poli.

### <a name="remarks"></a>Poznámky

Tento iterátor lze použít s algoritmy STL, jako je `std::sort` například pro práci na prvcích v poli.

## <a name="data"></a>WriteOnlyArray::D vlastnost ATA

Ukazatel na vyrovnávací paměť dat.

### <a name="syntax"></a>Syntaxe

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na bajty nezpracovaného pole.

## <a name="end"></a>WriteOnlyArray:: end – metoda

Vrátí ukazatel na jeden za poslední prvek v poli.

### <a name="syntax"></a>Syntaxe

```cpp
T* end() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel iterátoru na jeden za poslední prvek v poli.

### <a name="remarks"></a>Poznámky

Tento iterátor lze použít s algoritmy STL k provádění operací, jako jsou `std::sort` například prvky pole.

## <a name="fastpass"></a>WriteOnlyArray:: FastPass – vlastnost

Určuje, zda lze provést optimalizaci interního FastPass. Neurčeno pro použití uživatelským kódem.

### <a name="syntax"></a>Syntaxe

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která označuje, zda je pole FastPass.

## <a name="get"></a>WriteOnlyArray:: get – metoda

Vrátí prvek na zadaném indexu.

### <a name="syntax"></a>Syntaxe

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>Parametry

*indexArg*<br/>
Index, který se má použít.

### <a name="return-value"></a>Návratová hodnota

## <a name="length"></a>WriteOnlyArray:: Length – vlastnost

Vrátí počet prvků v poli přiděleném volajícímu.

### <a name="syntax"></a>Syntaxe

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v poli.

## <a name="set"></a>WriteOnlyArray:: set – funkce

Nastaví zadanou hodnotu v zadaném indexu v poli.

### <a name="syntax"></a>Syntaxe

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>Parametry

*indexArg*<br/>
Index elementu, který se má nastavit

*valueArg*<br/>
Hodnota, která má být `indexArg`nastavena na hodnotu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek, který byl právě nastaven.

### <a name="remarks"></a>Poznámky

Další informace o tom, jak interpretovat hodnotu HRESULT, najdete v tématu [Struktura chybových kódů modelu COM](/windows/win32/com/structure-of-com-error-codes).

## <a name="see-also"></a>Viz také:

[Obor názvů platformy](platform-namespace-c-cx.md)<br/>
[Vytváření komponent prostředí Windows Runtime v nástrojiC++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
