---
title: Třída COleSafeArray
ms.date: 08/29/2019
f1_keywords:
- COleSafeArray
- AFXDISP/COleSafeArray
- AFXDISP/COleSafeArray::COleSafeArray
- AFXDISP/COleSafeArray::AccessData
- AFXDISP/COleSafeArray::AllocData
- AFXDISP/COleSafeArray::AllocDescriptor
- AFXDISP/COleSafeArray::Attach
- AFXDISP/COleSafeArray::Clear
- AFXDISP/COleSafeArray::Copy
- AFXDISP/COleSafeArray::Create
- AFXDISP/COleSafeArray::CreateOneDim
- AFXDISP/COleSafeArray::Destroy
- AFXDISP/COleSafeArray::DestroyData
- AFXDISP/COleSafeArray::DestroyDescriptor
- AFXDISP/COleSafeArray::Detach
- AFXDISP/COleSafeArray::GetByteArray
- AFXDISP/COleSafeArray::GetDim
- AFXDISP/COleSafeArray::GetElement
- AFXDISP/COleSafeArray::GetElemSize
- AFXDISP/COleSafeArray::GetLBound
- AFXDISP/COleSafeArray::GetOneDimSize
- AFXDISP/COleSafeArray::GetUBound
- AFXDISP/COleSafeArray::Lock
- AFXDISP/COleSafeArray::PtrOfIndex
- AFXDISP/COleSafeArray::PutElement
- AFXDISP/COleSafeArray::Redim
- AFXDISP/COleSafeArray::ResizeOneDim
- AFXDISP/COleSafeArray::UnaccessData
- AFXDISP/COleSafeArray::Unlock
helpviewer_keywords:
- COleSafeArray [MFC], COleSafeArray
- COleSafeArray [MFC], AccessData
- COleSafeArray [MFC], AllocData
- COleSafeArray [MFC], AllocDescriptor
- COleSafeArray [MFC], Attach
- COleSafeArray [MFC], Clear
- COleSafeArray [MFC], Copy
- COleSafeArray [MFC], Create
- COleSafeArray [MFC], CreateOneDim
- COleSafeArray [MFC], Destroy
- COleSafeArray [MFC], DestroyData
- COleSafeArray [MFC], DestroyDescriptor
- COleSafeArray [MFC], Detach
- COleSafeArray [MFC], GetByteArray
- COleSafeArray [MFC], GetDim
- COleSafeArray [MFC], GetElement
- COleSafeArray [MFC], GetElemSize
- COleSafeArray [MFC], GetLBound
- COleSafeArray [MFC], GetOneDimSize
- COleSafeArray [MFC], GetUBound
- COleSafeArray [MFC], Lock
- COleSafeArray [MFC], PtrOfIndex
- COleSafeArray [MFC], PutElement
- COleSafeArray [MFC], Redim
- COleSafeArray [MFC], ResizeOneDim
- COleSafeArray [MFC], UnaccessData
- COleSafeArray [MFC], Unlock
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
ms.openlocfilehash: a7be9910b573cb5bc430d6608e75ce6661b71bc2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374866"
---
# <a name="colesafearray-class"></a>Třída COleSafeArray

Třída pro práci s poli libovolného typu a dimenze.

