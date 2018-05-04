---
title: Třída CComCoClass | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
dev_langs:
- C++
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 738d7e937acf2d3299be97b4f091c698582911d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ccomcoclass-class"></a>CComCoClass – třída
Tato třída poskytuje metody pro vytvoření instance třídy a získání jeho vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, const CLSID* pclsid = &CLSID_NULL>  
class CComCoClass
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `CComCoClass`.  
  
 *pclsid*  
 Ukazatel na CLSID objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCoClass::CreateInstance](#createinstance)|(Statické) Vytvoří instanci třídy a dotazy na rozhraní.|  
|[CComCoClass::Error](#error)|(Statické) Vrátí informace o chybě bohaté klientovi.|  
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|(Statické) Vrátí identifikátor třídy objektu.|  
|[CComCoClass::GetObjectDescription](#getobjectdescription)|(Statické) Přepsání vrátit popis objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CComCoClass` poskytuje metody pro načítání CLSID objektu, nastavení informací o chybách a vytváření instancí třídy. Jakákoli třída zaregistrovaný v [mapování objektu](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f) by měl být odvozen od `CComCoClass`.  
  
 `CComCoClass` také definuje výchozí třídu objektu pro vytváření a agregaci modelu pro objekt. `CComCoClass` používá následující dvě makra:  
  
- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) deklaruje objektu pro vytváření tříd jako [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).  
  
- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) deklaruje, že se dají agregovat objektu.  
  
 Buď tato výchozí nastavení můžete přepsat zadáním jiného makra v definici vaší třídy. Chcete-li například použít [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) místo `CComClassFactory`, zadejte [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) makro:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="createinstance"></a>  CComCoClass::CreateInstance  
 Pomocí těchto `CreateInstance` funkce vytvořit instanci třídy COM objektu a načíst ukazatele rozhraní bez použití rozhraní API modelu COM.  
  
```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `Q`  
 Rozhraní COM, která má být vrácen prostřednictvím `pp`.  
  
 *punkOuter*  
 [v] Vnější neznámý nebo řízení Neznámý agregace.  
  
 `pp`  
 [out] Adresa ukazatel proměnné, která obdrží ukazatele požadované rozhraní, pokud je vytvoření úspěšné.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu. V tématu [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615) ve Windows SDK pro popis možné vrácené hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Použijte první přetížení tuto funkci pro vytvoření objektu typické; Pokud budete potřebovat k agregaci objekt vytváří, použijte druhý přetížení.  
  
 Třídy ATL implementace požadovaný objekt COM (který je třída, která slouží jako první parametr šablony [CComCoClass](../../atl/reference/ccomcoclass-class.md)) musí být ve stejném projektu jako volající kód. Vytvoření objektu COM se provádí pomocí objektu pro vytváření tříd zaregistrovat pro tuto třídu ATL.  
  
 Tyto funkce jsou užitečné pro vytváření objektů, které mají bránily se externě vytvořitelné pomocí [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) makro. Jsou užitečné v situacích, kde chcete vyhnout rozhraní API modelu COM z důvodů efektivitu.  
  
 Všimněte si, že rozhraní `Q` musí mít IID s ním spojená, který se dá načíst pomocí [__uuidof –](../../cpp/uuidof-operator.md) operátor.  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu `CDocument` ATL třídy generované v průvodci je odvozený od `CComCoClass` , která implementuje **IDocument** rozhraní. Třída je registrována v mapování objektu s `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO` makro, klienti nelze vytvořit instance dokumentu pomocí [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615). `CApplication` je třída typu CoClass, která poskytuje metodu na jednom vlastní rozhraní modelu COM, k vytvoření instance třídy dokumentu. Kód uvedený níže ukazuje, jak snadno ji k vytvoření instance třídy dokumentů pomocí `CreateInstance` člen zděděno z `CComCoClass` základní třídy.  
  
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
 `lpszDesc`  
 [v] Řetězec popisující chybu. Unicode verze `Error` Určuje, že `lpszDesc` je typu **LPCOLESTR**; verze ANSI Určuje typ `LPCSTR`.  
  
 `iid`  
 [v] Identifikátory IID rozhraní definování chyba nebo `GUID_NULL` (výchozí hodnota) Pokud chyba je definována v operačním systému.  
  
 `hRes`  
 [v] `HRESULT` Chcete vrácen volajícímu. Výchozí hodnota je 0. Další podrobnosti o `hRes`, najdete v části poznámky.  
  
 `nID`  
 [v] Identifikátor prostředku, uloží řetězec popis chyby. Tato hodnota by měla být mezi hodnotu 0x0200 a 0xFFFF, (včetně). V sestavení pro ladění **ASSERT** dojde, pokud `nID` index není platný řetězec. V sestavení pro vydání řetězec popis chyby. bude nastavena na "Neznámá chyba."  
  
 `dwHelpID`  
 [v] Identifikátor nápovědy Kontext chyby.  
  
 `lpszHelpFile`  
 [v] Cesta a název souboru nápovědy popisující chybu.  
  
 `hInst`  
 [v] Popisovač pro prostředek. Ve výchozím nastavení je tento parametr **_AtlModule::GetResourceInstance**, kde **_AtlModule** je globální instance [CAtlModule](../../atl/reference/catlmodule-class.md).  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu. Podrobnosti najdete v tématu poznámky.  
  
### <a name="remarks"></a>Poznámky  
 K volání `Error`, musí implementovat objektu `ISupportErrorInfo Interface` rozhraní.  
  
 Pokud `hRes` parametr je nenulové hodnoty, pak `Error` vrací hodnotu `hRes`. Pokud `hRes` nula, pak je první čtyři verze `Error` vrátit `DISP_E_EXCEPTION`. Poslední dvě verze vrátit výsledek makro **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)**.  
  
##  <a name="getobjectclsid"></a>  CComCoClass::GetObjectCLSID  
 Zajišťuje konzistentní způsob načítání CLSID objektu.  
  
```
static const CLSID& WINAPI GetObjectCLSID();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor třídy objektu.  
  
##  <a name="getobjectdescription"></a>  CComCoClass::GetObjectDescription  
 Tato statická funkce načte textový popis pro třídu objektu.  
  
```
static LPCTSTR WINAPI GetObjectDescription();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popis objektu třídy.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace vrací **NULL**. Mohou přepsat tuto metodu s [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) makro. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]  
  
 `GetObjectDescription` je volána metodou **IComponentRegistrar::GetComponents**. **IComponentRegistrar** je automatizace rozhraní, které vám umožní zaregistrovat a zrušit registraci jednotlivých součástí v nástroji knihovny DLL. Když vytvoříte objekt součást registrátora s Průvodce projektem ATL, průvodce bude automaticky provádět **IComponentRegistrar** rozhraní. **IComponentRegistrar** se obvykle používá server Microsoft transakce.  
  
 Další informace o Průvodci projektu knihovny ATL, najdete v článku [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
