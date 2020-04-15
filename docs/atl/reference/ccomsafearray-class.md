---
title: Třída CComSafeArray
ms.date: 05/06/2019
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
ms.openlocfilehash: d1e72d364858ea31541d574ed77bdc8ccca7d748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327393"
---
# <a name="ccomsafearray-class"></a>Třída CComSafeArray

Tato třída je obálka `SAFEARRAY` pro strukturu.

## <a name="syntax"></a>Syntaxe

```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat, která mají být uložena v poli.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComSafeArray::CcomSafeArray](#ccomsafearray)|Konstruktor|
|[CComSafeArray::~CComSafeArray](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComSafeArray::Přidat](#add)|Přidá jeden nebo více `SAFEARRAY` prvků nebo `CComSafeArray`struktury do .|
|[CComSafeArray::Připojit](#attach)|Připojí `SAFEARRAY` strukturu k `CComSafeArray` objektu.|
|[CComSafeArray::CopyFrom](#copyfrom)|Zkopíruje obsah `SAFEARRAY` struktury do `CComSafeArray` objektu.|
|[CComSafeArray::CopyTo](#copyto)|Vytvoří kopii `CComSafeArray` objektu.|
|[CComSafeArray::Vytvořit](#create)|Vytvoří `CComSafeArray` objekt.|
|[CComSafeArray::Destroy](#destroy)|Zničí `CComSafeArray` objekt.|
|[CComSafeArray::Detach](#detach)|Odpojí `SAFEARRAY` od objektu. `CComSafeArray`|
|[CComSafeArray::Getat](#getat)|Načte jeden prvek z jednorozměrného pole.|
|[CComSafeArray::GetCount](#getcount)|Vrátí počet prvků v poli.|
|[CComSafeArray::GetDimensions](#getdimensions)|Vrátí počet dimenzí v poli.|
|[CComSafeArray::GetlowerBound](#getlowerbound)|Vrátí dolní mez pro danou dimenzi pole.|
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Vrátí adresu datového `m_psa` člena.|
|[CComSafeArray::Typ](#gettype)|Vrátí typ dat uložených v poli.|
|[CComSafeArray::GetupperBound](#getupperbound)|Vrátí horní mez pro libovolnou dimenzi pole.|
|[CComSafeArray::Lze sizovat](#issizable)|Testuje, `CComSafeArray` pokud lze velikost objektu.|
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Načte jeden prvek z vícerozměrného pole.|
|[CComSafeArray::multidimsetat](#multidimsetat)|Nastaví hodnotu prvku v vícerozměrném poli.|
|[CComSafeArray::Změna velikosti](#resize)|Změní velikost `CComSafeArray` objektu.|
|[CComSafeArray::Setat](#setat)|Nastaví hodnotu prvku v jednorozměrném poli.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CComSafeArray::operátor LPSAFEARRAY](#operator_lpsafearray)|Předává hodnotu `SAFEARRAY` ukazatel.|
|[CComSafeArray::operátor\[\]](ccomsafearray-class.md#operator_at)|Načte prvek z pole.|
|[CComSafeArray::operátor =](#operator_eq)|Operátor přiřazení.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Tento datový člen obsahuje `SAFEARRAY` adresu struktury.|

## <a name="remarks"></a>Poznámky

`CComSafeArray`poskytuje obálku pro třídu [SAFEARRAY Data Type,](/windows/win32/api/oaidl/ns-oaidl-safearray) takže je jednoduché vytvořit a spravovat jednorozměrná a vícerozměrná pole téměř všech typů podporovaných variantou.

`CComSafeArray`zjednodušuje předávání polí mezi procesy a navíc poskytuje další zabezpečení kontrolou hodnot indexu pole proti horním a dolním mezním hodnotám.

Dolní mez `CComSafeArray` může začínat libovolnou uživatelem definovanou hodnotou. pole, které jsou přístupné prostřednictvím jazyka C++ by však použít dolní mez 0. Jiné jazyky, jako je například Visual Basic může používat jiné ohraničovací hodnoty (například -10 až 10).

Použijte [CComSafeArray::Create](#create) k `CComSafeArray` vytvoření objektu a [CComSafeArray::Destroy](#destroy) jej odstranit.

A `CComSafeArray` může obsahovat následující podmnožinu datových typů VARIANT:

|TYP VAR|Popis|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|dlouhé|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|desetinný ukazatel|
|VT_VARIANT|ukazatel varianty|
|VT_CY|Měna – datový typ|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsafe.h

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

## <a name="ccomsafearrayadd"></a><a name="add"></a>CComSafeArray::Přidat

Přidá jeden nebo více `SAFEARRAY` prvků nebo `CComSafeArray`struktury do .

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parametry

*psaSrc*<br/>
Ukazatel na `SAFEARRAY` objekt.

*ulCount*<br/>
Počet objektů, které chcete přidat do pole.

*Pt*<br/>
Ukazatel na jeden nebo více objektů, které mají být přidány do pole.

*t*<br/>
Odkaz na objekt, který má být přidán do pole.

*bKopie*<br/>
Označuje, zda má být vytvořena kopie dat. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Nové objekty jsou připojeny na `SAFEARRAY` konec existujícího objektu. Přidání objektu do `SAFEARRAY` vícerozměrného objektu není podporováno. Při přidávání existující pole objektů musí obě pole obsahovat prvky stejného typu.

Příznak *bCopy* se bere v úvahu při přidání prvků typu BSTR nebo VARIANT do pole. Výchozí hodnota TRUE zajišťuje, že je při přidání prvku do pole provedena nová kopie dat.

## <a name="ccomsafearrayattach"></a><a name="attach"></a>CComSafeArray::Připojit

Připojí `SAFEARRAY` strukturu k `CComSafeArray` objektu.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*psaSrc*<br/>
Ukazatel na `SAFEARRAY` strukturu.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Připojí k `SAFEARRAY` `CComSafeArray` objektu strukturu a `CComSafeArray` zpřístupní existující metody.

## <a name="ccomsafearrayccomsafearray"></a><a name="ccomsafearray"></a>CComSafeArray::CcomSafeArray

Konstruktor

```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*Vázán*<br/>
Struktura. `SAFEARRAYBOUND`

