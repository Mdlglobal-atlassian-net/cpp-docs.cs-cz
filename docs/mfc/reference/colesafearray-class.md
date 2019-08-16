---
title: COleSafeArray – třída
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
ms.openlocfilehash: b947678acc89bad96ce01b93e79cbaa141411ec4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503784"
---
# <a name="colesafearray-class"></a>COleSafeArray – třída

Třída pro práci s poli libovolného typu a rozměru.

## <a name="syntax"></a>Syntaxe

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|`COleSafeArray` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|Načte ukazatel na data pole.|
|[COleSafeArray::AllocData](#allocdata)|Přidělí paměť poli.|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Přidělí paměť pro bezpečný popisovač pole.|
|[COleSafeArray::Attach](#attach)|Poskytuje ovládací prvek `COleSafeArray` pro existující `VARIANT` pole objektu.|
|[COleSafeArray:: Clear](#clear)|Uvolní všechna data v podkladu `VARIANT`.|
|[COleSafeArray::Copy](#copy)|Vytvoří kopii existujícího pole.|
|[COleSafeArray:: Create](#create)|Vytvoří zabezpečené pole.|
|[COleSafeArray::CreateOneDim](#createonedim)|Vytvoří jednorozměrného `COleSafeArray` objektu.|
|[COleSafeArray::D estroy](#destroy)|Odstraní existující pole.|
|[COleSafeArray::DestroyData](#destroydata)|Zničí data v bezpečném poli.|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Odstraní popisovač bezpečného pole.|
|[COleSafeArray::Detach](#detach)|Odpojí pole variant od `COleSafeArray` objektu (takže data nebudou uvolněna).|
|[COleSafeArray::GetByteArray](#getbytearray)|Zkopíruje obsah pole Safe do [CByteArray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray::GetDim](#getdim)|Vrátí počet rozměrů v poli.|
|[COleSafeArray:: Get– element](#getelement)|Načte jeden prvek bezpečného pole.|
|[COleSafeArray::GetElemSize](#getelemsize)|Vrátí velikost (v bajtech) jednoho prvku v bezpečném poli.|
|[COleSafeArray::GetLBound](#getlbound)|Vrátí dolní mez pro libovolnou dimenzi bezpečného pole.|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Vrátí počet prvků v `COleSafeArray` jednorozměrném objektu.|
|[COleSafeArray::GetUBound](#getubound)|Vrátí horní mez pro libovolnou dimenzi bezpečného pole.|
|[COleSafeArray::Lock](#lock)|Zvýší počet zámků pole a umístí ukazatel na data pole v popisovači pole.|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Vrátí ukazatel na indexovaný element.|
|[COleSafeArray::P utElement](#putelement)|Přiřadí jeden prvek k poli.|
|[COleSafeArray:: ReDim](#redim)|Změní nejméně významnou (pravé) hranici bezpečného pole.|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Změní počet prvků v `COleSafeArray` jednorozměrném objektu.|
|[COleSafeArray::UnaccessData](#unaccessdata)|Sníží počet zámků pole a neověřuje ukazatel, který získá `AccessData`.|
|[COleSafeArray:: Unlock](#unlock)|Sníží počet zámků pole tak, aby se mohl uvolnit nebo změnit jeho velikost.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[COleSafeArray:: operator LPCVARIANT](#operator_lpcvariant)|Přistupuje k podkladové `VARIANT` struktuře `COleSafeArray` objektu.|
|[COleSafeArray:: operator LPVARIANT](#operator_lpvariant)|Přistupuje k podkladové `VARIANT` struktuře `COleSafeArray` objektu.|
|[COleSafeArray:: operator =](#operator_eq)|Kopíruje hodnoty do `COleSafeArray` objektu (`SAFEARRAY`, `VARIANT`, `COleVariant`nebo `COleSafeArray` Array).|
|[COleSafeArray:: operator = = – operátor](#operator_eq_eq)|Porovná dvě pole variant`SAFEARRAY`( `VARIANT`, `COleVariant`, nebo `COleSafeArray` pole).|
|[COleSafeArray:: operator&lt;&lt;](#operator_lt_lt)|Vypíše obsah `COleSafeArray` objektu do kontextu výpisu paměti.|

## <a name="remarks"></a>Poznámky

`COleSafeArray`je odvozen ze struktury OLE `VARIANT` . Členské funkce `SAFEARRAY` OLE jsou k dispozici `COleSafeArray`prostřednictvím a také sada členských funkcí navržených speciálně pro jednorozměrné pole bajtů.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

##  <a name="accessdata"></a>COleSafeArray::AccessData

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

##  <a name="allocdata"></a>  COleSafeArray::AllocData

Přidělí paměť bezpečnému poli.

```
void AllocData();
```

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="allocdescriptor"></a>COleSafeArray::AllocDescriptor

Přidělí paměť pro popisovač bezpečného pole.

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Parametry

*dwDims*<br/>
Počet rozměrů v poli Safe.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="attach"></a>  COleSafeArray::Attach

Poskytuje řízení dat v existujícím `VARIANT` poli `COleSafeArray` objektu.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
A `VARIANT` objektu. Parametr *varSrc* musí mít parametr VARTYPE [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum).

### <a name="remarks"></a>Poznámky

Typ zdroje `VARIANT`je nastavený na VT_EMPTY. Tato funkce vymaže aktuální data pole, pokud existují.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleSafeArray:: AccessData](#accessdata).

##  <a name="clear"></a>COleSafeArray:: Clear

Vymaže pole Safe.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

Funkce vymaže bezpečné pole `VARTYPE` nastavením objektu na VT_EMPTY. Aktuální obsah se uvolní a pole se uvolní.

##  <a name="colesafearray"></a>COleSafeArray::COleSafeArray

`COleSafeArray` Vytvoří objekt.

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
Existující `COleSafeArray` objekt nebo `SAFEARRAY` bude zkopírován do nového `COleSafeArray` objektu.

*vtSrc*<br/>
VARTYPE nového `COleSafeArray` objektu.

*psaSrc*<br/>
Ukazatel `SAFEARRAY` na objekt, který má být zkopírován do nového `COleSafeArray` objektu.

*varSrc*<br/>
Existující `VARIANT` objekt nebo `COleVariant` objekt, který má být zkopírován do `COleSafeArray` nového objektu.

*pSrc*<br/>
Ukazatel na `VARIANT` objekt, který má být zkopírován do nového `COleSafeArray` objektu.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory vytvoří nové `COleSafeArray` objekty. Není-li parametr zadán, je vytvořen `COleSafeArray` prázdný objekt (VT_EMPTY). Pokud je `COleSafeArray` zkopírován z jiného pole, jehož parametr VARTYPE je známý implicitně ( `COleSafeArray`a `COleVariant`, nebo `VARIANT`), je objekt VARTYPE zdrojového pole zachován a nemusí být zadán. Pokud je `COleSafeArray` zkopírován z jiného pole, jehož ukazatel VARTYPE není znám (`SAFEARRAY`), musí být v parametru *vtSrc* zadán VARTYPE.

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="copy"></a>COleSafeArray:: Copy

Vytvoří kopii existujícího bezpečného pole.

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Parametry

*ppsa*<br/>
Ukazatel na umístění, ve kterém má být vrácen nový popisovač pole.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="create"></a>COleSafeArray:: Create

Přidělí a inicializuje data pro pole.

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
Základní typ pole (tj. typ VARTYPE každého prvku pole). Typ VARTYPE je omezen na podmnožinu variantních typů. Není možné nastavit VT_ARRAY ani příznak VT_BYREF. VT_EMPTY a VT_NULL nejsou platnými základními typy pro pole. Všechny ostatní typy jsou právní.

*dwDims*<br/>
Počet rozměrů v poli To lze změnit poté, co je pole Vytvořeno pomocí [ReDim](#redim).

*rgElements*<br/>
Ukazatel na pole s počtem prvků pro každou dimenzi v poli.

*rgsabounds*<br/>
Ukazatel na vektor mezí (jeden pro každou dimenzi), který se má pro pole přidělit.

### <a name="remarks"></a>Poznámky

Tato funkce vymaže v případě potřeby aktuální data pole. Při chybě funkce vyvolá výjimku [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="createonedim"></a>COleSafeArray::CreateOneDim

Vytvoří nový jednorozměrné `COleSafeArray` objekt.

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>Parametry

*vtSrc*<br/>
Základní typ pole (tj. typ VARTYPE každého prvku pole).

*dwElements*<br/>
Počet prvků v poli. To lze změnit poté, co je pole Vytvořeno pomocí [ResizeOneDim](#resizeonedim).

*pvSrcData*<br/>
Ukazatel na data, která se mají zkopírovat do pole.

*nLBound*<br/>
Dolní mez pole

### <a name="remarks"></a>Poznámky

Funkce přiděluje a inicializuje data pro pole a kopíruje zadaná data, pokud ukazatel *pvSrcData* není null.

Při chybě funkce vyvolá výjimku [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

##  <a name="destroy"></a>COleSafeArray::D estroy

Odstraní existující popisovač pole a všechna data v poli.

```
void Destroy();
```

### <a name="remarks"></a>Poznámky

Pokud jsou objekty uloženy v poli, každý objekt je uvolněn. Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="destroydata"></a>  COleSafeArray::DestroyData

Zničí všechna data v bezpečném poli.

```
void DestroyData();
```

### <a name="remarks"></a>Poznámky

Pokud jsou objekty uloženy v poli, každý objekt je uvolněn. Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="destroydescriptor"></a>COleSafeArray::D estroyDescriptor

Odstraní popisovač bezpečného pole.

```
void DestroyDescriptor();
```

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="detach"></a>COleSafeArray::D etach

Odpojí `COleSafeArray` data od objektu. `VARIANT`

```
VARIANT Detach();
```

### <a name="return-value"></a>Návratová hodnota

Podkladová `VARIANT` hodnota `COleSafeArray` objektu.

### <a name="remarks"></a>Poznámky

Funkce odpojí data v bezpečném poli nastavením VARTYPE objektu na VT_EMPTY. Je zodpovědností volajícího uvolnit pole voláním funkce Windows [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear).

Při chybě funkce vyvolá výjimku [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleSafeArray::P utelement](#putelement).

##  <a name="getbytearray"></a>COleSafeArray:: getbytearray

Zkopíruje obsah bezpečného pole do `CByteArray`.

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parametry

*psaný*<br/>
Odkaz na objekt [CByteArray](../../mfc/reference/cbytearray-class.md) .

##  <a name="getdim"></a>COleSafeArray::GetDim

Vrátí počet rozměrů v `COleSafeArray` objektu.

```
DWORD GetDim();
```

### <a name="return-value"></a>Návratová hodnota

Počet rozměrů v poli trezoru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="getelement"></a>COleSafeArray:: Get– element

Načte jeden prvek bezpečného pole.

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parametry

*rgIndices*<br/>
Ukazatel na pole indexů pro každou dimenzi pole.

*pvData*<br/>
Ukazatel na umístění pro umístění elementu pole.

### <a name="remarks"></a>Poznámky

Tato funkce automaticky volá funkce `SafeArrayLock` systému Windows a `SafeArrayUnlock` před a po načtení prvku. Je-li datový prvek řetězec, objekt nebo varianta, funkce zkopíruje prvek správným způsobem. Parametr *pvData* by měl ukazovat na velkou vyrovnávací paměť, která bude obsahovat element.

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

##  <a name="getelemsize"></a>COleSafeArray::GetElemSize

Načte velikost elementu v `COleSafeArray` objektu.

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Návratová hodnota

Velikost prvků bezpečného pole v bajtech.

##  <a name="getlbound"></a>COleSafeArray::GetLBound

Vrátí dolní mez pro libovolnou dimenzi `COleSafeArray` objektu.

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Parametry

*dwDim*<br/>
Dimenze pole, pro kterou chcete získat dolní mez.

*pLBound*<br/>
Ukazatel na umístění pro návrat dolní meze.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá výjimku [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

##  <a name="getonedimsize"></a>COleSafeArray::GetOneDimSize

Vrátí počet prvků v `COleSafeArray` jednorozměrném objektu.

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Návratová hodnota

Počet elementů v jednorozměrném poli zabezpečení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleSafeArray:: CreateOneDim](#createonedim).

##  <a name="getubound"></a>COleSafeArray::GetUBound

Vrátí horní mez pro libovolnou dimenzi bezpečného pole.

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Parametry

*dwDim*<br/>
Dimenze pole, pro kterou se má získat horní mez

*pUBound*<br/>
Ukazatel na umístění pro návrat horní meze.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá výjimku [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

##  <a name="lock"></a>COleSafeArray:: Lock

Zvýší počet zámků pole a umístí ukazatel na data pole v popisovači pole.

```
void Lock();
```

### <a name="remarks"></a>Poznámky

Při chybě vyvolá [COleException](../../mfc/reference/coleexception-class.md).

Ukazatel v popisovači pole je platný, dokud `Unlock` není voláno. Volání mohou být vnořena; je požadován stejný počet `Unlock` volání. `Lock`

Pole nelze odstranit, je-li uzamčeno.

##  <a name="operator_lpcvariant"></a>COleSafeArray:: operator LPCVARIANT

Zavolejte Tento operátor přetypování pro přístup k `VARIANT` podkladové `COleSafeArray` struktuře pro tento objekt.

```
operator LPCVARIANT() const;
```

##  <a name="operator_lpvariant"></a>COleSafeArray:: operator LPVARIANT

Zavolejte Tento operátor přetypování pro přístup k `VARIANT` podkladové `COleSafeArray` struktuře pro tento objekt.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Poznámky

Všimněte si, že změna hodnoty ve `VARIANT` struktuře, ke které se přistupovalo pomocí ukazatele vráceného touto funkcí, `COleSafeArray` změní hodnotu tohoto objektu.

##  <a name="operator_eq"></a>COleSafeArray:: operator =

Tyto přetížené operátory přiřazení zkopírují zdrojové hodnoty do tohoto `COleSafeArray` objektu.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
  COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Poznámky

Následuje stručný popis každého operátoru:

- **operator = (** *saSrc* **)** – operátor Zkopíruje existující `COleSafeArray` objekt do tohoto objektu.

- **operator = (** *varSrc* **)** – operátor Zkopíruje existující `VARIANT` pole nebo `COleVariant` do tohoto objektu.

- **operator = (** *pSrc* **)** – operátor Zkopíruje objekt `VARIANT` Array, k němuž přistupoval *pSrc* , do tohoto objektu.

##  <a name="operator_eq_eq"></a>COleSafeArray:: operator = = – operátor

Tento operátor porovná dvě pole`SAFEARRAY`( `VARIANT`, `COleVariant`, nebo `COleSafeArray` pole) a vrátí nenulovou hodnotu, pokud jsou stejné; jinak 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Poznámky

Dvě pole jsou shodná, pokud mají stejný počet rozměrů, stejnou velikost v každé dimenzi a stejné hodnoty prvků.

##  <a name="operator_lt_lt"></a>COleSafeArray:: operator&lt;&lt;

Operátor vložení (< <) podporuje diagnostický dumping a ukládání `COleSafeArray` objektu do archivu. `COleSafeArray`

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

##  <a name="ptrofindex"></a>COleSafeArray::P trOfIndex

Vrací ukazatel na prvek určený hodnotami indexu.

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Parametry

*rgIndices*<br/>
Pole hodnot indexu, které identifikují prvek pole. Musí být zadány všechny indexy elementu.

*ppvData*<br/>
Při návratu se ukazatel na prvek identifikovaný hodnotami v *rgIndices*.

##  <a name="putelement"></a>COleSafeArray::P utElement

Přiřadí jeden prvek k poli.

```
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parametry

*rgIndices*<br/>
Ukazatel na pole indexů pro každou dimenzi pole.

*pvData*<br/>
Ukazatel na data, která chcete přiřadit poli. Typy variant VT_DISPATCH, VT_UNKNOWN a VT_BSTR jsou ukazatele a nevyžadují jinou úroveň dereference.

### <a name="remarks"></a>Poznámky

Tato funkce automaticky volá funkci Windows Functions [SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock) a [SafeArrayUnlock](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) před a po přiřazení elementu. Je-li datový prvek řetězec, objekt nebo varianta, funkce jej zkopíruje správně a pokud je existující prvek řetězec, objekt nebo varianta, je vymazána správně.

Všimněte si, že můžete mít více zámků v poli, takže můžete umístit prvky do pole, když je pole uzamčeno jinými operacemi.

Při chybě funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

##  <a name="redim"></a>COleSafeArray:: ReDim

Změní nejméně významnou (pravé) hranici bezpečného pole.

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Parametry

*psaboundNew*<br/>
Ukazatel na novou strukturu svázanou v bezpečném poli obsahující nové pole vázaného. Je možné změnit pouze nejmenší důležitou dimenzi pole.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá výjimku [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="resizeonedim"></a>COleSafeArray::ResizeOneDim

Změní počet prvků v `COleSafeArray` jednorozměrném objektu.

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Parametry

*dwElements*<br/>
Počet prvků v jednorozměrném poli s jedním rozměrem.

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá výjimku [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleSafeArray:: CreateOneDim](#createonedim).

##  <a name="unaccessdata"></a>COleSafeArray::UnaccessData

Sníží počet zámků pole a neověřuje ukazatel, který získá `AccessData`.

```
void UnaccessData();
```

### <a name="remarks"></a>Poznámky

Při chybě funkce vyvolá výjimku [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [COleSafeArray:: AccessData](#accessdata).

##  <a name="unlock"></a>COleSafeArray:: Unlock

Sníží počet zámků pole tak, aby se mohl uvolnit nebo změnit jeho velikost.

```
void Unlock();
```

### <a name="remarks"></a>Poznámky

Tato funkce se volá po dokončení přístupu k datům v poli. Při chybě vyvolá [COleException](../../mfc/reference/coleexception-class.md).

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleVariant – třída](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
