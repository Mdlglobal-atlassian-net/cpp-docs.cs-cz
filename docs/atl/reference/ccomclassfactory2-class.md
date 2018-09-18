---
title: Ccomclassfactory2 – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05fcef5ee1141de8261bc4ecc813cd573fb8f901
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099498"
---
# <a name="ccomclassfactory2-class"></a>Ccomclassfactory2 – třída

Tato třída implementuje [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) rozhraní.

## <a name="syntax"></a>Syntaxe

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>Parametry

*Licence*<br/>
Třída, která implementuje následující statické funkce:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComClassFactory2::CreateInstance](#createinstance)|Vytvoří objekt zadaným identifikátorem CLSID.|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|Zadaný licenčního kódu vytvoří objekt zadaným identifikátorem CLSID.|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Načte informace, které popisují licenční možnosti objektu pro vytváření tříd.|
|[CComClassFactory2::LockServer](#lockserver)|Zamkne objekt pro vytváření tříd v paměti.|
|[CComClassFactory2::RequestLicKey](#requestlickey)|Vytvoří a vrátí licenční klíč.|

## <a name="remarks"></a>Poznámky

`CComClassFactory2` implementuje [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) rozhraní, která je rozšířením z [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2` vytvoření ovládacích prvků objektu prostřednictvím licenci. Třída objekt pro vytváření, provádění na licencovanou počítači může poskytnout za běhu licenční klíč. Tento licenční klíč umožňuje aplikaci k vytvoření instance objektů při úplné počítač licence neexistuje.

Objekty knihovny ATL obvykle získat objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), který deklaruje [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactory2`, zadejte [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) makra v definici třídy objektu. Příklad:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`, parametr šablony `CComClassFactory2`, musí implementovat statické funkce `VerifyLicenseKey`, `GetLicenseKey`, a `IsLicenseValid`. Následuje příklad licenci jednoduše třídy:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2` je odvozen z obou `CComClassFactory2Base` a *licence*. `CComClassFactory2Base`, pak je odvozena z `IClassFactory2` a `CComObjectRootEx< CComGlobalsThreadModel >`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="createinstance"></a>  CComClassFactory2::CreateInstance

Vytvoří objekt zadaným identifikátorem CLSID a načte ukazatel rozhraní k tomuto objektu.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
[in] Pokud se objekt vytváří jako součást agregace, pak *pUnkOuter* musí být vnější neznámá. V opačném případě *pUnkOuter* musí mít hodnotu NULL.

*riid*<br/>
[in] Identifikátor IID požadované rozhraní. Pokud *pUnkOuter* je jiná než NULL, *riid* musí být `IID_IUnknown`.

*ppvObj*<br/>
[out] Ukazatel na ukazatel rozhraní, který je identifikován *riid*. Pokud objekt nepodporuje toto rozhraní *ppvObj* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Vyžaduje, aby počítač k plně licencované. Úplné počítač licence neexistuje, kontaktujte [CreateInstanceLic](#createinstancelic).

##  <a name="createinstancelic"></a>  CComClassFactory2::CreateInstanceLic

Podobně jako [CreateInstance](#createinstance), s tím rozdílem, že `CreateInstanceLic` vyžaduje licenční klíč.

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
[in] Pokud se objekt vytváří jako součást agregace, pak *pUnkOuter* musí být vnější neznámá. V opačném případě *pUnkOuter* musí mít hodnotu NULL.

*pUnkReserved*<br/>
[in] Nepoužívá se. Musí mít hodnotu NULL.

*riid*<br/>
[in] Identifikátor IID požadované rozhraní. Pokud *pUnkOuter* je jiná než NULL, *riid* musí být `IID_IUnknown`.

*bstrKey*<br/>
[in] Za běhu licenční klíč dříve získány z volání `RequestLicKey`. Tento klíč se vyžaduje k vytvoření objektu.

*ppvObject*<br/>
[out] Ukazatel na ukazatel rozhraní určené *riid*. Pokud objekt nepodporuje toto rozhraní *ppvObject* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Můžete získat licenční klíč pomocí [RequestLicKey](#requestlickey). Chcete-li vytvořit objekt nelicencovaného počítači, je nutné volat `CreateInstanceLic`.

##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo

Vyplní [LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo) struktura s informacemi, které popisují objekt pro vytváření tříd v možnosti licencování.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>Parametry

*pLicInfo*<br/>
[out] Ukazatel `LICINFO` struktury.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

`fRuntimeKeyAvail` Člena této struktury určuje, zda, zadány licenční klíč, objekt pro vytváření tříd umožňuje objektů nelicencovaného počítači. *FLicVerified* člen označuje, zda licenci úplné počítače existuje.

##  <a name="lockserver"></a>  CComClassFactory2::LockServer

Inkrementuje a dekrementuje počet zámků modulů voláním `_Module::Lock` a `_Module::Unlock`v uvedeném pořadí.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*hejna*<br/>
[in] Při hodnotě TRUE se zvýší počet zámků; v opačném případě je snížen počet zámků.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

`_Module` odkazuje na globální instanci [ccommodule –](../../atl/reference/ccommodule-class.md) nebo z něj odvozenou třídu.

Volání `LockServer` umožňuje klientovi opřete se o objekt pro vytváření tříd tak, aby více objektů lze rychle vytvořit.

##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey

Vytvoří a vrátí licenční klíč, za předpokladu, že `fRuntimeKeyAvail` člena [LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo) struktura je TRUE.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
[in] Nepoužívá se. Musí být nula.

*pbstrKey*<br/>
[out] Ukazatel na licenční klíč.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Licenční klíč se požaduje pro volání [CreateInstanceLic](#createinstancelic) pro vytvoření objektu nelicencovaného počítači. Pokud `fRuntimeKeyAvail` má hodnotu FALSE, pak objekty lze vytvořit pouze na plně licencovanou počítači.

Volání [GetLicInfo](#getlicinfo) k načtení hodnoty z `fRuntimeKeyAvail`.

## <a name="see-also"></a>Viz také

[CComClassFactoryAutoThread – třída](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClassFactorySingleton – třída](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