*ulCount*<br/>
Počet prvků v poli.

*LLBound*<br/>
Dolní mez hodnota; to znamená, že index první prvek v poli.

*pBound*<br/>
Ukazatel na `SAFEARRAYBOUND` strukturu.

*uDims*<br/>
Počet dimenzí v poli.

*saSrc řekl:*<br/>
Odkaz na `SAFEARRAY` strukturu `CComSafeArray` nebo objekt. V obou případech konstruktor používá tento odkaz k vytvoření kopie pole, takže pole není odkazováno po konstrukci.

*psaSrc*<br/>
Ukazatel na `SAFEARRAY` strukturu. Konstruktor používá tuto adresu k vytvoření kopie pole, takže pole není odkazováno po konstrukci.

### <a name="remarks"></a>Poznámky

Vytvoří `CComSafeArray` objekt.

## <a name="ccomsafearrayccomsafearray"></a><a name="dtor"></a>CComSafeArray::~CComSafeArray

Destruktor.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

## <a name="ccomsafearraycopyfrom"></a><a name="copyfrom"></a>CComSafeArray::CopyFrom

Zkopíruje obsah `SAFEARRAY` struktury do `CComSafeArray` objektu.

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
Ukazatel na `SAFEARRAY` kopírovat.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda zkopíruje `SAFEARRAY` obsah do `CComSafeArray` aktuálního objektu. Stávající obsah pole jsou nahrazeny.

## <a name="ccomsafearraycopyto"></a><a name="copyto"></a>CComSafeArray::CopyTo

Vytvoří kopii `CComSafeArray` objektu.

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
Ukazatel na umístění, ve kterém `SAFEARRAY`chcete vytvořit nový .

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda zkopíruje `CComSafeArray` obsah objektu do `SAFEARRAY` struktury.

## <a name="ccomsafearraycreate"></a><a name="create"></a>CComSafeArray::Vytvořit

