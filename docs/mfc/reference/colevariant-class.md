---
title: COleVariant – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 41a93a89ed0ace158a0864d7987cafd838eed304
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853738"
---
# <a name="colevariant-class"></a>COleVariant – třída
Zapouzdřuje [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) datového typu.  
  
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
|[COleVariant::Attach](#attach)|Připojí hodnotu typu VARIANT pro `COleVariant`.|  
|[COleVariant::ChangeType](#changetype)|Změní typ variant této `COleVariant` objektu.|  
|[COleVariant::Clear](#clear)|Smaže `COleVariant` objektu.|  
|[COleVariant::Detach](#detach)|Odpojí hodnotu typu VARIANT z `COleVariant` a vrátí typu VARIANT.|  
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Načte pole bajtů z existujícího pole typu variant.|  
|[COleVariant::SetString](#setstring)|Nastaví řetězec pro konkrétní typ, obvykle ANSI.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|Převede `COleVariant` hodnoty do `LPCVARIANT`.|  
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|Převede `COleVariant` objektu do `LPVARIANT`.|  
|[COleVariant::operator =](#operator_eq)|Zkopíruje `COleVariant` hodnotu.|  
|[COleVariant::operator ==](#operator_eq_eq)|Porovná dva `COleVariant` hodnoty.|  
|[COleVariant::operator &lt; &lt;, &gt;&gt;](#operator_lt_lt__gt_gt)|Výstupy `COleVariant` hodnota, která se `CArchive` nebo `CDumpContext` a vstupy `COleVariant` objektu z `CArchive`.|  
  
## <a name="remarks"></a>Poznámky  
 Tento datový typ se používá v automatizace OLE. Konkrétně [DISPPARAMS](http://msdn.microsoft.com/a16e5a21-766e-4287-b039-13429aa78f8b) struktura obsahuje ukazatel na pole typu VARIANT struktur. A `DISPPARAMS` struktura se používá k předání parametrů [IDispatch::Invoke](http://msdn.microsoft.com/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
> [!NOTE]
>  Tato třída je odvozena z `VARIANT` struktury. To znamená, že můžete předat `COleVariant` parametrem, který volá `VARIANT` a datové členy `VARIANT` struktury jsou dostupné datové členy `COleVariant`.  
  
 Dvě třídy MFC související [COleCurrency](../../mfc/reference/colecurrency-class.md) a [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) zapouzdření variant – datové typy měny ( `VT_CY`) data a času ( `VT_DATE`). `COleVariant` Třídy je často používána ve třídách rozhraní DAO, viz tyto třídy pro typická využití této třídy, například [cdaoquerydef –](../../mfc/reference/cdaoquerydef-class.md) a [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 Další informace najdete v tématu [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118), [měny](http://msdn.microsoft.com/5e81273c-7289-45c7-93c0-32c1553f708e), [DISPPARAMS](http://msdn.microsoft.com/a16e5a21-766e-4287-b039-13429aa78f8b), a [IDispatch::Invoke](http://msdn.microsoft.com/964ade8e-9d8a-4d32-bd47-aa678912a54d) položky v sadě Windows SDK.  
  
 Další informace o `COleVariant` třídy a jeho použití v automatizace OLE, naleznete v tématu "Předání parametrů v OLE Automation" v článku [automatizace](../../mfc/automation.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `tagVARIANT`  
  
 `COleVariant`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
  
##  <a name="attach"></a>  COleVariant::Attach  
 Voláním této funkce se připojit daný [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) objektů na aktuální `COleVariant` objektu.  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *varSrc*  
 Existující `VARIANT` objektu, který chcete připojit k aktuální `COleVariant` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nastaví [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) z *varSrc* VT_EMPTY.  
  
 Další informace najdete v tématu [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) a [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) položky v sadě Windows SDK.  
  
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
 Existující `COleVariant` nebo `VARIANT` objektu, které se mají zkopírovat do nové `COleVariant` objektu.  
  
 *pSrc*  
 Ukazatel `VARIANT` objekt, který bude kopírován do nového `COleVariant` objektu.  
  
 *lpszSrc*  
 Řetězec zakončený hodnotou null ke zkopírování do nové `COleVariant` objektu.  
  
 *vtSrc*  
 `VARTYPE` Pro novou `COleVariant` objektu.  
  
 *strSrc*  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu, které se mají zkopírovat do nové `COleVariant` objektu.  
  
 *nSrc*, *lSrc*  
 Číselné hodnoty, které se mají zkopírovat do nové `COleVariant` objektu.  
  
 *vtSrc*  
 `VARTYPE` Pro novou `COleVariant` objektu.  
  
 *curSrc*  
 A [COleCurrency](../../mfc/reference/colecurrency-class.md) objektu, které se mají zkopírovat do nové `COleVariant` objektu.  
  
 *fltSrc*, *dblSrc*  
 Číselné hodnoty, které se mají zkopírovat do nové `COleVariant` objektu.  
  
 *timeSrc*  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objektu, které se mají zkopírovat do nové `COleVariant` objektu.  
  
 *arrSrc*  
 A [CByteArray](../../mfc/reference/cbytearray-class.md) objektu, které se mají zkopírovat do nové `COleVariant` objektu.  
  
 *lbSrc*  
 A [CLongBinary](../../mfc/reference/clongbinary-class.md) objektu, které se mají zkopírovat do nové `COleVariant` objektu.  
  
 *PIDL*  
 Ukazatel [ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321) struktury, které se mají zkopírovat do nové `COleVariant` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tyto konstruktory vytvořit nový `COleVariant` objekty inicializovány na zadanou hodnotu. Následuje stručný popis každého z těchto konstruktorů.  
  
- **() COleVariant** vytvoří prázdnou `COleVariant` objekt VT_EMPTY.  
  
- **COleVariant (** *varSrc* **)** zkopíruje existující `VARIANT` nebo `COleVariant` objektu. Typ varianty se zachová.  
  
- **COleVariant (** `pSrc` **)** zkopíruje existující `VARIANT` nebo `COleVariant` objektu. Typ varianty se zachová.  
  
- **COleVariant (** `lpszSrc` **)** zkopíruje řetězec do nového objektu VT_BSTR (UNICODE).  
  
- **COleVariant (** `lpszSrc` **,** `vtSrc` **)** zkopíruje řetězec do nového objektu. Parametr *vtSrc* musí být VT_BSTR (UNICODE) nebo VT_BSTRT (ANSI).  
  
- **COleVariant (** `strSrc` **)** zkopíruje řetězec do nového objektu VT_BSTR (UNICODE).  
  
- **COleVariant (** `nSrc` **)** zkopíruje do nového objektu VT_UI1 8bitové celé číslo.  
  
- **COleVariant (** `nSrc` **,** `vtSrc` **)** zkopíruje 16bitové celé číslo (nebo logická hodnota) do nového objektu. Parametr *vtSrc* musí být VT_I2 nebo VT_BOOL.  
  
- **COleVariant (** `lSrc` **,** `vtSrc` **)** zkopíruje 32bitové celé číslo (nebo hodnota SCODE) do nového objektu. Parametr *vtSrc* musí být VT_I4, VT_ERROR nebo VT_BOOL.  
  
- **COleVariant (** `curSrc` **)** kopie `COleCurrency` hodnoty do nového objektu VT_CY.  
  
- **COleVariant (** `fltSrc` **)** zkopíruje do nového objektu VT_R4 32bitová hodnota s plovoucí desetinnou čárkou.  
  
- **COleVariant (** `dblSrc` **)** zkopíruje do nového objektu VT_R8 64 bitů hodnotu s plovoucí desetinnou čárkou.  
  
- **COleVariant (** `timeSrc` **)** kopie `COleDateTime` hodnoty do nového objektu VT_DATE.  
  
- **COleVariant (** `arrSrc` **)** kopie `CByteArray` do nového objektu VT_EMPTY objektu.  
  
- **COleVariant (** `lbSrc` **)** kopie `CLongBinary` do nového objektu VT_EMPTY objektu.  
  
 Další informace o SCODE najdete v tématu [struktura kódy chyb COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) v sadě Windows SDK.  
  
##  <a name="changetype"></a>  COleVariant::ChangeType  
 Převede typ variant hodnoty v tomto `COleVariant` objektu.  
  
```  
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *VarType*  
 [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) to `COleVariant` objektu.  
  
 *pSrc*  
 Ukazatel [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) objekt k převodu. Pokud je tato hodnota NULL, to `COleVariant` objekt se používá jako zdroj pro převod.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118), [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4), a [VariantChangeType](http://msdn.microsoft.com/48a51e32-95d7-4eeb-8106-f5043ffa2fd1) položky v sadě Windows SDK.  
  
##  <a name="clear"></a>  COleVariant::Clear  
 Vymaže `VARIANT`.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Tím se nastaví VT_EMPTY VARTYPE pro tento objekt. `COleVariant` Tuto funkci volá destruktor.  
  
 Další informace najdete v tématu `VARIANT`, VARTYPE, a `VariantClear` položky v sadě Windows SDK.  
  
##  <a name="detach"></a>  COleVariant::Detach  
 Odpojí základní [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) objektu z tohoto `COleVariant` objektu.  
  
```  
VARIANT Detach();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nastaví [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) to `COleVariant` objekt VT_EMPTY.  
  
> [!NOTE]
>  Po volání `Detach`, je odpovědností volajícího k volání `VariantClear` na výslednou `VARIANT` struktury.  
  
 Další informace najdete v tématu [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118), [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4), a [VariantClear](http://msdn.microsoft.com/28741d81-8404-4f85-95d3-5c209ec13835) položky v sadě Windows SDK.  
  
##  <a name="getbytearrayfromvariantarray"></a>  COleVariant::GetByteArrayFromVariantArray  
 Načte pole bajtů z existujícího pole typu variant  
  
```  
void GetByteArrayFromVariantArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>Parametry  
 *Bajty*  
 Odkaz na existující [CByteArray](../../mfc/reference/cbytearray-class.md) objektu.  
  
##  <a name="operator_lpcvariant"></a>  COleVariant::operator LPCVARIANT  
 Vrátí tento operátor přetypování `VARIANT` strukturu, jejíž hodnota je zkopírován z tohoto `COleVariant` objektu.  
  
```  
operator LPCVARIANT() const; 
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="operator_lpvariant"></a>  COleVariant::operator LPVARIANT  
 Tento operátor přetypování pro přístup k podkladové volání `VARIANT` strukturu pro to `COleVariant` objektu.  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  Změna hodnoty v `VARIANT` struktura přistupuje vrácený touto funkcí ukazatel se změní hodnota tohoto `COleVariant` objektu.  
  
##  <a name="operator_eq"></a>  COleVariant::operator =  
 Zkopírování těchto přetížených operátorech přiřazení zdrojová hodnota do tohoto `COleVariant` objektu.  
  
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
 Následuje stručný popis jednotlivých operátorů:  
  
- **Operator = (** *varSrc ***)** zkopíruje existující typ VARIANT nebo `COleVariant` objektu do tohoto objektu.  
  
- **Operator = (** `pSrc` **)** zkopíruje objekt VARIANT přistupuje *pSrc* do tohoto objektu.  
  
- **Operator = (** `lpszSrc` **)** zkopíruje do tohoto objektu řetězec zakončený hodnotou null a nastaví VARTYPE VT_BSTR.  
  
- **operátor = (** `strSrc` **)** kopie [CString](../../atl-mfc-shared/reference/cstringt-class.md) do tento objekt a nastaví VARTYPE k VT_BSTR objektu.  
  
- **Operator = (** `nSrc` **)** zkopíruje do tohoto objektu na hodnotu 8 nebo 16bitové celé číslo. Pokud *nSrc* je hodnota 8 bitů, VARTYPE tohoto objektu nastavena na VT_UI1. Pokud *nSrc* je 16bitová hodnota a VARTYPE tohoto objektu je VT_BOOL, je uchované; v opačném případě, že je nastavena na VT_I2.  
  
- **Operator = (** `lSrc` **)** kopíruje hodnotu 32bitového celého čísla do tohoto objektu. Je-li VARTYPE tohoto VT_ERROR, zůstane; v opačném případě je nastavena na VT_I4.  
  
- **operátor = (** `curSrc` **)** kopie [COleCurrency](../../mfc/reference/colecurrency-class.md) do tento objekt a nastaví VARTYPE k VT_CY objektu.  
  
- **Operator = (** `fltSrc` **)** zkopíruje do tohoto objektu 32bitová hodnota s plovoucí desetinnou čárkou a nastaví VARTYPE VT_R4.  
  
- **Operator = (** `dblSrc` **)** kopíruje hodnotu s plovoucí desetinnou čárkou 64-bit na tento objekt a nastaví VARTYPE VT_R8.  
  
- **operátor = (** `dateSrc` **)** kopie [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) do tento objekt a nastaví VARTYPE k VT_DATE objektu.  
  
- **operátor = (** `arrSrc` **)** kopie [CByteArray](../../mfc/reference/cbytearray-class.md) objektu do tohoto `COleVariant` objektu.  
  
- **operátor = (** `lbSrc` **)** kopie [CLongBinary](../../mfc/reference/clongbinary-class.md) objektu do tohoto `COleVariant` objektu.  
  
 Další informace najdete v tématu [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) a [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) položky v sadě Windows SDK.  
  
##  <a name="operator_eq_eq"></a>  COleVariant::operator ==  
 Tento operátor porovná dvě varianty hodnoty a vrátí nenulovou hodnotu, pokud jsou totožné; jinak 0.  
  
```  
BOOL operator==(const VARIANT& varSrc) const; 
BOOL operator==(LPCVARIANT pSrc) const;
```  
  
##  <a name="operator_lt_lt__gt_gt"></a>  COleVariant::operator &lt; &lt;, &gt;&gt;  
 Výstupy `COleVariant` hodnota, která se `CArchive` nebo `CdumpContext` a vstupy `COleVariant` objektu z `CArchive`.  
  
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
 `COleVariant` Vložení ( **< \<**) – operátor podporuje diagnostiku vypsání a ukládání do archivu. Extrakce ( **>>**) – operátor podporuje načítání z archivu.  
  
##  <a name="setstring"></a>  COleVariant::SetString  
 Nastaví řetězec do určitého typu.  
  
```  
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSrc*  
 Řetězec zakončený hodnotou null ke zkopírování do nové `COleVariant` objektu.  
  
 *vtSrc*  
 VARTYPE pro novou `COleVariant` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Parametr *vtSrc* musí být VT_BSTR (UNICODE) nebo VT_BSTRT (ANSI). `SetString` se obvykle používá k sadu řetězců na ANSI, protože výchozí hodnota pro [COleVariant::COleVariant](#colevariant) konstruktor s řetězci nebo parametr ukazatel na řetězec a žádné VARTYPE je kódování UNICODE.  
  
 Sady záznamů rozhraní DAO v kódování UNICODE sestavení očekává, že řetězců, které mají být ANSI. Proto pro rozhraní DAO funkcí, které používají `COleVariant` objektů, pokud nevytváříte sady záznamů ve formátu UNICODE, je nutné použít **COleVariant::COleVariant (** `lpszSrc` **,** `vtSrc` **)**  formu konstruktor s *vtSrc* nastavit VT_BSTRT (ANSI) nebo použít `SetString` s *vtSrc* nastavený na VT_BSTRT abyste měli řetězců v kódu ANSI. Například `CDaoRecordset` funkce [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) a [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) použít `COleVariant` objektů jako parametry. Tyto objekty musí být ANSI, pokud není sada záznamů rozhraní DAO kódování UNICODE.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



