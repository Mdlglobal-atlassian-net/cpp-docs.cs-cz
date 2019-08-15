---
title: CComSafeArray – třída
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
ms.openlocfilehash: 36750990dc62d5b24cf1107ac8a2724df787a47d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496998"
---
# <a name="ccomsafearray-class"></a>CComSafeArray – třída

Tato třída je obálkou pro `SAFEARRAY` strukturu.

## <a name="syntax"></a>Syntaxe

```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat, který bude uložen v poli.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComSafeArray::CComSafeArray](#ccomsafearray)|Konstruktor|
|[CComSafeArray::~CComSafeArray](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComSafeArray:: Add](#add)|Přidá jeden nebo více prvků nebo `SAFEARRAY` struktury `CComSafeArray`do.|
|[CComSafeArray:: Attach](#attach)|`SAFEARRAY` Připojí strukturu`CComSafeArray` k objektu.|
|[CComSafeArray::CopyFrom](#copyfrom)|Zkopíruje obsah `SAFEARRAY` struktury `CComSafeArray` do objektu.|
|[CComSafeArray:: CopyTo](#copyto)|Vytvoří kopii `CComSafeArray` objektu.|
|[CComSafeArray:: Create](#create)|`CComSafeArray` Vytvoří objekt.|
|[CComSafeArray::D estroy](#destroy)|`CComSafeArray` Odstraní objekt.|
|[CComSafeArray::D etach](#detach)|Odpojí `CComSafeArray` objekt odobjektu.`SAFEARRAY`|
|[CComSafeArray::GetAt](#getat)|Načte jeden prvek z jednorozměrného pole.|
|[CComSafeArray:: GetCount](#getcount)|Vrátí počet prvků v poli.|
|[CComSafeArray:: GetDimensions](#getdimensions)|Vrátí počet rozměrů v poli.|
|[CComSafeArray::GetLowerBound](#getlowerbound)|Vrátí dolní mez pro danou dimenzi pole.|
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Vrátí adresu `m_psa` datového členu.|
|[CComSafeArray:: GetType](#gettype)|Vrátí typ dat uložených v poli.|
|[CComSafeArray::GetUpperBound](#getupperbound)|Vrátí horní mez pro libovolnou dimenzi pole.|
|[CComSafeArray::-proměnlivé](#issizable)|Testuje, zda `CComSafeArray` lze změnit velikost objektu.|
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Načte jeden prvek z multidimenzionálního pole.|
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|Nastaví hodnotu prvku v multidimenzionálním poli.|
|[CComSafeArray:: Resize](#resize)|Změní velikost `CComSafeArray` objektu.|
|[CComSafeArray::SetAt](#setat)|Nastaví hodnotu prvku v jednorozměrném poli.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CComSafeArray:: operator LPSAFEARRAY](#operator_lpsafearray)|Přetypování hodnoty na `SAFEARRAY` ukazatel.|
|[CComSafeArray:: operator\[\]](ccomsafearray-class.md#operator_at)|Načte prvek z pole.|
|[CComSafeArray:: operator =](#operator_eq)|Operátor přiřazení|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Tento datový člen uchovává adresu `SAFEARRAY` struktury.|

## <a name="remarks"></a>Poznámky

`CComSafeArray`poskytuje obálku pro třídu [datového typu SafeArray](/windows/win32/api/oaidl/ns-oaidl-tagsafearray) , což usnadňuje vytváření a správu jednoduchých a multidimenzionálních polí téměř kteréhokoli typu PODPOROVANÉho variantou.

`CComSafeArray`zjednodušuje předávání polí mezi procesy a navíc poskytuje dodatečné zabezpečení kontrolou hodnot indexu pole v horních a dolních mezích.

Dolní mez prvku `CComSafeArray` může začínat jakoukoli uživatelsky definovanou hodnotou. pole, ke kterým se dá přistupovat, ale C++ musí používat spodní hranici 0. Jiné jazyky, například Visual Basic, mohou používat jiné meze (například-10 až 10).

Pomocí [CComSafeArray:: Create](#create) vytvořte `CComSafeArray` objekt a [CComSafeArray::D estroy](#destroy) pro jeho odstranění.

`CComSafeArray` Může obsahovat následující podmnožinu datových typů variant:

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
|VT_UI8|ulonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|desetinný ukazatel|
|VT_VARIANT|variantní ukazatel|
|VT_CY|Měna – datový typ|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsafe. h

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

##  <a name="add"></a>CComSafeArray:: Add

Přidá jeden nebo více prvků nebo `SAFEARRAY` struktury `CComSafeArray`do.

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parametry

*psaSrc*<br/>
Ukazatel na `SAFEARRAY` objekt.

*ulCount*<br/>
Počet objektů, které mají být přidány do pole.

*pT*<br/>
Ukazatel na jeden nebo více objektů, které mají být přidány do pole.

*t*<br/>
Odkaz na objekt, který má být přidán do pole.

*bCopy*<br/>
Určuje, zda má být vytvořena kopie dat. Výchozí hodnota je TRUE (pravda).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Nové objekty jsou připojeny na konec existujícího `SAFEARRAY` objektu. Přidání objektu k multidimenzionálnímu `SAFEARRAY` objektu není podporováno. Při přidávání existujícího pole objektů musí obě pole obsahovat elementy stejného typu.

Příznak *bcopy* je při přidání prvků typu BSTR nebo variant do pole přihlédnuto. Výchozí hodnota TRUE zajišťuje, aby se při přidání prvku do pole vytvořila nová kopie dat.

##  <a name="attach"></a>CComSafeArray:: Attach

`SAFEARRAY` Připojí strukturu`CComSafeArray` k objektu.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*psaSrc*<br/>
Ukazatel na `SAFEARRAY` strukturu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Připojí k objektu strukturu a zpřístupní stávající `CComSafeArray` metody. `SAFEARRAY` `CComSafeArray`

##  <a name="ccomsafearray"></a>CComSafeArray::CComSafeArray

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
`SAFEARRAYBOUND` Struktura.

*ulCount*<br/>
Počet prvků v poli.

*lLBound*<br/>
Hodnota dolní meze; To znamená index prvního prvku v poli.

*pBound*<br/>
Ukazatel na `SAFEARRAYBOUND` strukturu.

*uDims*<br/>
Počet rozměrů v poli.

*saSrc*<br/>
Odkaz na `SAFEARRAY` strukturu nebo `CComSafeArray` objekt. V obou případech konstruktor používá tento odkaz k vytvoření kopie pole, takže pole není odkazováno po konstrukci.

*psaSrc*<br/>
Ukazatel na `SAFEARRAY` strukturu. Konstruktor používá tuto adresu k vytvoření kopie pole, takže pole není odkazováno po konstrukci.

### <a name="remarks"></a>Poznámky

`CComSafeArray` Vytvoří objekt.

##  <a name="dtor"></a>CComSafeArray:: ~ CComSafeArray

Destruktor.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="copyfrom"></a>CComSafeArray::CopyFrom

Zkopíruje obsah `SAFEARRAY` struktury `CComSafeArray` do objektu.

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
`SAFEARRAY` Ukazatel na kopírování.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda zkopíruje obsah `SAFEARRAY` do aktuálního `CComSafeArray` objektu. Existující obsah pole je nahrazen.

##  <a name="copyto"></a>CComSafeArray:: CopyTo

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

Tato metoda zkopíruje obsah `CComSafeArray` objektu `SAFEARRAY` do struktury.

##  <a name="create"></a>CComSafeArray:: Create

`CComSafeArray`Vytvoří.

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>Parametry

*pBound*<br/>
Ukazatel na `SAFEARRAYBOUND` objekt.

*uDims*<br/>
Počet rozměrů v poli.

*ulCount*<br/>
Počet prvků v poli.

*lLBound*<br/>
Hodnota dolní meze; To znamená index prvního prvku v poli.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Objekt lze vytvořit z existující `SAFEARRAYBOUND` struktury a počtu rozměrů nebo zadáním počtu prvků v poli a dolní meze. `CComSafeArray` Pokud má být k poli přistup z C++, dolní hranice by měla být 0. Jiné jazyky mohou pro dolní mez použít jiné hodnoty (například Visual Basic podporuje pole s prvky s rozsahem, například-10 až 10).

##  <a name="destroy"></a>CComSafeArray::D estroy

`CComSafeArray` Odstraní objekt.

```
HRESULT Destroy();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Odstraní existující `CComSafeArray` objekt a všechna data, která obsahuje.