Vytvoří `CComSafeArray`.

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>Parametry

*pBound*<br/>
Ukazatel na `SAFEARRAYBOUND` objekt.

*uDims*<br/>
Počet dimenzí v poli.

*ulCount*<br/>
Počet prvků v poli.

*LLBound*<br/>
Dolní mez hodnota; to znamená, že index první prvek v poli.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Objekt `CComSafeArray` lze vytvořit z `SAFEARRAYBOUND` existující struktury a počet dimenzí nebo zadáním počtu prvků v poli a dolní mez. Pokud pole má být přístupné z Jazyka C++, dolní mez by měla být 0. Jiné jazyky mohou povolit jiné hodnoty pro dolní mez (například Visual Basic podporuje pole s prvky s rozsahem, jako je například -10 až 10).

## <a name="ccomsafearraydestroy"></a><a name="destroy"></a>CComSafeArray::Destroy

Zničí `CComSafeArray` objekt.

```
HRESULT Destroy();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Zničí existující `CComSafeArray` objekt a všechna data, která obsahuje.

## <a name="ccomsafearraydetach"></a><a name="detach"></a>CComSafeArray::Detach

Odpojí `SAFEARRAY` od objektu. `CComSafeArray`

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `SAFEARRAY` objekt.

### <a name="remarks"></a>Poznámky

Tato metoda odpojí `SAFEARRAY` objekt `CComSafeArray` od objektu.

## <a name="ccomsafearraygetat"></a><a name="getat"></a>CComSafeArray::Getat

Načte jeden prvek z jednorozměrného pole.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Parametry

*Lindex*<br/>
Číslo indexu hodnoty v poli vrátit.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na povinný prvek pole.

## <a name="ccomsafearraygetcount"></a><a name="getcount"></a>CComSafeArray::GetCount

Vrátí počet prvků v poli.

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Dimenze pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v poli.

### <a name="remarks"></a>Poznámky

Při použití s vícerozměrným polem vrátí tato metoda počet prvků pouze v určité dimenzi.

## <a name="ccomsafearraygetdimensions"></a><a name="getdimensions"></a>CComSafeArray::GetDimensions

Vrátí počet dimenzí v poli.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet dimenzí v poli.

## <a name="ccomsafearraygetlowerbound"></a><a name="getlowerbound"></a>CComSafeArray::GetlowerBound

Vrátí dolní mez pro danou dimenzi pole.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Dimenze pole, pro které chcete získat dolní mez. Pokud je vynechán, výchozí hodnota je 0.

### <a name="return-value"></a>Návratová hodnota

Vrátí dolní mez.

### <a name="remarks"></a>Poznámky

Pokud je dolní mez 0, znamená to pole podobné C, jehož prvním prvkem je číslo elementu 0. V případě chyby, například neplatný argument dimenze, `AtlThrow` tato metoda volá s HRESULT popisující chybu.

## <a name="ccomsafearraygetsafearrayptr"></a><a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr

Vrátí adresu datového `m_psa` člena.

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na datový člen [CComSafeArray::m_psa.](#m_psa)

## <a name="ccomsafearraygettype"></a><a name="gettype"></a>CComSafeArray::Typ

Vrátí typ dat uložených v poli.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí typ dat uložených v poli, což může být libovolný z následujících typů:

|TYP VAR|Popis|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|dlouhé|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|desetinný ukazatel|
|VT_VARIANT|ukazatel varianty|
|VT_CY|Měna – datový typ|

## <a name="ccomsafearraygetupperbound"></a><a name="getupperbound"></a>CComSafeArray::GetupperBound

Vrátí horní mez pro libovolnou dimenzi pole.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Dimenze pole, pro které chcete získat horní mez. Pokud je vynechán, výchozí hodnota je 0.

### <a name="return-value"></a>Návratová hodnota

Vrátí horní mez. Tato hodnota je včetně, maximální platný index pro tuto dimenzi.

### <a name="remarks"></a>Poznámky

V případě chyby, například neplatný argument dimenze, `AtlThrow` tato metoda volá s HRESULT popisující chybu.

## <a name="ccomsafearrayissizable"></a><a name="issizable"></a>CComSafeArray::Lze sizovat

Testuje, `CComSafeArray` pokud lze velikost objektu.

```
bool IsSizable() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu `CComSafeArray` PRAVDA, pokud lze velikost velikosti hodnotit, nepravda, pokud ji nelze.

