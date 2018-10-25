---
title: Ccomsafearray – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6537cdb9e7ff9806bef3bfec85a94e0d50808477
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078463"
---
# <a name="ccomsafearray-class"></a>Ccomsafearray – třída

Tato třída představuje obálku pro `SAFEARRAY` struktury.

## <a name="syntax"></a>Syntaxe

```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat uložených v poli.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComSafeArray::CComSafeArray](#ccomsafearray)|Konstruktor|
|[Ccomsafearray –:: ~ ccomsafearray –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComSafeArray::Add](#add)|Přidá jeden nebo více prvků, nebo `SAFEARRAY` do struktury `CComSafeArray`.|
|[CComSafeArray::Attach](#attach)|Připojí `SAFEARRAY` struktury k `CComSafeArray` objektu.|
|[CComSafeArray::CopyFrom](#copyfrom)|Zkopíruje obsah objektu `SAFEARRAY` struktury do `CComSafeArray` objektu.|
|[CComSafeArray::CopyTo](#copyto)|Vytvoří kopii `CComSafeArray` objektu.|
|[CComSafeArray::Create](#create)|Vytvoří `CComSafeArray` objektu.|
|[CComSafeArray::Destroy](#destroy)|Odstraní `CComSafeArray` objektu.|
|[CComSafeArray::Detach](#detach)|Odpojí `SAFEARRAY` z `CComSafeArray` objektu.|
|[CComSafeArray::GetAt](#getat)|Načte jeden element z jednorozměrné pole.|
|[CComSafeArray::GetCount](#getcount)|Vrátí počet prvků v poli.|
|[CComSafeArray::GetDimensions](#getdimensions)|Vrátí počet dimenzí v poli.|
|[CComSafeArray::GetLowerBound](#getlowerbound)|Vrátí dolní mez pro daný rozměru pole.|
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Vrátí adresu `m_psa` datový člen.|
|[CComSafeArray::GetType](#gettype)|Vrátí typ dat uložených v poli.|
|[CComSafeArray::GetUpperBound](#getupperbound)|Vrátí horní mez pro všechny dimenze pole.|
|[CComSafeArray::IsSizable](#issizable)|Testuje, zda `CComSafeArray` objektu můžete změnit velikost.|
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Načte jeden element z multidimenzionálního pole.|
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|Nastaví hodnotu prvku v multidimenzionálního pole.|
|[CComSafeArray::Resize](#resize)|Změní velikost `CComSafeArray` objektu.|
|[CComSafeArray::SetAt](#setat)|Nastaví hodnotu prvku v jednorozměrné pole.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|Přetypování hodnoty `SAFEARRAY` ukazatele.|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Načte prvek z pole.|
|[CComSafeArray::operator =](#operator_eq)|Operátor přiřazení.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Tento datový člen udržuje adresu `SAFEARRAY` struktury.|

## <a name="remarks"></a>Poznámky

`CComSafeArray` poskytuje obálku pro [datový typ SAFEARRAY](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagsafearray) třídy, což představuje jednoduché vytvářet a spravovat jeden – a vícedimenzionální pole téměř jakýkoli z typů nepodporuje typ VARIANT.

`CComSafeArray` předávání polí mezi procesy zjednodušuje a navíc nabízí další bezpečnostní kontrolou hodnoty indexu pole s horní a dolní meze.

Dolní mez `CComSafeArray` můžete spustit na libovolné uživatelem definovanou hodnotu; pole, které jsou přístupné prostřednictvím C++ však používejte dolní mez 0. Další jazyky, jako je například Visual Basic mohou používat ostatní ohraničující hodnoty (například -10 do 10).

Použití [CComSafeArray::Create](#create) k vytvoření `CComSafeArray` objektu, a [CComSafeArray::Destroy](#destroy) ho odstranit.

A `CComSafeArray` může obsahovat následující dílčí typ VARIANT datové typy:

|VARTYPE|Popis|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ULONGLONG|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|desetinné ukazatele|
|VT_VARIANT|varianty ukazatele|
|VT_CY|Měna – datový typ|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsafe.h

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

##  <a name="add"></a>  CComSafeArray::Add

Přidá jeden nebo více prvků, nebo `SAFEARRAY` do struktury `CComSafeArray`.

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parametry

*psaSrc*<br/>
Ukazatel `SAFEARRAY` objektu.

*ulCount*<br/>
Počet objektů, které chcete přidat do pole.

*PT*<br/>
Ukazatel na jeden nebo více objektů, které mají být přidány do pole.

*t*<br/>
Odkaz na objekt, který chcete přidat do pole.

*bCopy*<br/>
Určuje, zda má být vytvořena kopie data. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Nové objekty, které se připojují na konci existujícího `SAFEARRAY` objektu. Přidání objektu do multidimenzionální `SAFEARRAY` objekt není podporován. Při přidávání existujícího pole objektů, obě pole musí obsahovat prvky stejného typu.

*BCopy* příznak je vzít v úvahu při prvky typu BSTR nebo VARIANTU jsou přidány do pole. Výchozí hodnota true zajistí, že nová kopie je provedeno dat, když bude prvek přidán do pole.

##  <a name="attach"></a>  CComSafeArray::Attach

Připojí `SAFEARRAY` struktury k `CComSafeArray` objektu.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*psaSrc*<br/>
Ukazatel `SAFEARRAY` struktury.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Připojí `SAFEARRAY` struktury k `CComSafeArray` objekt, což existující `CComSafeArray` dostupné metody.

##  <a name="ccomsafearray"></a>  CComSafeArray::CComSafeArray

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

*vázaný*<br/>
A `SAFEARRAYBOUND` struktury.

*ulCount*<br/>
Počet prvků v poli.

*lLBound*<br/>
Hodnota dolní mez; To znamená, že index prvního prvku v poli.

*pBound*<br/>
Ukazatel `SAFEARRAYBOUND` struktury.

*uDims*<br/>
Počet dimenzí v poli.

*saSrc*<br/>
Odkaz na `SAFEARRAY` struktury nebo `CComSafeArray` objektu. V obou případech konstruktor používá tento odkaz k vytvoření kopie pole, takže po vytvoření se neodkazuje pole.

*psaSrc*<br/>
Ukazatel `SAFEARRAY` struktury. Konstruktor používá tuto adresu k vytvoření kopie pole, takže po vytvoření se neodkazuje pole.

### <a name="remarks"></a>Poznámky

Vytvoří `CComSafeArray` objektu.

##  <a name="dtor"></a>  Ccomsafearray –:: ~ ccomsafearray –

Destruktor.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="copyfrom"></a>  CComSafeArray::CopyFrom

Zkopíruje obsah objektu `SAFEARRAY` struktury do `CComSafeArray` objektu.

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
Ukazatel `SAFEARRAY` ke kopírování.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda kopíruje obsah `SAFEARRAY` do aktuální `CComSafeArray` objektu. Nahrazují se existující obsah pole.

##  <a name="copyto"></a>  CComSafeArray::CopyTo

Vytvoří kopii `CComSafeArray` objektu.

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
Ukazatel na umístění, ve kterém chcete vytvořit nový `SAFEARRAY`.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda zkopíruje obsah objektu `CComSafeArray` objektů do `SAFEARRAY` struktura.

##  <a name="create"></a>  CComSafeArray::Create

Vytvoří `CComSafeArray`.

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>Parametry

*pBound*<br/>
Ukazatel `SAFEARRAYBOUND` objektu.

*uDims*<br/>
Počet dimenzí v poli.

*ulCount*<br/>
Počet prvků v poli.

*lLBound*<br/>
Hodnota dolní mez; To znamená, že index prvního prvku v poli.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

A `CComSafeArray` objekt můžete vytvořit ze stávajícího `SAFEARRAYBOUND` strukturu a počet rozměrů, nebo tak, že určíte počet prvků v poli a dolní mez. Pokud chcete přistupovat z aplikace Visual C++ je pole, musí být dolní mez 0. Další jazyky vám umožní jiné hodnoty pro dolní mez (například Visual Basic podporuje pole s prvky s rozsahem například -10-10).

##  <a name="destroy"></a>  CComSafeArray::Destroy

Odstraní `CComSafeArray` objektu.

```
HRESULT Destroy();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Odstraní existující `CComSafeArray` objektu a všechna data obsahuje.