##  <a name="detach"></a>CComSafeArray::D etach

Odpojí `CComSafeArray` objekt odobjektu.`SAFEARRAY`

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `SAFEARRAY` objekt.

### <a name="remarks"></a>Poznámky

Tato metoda odpojí `SAFEARRAY` objekt `CComSafeArray` od objektu.

##  <a name="getat"></a>CComSafeArray::GetAt

Načte jeden prvek z jednorozměrného pole.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Parametry

*lIndex*<br/>
Číslo indexu hodnoty v poli, které se má vrátit.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na požadovaný prvek pole.

##  <a name="getcount"></a>CComSafeArray:: GetCount

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

Při použití s multidimenzionálním polem Tato metoda vrátí počet prvků pouze v konkrétní dimenzi.

##  <a name="getdimensions"></a>CComSafeArray:: GetDimensions

Vrátí počet rozměrů v poli.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet rozměrů v poli.

##  <a name="getlowerbound"></a>CComSafeArray::GetLowerBound

Vrátí dolní mez pro danou dimenzi pole.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Dimenze pole, pro kterou chcete získat dolní mez. Je-li tento parametr vynechán, je výchozí hodnota 0.

### <a name="return-value"></a>Návratová hodnota

Vrátí dolní mez.

### <a name="remarks"></a>Poznámky

