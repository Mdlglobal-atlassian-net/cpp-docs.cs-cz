---
title: Cobarray – třída
ms.date: 11/04/2016
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
ms.openlocfilehash: 78d736b53a2febe4f4a026e3aaf9db14dd7f9c0b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300402"
---
# <a name="cobarray-class"></a>Cobarray – třída

Podporuje pole `CObject` ukazatele.

## <a name="syntax"></a>Syntaxe

```
class CObArray : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CObArray::CObArray](#cobarray)|Vytvoří prázdné pole `CObject` ukazatele.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CObArray::Add](#add)|Přidá prvek na konec pole. v případě potřeby se zvětší pole.|
|[CObArray::Append](#append)|Připojí další pole k poli; v případě potřeby se zvětší pole.|
|[CObArray::Copy](#copy)|Zkopíruje jiného objektu array do pole. v případě potřeby se zvětší pole.|
|[CObArray::ElementAt](#elementat)|Vrátí dočasný odkaz na ukazatel na prvek v poli.|
|[CObArray::FreeExtra](#freeextra)|Uvolní všechny nevyužité paměti nad aktuální horní mez.|
|[CObArray::GetAt](#getat)|Vrátí hodnotu na daném indexu.|
|[CObArray::GetCount](#getcount)|Získá počet elementů v tomto poli.|
|[CObArray::GetData](#getdata)|Umožňuje přístup k prvkům v poli. Může mít hodnotu NULL.|
|[CObArray::GetSize](#getsize)|Získá počet elementů v tomto poli.|
|[CObArray::GetUpperBound](#getupperbound)|Vrátí největší platný index.|
|[CObArray::InsertAt](#insertat)|Vloží zadaný index elementu (nebo všechny prvky v jiného objektu array).|
|[CObArray::IsEmpty](#isempty)|Určuje, zda je pole prázdné.|
|[CObArray::RemoveAll](#removeall)|Odebere všechny prvky z tohoto pole.|
|[CObArray::RemoveAt](#removeat)|Odebere element na konkrétní indexu.|
|[CObArray::SetAt](#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CObArray::SetAtGrow](#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby se zvětší pole.|
|[CObArray::SetSize](#setsize)|Nastaví počet prvků, které mají být obsažena v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CObArray::operator \[ \]](#operator_at)|Nastaví nebo získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

Tato pole objektu se podobají polím jazyka C, ale můžete dynamicky zmenšit nebo zvětšit podle potřeby.

Indexy pole vždy spustit na pozici 0. Můžete rozhodnout, jestli se má opravit horní mez nebo povolit pole, které chcete rozbalit přidat prvky za aktuální mez. Paměť je přidělena souvisle horní mez, i když některé prvky jsou null.

V části Win32, velikost `CObArray` objektu je omezená jenom na dostupné paměti.

Stejně jako u pole jazyka C, čas přístupu `CObArray` indexovaný prvek je konstantní a je nezávislý na velikost pole.

`CObArray` zahrnuje IMPLEMENT_SERIAL – makro na podporu serializace a výpis z jeho prvků. Pokud pole `CObject` ukazatele je uložit do archivu, s operátorem vložení přetížené nebo se `Serialize` členské funkce se každý `CObject` elementu, pak serializován spolu s jeho index pole.

Pokud potřebujete s výpisem paměti jednotlivých `CObject` prvky v poli, je nutné nastavit hloubka `CDumpContext` objektu na hodnotu 1 nebo větší.

Když `CObArray` odstranění objektu nebo při jeho prvky jsou odebrány, pouze `CObject` ukazatele jsou odebrány, nikoliv objekty, které odkazují.

> [!NOTE]
>  Před použitím pole, použijte `SetSize` vytvoření jeho velikost a přidělit paměť pro něj. Pokud nepoužijete `SetSize`, přidání prvků pole způsobí, že ho bude často nevyčerpané a zkopírovat. Časté realokace a kopírování jsou neefektivní a může fragmentovat paměti.

Odvození třídy pole je podobné seznamu odvození. Podrobnosti o odvození třídy seznamu zvláštní účely, najdete v článku [kolekce](../../mfc/collections.md).

> [!NOTE]
>  Pokud chcete serializovat pole, je nutné použít IMPLEMENT_SERIAL – makro v implementaci odvozené třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

##  <a name="add"></a>  CObArray::Add

Přidá nový prvek na konec pole, stále se rozšiřující pole o 1.

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>Parametry

*newElement*<br/>
`CObject` Ukazatel přidávané do tohoto pole.

### <a name="return-value"></a>Návratová hodnota

Index elementu přidal.

### <a name="remarks"></a>Poznámky

Pokud [SetSize](#setsize) se používá se *nGrowBy* hodnotu větší než 1, pak paměť navíc mohou být přiděleny. Horní mez, ale zvýší pouze 1.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::Add`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Add( BYTE** `newElement` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Přidat INT_PTR (DWORD** `newElement` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Přidat INT_PTR (void** <strong>\*</strong> `newElement` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Přidat INT_PTR (LPCTSTR** `newElement` **); throw (cmemoryexception –\* );**<br /><br /> **INT_PTR Add(const CString&** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Add( UINT** `newElement` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Přidat INT_PTR (slovo** `newElement` **);**<br /><br /> **throw (cmemoryexception –\* );**|

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

Výsledky z této aplikace jsou následující:

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

##  <a name="append"></a>  CObArray::Append

Voláním této členské funkce přidat obsah jiného objektu array do konce daného pole.

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Zdrojové elementy, které se mají připojit k poli.

### <a name="return-value"></a>Návratová hodnota

Index první připojený prvek.

### <a name="remarks"></a>Poznámky

Pole musí být stejného typu.

V případě potřeby `Append` může přidělit extra paměť pro plnění prvky k poli.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::Append`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Připojit INT_PTR (const CByteArray &** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Připojit INT_PTR (const cdwordarray – &** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Připojit INT_PTR (const cptrarray – &** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Připojit INT_PTR (const cstringarray – &** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Připojit INT_PTR (const cuintarray – &** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Připojit INT_PTR (const cwordarray – &** *src* **);**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

##  <a name="copy"></a>  CObArray::Copy

Voláním této členské funkce přepsat prvky daného pole prvků jiného pole stejného typu.

```
void Copy(const CObArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Zdrojové elementy, které se mají zkopírovat do pole.

### <a name="remarks"></a>Poznámky

`Copy` Nelze uvolnit paměť; Nicméně, v případě potřeby `Copy` může přidělit extra paměť pro plnění elementů zkopírovaných k poli.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::Copy`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void kopírování (const CByteArray &** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void kopírování (const cdwordarray – &** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void kopírování (const cptrarray – &** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void kopírování (const cstringarray – &** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void kopírování (const cuintarray – &** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void kopírování (const cwordarray – &** *src* **);**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

##  <a name="cobarray"></a>  CObArray::CObArray

Vytvoří prázdnou `CObject` ukazatel pole.

```
CObArray();
```

### <a name="remarks"></a>Poznámky

Pole roste současně jeden element.

V následující tabulce jsou uvedeny další konstruktory, které jsou podobné `CObArray::CObArray`.

|Třída|Konstruktor|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray( );**|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

##  <a name="elementat"></a>  CObArray::ElementAt

Vrátí dočasný odkaz na ukazatel na prvek v poli.

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené `GetUpperBound`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CObject` ukazatele.

### <a name="remarks"></a>Poznámky

Používá se k implementaci levé straně operátoru pro pole. Všimněte si, že se jedná o pokročilé funkce, která by měla sloužit pouze k implementaci operátory zvláštní pole.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::ElementAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& ElementAt( INT_PTR** `nIndex` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & ElementAt (INT_PTR** `nIndex` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& ElementAt( INT_PTR** `nIndex` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString – & ElementAt (INT_PTR** `nIndex` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& ElementAt( INT_PTR** `nIndex` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD & ElementAt (INT_PTR** `nIndex` **);**|

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CObArray::GetSize](#getsize).

##  <a name="freeextra"></a>  CObArray::FreeExtra

Uvolní všechny další paměť, která byla přidělena, zatímco se zvětšil na velikost pole.

```
void FreeExtra();
```

### <a name="remarks"></a>Poznámky

Tato funkce nemá žádný vliv na velikost nebo horní hranice pole.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::FreeExtra`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra( );**|

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CObArray::GetData](#getdata).

##  <a name="getat"></a>  CObArray::GetAt

Vrátí prvek pole v zadaném indexu.

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené `GetUpperBound`.

### <a name="return-value"></a>Návratová hodnota

`CObject` Ukazatel element, momentálně na tomto indexu.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Předání zápornou hodnotu nebo hodnotu větší než hodnota vrácená `GetUpperBound` způsobí neplatnost kontrolního výrazu.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::GetAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**GetAt BAJTŮ (INT_PTR** `nIndex` **) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt (INT_PTR** `nIndex` **) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt (INT_PTR** `nIndex` **) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString – GetAt (INT_PTR** `nIndex` **) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt (INT_PTR** `nIndex` **) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt (INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

##  <a name="getcount"></a>  CObArray::GetCount

Vrátí počet prvků pole.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v tomto poli.

### <a name="remarks"></a>Poznámky

Voláním této metody lze načíst počet prvků v poli. Vzhledem k tomu, že indexy jsou počítány od nuly, velikost je větší než nejvyšší index 1.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::GetCount`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount (const;)**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount (const;)**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount (const;)**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount (const;)**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount (const;)**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount (const;)**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

##  <a name="getdata"></a>  CObArray::GetData

Tuto funkci člena můžete použijte k získání přímý přístup k prvkům v poli.

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole `CObject` ukazatele.

### <a name="remarks"></a>Poznámky

Pokud nejsou k dispozici, žádné elementy `GetData` vrátí hodnotu null.

Zatímco přímý přístup k prvkům pole můžete pracovat rychleji, buďte opatrní při volání metody `GetData`; všechny chyby, můžete provést přímo vliv na elementy vaše pole.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::GetData`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const BAJTŮ\* const; () GetData BAJTŮ\* GetData ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const DWORD\* GetData const (); DWORD\* GetData ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const void\* \* (GetData) const; void\* \* GetData ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Const CString\* const; () GetData CString –\* GetData ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const UINT\* const; () GetData UINT\* GetData ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**argument WORD\* const; () GetData WORD\* GetData ();**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

##  <a name="getsize"></a>  CObArray::GetSize

Vrátí velikost pole.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že indexy jsou počítány od nuly, velikost je větší než nejvyšší index 1.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::GetSize`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR getsize – (const;)**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR getsize – (const;)**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR getsize – (const;)**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR getsize – (const;)**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR getsize – (const;)**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR getsize – (const;)**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

##  <a name="getupperbound"></a>  CObArray::GetUpperBound

Vrátí aktuální horní mez tohoto pole.

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>Návratová hodnota

Index (založený na nule) horní mez.

### <a name="remarks"></a>Poznámky

Protože pole indexy jsou počítány od nuly, tato funkce vrátí hodnotu 1 menší než `GetSize`.

Podmínka `GetUpperBound( )` = -1 znamená, že pole neobsahuje žádné elementy.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::GetUpperBound`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound (const;)**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound (const;)**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound (const;)**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound (const;)**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound (const;)**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound (const;)**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

##  <a name="insertat"></a>  CObArray::InsertAt

Vloží zadaný index elementu (nebo všechny prvky v jiného objektu array).

```
void InsertAt(
    INT_PTR nIndex,
    CObject* newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CObArray* pNewArray);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který může být větší než hodnota vrácená `GetUpperBound`.

*newElement*<br/>
`CObject` Ukazatel na umístit do tohoto pole. A *newElement* hodnoty NULL povolené.

*nCount*<br/>
Počet pokusů, které tento prvek by měl být vložen (výchozí nastavení: 1).

*nStartIndex*<br/>
Celočíselný index, který může být větší než hodnota vrácená `GetUpperBound`.

*pNewArray*<br/>
Další pole obsahující prvky, které mají být přidány do tohoto pole.

### <a name="remarks"></a>Poznámky

První verze `InsertAt` vloží jeden prvek (nebo více kopií prvku) na zadaný index v poli. Probíhající, posune (zvýšením index) existující element v indexu a posune všech prvků nad ním.

Druhá verze vloží všechny prvky z jiného `CObArray` kolekce počínaje *nStartIndex* pozici.

`SetAt` Funkce naproti tomu nahradí jeden prvek určeného pole a nepřesune žádné prvky.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::InsertAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, BYTE** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (cmemoryexception –\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CByteArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (cmemoryexception –\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CDWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (cmemoryexception –\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CPtrArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (cmemoryexception –\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, cstringarray –** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, UINT** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (cmemoryexception –\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, cuintarray –** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, WORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (cmemoryexception –\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (cmemoryexception –\* );**|

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

Výsledky z této aplikace jsou následující:

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

##  <a name="isempty"></a>  CObArray::IsEmpty

Určuje, zda je pole prázdné.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je pole prázdné; jinak 0.

##  <a name="operator_at"></a>  [] Č. CObArray::operator

Tyto operátoru dolního indexu jsou vhodné náhradou za `SetAt` a `GetAt` funkce.

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>Poznámky

Volá se, první operátor pro pole, která nejsou **const**, může být použita na pravé straně (r) nebo (l hodnota) levé straně příkazu přiřazení. Druhý, volá se pro **const** pole, může být použita pouze na pravé straně.

Ladicí verze knihovny vyhodnotí, pokud hodnota argumentu subscript (buď v levé nebo pravé straně příkazu přiřazení) je mimo rozsah.

V následující tabulce jsou uvedeny ostatní operátory, které jsou podobné `CObArray::operator []`.

|Třída|Operátor|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Operátor & BYTE [] (int_ptr** `nindex`  **\);**<br /><br /> **BYTE [] – operátor (int_ptr** `nindex`  **\) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & – operátor [] (int_ptr** `nindex`  **\);**<br /><br /> **DWORD – operátor [] (int_ptr** `nindex`  **\) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& operator [](int_ptr** `nindex` **\);**<br /><br /> **void\* operator [] (int_ptr** `nindex`  **\) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& operator [](int_ptr** `nindex` **\);**<br /><br /> **CString – operator [] (int_ptr** `nindex`  **\) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& operator [](int_ptr** `nindex` **\);**<br /><br /> **UINT operator [] (int_ptr** `nindex`  **\) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD & – operátor [] (int_ptr** `nindex`  **\);**<br /><br /> **SLOVO operator [] (int_ptr** `nindex`  **\) const;**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

##  <a name="removeall"></a>  CObArray::RemoveAll

Odebere všechny ukazatele z tohoto pole, ale nedojde k odstranění ve skutečnosti `CObject` objekty.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Pokud už je pole prázdné, tato funkce stále pracuje.

`RemoveAll` Funkce uvolní všechny paměti používané pro úložiště ukazatele.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::RemoveAll`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void (RemoveAll);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void (RemoveAll);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void (RemoveAll);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void (RemoveAll);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void (RemoveAll);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void (RemoveAll);**|

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

##  <a name="removeat"></a>  CObArray::RemoveAt

Odebere jeden nebo více prvků počínaje zadaným indexem v poli.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené `GetUpperBound`.

*nCount*<br/>
Počet prvků, které mají odebrat.

### <a name="remarks"></a>Poznámky

Probíhající Posune dolů všechny prvky nad odebrání těchto elementů. To sníží horní mez pole, ale ne uvolnění paměti.

Pokud se pokusíte odebrat více elementů než jsou obsaženy v poli výše odebrání bodu, pak vyhodnotí ladicí verze knihovny.

`RemoveAt` Funkce odebere `CObject` ukazatel z pole, ale nedojde k odstranění samotného objektu.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::RemoveAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** *nCount* **= 1 );**|

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

Výsledky z této aplikace jsou následující:

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

##  <a name="setat"></a>  CObArray::SetAt

Nastaví prvek pole v zadaném indexu.

```
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené `GetUpperBound`.

*newElement*<br/>
Ukazatel objektu, který má být vložen do tohoto pole. Je povolena hodnota NULL.

### <a name="remarks"></a>Poznámky

`SetAt` nezpůsobí pole, které chcete zvětšit. Použití `SetAtGrow` Pokud chcete, aby pole, které chcete automaticky zvětšovat.

Ujistěte se, že představuje hodnotu indexu platná pozice v poli. Pokud je mimo rozsah, pak vyhodnotí ladicí verze knihovny.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::SetAt`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt (INT_PTR** `nIndex` **, BYTE** `newElement` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, DWORD** `newElement` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, UINT** `newElement` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, WORD** `newElement` **);**|

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

Výsledky z této aplikace jsou následující:

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

##  <a name="setatgrow"></a>  CObArray::SetAtGrow

Nastaví prvek pole v zadaném indexu.

```
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0.

*newElement*<br/>
Ukazatel objektu, který chcete přidat do tohoto pole. Je povolena hodnota NULL.

### <a name="remarks"></a>Poznámky

Pole se automaticky zvětší v případě potřeby (to znamená, horní mez objektů je upravena podle nového prvku posouvají).

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::SetAtGrow`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, BYTE** `newElement` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, UINT** `newElement` **);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, WORD** `newElement` **);**<br /><br /> **throw (cmemoryexception –\* );**|

### <a name="example"></a>Příklad

  Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

Výsledky z této aplikace jsou následující:

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

##  <a name="setsize"></a>  CObArray::SetSize

Vytvoří velikost existující nebo prázdné pole. přidělí paměť v případě potřeby.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parametry

*nNewSize*<br/>
Nová velikost pole (počet prvků). Musí být větší než nebo rovna 0.

*nGrowBy*<br/>
Minimální počet slotů element přidělit, pokud je nutné zvýšit velikost.

### <a name="remarks"></a>Poznámky

Pokud nová velikost je menší než původní velikost, pole jsou oříznuté a všechny nevyužité paměti se uvolní. Z důvodu efektivity volání `SetSize` k nastavení velikosti pole před jeho použitím. Díky tomu potřeba přidělit jinému uživateli a zkopírujte pole pokaždé, když se přidá položka.

*NGrowBy* parametr ovlivňuje přidělení vnitřní paměti, zatímco roste pole. Jeho použití nikdy ovlivňuje velikost pole, jak je hlásí `GetSize` a `GetUpperBound`.

Pokud se zvětšil velikost pole, přiděleny všechny nově **CObject** <strong>\*</strong> ukazatele jsou nastaveny na hodnotu NULL.

Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::SetSize`.

|Třída|Členská funkce|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (cmemoryexception –\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (cmemoryexception –\* );**|

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CObArray::GetData](#getdata).

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CStringArray – třída](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray – třída](../../mfc/reference/cptrarray-class.md)<br/>
[CByteArray – třída](../../mfc/reference/cbytearray-class.md)<br/>
[CWordArray – třída](../../mfc/reference/cwordarray-class.md)<br/>
[CDWordArray – třída](../../mfc/reference/cdwordarray-class.md)
