---
title: Třída CObArray
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
ms.openlocfilehash: 7b923fd9231d3652d8d2f1750a8024d15287811e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360450"
---
# <a name="cobarray-class"></a>Třída CObArray

Podporuje pole `CObject` ukazatelů.

## <a name="syntax"></a>Syntaxe

```
class CObArray : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CobArray::CObArray](#cobarray)|Vytvoří prázdné pole `CObject` pro ukazatele.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CobArray::Přidat](#add)|Přidá prvek na konec pole; v případě potřeby pole zvětší.|
|[CObArray::Připojit](#append)|Připojí k poli jiné pole; v případě potřeby pole zvětší.|
|[CobArray::Kopírovat](#copy)|Zkopíruje do pole jiné pole. v případě potřeby pole zvětší.|
|[CobArray::Elementat](#elementat)|Vrátí dočasný odkaz na ukazatel prvku v rámci pole.|
|[CobArray::FreeExtra](#freeextra)|Uvolní veškerou nepoužitou paměť nad aktuální horní mez.|
|[CobArray::Získat](#getat)|Vrátí hodnotu v daném indexu.|
|[CobArray::GetCount](#getcount)|Získá počet prvků v tomto poli.|
|[CobArray::GetData](#getdata)|Umožňuje přístup k prvkům v poli. Může být NULL.|
|[CobArray::GetSize](#getsize)|Získá počet prvků v tomto poli.|
|[CobArray::GetupperBound](#getupperbound)|Vrátí největší platný index.|
|[CobArray::InsertAt](#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) v zadaném indexu.|
|[CobArray::Jeprázdný](#isempty)|Určuje, zda je pole prázdné.|
|[CobArray::RemoveAll](#removeall)|Odebere všechny prvky z tohoto pole.|
|[CobArray::Removeat](#removeat)|Odebere prvek v určitém indexu.|
|[CobArray::Setat](#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CobArray::Setatgrow](#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby pole zvětší.|
|[CobArray::SetSize](#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CObArray::operátor \[\]](#operator_at)|Nastaví nebo získá prvek na zadaný index.|

## <a name="remarks"></a>Poznámky

Tato pole objektů jsou podobná polím C, ale mohou se dynamicky zmenšovat a podle potřeby zvětšovat.

Indexy pole vždy začínají na pozici 0. Můžete se rozhodnout, zda chcete opravit horní mez nebo povolit pole rozbalit při přidání prvků za aktuální vazbu. Paměť je přidělena souvisle k horní mez, i v případě, že některé prvky jsou null.

V části Win32 je `CObArray` velikost objektu omezena pouze na dostupnou paměť.

Stejně jako u pole C `CObArray` je přístupová doba pro indexovaný prvek konstantní a je nezávislá na velikosti pole.

`CObArray`obsahuje makro IMPLEMENT_SERIAL pro podporu serializace a dumpingu jeho prvků. Pokud pole `CObject` ukazatelů je uložen do archivu, buď s přetížené vložení `Serialize` operátor nebo `CObject` s členovou funkcí, každý prvek je zase serializován spolu s jeho index pole.

Pokud potřebujete výpis jednotlivých `CObject` prvků v poli, musíte nastavit `CDumpContext` hloubku objektu na 1 nebo vyšší.

Při `CObArray` odstranění objektu nebo při odebrání jeho `CObject` prvků jsou odebrány pouze ukazatele, nikoli objekty, na které odkazují.

> [!NOTE]
> Před použitím pole `SetSize` použijte k vytvoření jeho velikosti a přidělení paměti pro něj. Pokud nepoužijete `SetSize`, přidání prvků do pole způsobí, že často přerozděleny a zkopírovány. Časté přerozdělení a kopírování jsou neefektivní a může fragmentovat paměť.

Odvození třídy pole je podobné odvození seznamu. Podrobnosti o odvození třídy seznamu pro zvláštní účely naleznete v článku [Sbírky](../../mfc/collections.md).

> [!NOTE]
> Pokud chcete pole serializovat, musíte při implementaci odvozené třídy použít makro IMPLEMENT_SERIAL.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="cobarrayadd"></a><a name="add"></a>CobArray::Přidat

Přidá nový prvek na konec pole, rostoucí pole o 1.

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>Parametry

*newElement*<br/>
Ukazatel, `CObject` který má být přidán do tohoto pole.

### <a name="return-value"></a>Návratová hodnota

Index přidaného prvku.

### <a name="remarks"></a>Poznámky

Pokud [SetSize](#setsize) byl použit s *nGrowBy* hodnota větší než 1, pak může být přidělena další paměť. Horní mez se však zvýší pouze o 1.

V následující tabulce jsou uvedeny `CObArray::Add`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Přidat( BYTE** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Přidat( DWORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Přidat( void** <strong>\*</strong> `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR Add( LPCTSTR);** `newElement` **throw(\* CMemoryException );**<br /><br /> **INT_PTR Add (const CString&** `newElement` **);**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Přidat( UINT** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR Přidat( WORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Příklad

  Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

Výsledky tohoto programu jsou následující:

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a>CObArray::Připojit

Volání této členské funkce přidat obsah jiného pole na konec daného pole.

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Zdroj prvků, které mají být připojeny k poli.

### <a name="return-value"></a>Návratová hodnota

Index první ho připojit prvek.

### <a name="remarks"></a>Poznámky

Pole musí být stejného typu.

V případě `Append` potřeby může přidělit další paměť pro prvky připojené k poli.

V následující tabulce jsou uvedeny `CObArray::Append`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Append( const CByteArray&** *src* **);**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Append( const CDWordArray&** *src* **);**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Append( const CPtrArray&** *src* **);**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR Append( const CStringArray&** *src* **);**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Append( const CUIntArray&** *src* **);**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR Append( const CWordArray&** *src* **);**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a>CobArray::Kopírovat

Volání této členské funkce přepsat prvky daného pole s prvky jiného pole stejného typu.

```
void Copy(const CObArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Zdroj prvků, které mají být zkopírovány do pole.

### <a name="remarks"></a>Poznámky

`Copy`neuvolňuje paměť; však v `Copy` případě potřeby může přidělit další paměť pro prvky zkopírované do pole.

V následující tabulce jsou uvedeny `CObArray::Copy`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void Copy( const CByteArray&** *src* **);**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void Copy( const CDWordArray&** *src* **);**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**void Copy( const CPtrArray&** *src* **);**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**void Copy( const CStringArray&** *src* **);**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**void Copy( const CUIntArray&** *src);* **);**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**void Copy( const CWordArray&** *src* **);**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a>CobArray::CObArray

Vytvoří pole `CObject` prázdné horečné.

```
CObArray();
```

### <a name="remarks"></a>Poznámky

Pole zvětšuje jeden prvek najednou.

V následující tabulce jsou uvedeny další `CObArray::CObArray`konstruktory, které jsou podobné .

|Třída|Konstruktor|
|-----------|-----------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**CByteArray( );**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray( );**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray( );**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray( );**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray( );**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray( );**|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a>CobArray::Elementat

Vrátí dočasný odkaz na ukazatel prvku v rámci pole.

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší `GetUpperBound`než nebo rovno hodnotě vrácené .

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CObject` ukazatel.

### <a name="remarks"></a>Poznámky

Používá se k implementaci operátoru přiřazení na levé straně pro pole. Všimněte si, že se jedná o pokročilou funkci, která by měla být použita pouze k implementaci operátorů speciální pole.

V následující tabulce jsou uvedeny `CObArray::ElementAt`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**BYTE& ElementAt( INT_PTR** `nIndex` **);**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& ElementAt( INT_PTR** `nIndex` **);**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**neplatné\*& ElementAt( INT_PTR** `nIndex` **);**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& ElementAt( INT_PTR** `nIndex` **);**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& ElementAt( INT_PTR** `nIndex` **);**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& ElementAt( INT_PTR** `nIndex` **);**|

### <a name="example"></a>Příklad

  Viz příklad [cobarray::GetSize](#getsize).

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a>CobArray::FreeExtra

Uvolní všechny další paměti, která byla přidělena, zatímco pole bylo pěstováno.

```
void FreeExtra();
```

### <a name="remarks"></a>Poznámky

Tato funkce nemá žádný vliv na velikost nebo horní mez pole.

V následující tabulce jsou uvedeny `CObArray::FreeExtra`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra( );**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra( );**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra( );**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra( );**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra( );**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra( );**|

### <a name="example"></a>Příklad

  Viz příklad [cobarray::GetData](#getdata).

## <a name="cobarraygetat"></a><a name="getat"></a>CobArray::Získat

Vrátí prvek pole v zadaném indexu.

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší `GetUpperBound`než nebo rovno hodnotě vrácené .

### <a name="return-value"></a>Návratová hodnota

Prvek `CObject` ukazatele aktuálně v tomto indexu.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Předání záporné hodnoty nebo hodnoty větší `GetUpperBound` než hodnota vrácená hodnotou bude mít za následek neúspěšnou kontrolní výraz.

V následující tabulce jsou uvedeny `CObArray::GetAt`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**BYTE GetAt( INT_PTR** `nIndex` **) const;**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt( INT_PTR** `nIndex` **) const;**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt( INT_PTR** `nIndex` **) const;**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt( INT_PTR** `nIndex` **) const;**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt( INT_PTR** `nIndex` **) const;**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt( INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a>CobArray::GetCount

Vrátí počet prvků pole.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v poli.

### <a name="remarks"></a>Poznámky

Volání této metody načíst počet prvků v poli. Vzhledem k tomu, že indexy jsou založeny na nule, velikost je 1 větší než největší index.

V následující tabulce jsou uvedeny `CObArray::GetCount`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount( ) const;**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount( ) const;**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount( ) const;**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount( ) const;**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount( ) const;**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a>CobArray::GetData

Pomocí této členské funkce získat přímý přístup k prvkům v poli.

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole `CObject` ukazatelů.

### <a name="remarks"></a>Poznámky

Pokud nejsou k `GetData` dispozici žádné prvky, vrátí hodnotu null.

Zatímco přímý přístup k prvkům pole vám může pomoci pracovat `GetData`rychleji, buďte opatrní při volání ; všechny chyby, které provedete, přímo ovlivňují prvky pole.

V následující tabulce jsou uvedeny `CObArray::GetData`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**const BYTE\* GetData( ) const; BYTE\* GetData( );**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**const DWORD\* GetData( ) const;DWORD\* GetData( );**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**const\* \* void GetData( )\* \* const;void GetData( );**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString\* GetData( ) const; CString\* GetData( );**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**const UINT\* GetData( ) const; UINT\* GetData( );**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**const\* WORD GetData( ) const; WORD\* GetData( );**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a>CobArray::GetSize

Vrátí velikost pole.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že indexy jsou založeny na nule, velikost je 1 větší než největší index.

V následující tabulce jsou uvedeny `CObArray::GetSize`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize( ) const;**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize( ) const;**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize( ) const;**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize( ) const;**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize( ) const;**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a>CobArray::GetupperBound

Vrátí aktuální horní mez tohoto pole.

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>Návratová hodnota

Index horní mez (na základě nuly).

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že indexy pole jsou `GetSize`od nuly, vrátí tato funkce hodnotu 1 menší než .

Podmínka `GetUpperBound( )` = -1 označuje, že pole neobsahuje žádné prvky.

V následující tabulce jsou uvedeny `CObArray::GetUpperBound`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound( ) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a>CobArray::InsertAt

Vloží prvek (nebo všechny prvky v jiném poli) v zadaném indexu.

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
Index celého čísla, který může být `GetUpperBound`větší než hodnota vrácená .

*newElement*<br/>
Ukazatel, `CObject` který má být umístěn v tomto poli. *NewElement* hodnoty NULL je povolena.

*nCount*<br/>
Počet, kolikrát by měl být tento prvek vložen (výchozí hodnota je 1).

*nStartIndex*<br/>
Index celého čísla, který může být `GetUpperBound`větší než hodnota vrácená .

*pNewArray*<br/>
Jiné pole, které obsahuje prvky, které mají být přidány do tohoto pole.

### <a name="remarks"></a>Poznámky

První verze `InsertAt` vloží jeden prvek (nebo více kopií prvku) na zadaný index v poli. V procesu posune nahoru (zvýšením indexu) existující prvek v tomto indexu a posune všechny prvky nad ním.

Druhá verze vloží všechny prvky `CObArray` z jiné kolekce, počínaje pozici *nStartIndex.*

Funkce `SetAt` naopak nahradí jeden zadaný prvek pole a neposune žádné prvky.

V následující tabulce jsou uvedeny `CObArray::InsertAt`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, BYTE** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CByteArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CDWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CPtrArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CStringArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, UINT** `newElement` , **int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CUIntArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, WORD** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Příklad

  Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

Výsledky tohoto programu jsou následující:

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a>CobArray::Jeprázdný

Určuje, zda je pole prázdné.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je pole prázdné; jinak 0.

## <a name="cobarrayoperator--"></a><a name="operator_at"></a>CObArray::operátor [ ]

Tyto dolní index operátory jsou `SetAt` `GetAt` vhodnou náhradou za a funkce.

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>Poznámky

První operátor, volaný pro pole, která nejsou **const**, mohou být použity na pravé (r-hodnota) nebo vlevo (l-hodnota) příkazu přiřazení. Druhý, volal pro **const** pole, lze použít pouze na pravé straně.

Ladicí verze knihovny uplatňuje, pokud je dolní index (na levé nebo pravé straně příkazu přiřazení) mimo hranice.

V následující tabulce jsou uvedeny `CObArray::operator []`další operátory, které jsou podobné .

|Třída|Operátor|
|-----------|--------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**provozovatel& BYTE [](int_ptr** `nindex` ** \);**<br /><br /> **OPERÁTOR BYTE [](int_ptr** `nindex` ** \) const;**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Operátor& DWORD [](int_ptr** `nindex` ** \);**<br /><br /> **DWORD operátor [](int_ptr** `nindex` ** \) const;**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**provozovatel\*& nuly [](int_ptr** `nindex` ** \);**<br /><br /> **void\* operátor [](int_ptr** `nindex` ** \) const;**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& operátor [](int_ptr** `nindex` ** \);**<br /><br /> **CString operátor [](int_ptr** `nindex` ** \) const;**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& operátor [](int_ptr** `nindex` ** \);**<br /><br /> **UINT operátor [](int_ptr** `nindex` ** \) const;**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& operátor [](int_ptr** `nindex` ** \);**<br /><br /> **WORD operátor [](int_ptr** `nindex` ** \) const;**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a>CobArray::RemoveAll

Odebere všechny ukazatele z tohoto pole, ale `CObject` ve skutečnosti objekty neodstraní.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Pokud je pole již prázdné, funkce stále funguje.

Funkce `RemoveAll` uvolní všechny paměti používané pro úložiště ukazatele.

V následující tabulce jsou uvedeny `CObArray::RemoveAll`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll( );**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll( );**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll( );**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll( );**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll( );**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Příklad

Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a>CobArray::Removeat

Odebere jeden nebo více prvků začínajících na zadaný index v poli.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší `GetUpperBound`než nebo rovno hodnotě vrácené .

*nCount*<br/>
Počet prvků odebrat.

### <a name="remarks"></a>Poznámky

V procesu posune dolů všechny prvky nad odstraněné prvky. Sníží horní mez pole, ale neuvolní paměť.

Pokud se pokusíte odebrat více prvků, než jsou obsaženy v poli nad bodem odebrání, pak ladicí verze knihovny tvrdí.

Funkce `RemoveAt` odebere `CObject` ukazatel z pole, ale neodstraní samotný objekt.

V následující tabulce jsou uvedeny `CObArray::RemoveAt`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void Removeat( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void Removeat( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**void Removeat( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**void Removeat( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**void Removeat( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** *nCount* **= 1 );**|

### <a name="example"></a>Příklad

  Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

Výsledky tohoto programu jsou následující:

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a>CobArray::Setat

Nastaví prvek pole na zadaný index.

```
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší `GetUpperBound`než nebo rovno hodnotě vrácené .

*newElement*<br/>
Ukazatel objektu, který má být vložen do tohoto pole. Hodnota NULL je povolena.

### <a name="remarks"></a>Poznámky

`SetAt`nezpůsobí, že pole zvětšovat. Použijte, `SetAtGrow` pokud chcete, aby pole automaticky rostlo.

Je nutné zajistit, aby hodnota indexu představuje platnou pozici v poli. Pokud je mimo hranice, pak debug verze knihovny tvrdí.

V následující tabulce jsou uvedeny `CObArray::SetAt`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void SetAt( INT_PTR** `nIndex` **, BYTE** `newElement` **);**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, DWORD** `newElement` **);**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**void Setat( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**void Setat( INT_PTR** `nIndex` **, UINT** `newElement` **);**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, WORD** `newElement` **);**|

### <a name="example"></a>Příklad

  Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

Výsledky tohoto programu jsou následující:

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a>CobArray::Setatgrow

Nastaví prvek pole na zadaný index.

```
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celého čísla, který je větší nebo roven 0.

*newElement*<br/>
Ukazatel objektu, který má být přidán do tohoto pole. Hodnota NULL je povolena.

### <a name="remarks"></a>Poznámky

Pole se v případě potřeby automaticky zvětší (to znamená, že horní mez je upravena tak, aby vyhovovala novému prvku).

V následující tabulce jsou uvedeny `CObArray::SetAtGrow`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, BYTE** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void Setatgrow( INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**void Setatgrow( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**void Setatgrow( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, UINT);** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, WORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Příklad

  Viz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pro výpis `CAge` třídy používané ve všech příkladech kolekce.

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

Výsledky tohoto programu jsou následující:

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a>CobArray::SetSize

Vytvoří velikost prázdného nebo existujícího pole; v případě potřeby přidělí paměť.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parametry

*nNová velikost*<br/>
Nová velikost pole (počet prvků). Musí být větší než nebo rovno 0.

*nGrowBy*<br/>
Minimální počet slotů element udělit, pokud je nutné zvýšení velikosti.

### <a name="remarks"></a>Poznámky

Pokud je nová velikost menší než stará velikost, pole je zkráceno a uvolněna je všechna nevyužitá paměť. Z důvodu `SetSize` efektivity volejte nastavení velikosti pole před jeho použitím. Tím se zabrání nutnosti přerozdělit a zkopírovat pole při každém přidání položky.

Parametr *nGrowBy* ovlivňuje přidělení vnitřní paměti, zatímco pole roste. Jeho použití nikdy neovlivní velikost `GetSize` `GetUpperBound`pole podle a .

Pokud velikost pole vzrostla, všechny nově přidělené ukazatele **CObject** <strong>\*</strong> jsou nastaveny na hodnotu NULL.

V následující tabulce jsou uvedeny `CObArray::SetSize`další členské funkce, které jsou podobné .

|Třída|Členská funkce|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw( CMemoryException\* );**|
|[Pole CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Příklad

  Viz příklad [cobarray::GetData](#getdata).

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CStringArray](../../mfc/reference/cstringarray-class.md)<br/>
[Třída CPtrArray](../../mfc/reference/cptrarray-class.md)<br/>
[Třída CByteArray](../../mfc/reference/cbytearray-class.md)<br/>
[CWordArray – třída](../../mfc/reference/cwordarray-class.md)<br/>
[Třída CDWordArray](../../mfc/reference/cdwordarray-class.md)
