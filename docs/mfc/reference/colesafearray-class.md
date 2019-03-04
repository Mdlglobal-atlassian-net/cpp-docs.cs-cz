---
title: Colesafearray – třída
ms.date: 08/27/2018
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
ms.openlocfilehash: 0833dca9311689063c2ebeadd3942d9f5ce376e2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267157"
---
# <a name="colesafearray-class"></a>Colesafearray – třída

Třída pro práci s poli libovolného typu a rozměru.

## <a name="syntax"></a>Syntaxe

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|Vytvoří `COleSafeArray` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|Načte ukazatel na data pole.|
|[COleSafeArray::AllocData](#allocdata)|Přiděluje paměť pro pole.|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Přiděluje paměť pro bezpečné pole deskriptoru.|
|[COleSafeArray::Attach](#attach)|Dává kontrolu nad stávající `VARIANT` pole na `COleSafeArray` objektu.|
|[COleSafeArray::Clear](#clear)|Uvolní všechna data v základním `VARIANT`.|
|[COleSafeArray::Copy](#copy)|Vytvoří kopii existujícího pole.|
|[COleSafeArray::Create](#create)|Vytvoří bezpečným polím.|
|[COleSafeArray::CreateOneDim](#createonedim)|Vytvoří jednorozměrný `COleSafeArray` objektu.|
|[COleSafeArray::Destroy](#destroy)|Odstraní existující pole.|
|[COleSafeArray::DestroyData](#destroydata)|Zničí data v bezpečné pole.|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Zničí popisovač bezpečným polím.|
|[COleSafeArray::Detach](#detach)|Odpojí z pole typu VARIANT `COleSafeArray` objektu (tak, aby se neuvolní data).|
|[COleSafeArray::GetByteArray](#getbytearray)|Zkopíruje obsah do bezpečného pole [CByteArray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray::GetDim](#getdim)|Vrátí počet dimenzí v poli.|
|[COleSafeArray::GetElement](#getelement)|Načte jeden element bezpečné pole.|
|[COleSafeArray::GetElemSize](#getelemsize)|Vrátí velikost v bajtech, jeden prvek bezpečné pole.|
|[COleSafeArray::GetLBound](#getlbound)|Vrátí dolní mez pro všechny dimenze pole s bezpečné.|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Vrátí počet prvků v jednorozměrné pole `COleSafeArray` objektu.|
|[COleSafeArray::GetUBound](#getubound)|Vrátí horní mez pro všechny dimenze pole s bezpečné.|
|[COleSafeArray::Lock](#lock)|Pak inkrementuje počet pole a popisovače pole umístí ukazatel na data pole.|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Vrací ukazatel na indexovaný prvek.|
|[COleSafeArray::PutElement](#putelement)|Do pole přiřadí jeden element.|
|[COleSafeArray::Redim](#redim)|Změní nejméně významnou (parametr nejvíce vpravo) mez bezpečným polím.|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Změní počet prvků v jednorozměrném `COleSafeArray` objektu.|
|[COleSafeArray::UnaccessData](#unaccessdata)|Sníží počet pole zámek a zruší platnost ukazatel získaný pomocí `AccessData`.|
|[COleSafeArray::Unlock](#unlock)|Dekrementuje počet zámků pole tak může být uvolněn nebo změně velikosti.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|Přistupuje k podkladovým `VARIANT` struktury `COleSafeArray` objektu.|
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|Přistupuje k podkladovým `VARIANT` struktury `COleSafeArray` objektu.|
|[COleSafeArray::operator =](#operator_eq)|Zkopíruje hodnoty do `COleSafeArray` objektu (`SAFEARRAY`, `VARIANT`, `COleVariant`, nebo `COleSafeArray` pole).|
|[COleSafeArray::operator ==](#operator_eq_eq)|Porovná dvě varianty pole (`SAFEARRAY`, `VARIANT`, `COleVariant`, nebo `COleSafeArray` pole).|
|[COleSafeArray::operator &lt;&lt;](#operator_lt_lt)|Vypíše obsah `COleSafeArray` objektu v kontextu s výpisem paměti.|

## <a name="remarks"></a>Poznámky

`COleSafeArray` je odvozen od OLE `VARIANT` struktury. OLE `SAFEARRAY` členské funkce jsou dostupné prostřednictvím `COleSafeArray`, stejně jako sada členské funkce, které jsou vytvořené speciálně pro jednorozměrné pole bajtů.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Požadavky

**Header:** afxdisp.h

##  <a name="accessdata"></a>  COleSafeArray::AccessData

Načte ukazatel na data pole.

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>Parametry

*ppvData*<br/>
Ukazatel na ukazatel na data pole.

### <a name="remarks"></a>Poznámky

Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

##  <a name="allocdata"></a>  COleSafeArray::AllocData

Přiděluje paměť pro bezpečné pole.

```
void AllocData();
```

### <a name="remarks"></a>Poznámky

Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md).

##  <a name="allocdescriptor"></a>  COleSafeArray::AllocDescriptor

Přiděluje paměť pro popisovač bezpečným polím.

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Parametry

*dwDims*<br/>
Počet dimenzí v poli bezpečné.

### <a name="remarks"></a>Poznámky

Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md).

##  <a name="attach"></a>  COleSafeArray::Attach

Dává kontrolu nad daty v existujícím `VARIANT` pole na `COleSafeArray` objektu.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
A `VARIANT` objektu. *VarSrc* parametr musí mít VARTYPE [VT_ARRAY](/windows/desktop/api/wtypes/ne-wtypes-varenum).

### <a name="remarks"></a>Poznámky

Zdroj `VARIANT`jeho typ je nastaven na VT_EMPTY. Tato funkce vymaže aktuální dat pole, pokud existuje.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleSafeArray::AccessData](#accessdata).

##  <a name="clear"></a>  COleSafeArray::Clear

Vymaže bezpečné pole.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

Funkce vymaže bezpečné pole tak, že nastavíte `VARTYPE` objektu VT_EMPTY. Vydání aktuální obsah a je uvolněn pole.

##  <a name="colesafearray"></a>  COleSafeArray::COleSafeArray

Vytvoří `COleSafeArray` objektu.

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

*saSrc*<br/>
Existující `COleSafeArray` objektu nebo `SAFEARRAY` ke zkopírování do nové `COleSafeArray` objektu.

*vtSrc*<br/>
VARTYPE nového `COleSafeArray` objektu.

*psaSrc*<br/>
Ukazatel `SAFEARRAY` ke zkopírování do nové `COleSafeArray` objektu.

*varSrc*<br/>
Existující `VARIANT` nebo `COleVariant` objektu, které se mají zkopírovat do nové `COleSafeArray` objektu.

*pSrc*<br/>
Ukazatel `VARIANT` objektu, které se mají zkopírovat do nové `COleSafeArray` objektu.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory vytvořit nový `COleSafeArray` objekty. Pokud zde není žádný parametr, prázdná `COleSafeArray` (VT_EMPTY) je vytvořen objekt. Pokud `COleSafeArray` zkopírován z jiného objektu array je implicitně znám jehož VARTYPE ( `COleSafeArray`, `COleVariant`, nebo `VARIANT`), VARTYPE zdrojového pole je zachován a není nutné zadávat. Pokud `COleSafeArray` zkopírován z jiného objektu array není znám jehož VARTYPE (`SAFEARRAY`), VARTYPE musí být zadán v *vtSrc* parametru.

Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md).

##  <a name="copy"></a>  COleSafeArray::Copy

Vytvoří kopii existujícího pole bezpečné.

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Parametry

*ppsa*<br/>
Ukazatel na umístění, do kterého se vraťte novou popisovače pole.

### <a name="remarks"></a>Poznámky

Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md).

##  <a name="create"></a>  COleSafeArray::Create

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

*vtSrc*<br/>
Základní typ pole (to znamená, VARTYPE každý prvek pole). VARTYPE je omezen na podmnožinu typů variant. Je možné nastavit VT_ARRAY ani VT_BYREF příznak. VT_EMPTY a VT_NULL nejsou platné základní typy pro pole. Všechny ostatní typy jsou platné.

*dwDims*<br/>
Počet dimenzí v poli. To můžete změnit po vytvoření pole s [Redim](#redim).

*rgElements*<br/>
Ukazatel na pole počtu prvků pro každou dimenzi pole.

*rgsabounds*<br/>
Ukazatel na vektor hranice (jeden pro každou dimenzi) k přidělení pro toto pole.

### <a name="remarks"></a>Poznámky

Tato funkce vymaže aktuální data pole, v případě potřeby. Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="createonedim"></a>  COleSafeArray::CreateOneDim

Vytvoří novou jednorozměrné `COleSafeArray` objektu.

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>Parametry

*vtSrc*<br/>
Základní typ pole (to znamená, VARTYPE každý prvek pole).

*dwElements*<br/>
Počet prvků v poli. To můžete změnit po vytvoření pole s [ResizeOneDim](#resizeonedim).

*pvSrcData*<br/>
Ukazatel na data, která mají zkopírovat do pole.

*nLBound*<br/>
Dolní mez pole.

### <a name="remarks"></a>Poznámky

Funkce přiděluje a inicializuje data pro pole, zkopírování zadaná data v případě, že ukazatel *pvSrcData* nemá hodnotu NULL.

Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

##  <a name="destroy"></a>  COleSafeArray::Destroy

Odstraní existující popisovač pole a všechna data v poli.

```
void Destroy();
```

### <a name="remarks"></a>Poznámky

Pokud objekty jsou uloženy v poli, je vydána každého objektu. Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md).

##  <a name="destroydata"></a>  COleSafeArray::DestroyData

Odstraní všechna data v bezpečné pole.

```
void DestroyData();
```

### <a name="remarks"></a>Poznámky

Pokud objekty jsou uloženy v poli, je vydána každého objektu. Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md).

##  <a name="destroydescriptor"></a>  COleSafeArray::DestroyDescriptor

Zničí popisovač bezpečným polím.

```
void DestroyDescriptor();
```

### <a name="remarks"></a>Poznámky

Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md).

##  <a name="detach"></a>  COleSafeArray::Detach

Odpojí `VARIANT` data z `COleSafeArray` objektu.

```
VARIANT Detach();
```

### <a name="return-value"></a>Návratová hodnota

Základní `VARIANT` hodnotu `COleSafeArray` objektu.

### <a name="remarks"></a>Poznámky

Funkce odpojí data v bezpečné pole tak, že nastavíte VARTYPE objektu VT_EMPTY. Je odpovědností volajícího uvolnit voláním funkce Windows pole [VariantClear](/windows/desktop/api/oleauto/nf-oleauto-variantclear).

Při chybě, funkce vyvolá [coleexception –](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleSafeArray::PutElement](#putelement).

##  <a name="getbytearray"></a>  COleSafeArray::GetByteArray

Zkopíruje obsah do bezpečného pole `CByteArray`.

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parametry

*Bajty*<br/>
Odkaz na [CByteArray](../../mfc/reference/cbytearray-class.md) objektu.

##  <a name="getdim"></a>  COleSafeArray::GetDim

Vrátí počet dimenzí `COleSafeArray` objektu.

```
DWORD GetDim();
```

### <a name="return-value"></a>Návratová hodnota

Počet dimenzí v poli bezpečné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="getelement"></a>  COleSafeArray::GetElement

Načte jeden element bezpečné pole.

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parametry

*rgIndices*<br/>
Ukazatel na pole indexů pro jednotlivé rozměry pole.

*pvData*<br/>
Ukazatel na umístění, na prvek pole.

### <a name="remarks"></a>Poznámky

Tato funkce automaticky volá funkce systému windows `SafeArrayLock` a `SafeArrayUnlock` před a po načtení elementu. Pokud datový element je řetězec, objekt nebo typ variant, funkce zkopíruje element správným způsobem. Parametr *pvData* by měly odkazovat na velké nedostatek vyrovnávací paměti tak, aby obsahovala element.

Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

##  <a name="getelemsize"></a>  COleSafeArray::GetElemSize

Získá velikost prvku v `COleSafeArray` objektu.

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Návratová hodnota

Velikost v bajtech prvků bezpečným polím.

##  <a name="getlbound"></a>  COleSafeArray::GetLBound

Vrátí dolní mez pro všechny dimenze `COleSafeArray` objektu.

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Parametry

*dwDim*<br/>
Rozměry pole, pro který má být získána dolní mez.

*pLBound*<br/>
Ukazatel na umístění a vrátí dolní mez.

### <a name="remarks"></a>Poznámky

Při chybě, funkce vyvolá [coleexception –](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

##  <a name="getonedimsize"></a>  COleSafeArray::GetOneDimSize

Vrátí počet prvků v jednorozměrné pole `COleSafeArray` objektu.

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v nouzovém jednorozměrné pole.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleSafeArray::CreateOneDim](#createonedim).

##  <a name="getubound"></a>  COleSafeArray::GetUBound

Vrátí horní mez pro všechny dimenze pole s bezpečné.

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Parametry

*dwDim*<br/>
Rozměry pole, pro který má být získána horní mez.

*pUBound*<br/>
Ukazatel na umístění a vrátí horní mez.

### <a name="remarks"></a>Poznámky

Při chybě, funkce vyvolá [coleexception –](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

##  <a name="lock"></a>  COleSafeArray::Lock

Pak inkrementuje počet pole a umístit ukazatel na pole data v popisovače pole.

```
void Lock();
```

### <a name="remarks"></a>Poznámky

Při chybě, vyvolá výjimku [coleexception –](../../mfc/reference/coleexception-class.md).

Ukazatel do popisovače pole je platný až do `Unlock` je volána. Volání `Lock` mohou být vnořené; stejný počet volání `Unlock` jsou povinné.

Pole nejde odstranit, když je zamknutý.

##  <a name="operator_lpcvariant"></a>  COleSafeArray::operator LPCVARIANT

Tento operátor přetypování pro přístup k podkladové volání `VARIANT` strukturu pro to `COleSafeArray` objektu.

```
operator LPCVARIANT() const;
```

##  <a name="operator_lpvariant"></a>  COleSafeArray::operator LPVARIANT

Tento operátor přetypování pro přístup k podkladové volání `VARIANT` strukturu pro to `COleSafeArray` objektu.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Poznámky

Mějte na paměti tuto změnu hodnoty v `VARIANT` struktura přistupuje vrácený touto funkcí ukazatel se změní hodnota tohoto `COleSafeArray` objektu.

##  <a name="operator_eq"></a>  COleSafeArray::operator =

Zkopírování těchto přetížených operátorech přiřazení zdrojová hodnota do tohoto `COleSafeArray` objektu.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
  COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Poznámky

Následuje stručný popis jednotlivých operátorů:

- **Operator = (** *saSrc* **)** zkopíruje existující `COleSafeArray` objektu do tohoto objektu.

- **Operator = (** *varSrc* **)** zkopíruje existující `VARIANT` nebo `COleVariant` pole do tohoto objektu.

- **Operator = (** *pSrc* **)** kopie `VARIANT` objektu array přistupuje *pSrc* do tohoto objektu.

##  <a name="operator_eq_eq"></a>  COleSafeArray::operator ==

Tento operátor porovnání dvou polí (`SAFEARRAY`, `VARIANT`, `COleVariant`, nebo `COleSafeArray` pole) a vrátí nenulovou hodnotu, pokud jsou stejné; jinak 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Poznámky

Dvě pole jsou si rovny, pokud mají stejný počet dimenzí, stejné velikosti v jednotlivých dimenzí a element stejné hodnoty.

##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;

`COleSafeArray` Vložení (<<) – operátor podporuje diagnostiku vypsání a ukládání `COleSafeArray` objektu do archivu.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex

Vrací ukazatel na prvek určené hodnoty indexu.

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Parametry

*rgIndices*<br/>
Pole hodnot indexu, které identifikují prvek pole. Je třeba zadat všechny indexy pro element.

*ppvData*<br/>
Na návratové, ukazatel na prvek určený hodnotami v *rgIndices*.

##  <a name="putelement"></a>  COleSafeArray::PutElement

Do pole přiřadí jeden element.

```
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parametry

*rgIndices*<br/>
Ukazatel na pole indexů pro jednotlivé rozměry pole.

*pvData*<br/>
Ukazatel na data, která mají přiřadit k poli. VT_DISPATCH VT_UNKNOWN a VT_BSTR variant typy jsou ukazatele a nevyžadují další úroveň dereference.

### <a name="remarks"></a>Poznámky

Tato funkce automaticky volá funkce Windows [SafeArrayLock](/windows/desktop/api/oleauto/nf-oleauto-safearraylock) a [SafeArrayUnlock](/windows/desktop/api/oleauto/nf-oleauto-safearrayunlock) před a po přiřazení elementu. Pokud datový element je řetězec, objekt nebo typ variant, funkce zkopíruje ho správně, a pokud existující prvek je řetězec, objekt nebo typ variant, není správně zaškrtnuté.

Všimněte si, že máte několika zámky na pole, tak prvky můžete umístit do pole uzamčeném pole pomocí dalších operací.

Při chybě, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

##  <a name="redim"></a>  COleSafeArray::Redim

Změní nejméně významnou (parametr nejvíce vpravo) mez bezpečným polím.

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Parametry

*psaboundNew*<br/>
Ukazatel na novou bezpečné pole svázáno struktury obsahující nové hranice pole. Pouze nejméně významnou dimenzí pole mohou být změněny.

### <a name="remarks"></a>Poznámky

Při chybě, funkce vyvolá [coleexception –](../../mfc/reference/coleexception-class.md).

##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim

Změní počet prvků v jednorozměrném `COleSafeArray` objektu.

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Parametry

*dwElements*<br/>
Počet prvků v nouzovém jednorozměrné pole.

### <a name="remarks"></a>Poznámky

Při chybě, funkce vyvolá [coleexception –](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleSafeArray::CreateOneDim](#createonedim).

##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData

Sníží počet pole zámek a zruší platnost ukazatel získaný pomocí `AccessData`.

```
void UnaccessData();
```

### <a name="remarks"></a>Poznámky

Při chybě, funkce vyvolá [coleexception –](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleSafeArray::AccessData](#accessdata).

##  <a name="unlock"></a>  COleSafeArray::Unlock

Dekrementuje počet zámků pole tak může být uvolněn nebo změně velikosti.

```
void Unlock();
```

### <a name="remarks"></a>Poznámky

Tato funkce je volána po dokončení přístup k datům v poli. Při chybě, vyvolá výjimku [coleexception –](../../mfc/reference/coleexception-class.md).

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleVariant – třída](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