##  <a name="detach"></a>  CComSafeArray::Detach

Odpojí `SAFEARRAY` z `CComSafeArray` objektu.

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel `SAFEARRAY` objektu.

### <a name="remarks"></a>Poznámky

Tato metoda se odpojí `SAFEARRAY` objektu z `CComSafeArray` objektu.

##  <a name="getat"></a>  CComSafeArray::GetAt

Načte jeden element z jednorozměrné pole.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Indexové číslo hodnotu jako pole k vrácení.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na prvek povinné pole.

##  <a name="getcount"></a>  CComSafeArray::GetCount

Vrátí počet prvků v poli.

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Rozměry pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v poli.

### <a name="remarks"></a>Poznámky

Při použití s multidimenzionálního pole, tato metoda vrátí počet prvků v konkrétní dimenzi.

##  <a name="getdimensions"></a>  CComSafeArray::GetDimensions

Vrátí počet dimenzí v poli.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet dimenzí v poli.

##  <a name="getlowerbound"></a>  CComSafeArray::GetLowerBound

Vrátí dolní mez pro daný rozměru pole.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Rozměry pole, pro který má být získána dolní mez. Pokud tento parametr vynechán, výchozí hodnota je 0.

### <a name="return-value"></a>Návratová hodnota

Vrátí dolní mez.

### <a name="remarks"></a>Poznámky

