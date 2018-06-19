---
title: Třída CComSafeArray | Microsoft Docs
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
ms.openlocfilehash: 1c7c4e0603d70513194f8672752ec704011e8326
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366520"
---
# <a name="ccomsafearray-class"></a>CComSafeArray – třída
Tato třída je obálka pro **SAFEARRAY** struktura.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat se neukládají v poli.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSafeArray::CComSafeArray](#ccomsafearray)|Konstruktor|  
|[CComSafeArray:: ~ CComSafeArray](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSafeArray::Add](#add)|Přidá jeden či více elementů, nebo **SAFEARRAY** do struktury `CComSafeArray`.|  
|[CComSafeArray::Attach](#attach)|Připojí **SAFEARRAY** struktury k `CComSafeArray` objektu.|  
|[CComSafeArray::CopyFrom](#copyfrom)|Zkopíruje obsah **SAFEARRAY** struktury do `CComSafeArray` objektu.|  
|[CComSafeArray::CopyTo](#copyto)|Vytvoří kopii `CComSafeArray` objektu.|  
|[CComSafeArray::Create](#create)|Vytvoří `CComSafeArray` objektu.|  
|[CComSafeArray::Destroy](#destroy)|Zničí `CComSafeArray` objektu.|  
|[CComSafeArray::Detach](#detach)|Umožňuje odpojit **SAFEARRAY** z `CComSafeArray` objektu.|  
|[CComSafeArray::GetAt](#getat)|Načte jeden prvek z jednorozměrná pole.|  
|[CComSafeArray::GetCount](#getcount)|Vrátí počet prvků v poli.|  
|[CComSafeArray::GetDimensions](#getdimensions)|Vrátí počet dimenzí v poli.|  
|[CComSafeArray::GetLowerBound](#getlowerbound)|Vrátí dolní mez pro daný dimenze pole.|  
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Vrátí adresu `m_psa` – datový člen.|  
|[CComSafeArray::GetType](#gettype)|Vrátí typ dat uložených v poli.|  
|[CComSafeArray::GetUpperBound](#getupperbound)|Vrátí horní mez pro všechny dimenze pole.|  
|[CComSafeArray::IsSizable](#issizable)|Pokud testy `CComSafeArray` objektu můžete změnit.|  
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Načte jeden prvek z multidimenzionálního pole.|  
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|Nastaví hodnotu elementu v multidimenzionálního pole.|  
|[CComSafeArray::Resize](#resize)|Změní velikost `CComSafeArray` objektu.|  
|[CComSafeArray::SetAt](#setat)|Nastaví hodnotu elementu v jednorozměrná pole.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|Vrhá hodnota **SAFEARRAY** ukazatel.|  
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Načte z pole elementu.|  
|[CComSafeArray::operator =](#operator_eq)|Operátor přiřazení.|  

  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSafeArray::m_psa](#m_psa)|Tento člen dat obsahuje adresu **SAFEARRAY** struktura.|  
  
## <a name="remarks"></a>Poznámky  
 `CComSafeArray` poskytuje obálku pro [SAFEARRAY datový typ](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e) třídy, což představuje jednoduché k vytváření a správě jednoho a multidimenzionální pole téměř všechny typy podporovaných VARIANT.  
  
 `CComSafeArray` zjednodušuje předávání polí mezi procesy a kromě toho poskytuje další bezpečnostní kontrolou hodnoty indexu pole s horní a dolní meze.  
  
 Dolní mez `CComSafeArray` můžete spustit na jakékoli hodnotu definovanou uživatelem, ale, má pole, které jsou přístupné prostřednictvím C++ pomocí dolní mez 0. Další jazyky, jako je například jazyka Visual Basic mohou používat ostatní ohraničující hodnoty (například -10 až 10).  
  
 Použití [CComSafeArray::Create](#create) k vytvoření `CComSafeArray` objekt, a [CComSafeArray::Destroy](#destroy) ho odstranit.  
  
 A `CComSafeArray` může obsahovat následující podmnožinu VARIANT datových typů:  
  
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
|VT_DECIMAL|Decimal ukazatele|  
|VT_VARIANT|variant ukazatele|  
|VT_CY|Měna – datový typ|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsafe.h  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]  
  
##  <a name="add"></a>  CComSafeArray::Add  
 Přidá jeden či více elementů, nebo **SAFEARRAY** do struktury `CComSafeArray`.  
  
```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `psaSrc`  
 Ukazatel **SAFEARRAY** objektu.  
  
 `ulCount`  
 Počet objektů, které chcete přidat do pole.  
  
 *PT*  
 Ukazatel na jeden nebo více objektů, které mají být přidány do pole.  
  
 *t*  
 Odkaz na objekt, který má být přidán do pole.  
  
 `bCopy`  
 Určuje, zda má být vytvořena kopie data. Výchozí hodnota je **TRUE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Nové objekty, které se připojují na konci existující **SAFEARRAY** objektu. Přidávání objektů do multidimenzionální **SAFEARRAY** objekt není podporován. Při přidávání existující pole objektů, obě pole musí obsahovat elementy stejného typu.  
  
 `bCopy` Příznak je vzít v úvahu při elementy typu `BSTR` nebo **VARIANT** jsou přidány do pole. Výchozí hodnota **TRUE** zajistí, že o novou kopii přišla dat bude prvek přidán na pole.  
  
##  <a name="attach"></a>  CComSafeArray::Attach  
 Připojí **SAFEARRAY** struktury k `CComSafeArray` objektu.  
  
```
HRESULT Attach(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `psaSrc`  
 Ukazatel **SAFEARRAY** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Připojí **SAFEARRAY** struktury k `CComSafeArray` objekt, což existující `CComSafeArray` metody, které jsou k dispozici.  
  
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
 `bound`  
 A **SAFEARRAYBOUND** struktury.  
  
 `ulCount`  
 Počet prvků v poli.  
  
 `lLBound`  
 Hodnotu parametru dolní mez. To znamená, index první prvek v poli.  
  
 `pBound`  
 Ukazatel **SAFEARRAYBOUND** struktury.  
  
 `uDims`  
 Počet dimenzí v poli.  
  
 `saSrc`  
 Odkaz na **SAFEARRAY** struktura nebo `CComSafeArray` objektu. V obou případech konstruktoru používá tento odkaz kopii pole, takže pole neodkazuje po konstrukce.  
  
 `psaSrc`  
 Ukazatel **SAFEARRAY** struktura. Konstruktor používá tuto adresu k vytvoření kopie pole, takže pole neodkazuje po konstrukce.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří `CComSafeArray` objektu.  
  
##  <a name="dtor"></a>  CComSafeArray:: ~ CComSafeArray  
 Destruktor.  
  
```
~CComSafeArray() throw()
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="copyfrom"></a>  CComSafeArray::CopyFrom  
 Zkopíruje obsah **SAFEARRAY** struktury do `CComSafeArray` objektu.  
  
```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>Parametry  
 `ppArray`  
 Ukazatel **SAFEARRAY** ke kopírování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zkopíruje obsah **SAFEARRAY** do aktuální `CComSafeArray` objektu. Jsou nahradit existující obsah pole.  
  
##  <a name="copyto"></a>  CComSafeArray::CopyTo  
 Vytvoří kopii `CComSafeArray` objektu.  
  
```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>Parametry  
 `ppArray`  
 Ukazatel na umístění, do kterého chcete-li vytvořit nové **SAFEARRAY**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zkopíruje obsah `CComSafeArray` objektu do **SAFEARRAY** struktura.  
  
##  <a name="create"></a>  CComSafeArray::Create  
 Vytvoří `CComSafeArray`.  
  
```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pBound`  
 Ukazatel **SAFEARRAYBOUND** objektu.  
  
 `uDims`  
 Počet dimenzí v poli.  
  
 `ulCount`  
 Počet prvků v poli.  
  
 `lLBound`  
 Hodnotu parametru dolní mez. To znamená, index první prvek v poli.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 A `CComSafeArray` objekt můžete vytvořit z existující **SAFEARRAYBOUND** strukturu a počet dimenzí, nebo zadáním počet prvků v poli a dolní hranice. Pokud toto pole je přístupná z Visual C++, musí být dolní hranice 0. Další jazyky může povolit jiné hodnoty pro dolní hranice (například Visual Basic podporuje pole u elementů s rozsahem například -10 až 10).  
  
##  <a name="destroy"></a>  CComSafeArray::Destroy  
 Zničí `CComSafeArray` objektu.  
  
```
HRESULT Destroy();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Zničí existující `CComSafeArray` objekt a všechna data obsahuje.  
  
##  <a name="detach"></a>  CComSafeArray::Detach  
 Umožňuje odpojit **SAFEARRAY** z `CComSafeArray` objektu.  
  
```
LPSAFEARRAY Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel **SAFEARRAY** objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje odpojit **SAFEARRAY** objektu z `CComSafeArray` objektu.  
  
##  <a name="getat"></a>  CComSafeArray::GetAt  
 Načte jeden prvek z jednorozměrná pole.  
  
```
T& GetAt(LONG lIndex) const;
```  
  
### <a name="parameters"></a>Parametry  
 `lIndex`  
 Číslo index hodnoty v poli vrátit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na element požadované pole.  
  
##  <a name="getcount"></a>  CComSafeArray::GetCount  
 Vrátí počet prvků v poli.  
  
```
ULONG GetCount(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `uDim`  
 Rozměry pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet prvků v poli.  
  
### <a name="remarks"></a>Poznámky  
 Při použití s multidimenzionálního pole, tato metoda vrátí počet prvků v určité dimenze.  
  
##  <a name="getdimensions"></a>  CComSafeArray::GetDimensions  
 Vrátí počet dimenzí v poli.  
  
```
UINT GetDimensions() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet dimenzí v poli.  
  
##  <a name="getlowerbound"></a>  CComSafeArray::GetLowerBound  
 Vrátí dolní mez pro daný dimenze pole.  
  
```
LONG GetLowerBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `uDim`  
 Rozměry pole, pro které chcete získat dolní hranice. Pokud tento parametr vynechán, výchozí hodnota je 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí dolní hranice.  
  
### <a name="remarks"></a>Poznámky  
 Pokud dolní mez 0, znamená to C jako pole, jehož prvním prvkem je element číslo 0. V případě chyby, například dimenze neplatný argument, tato metoda volá `AtlThrow` s HRESULT popisující chybu.  
  
##  <a name="getsafearrayptr"></a>  CComSafeArray::GetSafeArrayPtr  
 Vrátí adresu `m_psa` – datový člen.  
  
```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel [CComSafeArray::m_psa](#m_psa) – datový člen.  
  
##  <a name="gettype"></a>  CComSafeArray::GetType  
 Vrátí typ dat uložených v poli.  
  
```
VARTYPE GetType() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí typ dat uložených v poli, což může být jedno z následujících typů:  
  
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
|VT_DECIMAL|Decimal ukazatele|  
|VT_VARIANT|variant ukazatele|  
|VT_CY|Měna – datový typ|  
  
##  <a name="getupperbound"></a>  CComSafeArray::GetUpperBound  
 Vrátí horní mez pro všechny dimenze pole.  
  
```
LONG GetUpperBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `uDim`  
 Rozměry pole, pro které chcete získat horní mez. Pokud tento parametr vynechán, výchozí hodnota je 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí horní mez. Tato hodnota je (včetně) maximální platný index pro tato dimenze.  
  
### <a name="remarks"></a>Poznámky  
 V případě chyby, například dimenze neplatný argument, tato metoda volá `AtlThrow` s HRESULT popisující chybu.  
  
##  <a name="issizable"></a>  CComSafeArray::IsSizable  
 Pokud testy `CComSafeArray` objektu můžete změnit.  
  
```
bool IsSizable() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud `CComSafeArray` jde změnit, **false** pokud ji nelze.  
  
##  <a name="m_psa"></a>  CComSafeArray::m_psa  
 Obsahuje adresu **SAFEARRAY** struktura získat přístup.  
  
```
LPSAFEARRAY m_psa;
```  
  
##  <a name="multidimgetat"></a>  CComSafeArray::MultiDimGetAt  
 Načte jeden prvek z multidimenzionálního pole.  
  
```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```  
  
### <a name="parameters"></a>Parametry  
 `alIndex`  
 Ukazatel na vektor indexů pro Každá dimenze v poli. Je krajní levá (nejvýznamnějších) dimenze `alIndex[0]`.  
  
 *t*  
 Vrátí odkaz na data.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="multidimsetat"></a>  CComSafeArray::MultiDimSetAt  
 Nastaví hodnotu elementu v multidimenzionálního pole.  
  
```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```  
  
### <a name="parameters"></a>Parametry  
 `alIndex`  
 Ukazatel na vektor indexů pro Každá dimenze v poli. Úplně vpravo (nejméně významný) dimenze je `alIndex`[0].  
  
 *T*  
 Určuje hodnotu nového elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Toto je multidimenzionální verze [CComSafeArray::SetAt](#setat).  
  
##  <a name="operator_at"></a>  CComSafeArray::operator \[\]  
 Načte z pole elementu.  
  
```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```  
  
### <a name="parameters"></a>Parametry  
 *Index, nIndex*  
 Index počet požadovaný element v poli.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí element příslušná pole.  
  
### <a name="remarks"></a>Poznámky  
 Podobné funkce, která se provede [CComSafeArray::GetAt](#getat), ale tento operátor pracuje pouze s jednorozměrná pole.  
  
##  <a name="operator_eq"></a>  CComSafeArray::operator =  
 Operátor přiřazení.  
  
```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `saSrc`  
 Odkaz na `CComSafeArray` objektu.  
  
 `psaSrc`  
 Ukazatel **SAFEARRAY** objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí typ dat uložených v poli.  
  
##  <a name="operator_lpsafearray"></a>  CComSafeArray::operator LPSAFEARRAY  
 Vrhá hodnota **SAFEARRAY** ukazatel.  
  
```
operator LPSAFEARRAY() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrhá hodnota **SAFEARRAY** ukazatel.  
  
##  <a name="resize"></a>  CComSafeArray::Resize  
 Změní velikost `CComSafeArray` objektu.  
  
```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pBound`  
 Ukazatel **SAFEARRAYBOUND** struktura, která obsahuje informace o počet elementů a dolní mez pole.  
  
 `ulCount`  
 Požadovaný počet objektů v poli změněnou velikostí.  
  
 `lLBound`  
 Dolní mez.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda pouze změní nejvíce vpravo dimenze. Ho nebude změnit velikost pole, které vracejí **IsResizable** jako **false**.  
  
##  <a name="setat"></a>  CComSafeArray::SetAt  
 Nastaví hodnotu elementu v jednorozměrná pole.  
  
```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lIndex`  
 Číslo indexu pole elementu, který chcete nastavit.  
  
 *t*  
 Nová hodnota zadaného elementu.  
  
 `bCopy`  
 Určuje, zda má být vytvořena kopie data. Výchozí hodnota je **TRUE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 `bCopy` Příznak je vzít v úvahu při elementy typu `BSTR` nebo **VARIANT** jsou přidány do pole. Výchozí hodnota **TRUE** zajistí, že o novou kopii přišla dat bude prvek přidán na pole.  
  
## <a name="see-also"></a>Viz také  
 [SAFEARRAY datový typ](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e)   
 [CComSafeArray::Create](#create)   
 [CComSafeArray::Destroy](#destroy)   
 [Přehled třídy](../../atl/atl-class-overview.md)
