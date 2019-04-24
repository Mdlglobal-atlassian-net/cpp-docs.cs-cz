---
title: Ccomptrbase – třída
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
ms.openlocfilehash: 5bb599b88671447e219421efacac7a2d8a5f7b06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246228"
---
# <a name="ccomptrbase-class"></a>Ccomptrbase – třída

Tato třída poskytuje základ pro inteligentní ukazatel tříd pomocí rutiny založené na modelu COM. paměti.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu, který může odkazovat inteligentního ukazatele.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComPtrBase::~CComPtrBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComPtrBase::Advise](#advise)|Volejte tuto metodu za účelem vytvoření připojení mezi `CComPtrBase`na bod připojení a jímkou klienta.|
|[CComPtrBase::Attach](#attach)|Volejte tuto metodu za účelem převzít vlastnictví stávajícího ukazatele.|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Volejte tuto metodu za účelem vytvoření objektu třídy přidružené k zadaným ID třídy nebo ID programu.|
|[CComPtrBase::CopyTo](#copyto)|Voláním této metody lze zkopírovat `CComPtrBase` ukazatel na jiné proměnné ukazatele.|
|[CComPtrBase::Detach](#detach)|Volejte tuto metodu za účelem uvolní vlastnictví ukazatele.|
|[CComPtrBase::IsEqualObject](#isequalobject)|Voláním této metody zkontrolujte, zda zadaný `IUnknown` odkazuje na stejný objekt přidružený k `CComPtrBase` objektu.|
|[CComPtrBase::QueryInterface](#queryinterface)|Voláním této metody vrátí ukazatel na zadané rozhraní.|
|[CComPtrBase::Release](#release)|Volejte tuto metodu za účelem uvolnění rozhraní.|
|[CComPtrBase::SetSite](#setsite)|Volejte tuto metodu za účelem nastavíte lokalitu `CComPtrBase` objektu `IUnknown` nadřazeného objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CComPtrBase::operator T *](#operator_t_star)|Operátor přetypování.|
|[CComPtrBase::operator!](#operator_not)|Operátor NOT.|
|[CComPtrBase::operator &](#operator_amp)|& – Operátor.|
|[CComPtrBase::operator *](#operator_star)|Operátor \*.|
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|Větší-než operátor.|
|[CComPtrBase::operator ==](#operator_eq_eq)|Operátor rovnosti.|
|[CComPtrBase::operator ->](#operator_ptr)|Operátor ukazatele na členy.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComPtrBase::p](#p)|Členské proměnné ukazatele data.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje základ pro jiné inteligentních ukazatelů, které používají rutiny správy paměti modelu COM, jako například [CComQIPtr](../../atl/reference/ccomqiptr-class.md) a [CComPtr](../../atl/reference/ccomptr-class.md). Odvozené třídy přidat svoje vlastní konstruktory a operátory, ale závisí na metody poskytované `CComPtrBase`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h

##  <a name="advise"></a>  CComPtrBase::Advise

Volejte tuto metodu za účelem vytvoření připojení mezi `CComPtrBase`na bod připojení a jímkou klienta.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
Ukazatel na straně klienta `IUnknown`.

*iid*<br/>
Identifikátor GUID je spojovací bod. Obvykle je to stejné jako odchozí rozhraní spravuje spojovací bod.

*pdw*<br/>
Ukazatel na soubor cookie, který jednoznačně identifikuje připojení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Zobrazit [AtlAdvise](connection-point-global-functions.md#atladvise) Další informace.

##  <a name="attach"></a>  CComPtrBase::Attach

Volejte tuto metodu za účelem převzít vlastnictví stávajícího ukazatele.

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Parametry

*p2*<br/>
`CComPtrBase` Objektu bude převzít vlastnictví tohoto ukazatele.

### <a name="remarks"></a>Poznámky

`Attach` volání [CComPtrBase::Release](#release) pro existující [CComPtrBase::p](#p) členskou proměnnou a pak přiřadí *p2* k `CComPtrBase::p`. Když `CComPtrBase` objekt převezme vlastnictví ukazatele, automaticky zavolá `Release` na ukazatel, který se odstraní ukazatel a všechny přidělené dat, pokud počet odkazů na objekt přejde na hodnotu 0.

##  <a name="dtor"></a>  Ccomptrbase –:: ~ ccomptrbase –

Destruktor.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní rozhraní, na které odkazuje `CComPtrBase`.

##  <a name="cocreateinstance"></a>  CComPtrBase::CoCreateInstance

Volejte tuto metodu za účelem vytvoření objektu třídy přidružené k zadaným ID třídy nebo ID programu.

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
Ukazatel na identifikátor ProgID, použít k obnovení identifikátor CLSID.

*pUnkOuter*<br/>
Pokud má hodnotu NULL, označuje, že se objekt vytváří jako součást agregace. Pokud není NULL, je ukazatel na agregovaný objekt `IUnknown` rozhraní (řízení `IUnknown`).

*dwClsContext*<br/>
Kontext, ve kterém se spustí kód, který spravuje nově vytvořený objekt.

*rclsid*<br/>
CLSID asociované s daty a kód, který se použije k vytvoření objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu, nebo REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING nebo E_NOINTERFACE při selhání. Zobrazit [CoCreateClassInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance) a [CLSIDFromProgID](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromprogid) popis těchto chyb.

### <a name="remarks"></a>Poznámky

Pokud první forma metoda je volána, [CLSIDFromProgID](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromprogid) slouží k obnovení identifikátor CLSID. Obě formy poté zavolejte [CoCreateClassInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud [CComPtrBase::p](#p) není shodný s hodnotou NULL.

##  <a name="copyto"></a>  CComPtrBase::CopyTo

Voláním této metody lze zkopírovat `CComPtrBase` ukazatel na jiné proměnné ukazatele.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Parametry

*ppT*<br/>
Adresa proměnné, které se zobrazí `CComPtrBase` ukazatele.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu, E_POINTER při selhání.

### <a name="remarks"></a>Poznámky

Kopie `CComPtrBase` ukazatel na *ppT*. Spolehněte se na odkaz [CComPtrBase::p](#p) členské proměnné se zvýší.

Chybu HRESULT bude vrácen v případě *ppT* je rovna hodnotě NULL. V sestavení ladění, dojde k chybě kontrolního výrazu Pokud *ppT* je rovna hodnotě NULL.

##  <a name="detach"></a>  CComPtrBase::Detach

Volejte tuto metodu za účelem uvolní vlastnictví ukazatele.

```
T* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii ukazatele.

### <a name="remarks"></a>Poznámky

Uvolní vlastnictví ukazatele, nastaví [CComPtrBase::p](#p) data členskou proměnnou na hodnotu NULL a vrátí kopii ukazatele.

##  <a name="isequalobject"></a>  CComPtrBase::IsEqualObject

Voláním této metody zkontrolujte, zda zadaný `IUnknown` odkazuje na stejný objekt přidružený k `CComPtrBase` objektu.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Parametry

*pOther*<br/>
`IUnknown *` k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud jsou objekty shodné, false, jinak.

##  <a name="operator_not"></a>  CComPtrBase::operator!

Operátor NOT.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud `CComHeapPtr` ukazatel je rovna hodnotě NULL, hodnotu false v opačném případě.

##  <a name="operator_amp"></a>  CComPtrBase::operator &amp;

& – Operátor.

```
T** operator&() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu objektu, na které odkazují `CComPtrBase` objektu.

##  <a name="operator_star"></a>  CComPtrBase::operator \*

Operátor \*.

```
T& operator*() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu [CComPtrBase::p](#p); to znamená, ukazatel na objekt, který odkazuje `CComPtrBase` objektu.

Pokud ladicí sestavení, dojde k chybě kontrolního výrazu Pokud [CComPtrBase::p](#p) není shodný s hodnotou NULL.

##  <a name="operator_eq_eq"></a>  CComPtrBase::operator ==

Operátor rovnosti.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*pT*<br/>
Ukazatel na objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud `CComPtrBase` a *pT* odkazovat na stejný objekt false v opačném případě.

##  <a name="operator_ptr"></a>  CComPtrBase::operator-&gt;

Operátor pointer-to-member.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu [CComPtrBase::p](#p) data členské proměnné.

### <a name="remarks"></a>Poznámky

Operátor volání metody ve třídě, na které odkazují `CComPtrBase` objektu. V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud `CComPtrBase` datový člen odkazuje na hodnotu NULL.

##  <a name="operator_lt"></a>  CComPtrBase::operator &lt;

Větší-než operátor.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Parametry

*pT*<br/>
Ukazatel na objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud ukazatel spravuje aktuální objekt je menší než ukazatel, ke kterému je porovnávána.

##  <a name="operator_t_star"></a>  CComPtrBase::operator T\*

Operátor přetypování.

```
operator T*() const throw();
```

### <a name="remarks"></a>Poznámky

Vrací ukazatel na objekt typu dat definovanému v šabloně třídy.

##  <a name="p"></a>  CComPtrBase::p

Členské proměnné ukazatele data.

```
T* p;
```

### <a name="remarks"></a>Poznámky

Tato členská proměnná uchovává informace o ukazatel.

##  <a name="queryinterface"></a>  CComPtrBase::QueryInterface

Voláním této metody vrátí ukazatel na zadané rozhraní.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Parametry

*Q*<br/>
Typ objektu, jehož ukazatel rozhraní je povinný.

*pp*<br/>
Adresa výstupní proměnné, která přijímá ukazatel požadované rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo E_NOINTERFACE při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda volá [IUnknown::QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud *pp* není shodný s hodnotou NULL.

##  <a name="release"></a>  CComPtrBase::Release

Volejte tuto metodu za účelem uvolnění rozhraní.

```
void Release() throw();
```

### <a name="remarks"></a>Poznámky

Se uvolní rozhraní, a [CComPtrBase::p](#p) nastaven na hodnotu NULL.

##  <a name="setsite"></a>  CComPtrBase::SetSite

Volejte tuto metodu za účelem nastavíte lokalitu `CComPtrBase` objektu `IUnknown` nadřazeného objektu.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Parametry

*punkParent*<br/>
Ukazatel `IUnknown` rozhraní nadřazeného prvku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda volá [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