Pokud je dolní hranice 0, znamená to pole typu C, jehož prvním prvkem je prvek číslo 0. V případě chyby, například neplatný argument dimenze, tato metoda volá `AtlThrow` s hodnotou HRESULT popisující chybu.

##  <a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr

Vrátí adresu `m_psa` datového členu.

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na datový člen [CComSafeArray:: m_psa](#m_psa) .

##  <a name="gettype"></a>CComSafeArray:: GetType

Vrátí typ dat uložených v poli.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí typ dat uložených v poli, což může být kterýkoli z následujících typů:

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
|VT_UI8|ulonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|desetinný ukazatel|
|VT_VARIANT|variantní ukazatel|
|VT_CY|Měna – datový typ|

##  <a name="getupperbound"></a>CComSafeArray::GetUpperBound

Vrátí horní mez pro libovolnou dimenzi pole.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Dimenze pole, pro kterou se má získat horní mez Je-li tento parametr vynechán, je výchozí hodnota 0.

### <a name="return-value"></a>Návratová hodnota

Vrátí horní mez. Tato hodnota je včetně maximálního platného indexu pro tuto dimenzi.

### <a name="remarks"></a>Poznámky

V případě chyby, například neplatný argument dimenze, tato metoda volá `AtlThrow` s hodnotou HRESULT popisující chybu.

##  <a name="issizable"></a>CComSafeArray::-proměnlivé

Testuje, zda `CComSafeArray` lze změnit velikost objektu.

```
bool IsSizable() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, `CComSafeArray` Pokud může být změněna velikost, false, pokud nemůže.

##  <a name="m_psa"></a>CComSafeArray::m_psa

Obsahuje adresu `SAFEARRAY` přistupované struktury.

```
LPSAFEARRAY m_psa;
```

##  <a name="multidimgetat"></a>CComSafeArray::MultiDimGetAt

Načte jeden prvek z multidimenzionálního pole.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>Parametry

*alIndex*<br/>
Ukazatel na vektor indexů pro každou dimenzi v poli. Nejvíce vlevo (nejvýznamnější) dimenze je `alIndex[0]`.

*t*<br/>
Odkaz na vrácená data.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="multidimsetat"></a>CComSafeArray::MultiDimSetAt

Nastaví hodnotu prvku v multidimenzionálním poli.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Parametry

*alIndex*<br/>
Ukazatel na vektor indexů pro každou dimenzi v poli. Rozměr nejvíce vpravo (nejméně významné) je `alIndex`[0].

*T*<br/>
Určuje hodnotu nového prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Toto je multidimenzionální verze [CComSafeArray:: SetAt](#setat).

##  <a name="operator_at"></a>CComSafeArray:: operator\[\]

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

Provede podobnou funkci [CComSafeArray:: GetAt](#getat), ale tento operátor funguje pouze s multidimenzionálními poli.

##  <a name="operator_eq"></a>CComSafeArray:: operator =

Operátor přiřazení

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*saSrc*<br/>
Odkaz na `CComSafeArray` objekt.

*psaSrc*<br/>
Ukazatel na `SAFEARRAY` objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí typ dat uložených v poli.

##  <a name="operator_lpsafearray"></a>CComSafeArray:: operator LPSAFEARRAY

Přetypování hodnoty na `SAFEARRAY` ukazatel.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Návratová hodnota

Přetypování hodnoty na `SAFEARRAY` ukazatel.

##  <a name="resize"></a>CComSafeArray:: Resize

Změní velikost `CComSafeArray` objektu.

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Parametry

*pBound*<br/>
Ukazatel na `SAFEARRAYBOUND` strukturu, která obsahuje informace o počtu elementů a dolní meze pole.

*ulCount*<br/>
Požadovaný počet objektů v poli se změněnou velikostí.

*lLBound*<br/>
Dolní mez.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda mění pouze velikost dimenze nejvíce vpravo. Nemění velikost polí, která vrací `IsResizable` hodnotu false.

##  <a name="setat"></a>CComSafeArray::SetAt

Nastaví hodnotu prvku v jednorozměrném poli.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parametry

*lIndex*<br/>
Indexové číslo prvku pole, které má být nastaveno.

*t*<br/>
Nová hodnota zadaného elementu.

*bCopy*<br/>
Určuje, zda má být vytvořena kopie dat. Výchozí hodnota je TRUE (pravda).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Příznak *bcopy* je při přidání prvků typu BSTR nebo variant do pole přihlédnuto. Výchozí hodnota TRUE zajišťuje, aby se při přidání prvku do pole vytvořila nová kopie dat.

## <a name="see-also"></a>Viz také:

[SAFEARRAY – datový typ](/windows/win32/api/oaidl/ns-oaidl-tagsafearray)<br/>
[CComSafeArray:: Create](#create)<br/>
[CComSafeArray::D estroy](#destroy)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
