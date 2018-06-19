---
title: Třída COleVariant | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
dev_langs:
- C++
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b7f0da1f53bf2c6b0e216195be37746eab9abd1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378518"
---
# <a name="colevariant-class"></a>COleVariant – třída
Zapouzdří [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) datového typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleVariant : public tagVARIANT  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleVariant::COleVariant](#colevariant)|Vytvoří `COleVariant` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleVariant::Attach](#attach)|Připojí **VARIANT** k `COleVariant`.|  
|[COleVariant::ChangeType](#changetype)|Změní typ varianty této `COleVariant` objektu.|  
|[COleVariant::Clear](#clear)|Vymaže to `COleVariant` objektu.|  
|[COleVariant::Detach](#detach)|Umožňuje odpojit **VARIANT** z `COleVariant` a vrátí **VARIANT**.|  
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Načte bajtové pole z existující variant pole.|  
|[COleVariant::SetString](#setstring)|Nastaví řetězec pro konkrétní typ, obvykle ANSI.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|Převede `COleVariant` hodnotu do `LPCVARIANT`.|  
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|Převede `COleVariant` objektu do `LPVARIANT`.|  
|[COleVariant::operator =](#operator_eq)|Kopie `COleVariant` hodnotu.|  
|[COleVariant::operator ==](#operator_eq_eq)|Porovná dva `COleVariant` hodnoty.|  
|[COleVariant::operator &lt; &lt;, &gt;&gt;](#operator_lt_lt__gt_gt)|Výstupy `COleVariant` hodnotu `CArchive` nebo `CDumpContext` a vstup `COleVariant` objektu z `CArchive`.|  
  
## <a name="remarks"></a>Poznámky  
 Tento datový typ se používá v automatizace OLE. Konkrétně [DISPPARAMS](http://msdn.microsoft.com/en-us/a16e5a21-766e-4287-b039-13429aa78f8b) struktura obsahuje ukazatele na pole **VARIANT** struktury. A **DISPPARAMS** struktura slouží k předat parametry do [volání metody IDispatch::Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
> [!NOTE]
>  Tato třída je odvozený od **VARIANT** struktura. To znamená, že můžete předat `COleVariant` v parametru, který volá pro **VARIANT** a že data členů **VARIANT** struktura jsou členy dat dostupný `COleVariant`.  
  
 Dva související třídy MFC [COleCurrency](../../mfc/reference/colecurrency-class.md) a [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zapouzdření variant – datové typy **MĚNA** ( `VT_CY`) a **datum** ( `VT_DATE`). `COleVariant` Třída se hojně používá v třídy DAO; viz tyto třídy pro typická využití této třídy, například [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) a [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 Další informace najdete v tématu [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118), [MĚNA](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e), [DISPPARAMS](http://msdn.microsoft.com/en-us/a16e5a21-766e-4287-b039-13429aa78f8b), a [volání metody IDispatch::Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d) položky v sadě Windows SDK.  
  
 Další informace o `COleVariant` třídy a jeho použití v OLE – automatizace, najdete v části "Předávání parametry v automatizace OLE" v článku [automatizace](../../mfc/automation.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `tagVARIANT`  
  
 `COleVariant`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
  
##  <a name="attach"></a>  COleVariant::Attach  
 Volání této funkce pro připojení danou [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) objektu na aktuální `COleVariant` objektu.  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *varSrc*  
 Existující **VARIANT** objekt, který má být připojen k aktuální `COleVariant` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se nastaví [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) z *varSrc* k `VT_EMPTY`.  
  
 Další informace najdete v tématu [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) a [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) položky v sadě Windows SDK.  
  
##  <a name="colevariant"></a>  COleVariant::COleVariant  
 Vytvoří `COleVariant` objektu.  
  
```  
COleVariant(); 
COleVariant(const VARIANT& varSrc); 
COleVariant(const COleVariant& varSrc); 
COleVariant(LPCVARIANT pSrc); 
COleVariant(LPCTSTR lpszSrc); 
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc); 
COleVariant(CString& strSrc); 
COleVariant(BYTE nSrc); 
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2); 
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4); 
COleVariant(const COleCurrency& curSrc); 
COleVariant(float fltSrc); 
COleVariant(double dblSrc); 
COleVariant(const COleDateTime& timeSrc); 
COleVariant(const CByteArray& arrSrc); 
COleVariant(const CLongBinary& lbSrc); 
COleVariant(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Parametry  
 *varSrc*  
 Existující `COleVariant` nebo **VARIANT** objekt, který má být zkopírován do nové `COleVariant` objektu.  
  
 `pSrc`  
 Ukazatel **VARIANT** objekt, který se zkopírují do nové `COleVariant` objektu.  
  
 `lpszSrc`  
 Řetězce ukončené hodnotou null zkopírovat do nové `COleVariant` objektu.  
  
 `vtSrc`  
 `VARTYPE` Pro nové `COleVariant` objektu.  
  
 `strSrc`  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který má být zkopírován do nové `COleVariant` objektu.  
  
 `nSrc`, `lSrc`  
 Číselné hodnoty, které se mají zkopírovat do nové `COleVariant` objektu.  
  
 `vtSrc`  
 `VARTYPE` Pro nové `COleVariant` objektu.  
  
 `curSrc`  
 A [COleCurrency](../../mfc/reference/colecurrency-class.md) objekt, který má být zkopírován do nové `COleVariant` objektu.  
  
 `fltSrc`, `dblSrc`  
 Číselné hodnoty, které se mají zkopírovat do nové `COleVariant` objektu.  
  
 `timeSrc`  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který má být zkopírován do nové `COleVariant` objektu.  
  
 `arrSrc`  
 A [CByteArray](../../mfc/reference/cbytearray-class.md) objekt, který má být zkopírován do nové `COleVariant` objektu.  
  
 `lbSrc`  
 A [CLongBinary](../../mfc/reference/clongbinary-class.md) objekt, který má být zkopírován do nové `COleVariant` objektu.  
  
 `pidl`  
 Ukazatel [ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321) struktury, které se mají zkopírovat do nové `COleVariant` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Všechny tyto konstruktory vytvořit nový `COleVariant` objekty inicializovat se zadanou hodnotou. Následuje stručný popis každého z těchto konstruktorů.  
  
- **(COleVariant)** vytvoří prázdnou `COleVariant` objektu `VT_EMPTY`.  
  
- **COleVariant (** *varSrc* **)** zkopíruje existující **VARIANT** nebo `COleVariant` objektu. Typ varianty se zachová.  
  
- **COleVariant (** `pSrc` **)** zkopíruje existující **VARIANT** nebo `COleVariant` objektu. Typ varianty se zachová.  
  
- **COleVariant (** `lpszSrc` **)** zkopíruje řetězec do nového objektu `VT_BSTR` (UNICODE).  
  
- **COleVariant (** `lpszSrc` **,** `vtSrc` **)** zkopíruje řetězec do nového objektu. Parametr `vtSrc` musí být `VT_BSTR` (UNICODE) nebo `VT_BSTRT` (ANSI).  
  
- **COleVariant (** `strSrc` **)** zkopíruje řetězec do nového objektu **VT_BSTR** (UNICODE).  
  
- **COleVariant (** `nSrc` **)** zkopíruje 8bitovou celočíselnou do nového objektu `VT_UI1`.  
  
- **COleVariant (** `nSrc` **,** `vtSrc` **)** zkopíruje 16bitové celé číslo (nebo logická hodnota) do nového objektu. Parametr `vtSrc` musí být `VT_I2` nebo `VT_BOOL`.  
  
- **COleVariant (** `lSrc` **,** `vtSrc` **)** zkopíruje 32bitové celé číslo (nebo `SCODE` hodnotu) do nového objektu. Parametr `vtSrc` musí být `VT_I4`, `VT_ERROR`, nebo `VT_BOOL`.  
  
- **COleVariant (** `curSrc` **)** kopie **COleCurrency** hodnotu do nového objektu `VT_CY`.  
  
- **COleVariant (** `fltSrc` **)** zkopíruje hodnotu s plovoucí desetinnou čárkou 32-bit do nového objektu `VT_R4`.  
  
- **COleVariant (** `dblSrc` **)** zkopíruje hodnotu s plovoucí desetinnou čárkou 64-bit do nového objektu `VT_R8`.  
  
- **COleVariant (** `timeSrc` **)** kopie `COleDateTime` hodnotu do nového objektu `VT_DATE`.  
  
- **COleVariant (** `arrSrc` **)** kopie `CByteArray` objektu do nového objektu `VT_EMPTY`.  
  
- **COleVariant (** `lbSrc` **)** kopie `CLongBinary` objektu do nového objektu `VT_EMPTY`.  
  
 Další informace o `SCODE`, najdete v části [struktura kódy chyb COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) ve Windows SDK.  
  
##  <a name="changetype"></a>  COleVariant::ChangeType  
 Převede typ variant hodnoty v tomto `COleVariant` objektu.  
  
```  
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `vartype`  
 [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) pro tento `COleVariant` objektu.  
  
 `pSrc`  
 Ukazatel [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) objekt, který chcete převést. Pokud je tato hodnota **NULL**tento `COleVariant` objekt se používá jako zdroj pro převod.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118), [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4), a [VariantChangeType](http://msdn.microsoft.com/en-us/48a51e32-95d7-4eeb-8106-f5043ffa2fd1) položky v sadě Windows SDK.  
  
##  <a name="clear"></a>  COleVariant::Clear  
 Vymaže **VARIANT**.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Tím se nastaví **VARTYPE** pro tento objekt, který chcete `VT_EMPTY`. `COleVariant` Destruktor volání této funkce.  
  
 Další informace najdete v tématu `VARIANT`, `VARTYPE`, a `VariantClear` položky v sadě Windows SDK.  
  
##  <a name="detach"></a>  COleVariant::Detach  
 Umožňuje odpojit základní [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) objekt z tohoto `COleVariant` objektu.  
  
```  
VARIANT Detach();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se nastaví [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) pro tento `COleVariant` do objektu `VT_EMPTY`.  
  
> [!NOTE]
>  Po volání **odpojení**, odpovídá volajícího k volání **VariantClear** na výsledná **VARIANT** struktura.  
  
 Další informace najdete v tématu [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118), [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4), a [VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835) položky v sadě Windows SDK.  
  
##  <a name="getbytearrayfromvariantarray"></a>  COleVariant::GetByteArrayFromVariantArray  
 Načte bajtové pole z existující variant pole  
  
```  
void GetByteArrayFromVariantArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>Parametry  
 `bytes`  
 Odkaz na existující [CByteArray](../../mfc/reference/cbytearray-class.md) objektu.  
  
##  <a name="operator_lpcvariant"></a>  COleVariant::operator LPCVARIANT  
 Tento operátor přetypování vrátí `VARIANT` struktura, jehož hodnota je zkopírována z tohoto `COleVariant` objektu.  
  
```  
operator LPCVARIANT() const; 
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="operator_lpvariant"></a>  COleVariant::operator LPVARIANT  
 Volání tento operátor přetypování pro přístup k základní `VARIANT` struktury pro tuto `COleVariant` objektu.  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  Změna hodnoty v **VARIANT** struktura přístup ukazatele, vrátí tato funkce se změní hodnota této `COleVariant` objektu.  
  
##  <a name="operator_eq"></a>  COleVariant::operator =  
 Tyto operátory přetížené přiřazení zkopírujte zdrojové hodnoty do této `COleVariant` objektu.  
  
```  
const COleVariant& operator=(const VARIANT& varSrc); 
const COleVariant& operator=(LPCVARIANT pSrc); 
const COleVariant& operator=(const COleVariant& varSrc); 
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc); 
const COleVariant& operator=(BYTE nSrc); 
const COleVariant& operator=(short nSrc); 
const COleVariant& operator=(long lSrc); 
const COleVariant& operator=(const COleCurrency& curSrc); 
const COleVariant& operator=(float fltSrc); 
const COleVariant& operator=(double dblSrc); 
const COleVariant& operator=(const COleDateTime& dateSrc); 
const COleVariant& operator=(const CByteArray& arrSrc); 
const COleVariant& operator=(const CLongBinary& lbSrc);
```  
  
### <a name="remarks"></a>Poznámky  
 Následuje stručný popis jednotlivých operátor:  
  
- **Operator = (** *varSrc ***)** zkopíruje existující **VARIANT** nebo `COleVariant` objektu do tohoto objektu.  
  
- **Operator = (** `pSrc` **)** kopie **VARIANT** objekt `pSrc` do tohoto objektu.  
  
- **Operator = (** `lpszSrc` **)** zkopíruje do tohoto objektu řetězce ukončené hodnotou null a nastaví **VARTYPE** k `VT_BSTR`.  
  
- **operátor = (** `strSrc` **)** kopie [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu do tento objekt a nastaví **VARTYPE** k `VT_BSTR`.  
  
- **Operator = (** `nSrc` **)** zkopíruje 8 nebo 16bitové celé číslo do tohoto objektu. Pokud `nSrc` je hodnota 8 bitů, **VARTYPE** tohoto objektu je nastaven na `VT_UI1`. Pokud `nSrc` je hodnota 16bitové a **VARTYPE** tohoto objektu je `VT_BOOL`, je ponecháno; jinak hodnota, je nastaven na hodnotu `VT_I2`.  
  
- **Operator = (** `lSrc` **)** zkopíruje 32bitové celé číslo hodnoty do tohoto objektu. Pokud **VARTYPE** tohoto objektu je `VT_ERROR`, je ponecháno; jinak hodnota, je nastaven na hodnotu `VT_I4`.  
  
- **operátor = (** `curSrc` **)** kopie [COleCurrency](../../mfc/reference/colecurrency-class.md) objektu do tento objekt a nastaví **VARTYPE** k `VT_CY`.  
  
- **Operator = (** `fltSrc` **)** zkopíruje hodnotu s plovoucí desetinnou čárkou 32-bit do tento objekt a nastaví **VARTYPE** k `VT_R4`.  
  
- **Operator = (** `dblSrc` **)** zkopíruje hodnotu s plovoucí desetinnou čárkou 64-bit do tento objekt a nastaví **VARTYPE** k `VT_R8`.  
  
- **operátor = (** `dateSrc` **)** kopie [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objektu do tento objekt a nastaví **VARTYPE** k `VT_DATE`.  
  
- **Operator = (** `arrSrc` **)** kopie [CByteArray](../../mfc/reference/cbytearray-class.md) objektu do této `COleVariant` objektu.  
  
- **Operator = (** `lbSrc` **)** kopie [CLongBinary](../../mfc/reference/clongbinary-class.md) objektu do této `COleVariant` objektu.  
  
 Další informace najdete v tématu [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) a [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) položky v sadě Windows SDK.  
  
##  <a name="operator_eq_eq"></a>  COleVariant::operator ==  
 Tento operátor porovná dvě hodnoty typu variant a vrátí nenulové hodnoty v případě, že jsou stejné; jinak 0.  
  
```  
BOOL operator==(const VARIANT& varSrc) const; 
BOOL operator==(LPCVARIANT pSrc) const;
```  
  
##  <a name="operator_lt_lt__gt_gt"></a>  COleVariant::operator &lt; &lt;, &gt;&gt;  
 Výstupy `COleVariant` hodnotu `CArchive` nebo **CdumpContext** a vstup `COleVariant` objektu z `CArchive`.  
  
```  
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,  
    OleVariant varSrc);
 
friend CArchive& AFXAPI operator<<(
    CArchive& ar,  
    COleVariant varSrc);
 
friend CArchive& AFXAPI operator>>(
    CArchive& ar,  
    COleVariant& varSrc);
```  
  
### <a name="remarks"></a>Poznámky  
 `COleVariant` Vložení ( **< \<**) operátor podporuje diagnostiku vypsání a ukládání do archivu. Extrahování ( **>>**) operátor podporuje načítání z archivu.  
  
##  <a name="setstring"></a>  COleVariant::SetString  
 Nastaví pro konkrétní typ řetězec.  
  
```  
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszSrc`  
 Řetězce ukončené hodnotou null zkopírovat do nové `COleVariant` objektu.  
  
 *VtSrc*  
 **VARTYPE** pro nové `COleVariant` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Parametr `vtSrc` musí být `VT_BSTR` (UNICODE) nebo `VT_BSTRT` (ANSI). `SetString` se obvykle používá ke nastavena řetězce na ANSI, protože je výchozí hodnotou [COleVariant::COleVariant](#colevariant) konstruktor s řetězec nebo řetězec ukazatel parametr a ne **VARTYPE** je kódování UNICODE.  
  
 Sady záznamů rozhraní DAO v kódování UNICODE sestavení očekává řetězců, které mají být ANSI. Proto pro rozhraní DAO funkce využívající `COleVariant` objekty, pokud nejsou vytvoření sady záznamů znakové sady UNICODE, je nutné použít **COleVariant::COleVariant (** `lpszSrc` **,** `vtSrc` **)**  formu konstruktor s `vtSrc` nastavena na `VT_BSTRT` (ANSI) nebo použijte `SetString` s `vtSrc` nastavena na `VT_BSTRT` aby řetězců v kódu ANSI. Například `CDaoRecordset` funkce [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) a [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) použít `COleVariant` objektů jako parametry. Tyto objekty musí být ANSI, pokud sady záznamů rozhraní DAO není kódování UNICODE.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