## <a name="ccomsafearraym_psa"></a><a name="m_psa"></a>CComSafeArray::m_psa

Obsahuje adresu `SAFEARRAY` přístupné struktury.

```
LPSAFEARRAY m_psa;
```

## <a name="ccomsafearraymultidimgetat"></a><a name="multidimgetat"></a>CComSafeArray::MultiDimGetAt

Načte jeden prvek z vícerozměrného pole.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>Parametry

*alIndex*<br/>
Ukazatel na vektor indexů pro každou dimenzi v poli. Nejlevější (nejvýznamnější) dimenze `alIndex[0]`je .

*t*<br/>
Odkaz na vrácená data.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="ccomsafearraymultidimsetat"></a><a name="multidimsetat"></a>CComSafeArray::multidimsetat

Nastaví hodnotu prvku v vícerozměrném poli.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Parametry

*alIndex*<br/>
Ukazatel na vektor indexů pro každou dimenzi v poli. Nejpravoúplnější (nejméně významná) dimenze je `alIndex`[0].

*T*<br/>
Určuje hodnotu nového prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Toto je vícerozměrná verze [CComSafeArray::SetAt](#setat).

## <a name="ccomsafearrayoperator-"></a><a name="operator_at"></a>CComSafeArray::operátor\[\]

Načte prvek z pole.

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>Parametry

*lIndex, nIndex*<br/>
Číslo indexu požadovaného prvku v poli.

### <a name="return-value"></a>Návratová hodnota

Vrátí příslušný prvek pole.

### <a name="remarks"></a>Poznámky

Provádí podobnou funkci [jako CComSafeArray::GetAt](#getat), ale tento operátor pracuje pouze s jednorozměrnými poli.

## <a name="ccomsafearrayoperator-"></a><a name="operator_eq"></a>CComSafeArray::operátor =

Operátor přiřazení.

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*saSrc řekl:*<br/>
Odkaz na `CComSafeArray` objekt.

*psaSrc*<br/>
Ukazatel na `SAFEARRAY` objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí typ dat uložených v poli.

## <a name="ccomsafearrayoperator-lpsafearray"></a><a name="operator_lpsafearray"></a>CComSafeArray::operátor LPSAFEARRAY

Předává hodnotu `SAFEARRAY` ukazatel.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Návratová hodnota

Předává hodnotu `SAFEARRAY` ukazatel.

## <a name="ccomsafearrayresize"></a><a name="resize"></a>CComSafeArray::Změna velikosti

Změní velikost `CComSafeArray` objektu.

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Parametry

*pBound*<br/>
Ukazatel na `SAFEARRAYBOUND` strukturu, která obsahuje informace o počtu prvků a dolní mez pole.

*ulCount*<br/>
Požadovaný počet objektů v poli se velikosti.

*LLBound*<br/>
Dolní mez.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda změní velikost pouze vpravo nejvíce dimenze. Nezmění velikost polí, která `IsResizable` se vrátí jako NEPRAVDA.

## <a name="ccomsafearraysetat"></a><a name="setat"></a>CComSafeArray::Setat

Nastaví hodnotu prvku v jednorozměrném poli.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parametry

*Lindex*<br/>
Číslo indexu prvku pole, který chcete nastavit.

*t*<br/>
Nová hodnota zadaného prvku.

*bKopie*<br/>
Označuje, zda má být vytvořena kopie dat. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Příznak *bCopy* se bere v úvahu při přidání prvků typu BSTR nebo VARIANT do pole. Výchozí hodnota TRUE zajišťuje, že je při přidání prvku do pole provedena nová kopie dat.

## <a name="see-also"></a>Viz také

[Datový typ SAFEARRAY](/windows/win32/api/oaidl/ns-oaidl-safearray)<br/>
[CComSafeArray::Vytvořit](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