## <a name="syntax"></a>Syntaxe

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|Vytvoří `COleSafeArray` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleSafeArray::Přístupová data](#accessdata)|Načte ukazatel na data pole.|
|[COleSafeArray::AllocData](#allocdata)|Přiděluje paměť pro pole.|
|[COleSafeArray::AllocDeskriptor](#allocdescriptor)|Přidělí paměť pro popisovač bezpečného pole.|
|[COleSafeArray::Připojit](#attach)|Poskytuje objektu `VARIANT` kontrolu nad `COleSafeArray` existujícím polem.|
|[COleSafeArray::Vymazat](#clear)|Uvolní všechna data v `VARIANT`podkladovém objektu .|
|[COleSafeArray::Kopírovat](#copy)|Vytvoří kopii existujícího pole.|
|[COleSafeArray::Vytvořit](#create)|Vytvoří bezpečné pole.|
|[COleSafeArray::CreateOneDim](#createonedim)|Vytvoří jednorozměrný `COleSafeArray` objekt.|
|[COleSafeArray::Destroy](#destroy)|Zničí existující pole.|
|[COleSafeArray::DestroyData](#destroydata)|Zničí data v bezpečném poli.|
|[COleSafeArray::DestroyDeskriptor](#destroydescriptor)|Zničí popisovač bezpečného pole.|
|[COleSafeArray::Detach](#detach)|Odpojí pole VARIANT od `COleSafeArray` objektu (tak, aby data nebyla uvolněna).|
|[COleSafeArray::GetByteArray](#getbytearray)|Zkopíruje obsah bezpečného pole do [cbytearray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray::GetDim](#getdim)|Vrátí počet dimenzí v poli.|
|[COleSafeArray::GetElement](#getelement)|Načte jeden prvek bezpečnépole.|
|[COleSafeArray::GetElemSize](#getelemsize)|Vrátí velikost jednoho prvku v bezpečném poli v bajtech.|
|[COleSafeArray::GetLBound](#getlbound)|Vrátí dolní mez pro libovolnou dimenzi bezpečného pole.|
|[COleSafeArray::GetonedimSize](#getonedimsize)|Vrátí počet prvků v jednorozměrném `COleSafeArray` objektu.|
|[COleSafeArray::GetuBound](#getubound)|Vrátí horní mez pro libovolnou dimenzi bezpečného pole.|
|[COleSafeArray::Zamknout](#lock)|Zvětšuje počet zámků pole a umístí ukazatel na data pole v popisovači pole.|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Vrátí ukazatel na indexovaný prvek.|
|[COleSafeArray::PutElement](#putelement)|Přiřadí jeden prvek do pole.|
|[COleSafeArray::Redim](#redim)|Změní nejméně významné (rightmost) vázána bezpečné pole.|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Změní počet prvků v jednorozměrném `COleSafeArray` objektu.|
|[COleSafeArray::UnaccessData](#unaccessdata)|Sníží počet zámků pole a zruší platnost ukazatele načteného `AccessData`.|
|[COleSafeArray::Odemknout](#unlock)|Sníží počet zámků pole, takže může být uvolněna nebo velikost.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[COleSafeArray::operátor LPCVARIANT](#operator_lpcvariant)|Přistupuje k základní `VARIANT` struktuře objektu. `COleSafeArray`|
|[COleSafeArray::operátor LPVARIANT](#operator_lpvariant)|Přistupuje k základní `VARIANT` struktuře objektu. `COleSafeArray`|
|[COleSafeArray::operátor =](#operator_eq)|Zkopíruje hodnoty `COleSafeArray` do`SAFEARRAY` `VARIANT`objektu ( , , `COleVariant`nebo `COleSafeArray` matice).|
|[COleSafeArray::operátor ==](#operator_eq_eq)|Porovná dvě pole varianty `VARIANT` `COleVariant`(`SAFEARRAY` `COleSafeArray` , , , nebo pole).|
|[COleSafeArray::operátor&lt;&lt;](#operator_lt_lt)|Výstupy obsah objektu `COleSafeArray` do kontextu výpisu.|

## <a name="remarks"></a>Poznámky

`COleSafeArray`pochází ze struktury `VARIANT` OLE. Členské `SAFEARRAY` funkce OLE jsou `COleSafeArray`k dispozici prostřednictvím , stejně jako sada členských funkcí speciálně navržených pro jednorozměrná pole bajtů.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="colesafearrayaccessdata"></a><a name="accessdata"></a>COleSafeArray::Přístupová data

Načte ukazatel na data pole.

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>Parametry

*ppvData*<br/>
Ukazatel na ukazatel na data pole.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

## <a name="colesafearrayallocdata"></a><a name="allocdata"></a>COleSafeArray::AllocData

Přiděluje paměť pro bezpečné pole.

```
void AllocData();
```

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayallocdescriptor"></a><a name="allocdescriptor"></a>COleSafeArray::AllocDeskriptor

Přidělí paměť pro popisovač bezpečného pole.

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Parametry

*dwDims*<br/>
Počet dimenzí v bezpečném poli.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayattach"></a><a name="attach"></a>COleSafeArray::Připojit

Poskytuje objektu kontrolu nad `VARIANT` daty `COleSafeArray` v existujícím poli.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
Objekt. `VARIANT` Parametr *varSrc* musí mít [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum)VARTYPE .

### <a name="remarks"></a>Poznámky

Typ `VARIANT`zdroje je nastaven na VT_EMPTY. Tato funkce vymaže aktuální pole data, pokud existuje.

### <a name="example"></a>Příklad

  Viz příklad [cOleSafeArray::AccessData](#accessdata).

## <a name="colesafearrayclear"></a><a name="clear"></a>COleSafeArray::Vymazat

Vymaže bezpečné pole.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

Funkce vymaže bezpečné `VARTYPE` pole nastavením objektu na VT_EMPTY. Aktuální obsah jsou uvolněny a pole je uvolněno.

## <a name="colesafearraycolesafearray"></a><a name="colesafearray"></a>COleSafeArray::COleSafeArray

Vytvoří `COleSafeArray` objekt.

```
COleSafeArray();

COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);

COleSafeArray(const COleSafeArray& saSrc);
COleSafeArray(const VARIANT& varSrc);
COleSafeArray(LPCVARIANT pSrc);
COleSafeArray(const COleVariant& varSrc);
```

### <a name="parameters"></a>Parametry

*saSrc řekl:*<br/>
Existující `COleSafeArray` objekt `SAFEARRAY` nebo chcete-li zkopírovat do nového `COleSafeArray` objektu.

*vtSrc řekl:*<br/>
VARTYPE nového `COleSafeArray` objektu.

*psaSrc*<br/>
Ukazatel na `SAFEARRAY` a, které mají `COleSafeArray` být zkopírovány do nového objektu.

*varSrc*<br/>
Existující `VARIANT` nebo `COleVariant` objekt, který má `COleSafeArray` být zkopírován do nového objektu.

*pSrc*<br/>
Ukazatel na `VARIANT` objekt, který má být `COleSafeArray` zkopírován do nového objektu.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory `COleSafeArray` vytvořit nové objekty. Pokud není žádný parametr, `COleSafeArray` je vytvořen prázdný objekt (VT_EMPTY). Pokud `COleSafeArray` je zkopírován z jiného pole, `COleSafeArray`jehož VARTYPE je znám implicitně (, , `COleVariant`nebo `VARIANT`), VARTYPE zdrojového pole je zachována a nemusí být zadán. Pokud `COleSafeArray` je zkopírován z jiného pole, jehož VARTYPE není znám (`SAFEARRAY`), vartype musí být zadán v *parametru vtSrc.*

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraycopy"></a><a name="copy"></a>COleSafeArray::Kopírovat

Vytvoří kopii existujícího bezpečného pole.

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Parametry

*ppsa*<br/>
Ukazatel na umístění, ve kterém chcete vrátit nový popisovač pole.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraycreate"></a><a name="create"></a>COleSafeArray::Vytvořit

Přiděluje a inicializuje data pro pole.

```
void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    DWORD* rgElements);

void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    SAFEARRAYBOUND* rgsabounds);
```

### <a name="parameters"></a>Parametry

*vtSrc řekl:*<br/>
Základní typ pole (to znamená VARTYPE každého prvku pole). VARTYPE je omezen na podmnožinu typů variant. Nelze nastavit příznak VT_ARRAY ani VT_BYREF. VT_EMPTY a VT_NULL nejsou platné základní typy pro pole. Všechny ostatní typy jsou legální.

*dwDims*<br/>
Počet dimenzí v poli. To lze změnit po vytvoření pole pomocí [Redim](#redim).

*rgElements*<br/>
Ukazatel na pole počet prvků pro každou dimenzi v poli.

*rgsabounds*<br/>
Ukazatel na vektor hranice (jeden pro každou dimenzi) pro pole.

### <a name="remarks"></a>Poznámky

Tato funkce vymaže aktuální data pole v případě potřeby. Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraycreateonedim"></a><a name="createonedim"></a>COleSafeArray::CreateOneDim

Vytvoří nový jednorozměrný `COleSafeArray` objekt.

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>Parametry

*vtSrc řekl:*<br/>
Základní typ pole (to znamená VARTYPE každého prvku pole).

*dwElements*<br/>
Počet prvků v poli. To lze změnit po vytvoření pole s [ResizeOneDim](#resizeonedim).

*pvSrcData*<br/>
Ukazatel na data, která chcete zkopírovat do pole.

*nLBound*<br/>
Dolní mez pole.

### <a name="remarks"></a>Poznámky

Funkce přiděluje a inicializuje data pro pole, kopírování zadaných dat, pokud ukazatel *pvSrcData* není NULL.

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

## <a name="colesafearraydestroy"></a><a name="destroy"></a>COleSafeArray::Destroy

Zničí existující popisovač pole a všechna data v poli.

```
void Destroy();
```

### <a name="remarks"></a>Poznámky

Pokud jsou objekty uloženy v poli, každý objekt je uvolněn. Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydestroydata"></a><a name="destroydata"></a>COleSafeArray::DestroyData

Zničí všechna data v bezpečném poli.

```
void DestroyData();
```

### <a name="remarks"></a>Poznámky

Pokud jsou objekty uloženy v poli, každý objekt je uvolněn. Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydestroydescriptor"></a><a name="destroydescriptor"></a>COleSafeArray::DestroyDeskriptor

Zničí popisovač bezpečného pole.

```
void DestroyDescriptor();
```

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydetach"></a><a name="detach"></a>COleSafeArray::Detach

Odpojí `VARIANT` data od `COleSafeArray` objektu.

```
VARIANT Detach();
```

### <a name="return-value"></a>Návratová hodnota

Základní `VARIANT` hodnota v `COleSafeArray` objektu.

### <a name="remarks"></a>Poznámky

Funkce odpojí data v bezpečném poli nastavením typu VARTYPE objektu na VT_EMPTY. Je odpovědností volajícího uvolnit pole voláním funkce Windows [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear).

Při chybě funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

  Viz příklad [cOleSafeArray::PutElement](#putelement).

## <a name="colesafearraygetbytearray"></a><a name="getbytearray"></a>COleSafeArray::GetByteArray

Zkopíruje obsah bezpečného pole `CByteArray`do .

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parametry

*Bajtů*<br/>
Odkaz na objekt [CByteArray.](../../mfc/reference/cbytearray-class.md)

## <a name="colesafearraygetdim"></a><a name="getdim"></a>COleSafeArray::GetDim

Vrátí počet dimenzí v objektu. `COleSafeArray`

```
DWORD GetDim();
```

### <a name="return-value"></a>Návratová hodnota

Počet dimenzí v bezpečném poli.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraygetelement"></a><a name="getelement"></a>COleSafeArray::GetElement

Načte jeden prvek bezpečnépole.

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parametry

*rgIndexy*<br/>
Ukazatel na pole indexů pro každou dimenzi pole.

*pvData*<br/>
Ukazatel na umístění umístit prvek pole.

### <a name="remarks"></a>Poznámky

Tato funkce automaticky volá `SafeArrayLock` `SafeArrayUnlock` funkce systému Windows a před a po načtení prvku. Pokud datový prvek je řetězec, objekt nebo varianta, funkce zkopíruje prvek správným způsobem. Parametr *pvData* by měl překážet na dostatečně velkou vyrovnávací paměť, která by prvek obsahovala.

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

## <a name="colesafearraygetelemsize"></a><a name="getelemsize"></a>COleSafeArray::GetElemSize

Načte velikost prvku v `COleSafeArray` objektu.

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Návratová hodnota

Velikost prvků bezpečného pole v bajtech.

## <a name="colesafearraygetlbound"></a><a name="getlbound"></a>COleSafeArray::GetLBound

Vrátí dolní mez pro `COleSafeArray` libovolnou dimenzi objektu.

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Parametry

*dwDim*<br/>
Dimenze pole, pro které chcete získat dolní mez.

*pLBound*<br/>
Ukazatel na umístění vrátit dolní mez.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

## <a name="colesafearraygetonedimsize"></a><a name="getonedimsize"></a>COleSafeArray::GetonedimSize

Vrátí počet prvků v jednorozměrném `COleSafeArray` objektu.

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v jednorozměrném bezpečném poli.

### <a name="example"></a>Příklad

  Viz příklad [cOleSafeArray::CreateOneDim](#createonedim).

## <a name="colesafearraygetubound"></a><a name="getubound"></a>COleSafeArray::GetuBound

Vrátí horní mez pro libovolnou dimenzi bezpečného pole.

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Parametry

*dwDim*<br/>
Dimenze pole, pro které chcete získat horní mez.

*pUBound*<br/>
Ukazatel na umístění vrátit horní mez.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

## <a name="colesafearraylock"></a><a name="lock"></a>COleSafeArray::Zamknout

Zvětšuje počet zámků pole a umístí ukazatel na data pole v popisovači pole.

```
void Lock();
```

### <a name="remarks"></a>Poznámky

Při chybě vyvolá [COleException](../../mfc/reference/coleexception-class.md).

Ukazatel v popisovači pole je `Unlock` platný, dokud není volána. Volání `Lock` lze vnořit; stejný počet volání `Unlock` jsou požadovány.

Pole nelze odstranit, pokud je uzamčeno.

## <a name="colesafearrayoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleSafeArray::operátor LPCVARIANT

Volání tohoto operátoru přetypování pro přístup k základní `VARIANT` struktuře pro tento `COleSafeArray` objekt.

```
operator LPCVARIANT() const;
```

## <a name="colesafearrayoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleSafeArray::operátor LPVARIANT

Volání tohoto operátoru přetypování pro přístup k základní `VARIANT` struktuře pro tento `COleSafeArray` objekt.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Poznámky

Všimněte si, že `VARIANT` změna hodnoty ve struktuře, ke které má `COleSafeArray` přístup ukazatel vrácený touto funkcí, změní hodnotu tohoto objektu.

## <a name="colesafearrayoperator-"></a><a name="operator_eq"></a>COleSafeArray::operátor =

Tyto přetížené operátory přiřazení zkopírují zdrojovou hodnotu do tohoto `COleSafeArray` objektu.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Poznámky

Stručný popis každého operátora je následující:

- **operátor =(** *saSrc* **)** Zkopíruje `COleSafeArray` existující objekt do tohoto objektu.

- **operátor =(** *varSrc* **)** Zkopíruje `VARIANT` existující `COleVariant` nebo matice do tohoto objektu.

- **operátor =(** *pSrc* **)** Zkopíruje `VARIANT` objekt pole, ke kterým *pSrc přistupuje,* do tohoto objektu.

## <a name="colesafearrayoperator-"></a><a name="operator_eq_eq"></a>COleSafeArray::operátor ==

Tento operátor porovná dvě`SAFEARRAY`pole `VARIANT` `COleVariant`( `COleSafeArray` , , , nebo pole) a vrátí nenulovou hodnotu, pokud jsou rovna; jinak 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Poznámky

Dvě pole jsou stejné, pokud mají stejný počet dimenzí, stejnou velikost v každé dimenzi a stejné hodnoty prvků.

## <a name="colesafearrayoperator-ltlt"></a><a name="operator_lt_lt"></a>COleSafeArray::operátor&lt;&lt;

Operátor `COleSafeArray` vložení (<<) podporuje diagnostický dumping a ukládání `COleSafeArray` objektu do archivu.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

## <a name="colesafearrayptrofindex"></a><a name="ptrofindex"></a>COleSafeArray::PtrOfIndex

Vrátí ukazatel na prvek určený hodnotami indexu.

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Parametry

*rgIndexy*<br/>
Pole hodnot indexu, které identifikují prvek pole. Musí být zadány všechny indexy pro prvek.

*ppvData*<br/>
Po návratu ukazatel na prvek identifikovaný hodnotami v *rgIndices*.

## <a name="colesafearrayputelement"></a><a name="putelement"></a>COleSafeArray::PutElement

Přiřadí jeden prvek do pole.

```
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parametry

*rgIndexy*<br/>
Ukazatel na pole indexů pro každou dimenzi pole.

*pvData*<br/>
Ukazatel na data, která chcete přiřadit k poli. VT_DISPATCH, VT_UNKNOWN a VT_BSTR typy variant jsou ukazatele a nevyžadují jinou úroveň dereference.

### <a name="remarks"></a>Poznámky

Tato funkce automaticky volá funkce systému Windows [SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock) a [SafeArrayUnlock](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) před a po přiřazení prvku. Pokud je datový prvek řetězec, objekt nebo varianta, funkce jej správně zkopíruje a pokud je existující prvek řetězec, objekt nebo varianta, je správně vymazán.

Všimněte si, že můžete mít více zámků v poli, takže můžete umístit prvky do pole, zatímco pole je uzamčeno jinými operacemi.

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

## <a name="colesafearrayredim"></a><a name="redim"></a>COleSafeArray::Redim

Změní nejméně významné (rightmost) vázána bezpečné pole.

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Parametry

*psaboundNovinka*<br/>
Ukazatel na novou bezpečnou strukturu vázané na pole obsahující novou vazbu pole. Může být změněna pouze nejméně významná dimenze pole.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayresizeonedim"></a><a name="resizeonedim"></a>COleSafeArray::ResizeOneDim

Změní počet prvků v jednorozměrném `COleSafeArray` objektu.

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Parametry

*dwElements*<br/>
Počet prvků v jednorozměrném bezpečném poli.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

  Viz příklad [cOleSafeArray::CreateOneDim](#createonedim).

## <a name="colesafearrayunaccessdata"></a><a name="unaccessdata"></a>COleSafeArray::UnaccessData

Sníží počet zámků pole a zruší platnost ukazatele načteného `AccessData`.

```
void UnaccessData();
```

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

  Viz příklad [cOleSafeArray::AccessData](#accessdata).

## <a name="colesafearrayunlock"></a><a name="unlock"></a>COleSafeArray::Odemknout

Sníží počet zámků pole, takže může být uvolněna nebo velikost.

```
void Unlock();
```

### <a name="remarks"></a>Poznámky

Tato funkce je volána po dokončení přístupu k datům v poli. Při chybě vyvolá [COleException](../../mfc/reference/coleexception-class.md).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleVariant třída](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
