---
title: CComPtrBase – třída
ms.date: 11/04/2016
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
ms.openlocfilehash: 689221ec77b21fc8bfaed2e929aee5402a4bc676
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496978"
---
# <a name="ccomptrbase-class"></a>CComPtrBase – třída

Tato třída poskytuje základ pro třídy inteligentních ukazatelů pomocí rutin paměti založených na modelu COM.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu, na který se má odkazovat inteligentní ukazatel

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComPtrBase:: ~ CComPtrBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComPtrBase:: Advise](#advise)|Voláním této metody vytvoříte připojení mezi `CComPtrBase`spojovacím bodem a jímkou klienta.|
|[CComPtrBase:: Attach](#attach)|Voláním této metody převezmete vlastnictví existujícího ukazatele.|
|[CComPtrBase:: CoCreateInstance](#cocreateinstance)|Voláním této metody vytvoříte objekt třídy přidružené k zadanému ID třídy nebo ID programu.|
|[CComPtrBase:: CopyTo](#copyto)|Zavolejte tuto metodu pro zkopírování `CComPtrBase` ukazatele na jinou proměnnou ukazatele.|
|[CComPtrBase::D etach](#detach)|Voláním této metody vydáte vlastnictví ukazatele.|
|[CComPtrBase::IsEqualObject](#isequalobject)|Voláním této metody zkontrolujete, zda `IUnknown` zadané body odkazují na stejný objekt přidružený `CComPtrBase` k objektu.|
|[CComPtrBase::QueryInterface](#queryinterface)|Voláním této metody vrátíte ukazatel na zadané rozhraní.|
|[CComPtrBase:: Release](#release)|Voláním této metody uvolníte rozhraní.|
|[CComPtrBase:: SetSite](#setsite)|Voláním této metody nastavíte lokalitu `CComPtrBase` objektu `IUnknown` na nadřazený objekt.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CComPtrBase:: operator T *](#operator_t_star)|Operátor přetypování.|
|[CComPtrBase:: operator!](#operator_not)|Operátor NOT.|
|[CComPtrBase:: operator &](#operator_amp)|Operátor &.|
|[CComPtrBase:: operator * – operátor](#operator_star)|Operátor \*.|
|[CComPtrBase:: operator <](#ccomptrbase__operator lt)|Operátor menší než.|
|[CComPtrBase:: operator = = – operátor](#operator_eq_eq)|Operátor rovnosti.|
|[CComPtrBase:: operator->](#operator_ptr)|Operátor pointer-to-members.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComPtrBase::p](#p)|Proměnná členu dat ukazatele.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje základ pro jiné inteligentní ukazatele, které používají rutiny správy paměti COM, například [CComQIPtr](../../atl/reference/ccomqiptr-class.md) a [CComPtr](../../atl/reference/ccomptr-class.md). Odvozené třídy přidávají své vlastní konstruktory a operátory, ale spoléhají na metody, které `CComPtrBase`poskytuje.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atlcomcli. h

##  <a name="advise"></a>CComPtrBase:: Advise

Voláním této metody vytvoříte připojení mezi `CComPtrBase`spojovacím bodem a jímkou klienta.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
Ukazatel na klienta `IUnknown`.

*iid*<br/>
Identifikátor GUID bodu připojení Obvykle je to stejné jako odchozí rozhraní spravované bodem připojení.

*pdw*<br/>
Ukazatel na soubor cookie, který jedinečně identifikuje připojení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [AtlAdvise](connection-point-global-functions.md#atladvise) .

##  <a name="attach"></a>CComPtrBase:: Attach

Voláním této metody převezmete vlastnictví existujícího ukazatele.

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Parametry

*p2*<br/>
`CComPtrBase` Objekt převezme vlastnictví tohoto ukazatele.

### <a name="remarks"></a>Poznámky

`Attach`volá [CComPtrBase:: Release](#release) v existující členské proměnné [CComPtrBase::p](#p) a potom `CComPtrBase::p`přiřadí *P2* . Když objekt převezme vlastnictví ukazatele, automaticky se zavolá `Release` na ukazatel, který odstraní ukazatel a veškerá přidělená data v případě, že počet odkazů objektu přechází na 0. `CComPtrBase`

##  <a name="dtor"></a>CComPtrBase:: ~ CComPtrBase

Destruktor.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní rozhraní, na které `CComPtrBase`ukazuje.

##  <a name="cocreateinstance"></a>CComPtrBase:: CoCreateInstance

Voláním této metody vytvoříte objekt třídy přidružené k zadanému ID třídy nebo ID programu.

```
HRESULT CoCreateInstance(
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```

### <a name="parameters"></a>Parametry

*szProgID*<br/>
Ukazatel na identifikátor ProgID, který se používá k obnovení CLSID.

*pUnkOuter*<br/>
Pokud má hodnotu NULL, znamená to, že objekt není vytvářen jako součást agregace. Pokud není null, je ukazatel na `IUnknown` rozhraní agregovaného objektu (řízení `IUnknown`).

*dwClsContext*<br/>
Kontext, ve kterém se spustí kód, který spravuje nově vytvořený objekt.

*rclsid*<br/>
Identifikátor CLSID přidružený k datům a kódu, který bude použit k vytvoření objektu.

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK při úspěchu nebo REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING nebo E_NOINTERFACE při selhání. Popis těchto chyb naleznete v tématu [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) a [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) .

### <a name="remarks"></a>Poznámky

V případě, že je volána první forma metody, je k obnovení CLSID použit [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) . Obě formuláře pak volají [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

V sestavení ladění dojde k chybě kontrolního výrazu, pokud [CComPtrBase::p](#p) se nerovná hodnotě null.

##  <a name="copyto"></a>CComPtrBase:: CopyTo

Zavolejte tuto metodu pro zkopírování `CComPtrBase` ukazatele na jinou proměnnou ukazatele.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Parametry

*ppT*<br/>
Adresa proměnné, která bude přijímat `CComPtrBase` ukazatel.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu, E_POINTER při selhání.

### <a name="remarks"></a>Poznámky

Zkopíruje ukazatel na *PPT.* `CComPtrBase` Počet odkazů na členskou proměnnou [CComPtrBase::p](#p) se zvýší.

Pokud je hodnota *PPT* rovna hodnotě null, bude vrácena chyba HRESULT. V sestavení ladění dojde k chybě kontrolního výrazu, pokud je hodnota *PPT* rovna hodnotě null.

##  <a name="detach"></a>CComPtrBase::D etach

Voláním této metody vydáte vlastnictví ukazatele.

```
T* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii ukazatele.

### <a name="remarks"></a>Poznámky

Uvolní vlastnictví ukazatele, nastaví proměnnou datového členu [CComPtrBase::p](#p) na hodnotu null a vrátí kopii ukazatele.

##  <a name="isequalobject"></a>CComPtrBase::IsEqualObject

Voláním této metody zkontrolujete, zda `IUnknown` zadané body odkazují na stejný objekt přidružený `CComPtrBase` k objektu.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Parametry

*pOther*<br/>
`IUnknown *` Pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud jsou objekty shodné, v opačném případě false.

##  <a name="operator_not"></a>CComPtrBase:: operator!

Operátor NOT.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, `CComHeapPtr` Pokud je ukazatel roven hodnotě null, jinak false.

##  <a name="operator_amp"></a>CComPtrBase:: operator&amp;

Operátor &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu objektu, na `CComPtrBase` který odkazuje objekt.

##  <a name="operator_star"></a>CComPtrBase:: operator\*

Operátor \*.

```
T& operator*() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu [CComPtrBase::p](#p); To znamená, že ukazatel na objekt odkazovaný `CComPtrBase` objektem.

Při ladění sestavení dojde k chybě kontrolního výrazu, pokud [CComPtrBase::p](#p) se nerovná hodnotě null.

##  <a name="operator_eq_eq"></a>CComPtrBase:: operator = = – operátor

Operátor rovnosti.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*pT*<br/>
Ukazatel na objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true `CComPtrBase` , pokud a *PT* odkazuje na stejný objekt, jinak false.

##  <a name="operator_ptr"></a>CComPtrBase:: operator-&gt;

Operátor pointer-to-member.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné datového členu [CComPtrBase::p](#p) .

### <a name="remarks"></a>Poznámky

Tento operátor použijte k volání metody ve třídě, na `CComPtrBase` kterou ukazuje objekt. V sestavení ladění dojde k selhání kontrolního výrazu, pokud `CComPtrBase` datový člen odkazuje na hodnotu null.

##  <a name="operator_lt"></a>CComPtrBase:: operator&lt;

Operátor menší než.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*pT*<br/>
Ukazatel na objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je ukazatel, který je spravován aktuálním objektem, menší než ukazatel, na který je porovnán.

##  <a name="operator_t_star"></a>CComPtrBase:: operator T\*

Operátor přetypování.

```
operator T*() const throw();
```

### <a name="remarks"></a>Poznámky

Vrací ukazatel na datový typ objektu definovaný v šabloně třídy.

##  <a name="p"></a>CComPtrBase::p

Proměnná členu dat ukazatele.

```
T* p;
```

### <a name="remarks"></a>Poznámky

Tato členská proměnná obsahuje informace o ukazateli.

##  <a name="queryinterface"></a>CComPtrBase:: QueryInterface

Voláním této metody vrátíte ukazatel na zadané rozhraní.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Parametry

*Q*<br/>
Typ objektu, jehož ukazatel rozhraní je povinný.

*pp*<br/>
Adresa výstupní proměnné, která přijímá ukazatel požadovaného rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo E_NOINTERFACE při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda volá [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).

V sestavení ladění dojde k chybě kontrolního výrazu, pokud se *PP* nerovná hodnotě null.

##  <a name="release"></a>CComPtrBase:: Release

Voláním této metody uvolníte rozhraní.

```
void Release() throw();
```

### <a name="remarks"></a>Poznámky

Rozhraní je uvolněno a [CComPtrBase::p](#p) je nastavena na hodnotu null.

##  <a name="setsite"></a>CComPtrBase:: SetSite

Voláním této metody nastavíte lokalitu `CComPtrBase` objektu `IUnknown` na nadřazený objekt.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Parametry

*punkParent*<br/>
Ukazatel na `IUnknown` rozhraní nadřazené položky.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda volá [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
