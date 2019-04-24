---
title: Platform::writeonlyarray – třída
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
ms.openlocfilehash: fb582106fe2f18e939f11180048a125c683ca2f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182935"
---
# <a name="platformwriteonlyarray-class"></a>Platform::writeonlyarray – třída

Představuje jednorozměrné pole, která slouží jako vstupní parametr, pokud volající předá pole pro metodu tak, aby vyplnil.

Tato třída ref je deklarován jako soukromý v vccorlib.h; proto není aktivováno v metadatech a je použitelné z jazyka C++. Tato třída je určena pouze pro použití jako vstupní parametr, který přijímá pole, které má přidělené volajícímu. Není constructible z uživatelského kódu. Povolí metodu C++ psát přímo do tohoto pole – vzor, který se označuje jako *FillArray* vzor. Další informace najdete v tématu [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="syntax"></a>Syntaxe

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Tyto metody mají interní přístupnost – to znamená, že jsou přístupné pouze v rámci C++ aplikace nebo komponenty.

|Název|Popis|
|----------|-----------------|
|[WriteOnlyArray::begin](#begin)|Iterátor odkazující na první prvek pole.|
|[WriteOnlyArray::Data](#data)|Ukazatel do vyrovnávací paměti dat.|
|[WriteOnlyArray::end](#end)|Iterátor, který odkazuje na jedno místo za posledním prvkem v poli.|
|[WriteOnlyArray::FastPass](#fastpass)|Označuje, zda pole můžete použít FastPass mechanismus, který představuje optimalizaci transparentně provádí systému. Nepoužívejte to ve vašem kódu|
|[WriteOnlyArray::Length](#length)|Vrátí počet prvků v poli.|
|[WriteOnlyArray::set](#set)|Nastaví zadaný element se zadanou hodnotou.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`WriteOnlyArray`

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: **/ZW**

**Metadata:** Platform.winmd

**Namespace:** Platforma

## <a name="begin"></a>  WriteOnlyArray::begin – metoda

Vrací ukazatel na první prvek v poli.

### <a name="syntax"></a>Syntaxe

```cpp
T* begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první prvek v poli.

### <a name="remarks"></a>Poznámky

Tato iterátoru lze použít s algoritmy STL, jako `std::sort` ovládajících prvků v poli.

## <a name="data"></a>  Vlastnost WriteOnlyArray::Data

Ukazatel do vyrovnávací paměti data.

### <a name="syntax"></a>Syntaxe

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nezpracovaná pole bajtů.

## <a name="end"></a>  WriteOnlyArray::end – metoda

Vrací ukazatel na jedno místo za posledním prvkem v poli.

### <a name="syntax"></a>Syntaxe

```cpp
T* end() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor ukazatel na jedno místo za posledním prvkem v poli.

### <a name="remarks"></a>Poznámky

Tato iterátoru lze použít s algoritmy STL můžete provádět operace, jako `std::sort` prvků pole.

## <a name="fastpass"></a>  Vlastnost WriteOnlyArray::FastPass

Určuje, zda lze provést interní FastPass optimalizace. Není určena pro použití v uživatelském kódu.

### <a name="syntax"></a>Syntaxe

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota určující, zda je pole FastPass.

## <a name="get"></a>  WriteOnlyArray::get – metoda

Vrátí hodnotu prvku na zadaném indexu.

### <a name="syntax"></a>Syntaxe

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>Parametry

*indexArg*<br/>
Index použít.

### <a name="return-value"></a>Návratová hodnota

## <a name="length"></a>  Vlastnost WriteOnlyArray::Length

Vrátí počet prvků v pole přidělené volajícímu.

### <a name="syntax"></a>Syntaxe

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v poli.

## <a name="set"></a>  WriteOnlyArray::set – funkce

Nastaví zadanou hodnotu na zadaný index v poli.

### <a name="syntax"></a>Syntaxe

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>Parametry

*indexArg*<br/>
Index prvku, který chcete nastavit.

*valueArg*<br/>
Hodnota k nastavení na `indexArg`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek, který byl právě nastavili.

### <a name="remarks"></a>Poznámky

Další informace o tom, jak interpretovat hodnota HRESULT, naleznete v tématu [struktura kódy chyb COM](/windows/desktop/com/structure-of-com-error-codes).

## <a name="see-also"></a>Viz také:

[Platforma Namespace](platform-namespace-c-cx.md)<br/>
[Vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
