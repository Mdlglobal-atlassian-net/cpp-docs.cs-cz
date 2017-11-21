---
title: "Třída COleSafeArray | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c703ecd53b8c74c44d13a67013313cbc816e67d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="colesafearray-class"></a>COleSafeArray – třída
Třída pro práci s poli libovolného typu a dimenze.  
  
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
|[COleSafeArray::AccessData](#accessdata)|Načte ukazatel na pole data.|  
|[COleSafeArray::AllocData](#allocdata)|Přidělí paměť pro pole.|  
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Pro bezpečné pole popisovač přidělí paměť.|  
|[COleSafeArray::Attach](#attach)|Umožňuje řízení existující **VARIANT** pole na `COleSafeArray` objektu.|  
|[COleSafeArray::Clear](#clear)|Uvolní všechna data v základní **VARIANT**.|  
|[COleSafeArray::Copy](#copy)|Vytvoří kopii existující pole.|  
|[COleSafeArray::Create](#create)|Vytvoří bezpečným polím.|  
|[COleSafeArray::CreateOneDim](#createonedim)|Vytvoří jednorozměrné `COleSafeArray` objektu.|  
|[COleSafeArray::Destroy](#destroy)|Zničí existující pole.|  
|[COleSafeArray::DestroyData](#destroydata)|Zničí data v bezpečným polím.|  
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Zničí popisovač bezpečným polím.|  
|[COleSafeArray::Detach](#detach)|Umožňuje odpojit **VARIANT** pole z `COleSafeArray` objektu (tak, aby neuvolní data).|  
|[COleSafeArray::GetByteArray](#getbytearray)|Zkopíruje obsah do zabezpečené pole [CByteArray](../../mfc/reference/cbytearray-class.md).|  
|[COleSafeArray::GetDim](#getdim)|Vrátí počet dimenzí v poli.|  
|[COleSafeArray::GetElement](#getelement)|Načte jediným elementem pole bezpečné.|  
|[COleSafeArray::GetElemSize](#getelemsize)|Vrátí velikost v bajtech jeden element ve bezpečným polím.|  
|[COleSafeArray::GetLBound](#getlbound)|Vrátí dolní hranice pro všechny dimenze bezpečným polím.|  
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Vrátí počet prvků v jednorozměrná `COleSafeArray` objektu.|  
|[COleSafeArray::GetUBound](#getubound)|Vrátí horní mez pro všechny dimenze bezpečným polím.|  
|[COleSafeArray::Lock](#lock)|Zvětší počet zámku pole a umístí ukazatel na pole data v popisovači pole.|  
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Vrací ukazatel na indexované elementu.|  
|[COleSafeArray::PutElement](#putelement)|Do pole přiřadí jediným elementem.|  
|[COleSafeArray::Redim](#redim)|Změní nejméně významný (nejvíce vpravo) mez bezpečným polím.|  
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Změní počet elementů ve jednorozměrné `COleSafeArray` objektu.|  
|[COleSafeArray::UnaccessData](#unaccessdata)|Snižuje počet pole zámek a zruší platnost ukazatele načíst `AccessData`.|  
|[COleSafeArray::Unlock](#unlock)|Snižuje zámek počet pole, může být uvolněno nebo ke změně velikosti.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|Přistupuje k základní **VARIANT** struktura `COleSafeArray` objektu.|  
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|Přistupuje k základní **VARIANT** struktura `COleSafeArray` objektu.|  
|[COleSafeArray::operator =](#operator_eq)|Zkopíruje hodnoty do `COleSafeArray` objektu ( **SAFEARRAY**, **VARIANT**, `COleVariant`, nebo `COleSafeArray` pole).|  
|[COleSafeArray::operator ==](#operator_eq_eq)|Porovná dvě pole typu variant ( **SAFEARRAY**, **VARIANT**, `COleVariant`, nebo `COleSafeArray` pole).|  
|[COleSafeArray::operator&lt;&lt;](#operator_lt_lt)|Vypíše obsah `COleSafeArray` objektu v kontextu výpis.|  
  
## <a name="remarks"></a>Poznámky  
 `COleSafeArray`odvozená z OLE **VARIANT** struktura. OLE **SAFEARRAY** členské funkce jsou k dispozici prostřednictvím `COleSafeArray`, stejně jako sada členských funkcí, které jsou vytvořené speciálně pro jednorozměrná pole bajtů.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `tagVARIANT`  
  
 `COleSafeArray`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
  
##  <a name="accessdata"></a>COleSafeArray::AccessData  
 Načte ukazatel na pole data.  
  
```  
void AccessData(void** ppvData);
```  
  
### <a name="parameters"></a>Parametry  
 `ppvData`  
 Ukazatel na ukazatel na pole data.  
  
### <a name="remarks"></a>Poznámky  
 V případě chyby, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]  
  
##  <a name="allocdata"></a>COleSafeArray::AllocData  
 Pro bezpečné pole přidělí paměť.  
  
```  
void AllocData();
```  
  
### <a name="remarks"></a>Poznámky  
 V případě chyby, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="allocdescriptor"></a>COleSafeArray::AllocDescriptor  
 Přidělí paměť pro popisovač bezpečným polím.  
  
```  
void AllocDescriptor(DWORD dwDims);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDims`  
 Počet dimenzí v zabezpečené pole.  
  
### <a name="remarks"></a>Poznámky  
 V případě chyby, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="attach"></a>COleSafeArray::Attach  
 Poskytuje kontrolu nad daty v existující **VARIANT** pole na `COleSafeArray` objektu.  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *varSrc*  
 A **VARIANT** objektu. *VarSrc* parametr musí mít [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)**VT_ARRAY**.  
  
### <a name="remarks"></a>Poznámky  
 Zdroj **VARIANT**je typ nastaven na `VT_EMPTY`. Tato funkce vymaže data aktuálního pole, pokud existuje.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [COleSafeArray::AccessData](#accessdata).  
  
##  <a name="clear"></a>COleSafeArray::Clear  
 Vymaže bezpečným polím.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Funkce vymaže bezpečným polím nastavením `VARTYPE` objektu `VT_EMPTY`. Aktuální obsah se a je vydání pole.  
  
##  <a name="colesafearray"></a>COleSafeArray::COleSafeArray  
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
 `saSrc`  
 Existující `COleSafeArray` objekt nebo **SAFEARRAY** zkopírovat do nové `COleSafeArray` objektu.  
  
 `vtSrc`  
 **VARTYPE** nový `COleSafeArray` objektu.  
  
 `psaSrc`  
 Ukazatel **SAFEARRAY** zkopírovat do nové `COleSafeArray` objektu.  
  
 *varSrc*  
 Existující **VARIANT** nebo `COleVariant` objekt, který má být zkopírován do nové `COleSafeArray` objektu.  
  
 `pSrc`  
 Ukazatel **VARIANT** objekt, který má být zkopírován do nové `COleSafeArray` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Všechny tyto konstruktory vytvořit nový `COleSafeArray` objekty. Pokud neexistuje žádný parametr prázdnou `COleSafeArray` je vytvořen objekt ( `VT_EMPTY`). Pokud `COleSafeArray` zkopírováno z jiného pole, jehož [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) se implicitně označuje ( `COleSafeArray`, `COleVariant`, nebo **VARIANT**), **VARTYPE** z zdrojové pole se zachovává a není nutné zadávat. Pokud `COleSafeArray` zkopírováno z jiného pole, jehož **VARTYPE** nezná ( **SAFEARRAY**), **VARTYPE** musí být zadány v `vtSrc` parametr.  
  
 V případě chyby, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="copy"></a>COleSafeArray::Copy  
 Vytvoří kopii existující bezpečným polím.  
  
```  
void Copy(LPSAFEARRAY* ppsa);
```  
  
### <a name="parameters"></a>Parametry  
 *ppsa*  
 Ukazatel na umístění, do které chcete vrátit nový popisovač pole.  
  
### <a name="remarks"></a>Poznámky  
 V případě chyby, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="create"></a>COleSafeArray::Create  
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
 `vtSrc`  
 Základní typ pole (který je **VARTYPE** jednotlivých prvků pole). **VARTYPE** je omezen na podmnožinu typy variant. Ani **VT_ARRAY** ani **VT_BYREF** může být nastaven příznak. `VT_EMPTY`a **VT_NULL** nejsou platné základní typy pro pole. Všechny ostatní typy jsou právní.  
  
 `dwDims`  
 Počet dimenzí v poli. To se dá změnit po vytvoření pole s [Redim](#redim).  
  
 *rgElements*  
 Ukazatel na pole počet elementů pro Každá dimenze v poli.  
  
 *rgsabounds*  
 Ukazatel na vektoru mezí (jeden pro každou dimenzi) přidělit pro pole.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vymaže data aktuálního pole v případě potřeby. V případě chyby, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="createonedim"></a>COleSafeArray::CreateOneDim  
 Vytvoří novou jednorozměrné `COleSafeArray` objektu.  
  
```  
void CreateOneDim(
    VARTYPE vtSrc,  
    DWORD dwElements,  
    const void* pvSrcData = NULL,  
    long nLBound = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `vtSrc`  
 Základní typ pole (který je **VARTYPE** jednotlivých prvků pole).  
  
 `dwElements`  
 Počet prvků v poli. To se dá změnit po vytvoření pole s [ResizeOneDim](#resizeonedim).  
  
 `pvSrcData`  
 Ukazatel na data chcete zkopírovat do pole.  
  
 *nLBound*  
 Dolní mez pole.  
  
### <a name="remarks"></a>Poznámky  
 Funkce přiděluje a inicializuje data pro toto pole kopírování zadaná data, pokud je ukazatel `pvSrcData` není **NULL**.  
  
 V případě chyby, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]  
  
##  <a name="destroy"></a>COleSafeArray::Destroy  
 Zničí popisovač existující pole a všechna data v poli.  
  
```  
void Destroy();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou objekty uložené v poli, každý objekt vydání. V případě chyby, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="destroydata"></a>COleSafeArray::DestroyData  
 Zničí všechna data v bezpečným polím.  
  
```  
void DestroyData();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou objekty uložené v poli, každý objekt vydání. V případě chyby, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="destroydescriptor"></a>COleSafeArray::DestroyDescriptor  
 Zničí popisovač bezpečným polím.  
  
```  
void DestroyDescriptor();
```  
  
### <a name="remarks"></a>Poznámky  
 V případě chyby, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="detach"></a>COleSafeArray::Detach  
 Umožňuje odpojit **VARIANT** data z `COleSafeArray` objektu.  
  
```  
VARIANT Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Základní **VARIANT** hodnotu `COleSafeArray` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Funkce odpojí data v bezpečným polím nastavením [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) objektu `VT_EMPTY`. Je zodpovědností volajícího k bezplatným pole voláním funkce systému Windows [VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835).  
  
 V případě chyby, funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [COleSafeArray::PutElement](#putelement).  
  
##  <a name="getbytearray"></a>COleSafeArray::GetByteArray  
 Zkopíruje obsah do zabezpečené pole `CByteArray`.  
  
```  
void GetByteArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>Parametry  
 `bytes`  
 Odkaz na [CByteArray](../../mfc/reference/cbytearray-class.md) objektu.  
  
##  <a name="getdim"></a>COleSafeArray::GetDim  
 Vrátí počet dimenzí v `COleSafeArray` objektu.  
  
```  
DWORD GetDim();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet dimenzí v zabezpečené pole.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="getelement"></a>COleSafeArray::GetElement  
 Načte jediným elementem pole bezpečné.  
  
```  
void GetElement(
    long* rgIndices,  
    void* pvData);
```  
  
### <a name="parameters"></a>Parametry  
 `rgIndices`  
 Ukazatel na pole indexů pro Každá dimenze pole.  
  
 `pvData`  
 Ukazatel na umístění pro element pole.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce automaticky volání funkce windows `SafeArrayLock` a `SafeArrayUnlock` před a po načtení elementu. Pokud datový prvek je řetězec, objekt nebo typ variant, funkce zkopíruje element správným způsobem. Parametr `pvData` by měla odkazovat na velké nedostatek vyrovnávací paměti tak, aby obsahovala elementu.  
  
 V případě chyby, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]  
  
##  <a name="getelemsize"></a>COleSafeArray::GetElemSize  
 Získá velikost elementu v `COleSafeArray` objektu.  
  
```  
DWORD GetElemSize();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost v bajtech, elementů bezpečným polím.  
  
##  <a name="getlbound"></a>COleSafeArray::GetLBound  
 Vrátí dolní mez pro všechny dimenze `COleSafeArray` objektu.  
  
```  
void GetLBound(
    DWORD dwDim,  
    long* pLBound);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDim`  
 Rozměry pole, pro které chcete získat dolní hranice.  
  
 *pLBound*  
 Ukazatel na umístění, které chcete vrátit dolní hranice.  
  
### <a name="remarks"></a>Poznámky  
 V případě chyby, funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]  
  
##  <a name="getonedimsize"></a>COleSafeArray::GetOneDimSize  
 Vrátí počet prvků v jednorozměrná `COleSafeArray` objektu.  
  
```  
DWORD GetOneDimSize();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů v jednorozměrné pole bezpečné.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [COleSafeArray::CreateOneDim](#createonedim).  
  
##  <a name="getubound"></a>COleSafeArray::GetUBound  
 Vrátí horní mez pro všechny dimenze bezpečným polím.  
  
```  
void GetUBound(
    DWORD dwDim,  
    long* pUBound);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDim`  
 Rozměry pole, pro které chcete získat horní mez.  
  
 *pUBound*  
 Ukazatel na umístění, které chcete vrátit horní mez.  
  
### <a name="remarks"></a>Poznámky  
 V případě chyby, funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]  
  
##  <a name="lock"></a>COleSafeArray::Lock  
 Zvýší počet zámek pole a umístěte ukazatel na pole data v popisovači pole.  
  
```  
void Lock();
```  
  
### <a name="remarks"></a>Poznámky  
 V případě chyby, vyvolá [COleException](../../mfc/reference/coleexception-class.md).  
  
 Ukazatele v popisovači pole je platný do `Unlock` je volána. Volání `Lock` mohou být vnořené; stejný počet volání `Unlock` jsou povinné.  
  
 Pole nelze odstranit, pokud je uzamčena.  
  
##  <a name="operator_lpcvariant"></a>COleSafeArray::operator LPCVARIANT  
 Volání tento operátor přetypování pro přístup k základní **VARIANT** struktury pro tuto `COleSafeArray` objektu.  
  
```  
operator LPCVARIANT() const;  
```  
  
##  <a name="operator_lpvariant"></a>COleSafeArray::operator LPVARIANT  
 Volání tento operátor přetypování pro přístup k základní **VARIANT** struktury pro tuto `COleSafeArray` objektu.  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že změna hodnoty v **VARIANT** struktura přístup ukazatele, vrátí tato funkce se změní hodnota této `COleSafeArray` objektu.  
  
##  <a name="operator_eq"></a>COleSafeArray::operator =  
 Tyto operátory přetížené přiřazení zkopírujte zdrojové hodnoty do této `COleSafeArray` objektu.  
  
```  
COleSafeArray& operator=(const COleSafeArray& saSrc);  
COleSafeArray& operator=(const VARIANT& varSrc);  
  COleSafeArray& operator=(LPCVARIANT pSrc);  
COleSafeArray& operator=(const COleVariant& varSrc);
```  
  
### <a name="remarks"></a>Poznámky  
 Následuje stručný popis jednotlivých operátor:  
  
- **Operator = (** *saSrc* **)** zkopíruje existující `COleSafeArray` objektu do tohoto objektu.  
  
- **Operator = (** *varSrc***)** zkopíruje existující **VARIANT** nebo `COleVariant` pole do tohoto objektu.  
  
- **Operator = (** `pSrc` **)** kopie **VARIANT** array – objekt přístup `pSrc` do tohoto objektu.  
  
##  <a name="operator_eq_eq"></a>COleSafeArray::operator ==  
 Tento operátor porovná dvě pole ( **SAFEARRAY**, **VARIANT**, `COleVariant`, nebo `COleSafeArray` pole) a vrátí nenulové hodnoty v případě, že jsou stejné; jinak hodnota 0.  
  
```  
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;  
   
BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;  
   
BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;  ```  
  
### Remarks  
 Two arrays are equal if they have an equal number of dimensions, equal size in each dimension, and equal element values.  
  
##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;  
 The `COleSafeArray` insertion (<<) operator supports diagnostic dumping and storing of a `COleSafeArray` object to an archive.  
  
```  
Operátor CDumpContext & AFXAPI << (CDumpContext & řadiče domény,  
    COleSafeArray & saSrc);
```  
  
##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex  
 Returns a pointer to the element specified by the index values.  
  
```  
void PtrOfIndex (dlouho * rgIndices,  
    void ** ppvData);
```  
  
### Parameters  
 `rgIndices`  
 An array of index values that identify an element of the array. All indexes for the element must be specified.  
  
 `ppvData`  
 On return, pointer to the element identified by the values in `rgIndices`.  
  
##  <a name="putelement"></a>  COleSafeArray::PutElement  
 Assigns a single element into the array.  
  
```  
void PutElement (dlouho * rgIndices,  
    void * pvData);
```  
  
### Parameters  
 `rgIndices`  
 Pointer to an array of indexes for each dimension of the array.  
  
 `pvData`  
 Pointer to the data to assign to the array. **VT_DISPATCH**, **VT_UNKNOWN**, and `VT_BSTR` variant types are pointers and do not require another level of indirection.  
  
### Remarks  
 This function automatically calls the Windows functions [SafeArrayLock](https://msdn.microsoft.com/library/windows/desktop/ms221492.aspx) and [SafeArrayUnlock](https://msdn.microsoft.com/library/windows/desktop/ms221246.aspx) before and after assigning the element. If the data element is a string, object, or variant, the function copies it correctly, and if the existing element is a string, object, or variant, it is cleared correctly.  
  
 Note that you can have multiple locks on an array, so you can put elements into an array while the array is locked by other operations.  
  
 On error, the function throws a [CMemoryException](../../mfc/reference/cmemoryexception-class.md) or [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
 [!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]  
  
##  <a name="redim"></a>  COleSafeArray::Redim  
 Changes the least significant (rightmost) bound of a safe array.  
  
```  
Redim void (SAFEARRAYBOUND * psaboundNew);
```  
  
### Parameters  
 *psaboundNew*  
 Pointer to a new safe array bound structure containing the new array bound. Only the least significant dimension of an array may be changed.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim  
 Changes the number of elements in a one-dimensional `COleSafeArray` object.  
  
```  
void ResizeOneDim (DWORD dwElements);
```  
  
### Parameters  
 `dwElements`  
 Number of elements in the one-dimensional safe array.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::CreateOneDim](#createonedim).  
  
##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData  
 Decrements the lock count of an array and invalidates the pointer retrieved by `AccessData`.  
  
```  
void UnaccessData();
```  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::AccessData](#accessdata).  
  
##  <a name="unlock"></a>  COleSafeArray::Unlock  
 Decrements the lock count of an array so it can be freed or resized.  
  
```  
void Unlock();
```  
  
### Remarks  
 This function is called after access to the data in an array is finished. On error, it throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
## See Also  
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)
