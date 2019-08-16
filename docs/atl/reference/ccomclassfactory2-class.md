---
title: CComClassFactory2 Class
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
ms.openlocfilehash: e34ebffc937c3e4ef1272fdf13ddcde7513d28e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497463"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 Class

Tato třída implementuje rozhraní [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) .

## <a name="syntax"></a>Syntaxe

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>Parametry

*průkaz*<br/>
Třída, která implementuje následující statické funkce:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComClassFactory2::CreateInstance](#createinstance)|Vytvoří objekt zadaného objektu CLSID.|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|V případě, že je zadán licenční klíč, vytvoří objekt zadaného objektu CLSID.|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Načte informace popisující možnosti licencování objektu pro vytváření tříd.|
|[CComClassFactory2::LockServer](#lockserver)|Zamkne objekt pro vytváření tříd v paměti.|
|[CComClassFactory2::RequestLicKey](#requestlickey)|Vytvoří a vrátí licenční klíč.|

## <a name="remarks"></a>Poznámky

`CComClassFactory2`implementuje rozhraní [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) , což je rozšíření [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`řídí vytváření objektů pomocí licence. Objekt pro vytváření tříd, který je spuštěn na licencovaném počítači, může poskytnout licenční klíč za běhu. Tento licenční klíč umožňuje aplikaci vytvářet instance objektů, pokud není k dispozici úplná licence na počítač.

Objekty ATL normálně získávají objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), které deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete- `CComClassFactory2`li použít, zadejte makro [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) v definici třídy vašeho objektu. Příklad:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`, `CComClassFactory2`parametr šablony do, musí implementovat statické funkce `VerifyLicenseKey`, `GetLicenseKey`a `IsLicenseValid`. Následuje příklad jednoduché třídy licence:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`je odvozen z obou `CComClassFactory2Base` i *licencí*. `CComClassFactory2Base`, zase, je odvozen z `IClassFactory2` a. `CComObjectRootEx< CComGlobalsThreadModel >`

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="createinstance"></a>CComClassFactory2:: CreateInstance

Vytvoří objekt zadaného identifikátoru CLSID a načte ukazatel rozhraní na tento objekt.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
pro Pokud se objekt vytváří jako součást agregace, pak musí být *pUnkOuter* vnějším neznámý. V opačném případě *pUnkOuter* musí mít hodnotu null.

*riid*<br/>
pro IID požadovaného rozhraní. Pokud *pUnkOuter* je jiný než null, musí být `IID_IUnknown`riid.

*ppvObj*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný *riid*. Pokud objekt nepodporuje toto rozhraní, je *ppvObj* nastaveno na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vyžaduje, aby byl počítač plně licencován. Pokud úplná licence na počítač neexistuje, zavolejte [CreateInstanceLic](#createinstancelic).

##  <a name="createinstancelic"></a>CComClassFactory2::CreateInstanceLic

Podobný funkci [CreateInstance](#createinstance), s výjimkou, že `CreateInstanceLic` vyžaduje licenční klíč.

```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
*/,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
pro Pokud se objekt vytváří jako součást agregace, pak musí být *pUnkOuter* vnějším neznámý. V opačném případě *pUnkOuter* musí mít hodnotu null.

*pUnkReserved*<br/>
pro Nepoužívá se. Musí mít hodnotu NULL.

*riid*<br/>
pro IID požadovaného rozhraní. Pokud *pUnkOuter* je jiný než null, musí být `IID_IUnknown`riid.

*bstrKey*<br/>
pro Licenční klíč za běhu dříve získaný z volání `RequestLicKey`. Tento klíč je nutný k vytvoření objektu.

*ppvObject*<br/>
mimo Ukazatel na ukazatel rozhraní určený parametrem *riid*. Pokud objekt nepodporuje toto rozhraní, je *ppvObject* nastaveno na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Licenční klíč můžete získat pomocí [RequestLicKey](#requestlickey). Aby bylo možné vytvořit objekt na počítači, který není držitelem licence, je nutné `CreateInstanceLic`zavolat.

##  <a name="getlicinfo"></a>CComClassFactory2::GetLicInfo

Vyplní strukturu [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) informacemi, které popisují možnosti licencování továrny tříd.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>Parametry

*pLicInfo*<br/>
mimo Ukazatel na `LICINFO` strukturu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`fRuntimeKeyAvail` Člen této struktury označuje, zda je pro objekt pro vytváření tříd uděleno vytváření objektů na nelicencovaných počítačích. Člen *fLicVerified* označuje, zda existuje úplná licence počítače.

##  <a name="lockserver"></a>  CComClassFactory2::LockServer

Zvýší a sníží počet zámků modulu voláním `_Module::Lock` a `_Module::Unlock`v uvedeném pořadí.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*stád*<br/>
pro Při hodnotě TRUE se zvýší počet zámků; v opačném případě se počet zámků sníží.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`_Module`odkazuje na globální instanci [CComModule](../../atl/reference/ccommodule-class.md) nebo z ní odvozené třídy.

Volání `LockServer` umožňuje klientovi umístit se do objektu pro vytváření tříd, aby bylo možné rychle vytvořit více objektů.

##  <a name="requestlickey"></a>CComClassFactory2::RequestLicKey

Vytvoří a vrátí licenční klíč za předpokladu, že `fRuntimeKeyAvail` člen struktury [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) má hodnotu true.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
pro Nepoužívá se. Musí mít hodnotu nula.

*pbstrKey*<br/>
mimo Ukazatel na licenční klíč.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pro volání [CreateInstanceLic](#createinstancelic) k vytvoření objektu na nelicencovaný počítač se vyžaduje licenční klíč. Pokud `fRuntimeKeyAvail` je hodnota false, pak lze objekty vytvořit pouze v plně licencovaném počítači.

Zavolejte [GetLicInfo](#getlicinfo) , aby se načetla hodnota `fRuntimeKeyAvail`.

## <a name="see-also"></a>Viz také:

[CComClassFactoryAutoThread – třída](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClassFactorySingleton – třída](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
