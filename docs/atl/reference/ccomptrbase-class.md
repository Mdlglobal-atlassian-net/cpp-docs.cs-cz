---
title: Třída CComPtrBase
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
ms.openlocfilehash: 7d450f7762b39d7fa8fae07230690eecb8edbb4d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327467"
---
# <a name="ccomptrbase-class"></a>Třída CComPtrBase

Tato třída poskytuje základ pro inteligentní třídy ukazatele pomocí rutiny paměti založené na com.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu, na který má inteligentní ukazatel odkazovat.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComPtrBase::~CComPtrBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComPtrBase::Poradit](#advise)|Volání této metody k vytvoření `CComPtrBase`připojení mezi 's spojovací bod a jímky klienta.|
|[CComPtrBase::Připojit](#attach)|Volání této metody převzít vlastnictví existující ukazatel.|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Volání této metody k vytvoření objektu třídy přidružené k zadané ID třídy nebo ID programu.|
|[CComPtrBase::Kopírovat](#copyto)|Volání této metody `CComPtrBase` zkopírovat ukazatel na jinou proměnnou ukazatele.|
|[CComPtrBase::Detach](#detach)|Volání této metody uvolnit vlastnictví ukazatele.|
|[CComPtrBase::IsEqualObject](#isequalobject)|Volání této metody ke `IUnknown` kontrole, pokud zadaný `CComPtrBase` odkazuje na stejný objekt přidružený k objektu.|
|[CComPtrBase::QueryInterface](#queryinterface)|Volání této metody vrátit ukazatel zadané rozhraní.|
|[CComPtrBase::Vydání](#release)|Volání této metody k uvolnění rozhraní.|
|[CComPtrBase::SetSite](#setsite)|Volání této metody nastavit web `CComPtrBase` objektu `IUnknown` nadřazeného objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CComPtrBase::operátor T*](#operator_t_star)|Operátor obsazení.|
|[CComPtrBase::operátor !](#operator_not)|Operátor NOT.|
|[CComPtrBase::&operátora](#operator_amp)|Operátor &.|
|[CComPtrBase::operátor *](#operator_star)|Operátor \*.|
|[CComPtrBase::<operátora](#ccomptrbase__operator lt)|Operátor menší než.|
|[CComPtrBase::operátor ==](#operator_eq_eq)|Operátor rovnosti.|
|[CComPtrBase::operátor ->](#operator_ptr)|Operátor ukazatele na členy.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComPtrBase::p](#p)|Proměnná datového prvku ukazatele.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje základ pro další inteligentní ukazatele, které používají rutiny správy paměti COM, jako je [například CComQIPtr](../../atl/reference/ccomqiptr-class.md) a [CComPtr](../../atl/reference/ccomptr-class.md). Odvozené třídy přidat své vlastní konstruktory a operátory, `CComPtrBase`ale spoléhají na metody poskytované .

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h

## <a name="ccomptrbaseadvise"></a><a name="advise"></a>CComPtrBase::Poradit

Volání této metody k vytvoření `CComPtrBase`připojení mezi 's spojovací bod a jímky klienta.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
Ukazatel na klienta `IUnknown`.

*Iid*<br/>
Identifikátor GUID spojovacího bodu. Obvykle je to stejné jako odchozí rozhraní spravované bodem připojení.

*Pdw*<br/>
Ukazatel na soubor cookie, který jednoznačně identifikuje připojení.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu AtlAdvise.](connection-point-global-functions.md#atladvise)

## <a name="ccomptrbaseattach"></a><a name="attach"></a>CComPtrBase::Připojit

Volání této metody převzít vlastnictví existující ukazatel.

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Parametry

*p2*<br/>
Objekt `CComPtrBase` převezme vlastnictví tohoto ukazatele.

### <a name="remarks"></a>Poznámky

`Attach`volá [CComPtrBase::Release](#release) na existující [cComPtrBase::p](#p) členské proměnné a `CComPtrBase::p`pak přiřadí *p2* . Když `CComPtrBase` objekt převezme vlastnictví ukazatele, bude `Release` automaticky volat na ukazatel, který odstraní ukazatel a všechna přidělená data, pokud počet odkazů na objekt přejde na 0.

## <a name="ccomptrbaseccomptrbase"></a><a name="dtor"></a>CComPtrBase::~CComPtrBase

Destruktor.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní rozhraní, na `CComPtrBase`které se vztahuje aplikace .

## <a name="ccomptrbasecocreateinstance"></a><a name="cocreateinstance"></a>CComPtrBase::CoCreateInstance

Volání této metody k vytvoření objektu třídy přidružené k zadané ID třídy nebo ID programu.

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
Ukazatel na ProgID, který se používá k obnovení CLSID.

*pUnkOuter*<br/>
Pokud null, označuje, že objekt není vytvářen jako součást agregace. Pokud non-NULL, je ukazatel na `IUnknown` rozhraní agregační `IUnknown`objektu (řízení).

*dwClsKontext*<br/>
Kontext, ve kterém bude spuštěn kód, který spravuje nově vytvořený objekt.

*rclsid (rclsid)*<br/>
IDENTIFIKÁTOR CLSID přidružený k datům a kódu, který bude použit k vytvoření objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch, nebo REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING nebo E_NOINTERFACE na selhání. Popis těchto chyb naleznete v tématu [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) a [CLSIDFromProgID.](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid)

### <a name="remarks"></a>Poznámky

Pokud je volána první forma metody, [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) se používá k obnovení CLSID. Oba formuláře pak volání [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

V sestaveních ladění dojde k chybě kontrolního výrazu, pokud [CComPtrBase::p](#p) není rovna hodnotě NULL.

## <a name="ccomptrbasecopyto"></a><a name="copyto"></a>CComPtrBase::Kopírovat

Volání této metody `CComPtrBase` zkopírovat ukazatel na jinou proměnnou ukazatele.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Parametry

*Ppt*<br/>
Adresa proměnné, která obdrží `CComPtrBase` ukazatel.

### <a name="return-value"></a>Návratová hodnota

Vrací S_OK na úspěch, E_POINTER na neúspěch.

### <a name="remarks"></a>Poznámky

Zkopíruje `CComPtrBase` ukazatel na *ppT*. Počet odkazů na [ccomptrbase::p](#p) členské proměnné je se zpřísňují.

Chyba HRESULT bude vrácena, pokud *ppT* se rovná NULL. V sestaveních ladění dojde k chybě kontrolního výrazu, pokud se *ppT* rovná hodnotě NULL.

## <a name="ccomptrbasedetach"></a><a name="detach"></a>CComPtrBase::Detach

Volání této metody uvolnit vlastnictví ukazatele.

```
T* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii ukazatele.

### <a name="remarks"></a>Poznámky

Uvolní vlastnictví ukazatele, nastaví proměnnou [CComPtrBase::p](#p) datového člena na HODNOTU NULL a vrátí kopii ukazatele.

## <a name="ccomptrbaseisequalobject"></a><a name="isequalobject"></a>CComPtrBase::IsEqualObject

Volání této metody ke `IUnknown` kontrole, pokud zadaný `CComPtrBase` odkazuje na stejný objekt přidružený k objektu.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Parametry

*pOstatní*<br/>
Porovnat. `IUnknown *`

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud jsou objekty identické, false otherwise.

## <a name="ccomptrbaseoperator-"></a><a name="operator_not"></a>CComPtrBase::operátor !

Operátor NOT.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu `CComHeapPtr` true, pokud je ukazatel rovna hodnotě NULL, false otherwise.

## <a name="ccomptrbaseoperator-amp"></a><a name="operator_amp"></a>CComPtrBase::operátor&amp;

Operátor &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu objektu, na `CComPtrBase` který objekt ukazuje.

## <a name="ccomptrbaseoperator-"></a><a name="operator_star"></a>CComPtrBase::operátor\*

Operátor \*.

```
T& operator*() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu [CComPtrBase::p](#p). to znamená ukazatel na objekt, na `CComPtrBase` který objekt odkazuje.

Pokud se vytvoří ladění, dojde k chybě kontrolního výrazu, pokud [CComPtrBase::p](#p) není rovna NULL.

## <a name="ccomptrbaseoperator-"></a><a name="operator_eq_eq"></a>CComPtrBase::operátor ==

Operátor rovnosti.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Ukazatel na objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true if `CComPtrBase` a *pT* přejděte na stejný objekt false.

## <a name="ccomptrbaseoperator--gt"></a><a name="operator_ptr"></a>CComPtrBase::operátor -&gt;

Operátor ukazatele na člen.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné [ccomptrbase::p](#p) datového člena.

### <a name="remarks"></a>Poznámky

Tento operátor slouží k volání metody ve `CComPtrBase` třídě, na kterou objekt ukazuje. V sestaveních ladění dojde k selhání `CComPtrBase` kontrolního výrazu, pokud datový člen odkazuje na hodnotu NULL.

## <a name="ccomptrbaseoperator-lt"></a><a name="operator_lt"></a>CComPtrBase::operátor&lt;

Operátor menší než.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Ukazatel na objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je ukazatel spravovaný aktuálním objektem menší než ukazatel, se kterým je porovnáván.

## <a name="ccomptrbaseoperator-t"></a><a name="operator_t_star"></a>CComPtrBase::operátor T\*

Operátor obsazení.

```
operator T*() const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí ukazatel na datový typ objektu definovaný v šabloně třídy.

## <a name="ccomptrbasep"></a><a name="p"></a>CComPtrBase::p

Proměnná datového prvku ukazatele.

```
T* p;
```

### <a name="remarks"></a>Poznámky

Tato členská proměnná obsahuje informace o ukazateli.

## <a name="ccomptrbasequeryinterface"></a><a name="queryinterface"></a>CComPtrBase::QueryInterface

Volání této metody vrátit ukazatel zadané rozhraní.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Parametry

*Q*<br/>
Typ objektu, jehož ukazatel rozhraní je požadováno.

*Stran*<br/>
Adresa výstupní proměnné, která přijímá požadovaný ukazatel rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch, nebo E_NOINTERFACE na neúspěch.

### <a name="remarks"></a>Poznámky

Tato metoda volá [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)).

V sestaveních ladění dojde k chybě kontrolního výrazu, pokud *se hodnota pp* nerovná hodnotě NULL.

## <a name="ccomptrbaserelease"></a><a name="release"></a>CComPtrBase::Vydání

Volání této metody k uvolnění rozhraní.

```
void Release() throw();
```

### <a name="remarks"></a>Poznámky

Rozhraní je uvolněno a [CComPtrBase::p](#p) je nastavena na hodnotu NULL.

## <a name="ccomptrbasesetsite"></a><a name="setsite"></a>CComPtrBase::SetSite

Volání této metody nastavit web `CComPtrBase` objektu `IUnknown` nadřazeného objektu.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Parametry

*punkParent*<br/>
Ukazatel na `IUnknown` rozhraní nadřazené.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda volá [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
