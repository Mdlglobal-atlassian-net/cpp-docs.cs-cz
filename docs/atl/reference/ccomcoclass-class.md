---
title: Třída CComCoClass
ms.date: 11/04/2016
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
ms.openlocfilehash: 11e724a982f3a2f404473dbdd34d848842cc8e14
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320827"
---
# <a name="ccomcoclass-class"></a>Třída CComCoClass

Tato třída poskytuje metody pro vytváření instancí třídy a získání jeho vlastností.

## <a name="syntax"></a>Syntaxe

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `CComCoClass`.

*pclsid (pclsid)*<br/>
Ukazatel na CLSID objektu.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CcomcoClass::CreateInstance](#createinstance)|(Statické) Vytvoří instanci třídy a dotazuje se na rozhraní.|
|[CcomcoClass::Chyba](#error)|(Statické) Vrátí rozšířené informace o chybě klientovi.|
|[CcomcoClass::GetObjectCLSID](#getobjectclsid)|(Statické) Vrátí identifikátor třídy objektu.|
|[CcomcoClass::Popis getobjectdescription](#getobjectdescription)|(Statické) Přepsáním vrátíte popis objektu.|

## <a name="remarks"></a>Poznámky

`CComCoClass`poskytuje metody pro načítání identifikátoru CLSID objektu, nastavení informací o chybách a vytváření instancí třídy. Všechny třídy registrované v mapě objektu by měly být odvozeny z `CComCoClass`.

`CComCoClass`také definuje výchozí třídy factory a agregace modelu pro váš objekt. `CComCoClass`používá následující dvě makra:

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) Deklaruje factory třídy [ccomclassfactory](../../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) Deklaruje, že váš objekt lze agregovat.

Některou z těchto výchozích hodnot můžete přepsat zadáním jiného makra v definici třídy. Chcete-li například použít [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) místo `CComClassFactory`, zadejte [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) makro:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomcoclasscreateinstance"></a><a name="createinstance"></a>CcomcoClass::CreateInstance

Tyto `CreateInstance` funkce slouží k vytvoření instance objektu COM a načtení ukazatele rozhraní bez použití rozhraní COM API.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>Parametry

*Q*<br/>
Rozhraní COM, které by měly být vráceny prostřednictvím *pp*.

*punkVnější*<br/>
[v] Vnější neznámý nebo ovládající neznámý agregátu.

*Stran*<br/>
[out] Adresa proměnné ukazatele, která obdrží požadovaný ukazatel rozhraní, pokud je vytvoření úspěšné.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT. Popis možných vrácených hodnot naleznete v části [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

První přetížení této funkce použijte pro vytvoření typického objektu; použijte druhé přetížení, když potřebujete agregovat vytvářený objekt.

Třída ATL implementující požadovaný objekt COM (to znamená třídu použitou jako první parametr šablony [ccomcoclass](../../atl/reference/ccomcoclass-class.md)) musí být ve stejném projektu jako volající kód. Vytvoření objektu COM provádí továrna třídy registrovaná pro tuto třídu KNIHOVNY ATL.

Tyto funkce jsou užitečné pro vytváření objektů, které jste zabránili externě creatable pomocí [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) makro. Jsou také užitečné v situacích, kdy se chcete vyhnout rozhraní COM API z důvodu efektivity.

Všimněte si, že rozhraní *Q* musí mít IID s ním spojené, které lze načíst pomocí [operátoru __uuidof.](../../cpp/uuidof-operator.md)

### <a name="example"></a>Příklad

V následujícím příkladu `CDocument` je průvodcegenem generované ATL `CComCoClass` třídy `IDocument` odvozené z, který implementuje rozhraní. Třída je registrována v mapě objektů s OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO makra, takže klienti nemohou vytvářet instance dokumentu pomocí [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance). `CApplication`je CoClass, který poskytuje metodu na jednom z vlastních rozhraní COM k vytvoření instancí třídy dokumentu. Níže uvedený kód ukazuje, jak snadné je vytvořit `CreateInstance` instance třídy `CComCoClass` dokumentu pomocí člena zděděného ze základní třídy.

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

## <a name="ccomcoclasserror"></a><a name="error"></a>CcomcoClass::Chyba

Tato statická funkce `IErrorInfo` nastaví rozhraní tak, aby klientovi poskytovalo informace o chybě.

```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>Parametry

*lpszDesc*<br/>
[v] Řetězec popisující chybu. Unicode verze `Error` určuje, že *lpszDesc* je typu LPCOLESTR; verze ANSI určuje typ LPCSTR.

*Iid*<br/>
[v] IID rozhraní definující chybu nebo GUID_NULL (výchozí hodnota), pokud je chyba definována operačním systémem.

*hRes*<br/>
[v] HRESULT, které chcete vrátit volajícímu. Výchozí hodnota je 0. Další podrobnosti o *hRes*naleznete v tématu Poznámky.

*Nid*<br/>
[v] Identifikátor prostředku, kde je uložen řetězec popisu chyby. Tato hodnota by měla ležet mezi 0x0200 a 0xFFFF, včetně. V sestavení chodu dojde k výsledku **ASSERT,** pokud *nID* neindexuje platný řetězec. V sestaveních verzí bude řetězec popisu chyby nastaven na "Neznámá chyba".

*dwHelpID*<br/>
[v] Identifikátor kontextu nápovědy pro chybu.

*soubor lpszHelpFile*<br/>
[v] Cesta a název souboru nápovědy popisující chybu.

*hInst*<br/>
[v] Popisovač prostředku. Ve výchozím nastavení `_AtlModule::GetResourceInstance`je `_AtlModule` tento parametr , kde je globální instance [CAtlModule](../../atl/reference/catlmodule-class.md).

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT. Podrobnosti naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

Chcete-li volat `Error`, `ISupportErrorInfo Interface` musí objekt implementovat rozhraní.

Pokud je parametr *hRes* nenulový, vrátí `Error` hodnotu *hRes*. Pokud *hRes* je nula, pak `Error` první čtyři verze vrácení DISP_E_EXCEPTION. Poslední dvě verze vrátí výsledek makro **MAKE_HRESULT( 1, FACILITY_ITF,** *nID* **)**.

## <a name="ccomcoclassgetobjectclsid"></a><a name="getobjectclsid"></a>CcomcoClass::GetObjectCLSID

Poskytuje konzistentní způsob načítání identifikátoru CLSID objektu.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor třídy objektu.

## <a name="ccomcoclassgetobjectdescription"></a><a name="getobjectdescription"></a>CcomcoClass::Popis getobjectdescription

Tato statická funkce načte textový popis objektu třídy.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>Návratová hodnota

Popis objektu třídy.

### <a name="remarks"></a>Poznámky

Výchozí implementace vrátí hodnotu NULL. Tuto metodu můžete přepsat [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) makry. Příklad:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription`je volána společností `IComponentRegistrar::GetComponents`. `IComponentRegistrar`je rozhraní automatizace, které umožňuje registrovat a odregistrovat jednotlivé součásti v knihovně DLL. Když vytvoříte objekt registrátora součástí pomocí Průvodce projektem knihovny ATL, průvodce automaticky implementuje `IComponentRegistrar` rozhraní. `IComponentRegistrar`obvykle používá Microsoft Transaction Server.

Další informace o Průvodci projektem atl naleznete v článku [Vytvoření projektu atl](../../atl/reference/creating-an-atl-project.md).

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
