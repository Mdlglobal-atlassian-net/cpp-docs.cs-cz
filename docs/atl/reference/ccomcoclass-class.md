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
ms.openlocfilehash: 51da70cc1972e6a69e28d7699703f803b6fa8701
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630695"
---
# <a name="ccomcoclass-class"></a>CComCoClass – třída

Tato třída poskytuje metody pro vytvoření instance třídy a získání jeho vlastnosti.

## <a name="syntax"></a>Syntaxe

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `CComCoClass`.

*pclsid*<br/>
Ukazatel na identifikátor CLSID objektu.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComCoClass::CreateInstance](#createinstance)|(Statické) Vytvoří instanci třídy a dotazy pro rozhraní.|
|[CComCoClass::Error](#error)|(Statické) Vrátí klientovi bohaté chybové informace.|
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|(Statické) Vrátí identifikátor třídy objektu.|
|[CComCoClass::GetObjectDescription](#getobjectdescription)|(Statické) Přepsání nastavení za účelem vrácení popis objektu.|

## <a name="remarks"></a>Poznámky

`CComCoClass` poskytuje metody pro načítání CLSID objektu, nastavení informací o chybách a vytváření instancí třídy. Všechny třídy registrován v mapě objektů by měl být odvozen od `CComCoClass`.

`CComCoClass` také definuje výchozí třídy objektu pro vytváření a agregace model objektu. `CComCoClass` používá následující dvě makra:

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) deklaruje objekt pro vytváření tříd bude [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) deklaruje, že objekt se dají agregovat.

Buď tato výchozí nastavení můžete přepsat zadáním jiného makra v definici třídy. Chcete-li například použít [ccomclassfactory2 –](../../atl/reference/ccomclassfactory2-class.md) místo `CComClassFactory`, zadejte [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) – makro:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="createinstance"></a>  CComCoClass::CreateInstance

Pomocí těchto `CreateInstance` funkce k vytvoření instance COM objektu a načíst ukazatel rozhraní bez použití rozhraní API modelu COM.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>Parametry

*Q*<br/>
Rozhraní modelu COM, která má být vrácena prostřednictvím *pp*.

*punkOuter*<br/>
[in] Vnější neznámá nebo řídící neznámou agregace.

*str*<br/>
[out] Adresa proměnné ukazatele, která přijímá ukazatel požadovaná rozhraní, pokud bude úspěšné vytvoření.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT. Zobrazit [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance) v sadě Windows SDK pro popis možných vrácených hodnot.

### <a name="remarks"></a>Poznámky

První přetížení této funkce použít pro vytvoření objektu typické; druhé přetížení použijte, pokud je potřeba započítat vytvářený objekt.

ATL – třídy implementace požadovaný objekt modelu COM (tedy třídu použitou jako první parametr šablony [CComCoClass](../../atl/reference/ccomcoclass-class.md)) musí být ve stejném projektu jako volající kód. Vytváření objektů COM se provádí zaregistrovaný pro tuto třídu knihovny ATL pro vytváření tříd.

Tyto funkce jsou užitečné pro vytváření objektů, které budete mít zabráněno externě vytvořitelný pomocí [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) – makro. Jsou také užitečné v situacích, ve kterém chcete se vyhnout rozhraní API modelu COM z důvodu efektivity.

Všimněte si, že rozhraní *Q* musí mít IID s ním spojená, který se dá načíst pomocí [__uuidof](../../cpp/uuidof-operator.md) operátor.

### <a name="example"></a>Příklad

V následujícím příkladu `CDocument` ATL – třídy generované v Průvodci pochází z `CComCoClass` , který implementuje `IDocument` rozhraní. Třída je registrována v mapě objektů s OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO – makro, aby klienti nelze vytvořit instance dokumentu pomocí [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance). `CApplication` je CoClass, která poskytuje metodu na jednom vlastním rozhraní modelu COM pro vytvoření instancí třídy dokumentu. Kód uvedený níže ukazuje, jak snadné ji k vytvoření instance třídy dokumentu pomocí `CreateInstance` člen zděděno z `CComCoClass` základní třídy.

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

##  <a name="error"></a>  CComCoClass::Error

Tato statická funkce nastaví `IErrorInfo` rozhraní k poskytování informací o chybách klienta.

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
[in] Řetězec popisující chybu. Verze Unicode `Error` Určuje, že *lpszDesc* je typ LPCOLESTR; verze ANSI Určuje typ LPCSTR.

*identifikátor IID*<br/>
[in] Identifikátor IID rozhraní definování chyb nebo GUID_NULL (výchozí hodnota), pokud chyba není definován v operačním systému.

*hRes*<br/>
[in] Hodnota HRESULT, který chcete vrátit zpět volajícímu. Výchozí hodnota je 0. Další podrobnosti o *hRes*, naleznete v oddílu Poznámky.

*nID*<br/>
[in] Identifikátor prostředku řetězce popisu chyby se mají ukládat. Tato hodnota by měla být mezi hodnotu 0x0200 a 0xFFFF (včetně). V sestavení ladění **ASSERT** dojde-li *nID* index není platný řetězec. V sestaveních pro vydání řetězce popisu chyby bude nastavena na "Neznámá chyba".

*dwHelpID*<br/>
[in] Identifikátor kontextu pomoc pro chybu.

*lpszHelpFile*<br/>
[in] Cesta a název souboru nápovědy popisující chybu.

*hInst*<br/>
[in] Popisovač pro prostředek. Ve výchozím nastavení, je tento parametr `_AtlModule::GetResourceInstance`, kde `_AtlModule` je globální instanci [catlmodule –](../../atl/reference/catlmodule-class.md).

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Chcete-li volat `Error`, musí implementovat objekt `ISupportErrorInfo Interface` rozhraní.

Pokud *hRes* parametr nenulovou hodnotu, je pak `Error` vrací hodnotu *hRes*. Pokud *hRes* je nula, pak první čtyři verzích `Error` vrátí DISP_E_EXCEPTION. Poslední dvě verze vrácení výsledku makra **MAKE_HRESULT (1, FACILITY_ITF,** *nID* **)**.

##  <a name="getobjectclsid"></a>  CComCoClass::GetObjectCLSID

Zajišťuje konzistentní způsob získávání CLSID objektu.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor třídy objektu.

##  <a name="getobjectdescription"></a>  CComCoClass::GetObjectDescription

Tato statická funkce načte textový popis objektu třídy.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>Návratová hodnota

Popis objektu třídy.

### <a name="remarks"></a>Poznámky

Výchozí implementace vrací hodnotu NULL. Mohou přepsat tuto metodu s [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) – makro. Příklad:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription` je volán `IComponentRegistrar::GetComponents`. `IComponentRegistrar` je rozhraní automatizace, která umožňuje vytvářet a rušit registraci jednotlivých komponent v knihovně DLL. Při vytváření objektu registrátora komponent pomocí Průvodce projektem ATL, průvodce automaticky provede `IComponentRegistrar` rozhraní. `IComponentRegistrar` se obvykle používá Microsoft Transaction Server.

Další informace o Průvodce projektem ATL naleznete v článku [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
