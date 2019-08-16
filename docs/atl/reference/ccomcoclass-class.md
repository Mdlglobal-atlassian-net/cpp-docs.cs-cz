---
title: CComCoClass – třída
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
ms.openlocfilehash: 5b4e39fa4d93893d288bb8de03d8a71b671be087
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497401"
---
# <a name="ccomcoclass-class"></a>CComCoClass – třída

Tato třída poskytuje metody pro vytváření instancí třídy a získání jejích vlastností.

## <a name="syntax"></a>Syntaxe

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `CComCoClass`odvozena z.

*pclsid*<br/>
Ukazatel na CLSID objektu.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComCoClass:: CreateInstance](#createinstance)|Tras Vytvoří instanci třídy a dotazy pro rozhraní.|
|[CComCoClass:: Error](#error)|Tras Vrátí klientovi informace s bohatou chybou.|
|[CComCoClass:: GetObjectCLSID](#getobjectclsid)|Tras Vrátí identifikátor třídy objektu.|
|[CComCoClass:: GetObjectDescription](#getobjectdescription)|Tras Přepsáním vrátíte popis objektu.|

## <a name="remarks"></a>Poznámky

`CComCoClass`poskytuje metody pro načtení identifikátoru CLSID objektu, nastavení informací o chybách a vytváření instancí třídy. Jakákoliv třída registrovaná v mapě objektu by měla být odvozena `CComCoClass`z.

`CComCoClass`definuje také výchozí objekt pro vytváření tříd a agregaci pro váš objekt. `CComCoClass`používá následující dvě makra:

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) Deklaruje objekt pro vytváření tříd, který bude [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) Deklaruje, že objekt může být agregován.

Jedno z těchto výchozích hodnot lze přepsat zadáním jiného makra v definici třídy. Chcete-li například použít [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) namísto `CComClassFactory`, zadejte makro [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) :

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="createinstance"></a>CComCoClass:: CreateInstance

Pomocí těchto `CreateInstance` funkcí můžete vytvořit instanci objektu COM a načíst ukazatel rozhraní bez použití rozhraní API modelu COM.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>Parametry

*Q*<br/>
Rozhraní COM, které má být vráceno pomocí *PP*.

*punkOuter*<br/>
pro Vnější neznámý nebo řídící neznámý druh agregace.

*pp*<br/>
mimo Adresa proměnné ukazatele, která obdrží požadovaný ukazatel rozhraní, pokud je vytváření úspěšné.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT. Popis možných vrácených hodnot naleznete v tématu [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) v Windows SDK.

### <a name="remarks"></a>Poznámky

Pro typické vytvoření objektu použijte první přetížení této funkce; druhé přetížení použijte v případě, že potřebujete agregovat vytvářený objekt.

Třída ATL implementující požadovaný objekt modelu COM (to znamená, že třída použitá jako první parametr šablony pro [CComCoClass](../../atl/reference/ccomcoclass-class.md)) musí být ve stejném projektu jako volající kód. Vytvoření objektu COM je prováděno objektem pro vytváření tříd zaregistrovaným pro tuto třídu ATL.

Tyto funkce jsou užitečné pro vytváření objektů, u kterých se vám zabránilo externě vytvořitelné pomocí makra [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) . Jsou také užitečné v situacích, kdy chcete zabránit rozhraní API modelu COM z důvodů efektivity.

Všimněte si, že k rozhraní *Q* musí být přidružen identifikátor IID, který lze načíst pomocí operátoru [__uuidof](../../cpp/uuidof-operator.md) .

### <a name="example"></a>Příklad

V následujícím příkladu `CDocument` je vygenerovaná Průvodce třídou ATL odvozenou z `CComCoClass` `IDocument` rozhraní, které implementuje rozhraní. Třída je registrována v mapě objektů pomocí makra OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO, takže klienti nemohou vytvářet instance dokumentu pomocí funkce [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance). `CApplication`je třída typu coclass, která poskytuje metodu na jednom z vlastních rozhraní COM k vytvoření instancí třídy dokumentu. Následující kód ukazuje, jak snadné je vytvořit instance třídy dokumentu pomocí `CreateInstance` člena zděděného `CComCoClass` ze základní třídy.

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

##  <a name="error"></a>CComCoClass:: Error

Tato statická funkce nastaví `IErrorInfo` rozhraní pro poskytování informací o chybách klientovi.

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
pro Řetězec popisující chybu. Verze `Error` Unicode určuje, že *lpszDesc* je typu LPCOLESTR; verze ANSI určuje typ LPCSTR.

*iid*<br/>
pro Identifikátor IID rozhraní definující chybu nebo GUID_NULL (výchozí hodnota), pokud je chyba definována operačním systémem.

*hRes*<br/>
pro Hodnota HRESULT, kterou chcete vrátit volajícímu. Výchozí hodnota je 0. Další podrobnosti o *hRes*najdete v tématu poznámky.

*nID*<br/>
pro Identifikátor prostředku, kde je uložen řetězec s popisem chyby. Tato hodnota by se měla nacházet mezi 0x0200 a 0xFFFF (včetně). V sestavení ladění bude výsledek **vyhodnocení** v případě, že *NID* neindexuje platný řetězec. V sestavení vydaných verzí se řetězec popisu chyby nastaví na "Neznámá chyba".

*dwHelpID*<br/>
pro Identifikátor kontextu nápovědu pro chybu.

*lpszHelpFile*<br/>
pro Cesta a název souboru Help popisujícího chybu.

*hInst*<br/>
pro Popisovač prostředku. Ve výchozím nastavení je `_AtlModule::GetResourceInstance`tento parametr, kde `_AtlModule` je globální instancí třídy [CAtlModule](../../atl/reference/catlmodule-class.md).

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Chcete- `Error`li volat, objekt musí `ISupportErrorInfo Interface` implementovat rozhraní.

Pokud je parametr *hRes* nenulový, `Error` vrátí hodnotu *hRes*. Pokud má *hRes* hodnotu nula, pak první čtyři verze `Error` návratového DISP_E_EXCEPTION. Poslední dvě verze vrátí výsledek makra **MAKE_HRESULT (1, FACILITY_ITF,** *NID* **)** .

##  <a name="getobjectclsid"></a>CComCoClass:: GetObjectCLSID

Poskytuje konzistentní způsob načítání identifikátoru CLSID objektu.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor třídy objektu.

##  <a name="getobjectdescription"></a>CComCoClass:: GetObjectDescription

Tato statická funkce načte textový popis objektu třídy.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>Návratová hodnota

Popis objektu třídy.

### <a name="remarks"></a>Poznámky

Výchozí implementace vrací hodnotu NULL. Tuto metodu můžete přepsat pomocí makra [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) . Příklad:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription`je volána nástrojem `IComponentRegistrar::GetComponents`. `IComponentRegistrar`je automatizační rozhraní, které umožňuje registrovat a odregistrovat jednotlivé komponenty v knihovně DLL. Při vytváření objektu registrátora komponent pomocí Průvodce projektem ATL Průvodce bude `IComponentRegistrar` rozhraní automaticky implementovat. `IComponentRegistrar`je obvykle používán serverem Microsoft Transaction Server.

Další informace o Průvodci projektem ATL naleznete v článku [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
