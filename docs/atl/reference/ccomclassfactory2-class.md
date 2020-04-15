---
title: Třída CComClassFactory2
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
ms.openlocfilehash: 0cb2064cfaea6317c4522ff917f3963fca2219b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321016"
---
# <a name="ccomclassfactory2-class"></a>Třída CComClassFactory2

Tato třída implementuje rozhraní [IClassFactory2.](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)

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

|Name (Název)|Popis|
|----------|-----------------|
|[CComClassFactory2::CreateInstance](#createinstance)|Vytvoří objekt zadaného identifikátoru CLSID.|
|[CComClassFactory2::CreateInstancelic](#createinstancelic)|Daný licenční klíč vytvoří objekt zadaného identifikátoru CLSID.|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Načte informace popisující možnosti licencování výrobce tříd.|
|[CComClassFactory2::LockServer](#lockserver)|Zamkne továrnu třídy v paměti.|
|[CComClassFactory2::RequestLicKey](#requestlickey)|Vytvoří a vrátí licenční klíč.|

## <a name="remarks"></a>Poznámky

`CComClassFactory2`implementuje rozhraní [IClassFactory2,](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) které je rozšířením [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`řídí vytváření objektů prostřednictvím licence. Továrna třídy spuštěná na licencovaném počítači může poskytnout licenční klíč za běhu. Tento licenční klíč umožňuje aplikaci vytvářet instance objektů, pokud neexistuje úplná licence počítače.

Objekty ATL obvykle získávají třídu odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)maker , který deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí třídy factory. Chcete-li použít `CComClassFactory2`, zadejte [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) makro v definici třídy objektu. Příklad:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`, musí parametr `CComClassFactory2`šablony do aplikace `VerifyLicenseKey` `GetLicenseKey`implementovat `IsLicenseValid`statické funkce , a . Následuje příklad jednoduché třídy licencí:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`pochází z `CComClassFactory2Base` obou a *licence*. `CComClassFactory2Base`, podle pořadí, `IClassFactory2` pochází `CComObjectRootEx< CComGlobalsThreadModel >`z a .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomclassfactory2createinstance"></a><a name="createinstance"></a>CComClassFactory2::CreateInstance

Vytvoří objekt zadaného identifikátoru CLSID a načte k tomuto objektu ukazatel rozhraní.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
[v] Pokud je objekt vytvářen jako součást agregace, pak *pUnkOuter* musí být vnější neznámý. V opačném případě *pUnkOuter* musí být NULL.

*riid řekl:*<br/>
[v] IID požadovanérozhraní. Pokud *pUnkOuter* není null, *riid* musí být `IID_IUnknown`.

*ppvObj*<br/>
[out] Ukazatel rozhraní určený *riid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppvObj* nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vyžaduje, aby byl počítač plně licencován. Pokud úplná licence počítače neexistuje, zavolejte [CreateInstanceLic](#createinstancelic).

## <a name="ccomclassfactory2createinstancelic"></a><a name="createinstancelic"></a>CComClassFactory2::CreateInstancelic

Podobně jako [CreateInstance](#createinstance) `CreateInstanceLic` , s výjimkou, že vyžaduje licenční klíč.

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
[v] Pokud je objekt vytvářen jako součást agregace, pak *pUnkOuter* musí být vnější neznámý. V opačném případě *pUnkOuter* musí být NULL.

*pUnkReserved*<br/>
[v] Nepoužívá se. Musí být null.

*riid řekl:*<br/>
[v] IID požadovanérozhraní. Pokud *pUnkOuter* není null, *riid* musí být `IID_IUnknown`.

*bstrKey*<br/>
[v] Kód licence run-time, který byl `RequestLicKey`dříve získán z volání do společnosti . Tento klíč je nutné vytvořit objekt.

*ppvObjekt*<br/>
[out] Ukazatel na ukazatel rozhraní určený *riid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppvObject* nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Licenční klíč můžete získat pomocí [requestlickey](#requestlickey). Chcete-li vytvořit objekt v počítači bez `CreateInstanceLic`licence, musíte volat .

## <a name="ccomclassfactory2getlicinfo"></a><a name="getlicinfo"></a>CComClassFactory2::GetLicInfo

Vyplní strukturu [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) informacemi, které popisují možnosti licencování továrny třídy.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>Parametry

*pLicInfo*<br/>
[out] Ukazatel na `LICINFO` strukturu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Člen `fRuntimeKeyAvail` této struktury označuje, zda za daný licenční klíč umožňuje factory třídy vytvářet objekty v nelicencovaném počítači. Člen *fLicVerified* označuje, zda existuje úplná licence počítače.

## <a name="ccomclassfactory2lockserver"></a><a name="lockserver"></a>CComClassFactory2::LockServer

Přírůstky a snížení počet zámek modulu `_Module::Lock` voláním `_Module::Unlock`a , v uvedeném pořadí.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Stádo*<br/>
[v] Pokud true, počet zámků se zpřísňuje; v opačném případě je snížen počet zámků.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`_Module`odkazuje na globální instanci [CComModule](../../atl/reference/ccommodule-class.md) nebo třídy odvozené z něj.

Volání `LockServer` umožňuje klientovi podržet továrnu třídy tak, aby bylo možné rychle vytvořit více objektů.

## <a name="ccomclassfactory2requestlickey"></a><a name="requestlickey"></a>CComClassFactory2::RequestLicKey

Vytvoří a vrátí licenční klíč za `fRuntimeKeyAvail` předpokladu, že člen struktury [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) je TRUE.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>Parametry

*dwVyhrazeno*<br/>
[v] Nepoužívá se. Musí být nula.

*pbstrKey*<br/>
[out] Ukazatel na licenční klíč.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pro volání [aplikace CreateInstanceLic](#createinstancelic) je vyžadován licenční klíč k vytvoření objektu v nelicencovaném počítači. Pokud `fRuntimeKeyAvail` je FALSE, pak objekty lze vytvořit pouze na plně licencovaném počítači.

Volání [GetLicInfo](#getlicinfo) načíst `fRuntimeKeyAvail`hodnotu .

## <a name="see-also"></a>Viz také

[Třída CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[Třída CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[Třída CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
