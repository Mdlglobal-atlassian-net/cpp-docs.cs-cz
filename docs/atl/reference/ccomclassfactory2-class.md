---
title: "Třída CComClassFactory2 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
dev_langs: C++
helpviewer_keywords: CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5b1626a9ce7ef729416f7e6e1a6d3c60836dbed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 – třída
Tato třída implementuje [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class license>  
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```  
  
#### <a name="parameters"></a>Parametry  
 *licence*  
 Třídu, která implementuje statické následující funkce:  
  
- **verifylicensekey – statické BOOL (BSTR** `bstr` **);**  
  
- **getlicensekey – statické BOOL (DWORD** `dwReserved` **, BSTR\***  `pBstr` **);**  
  
- **statické BOOL IsLicenseValid ();**  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComClassFactory2::CreateInstance](#createinstance)|Vytvoří objekt zadaného CLSID.|  
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|Zadaný klíč licencí vytvoří objekt zadaného CLSID.|  
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Načte informace, které popisují licencování možnosti objektu pro vytváření tříd.|  
|[CComClassFactory2::LockServer](#lockserver)|Zamkne objektu pro vytváření tříd v paměti.|  
|[CComClassFactory2::RequestLicKey](#requestlickey)|Vytvoří a vrátí licenční klíč.|  
  
## <a name="remarks"></a>Poznámky  
 `CComClassFactory2`implementuje [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) rozhraní, což je rozšíření z [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364). **IClassFactory2** ovládací prvky objektu vytváření licence. Spuštění licenční klíč můžete zadat třídu objektu pro vytváření, provádění na licencovanou počítači. Tento licenční klíč umožňuje aplikaci k vytváření instancí objektů při úplné počítač licence neexistuje.  
  
 Objekty knihovny ATL normálně získat objekt třídy odvozené z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), který deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactory2`, zadejte [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) makra v definici třídy objektu. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]  
  
 **CMyLicense**, parametr šablony k `CComClassFactory2`, musí implementovat statické funkce `VerifyLicenseKey`, `GetLicenseKey`, a `IsLicenseValid`. Následuje příklad jednoduchého licence třídy:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2`je odvozena z obou **CComClassFactory2Base** a *licence*. **CComClassFactory2Base**, pak je odvozena z **IClassFactory2** a **CComObjectRootEx\< CComGlobalsThreadModel >**.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CComObjectRootBase`  
  
 `license`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory2`  
  
 `CComClassFactory2`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="createinstance"></a>CComClassFactory2::CreateInstance  
 Vytvoří objekt zadaného CLSID a načte ukazatele rozhraní k tomuto objektu.  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkOuter`  
 [v] Pokud objekt se vytváří v rámci agregace, pak `pUnkOuter` musí být vnější neznámé. V opačném `pUnkOuter` musí být **NULL**.  
  
 `riid`  
 [v] Identifikátory IID požadované rozhraní. Pokud `pUnkOuter` jinou hodnotu než **NULL**, `riid` musí být **IID_IUnknown**.  
  
 `ppvObj`  
 [out] Ukazatel na ukazatel rozhraní identifikovaný `riid`. Pokud objekt nepodporuje toto rozhraní `ppvObj` je nastaven na **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Vyžaduje, aby počítač plně licenci. Pokud licence úplná počítači neexistuje, zavolejte [CreateInstanceLic](#createinstancelic).  
  
##  <a name="createinstancelic"></a>CComClassFactory2::CreateInstanceLic  
 Podobně jako [CreateInstance](#createinstance)kromě toho, že `CreateInstanceLic` vyžaduje licenční klíč.  
  
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
 `pUnkOuter`  
 [v] Pokud objekt se vytváří v rámci agregace, pak `pUnkOuter` musí být vnější neznámé. V opačném `pUnkOuter` musí být **NULL**.  
  
 *pUnkReserved*  
 [v] Nepoužívá se. Musí být **NULL**.  
  
 `riid`  
 [v] Identifikátory IID požadované rozhraní. Pokud `pUnkOuter` jinou hodnotu než **NULL**, `riid` musí být **IID_IUnknown**.  
  
 `bstrKey`  
 [v] Spuštění licenční klíč dříve získány z volání `RequestLicKey`. Tento klíč je potřeba vytvořit objekt.  
  
 `ppvObject`  
 [out] Ukazatel na ukazatel rozhraní určeného `riid`. Pokud objekt nepodporuje toto rozhraní `ppvObject` je nastaven na **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Můžete získat licenční klíč pomocí [RequestLicKey](#requestlickey). Chcete-li vytvořit objekt na počítači bez licence, musí volat `CreateInstanceLic`.  
  
##  <a name="getlicinfo"></a>CComClassFactory2::GetLicInfo  
 Vyplní celé [LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590) struktura s informacemi, které popisují objektu pro vytváření tříd je licencování možností.  
  
```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pLicInfo*  
 [out] Ukazatel na **LICINFO** struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 `fRuntimeKeyAvail` Členem tato struktura Určuje, zda, zadána licenční klíč objektu pro vytváření tříd umožňuje vytvořit na počítači bez licence objekty. *FLicVerified* člen označuje, zda existuje licenci úplné počítače.  
  
##  <a name="lockserver"></a>CComClassFactory2::LockServer  
 Zvýší a sníží počet zámek modulu voláním **_Module::Lock** a **_Module::Unlock**, v uvedeném pořadí.  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>Parametry  
 `fLock`  
 [v] Pokud **TRUE**, počet zámků je zvýšena; jinak hodnota, se odečte počet zámků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 **_Module** odkazuje na globální instance [CComModule](../../atl/reference/ccommodule-class.md) nebo z něj odvozenou třídu.  
  
 Volání metody `LockServer` umožňuje klienta tak, aby udržení na objekt pro vytváření tříd, aby více objektů můžete rychle vytvořit.  
  
##  <a name="requestlickey"></a>CComClassFactory2::RequestLicKey  
 Vytvoří a vrátí licenční klíč, za předpokladu, že `fRuntimeKeyAvail` členem [LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590) struktura je **TRUE**.  
  
```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>Parametry  
 `dwReserved`  
 [v] Nepoužívá se. Musí být nula.  
  
 `pbstrKey`  
 [out] Ukazatel na licenční klíč.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Licenční klíč se vyžaduje pro volání [CreateInstanceLic](#createinstancelic) pro vytvoření objektu na počítači bez licence. Pokud `fRuntimeKeyAvail` je **FALSE**, pak objekty lze vytvořit pouze na plně licencovanou počítači.  
  
 Volání [GetLicInfo](#getlicinfo) k načtení hodnoty z `fRuntimeKeyAvail`.  
  
## <a name="see-also"></a>Viz také  
 [CComClassFactoryAutoThread – třída](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComClassFactorySingleton – třída](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Přehled třídy](../../atl/atl-class-overview.md)