Pokud je dolní mez 0, znamená to C jako pole, jehož první prvek je prvek číslo 0. V případě chyby, například dimenze neplatný argument, tato metoda volá `AtlThrow` s chybou HRESULT popisující chybu.

##  <a name="getsafearrayptr"></a>  CComSafeArray::GetSafeArrayPtr

Vrátí adresu `m_psa` datový člen.

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel [CComSafeArray::m_psa](#m_psa) datový člen.

##  <a name="gettype"></a>  CComSafeArray::GetType

Vrátí typ dat uložených v poli.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí typ dat uložených v poli, které může být jedno z následujících typů:

|VARTYPE|Popis|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ULONGLONG|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|desetinné ukazatele|
|VT_VARIANT|varianty ukazatele|
|VT_CY|Měna – datový typ|

##  <a name="getupperbound"></a>  CComSafeArray::GetUpperBound

Vrátí horní mez pro všechny dimenze pole.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Rozměry pole, pro který má být získána horní mez. Pokud tento parametr vynechán, výchozí hodnota je 0.

### <a name="return-value"></a>Návratová hodnota

Vrátí horní mez. Tato hodnota je také zahrnuto, maximální platný index pro tuto dimenzi.

### <a name="remarks"></a>Poznámky

V případě chyby, například dimenze neplatný argument, tato metoda volá `AtlThrow` s chybou HRESULT popisující chybu.

##  <a name="issizable"></a>  CComSafeArray::IsSizable

Testuje, zda `CComSafeArray` objektu můžete změnit velikost.

```
bool IsSizable() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud `CComSafeArray` můžete změnit velikost, FALSE v případě nedostupnosti.

##  <a name="m_psa"></a>  CComSafeArray::m_psa

Udržuje adresu `SAFEARRAY` struktura získat přístup.

```
LPSAFEARRAY m_psa;
```

##  <a name="multidimgetat"></a>  CComSafeArray::MultiDimGetAt

Načte jeden element z multidimenzionálního pole.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>Parametry

*alIndex*<br/>
Ukazatel na vektor indexů pro jednotlivé rozměry pole. Úplně vlevo (nejvýznamnější) dimenze je `alIndex[0]`.

*t*<br/>
Vrátí odkaz na data.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="multidimsetat"></a>  CComSafeArray::MultiDimSetAt

Nastaví hodnotu prvku v multidimenzionálního pole.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Parametry

*alIndex*<br/>
Ukazatel na vektor indexů pro jednotlivé rozměry pole. Rozměr nejvíce vpravo (nejméně významnou) je `alIndex`[0].

*T*<br/>
Určuje hodnotu nového elementu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Toto je multidimenzionální verze [CComSafeArray::SetAt](#setat).

##  <a name="operator_at"></a>  CComSafeArray::operator \[\]

Načte prvek z pole.

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>Parametry

*Index, nIndex*<br/>
Indexové číslo požadovaný element v poli.

### <a name="return-value"></a>Návratová hodnota

Vrátí prvek odpovídající pole.

### <a name="remarks"></a>Poznámky

Podobně jako funkce, která se provede [CComSafeArray::GetAt](#getat), ale tento operátor funguje jenom jednorozměrná pole.

##  <a name="operator_eq"></a>  CComSafeArray::operator =

Operátor přiřazení.

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*saSrc*<br/>
Odkaz na `CComSafeArray` objektu.

*psaSrc*<br/>
Ukazatel `SAFEARRAY` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí typ dat uložených v poli.

##  <a name="operator_lpsafearray"></a>  CComSafeArray::operator LPSAFEARRAY

Přetypování hodnoty `SAFEARRAY` ukazatele.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Návratová hodnota

Přetypování hodnoty `SAFEARRAY` ukazatele.

##  <a name="resize"></a>  CComSafeArray::Resize

Změní velikost `CComSafeArray` objektu.

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Parametry

*pBound*<br/>
Ukazatel `SAFEARRAYBOUND` strukturu, která obsahuje informace o počtu prvků a dolní mez pole.

*ulCount*<br/>
Požadovaný počet objektů v poli se změněnou velikostí.

*lLBound*<br/>
Dolní mez.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda změní pouze rozměr nejvíce vpravo. Jeho nebude velikost pole, které vracejí `IsResizable` jako FALSE.

##  <a name="setat"></a>  CComSafeArray::SetAt

Nastaví hodnotu prvku v jednorozměrné pole.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
Číslo indexu elementu pole pro nastavení.

*t*<br/>
Nová hodnota zadaného prvku.

*bCopy*<br/>
Určuje, zda má být vytvořena kopie data. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

*BCopy* příznak je vzít v úvahu při prvky typu BSTR nebo VARIANTU jsou přidány do pole. Výchozí hodnota true zajistí, že nová kopie je provedeno dat, když bude prvek přidán do pole.

## <a name="see-also"></a>Viz také

[Datový typ SAFEARRAY](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagsafearray)<br/>
[CComSafeArray::Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
