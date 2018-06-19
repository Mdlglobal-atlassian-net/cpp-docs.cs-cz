---
title: Třída CComClassFactoryAutoThread | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 601f67d4a753dd617b9d7a3d5856ca64588a66c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363120"
---
# <a name="ccomclassfactoryautothread-class"></a>CComClassFactoryAutoThread – třída
Tato třída implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) rozhraní a umožňuje vytvořit v několika Apartment objekty.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComClassFactoryAutoThread 
   : public IClassFactory, 
     public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|Vytvoří objekt zadaného CLSID.|  
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Zamkne objektu pro vytváření tříd v paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `CComClassFactoryAutoThread` je podobná [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale umožňuje vytvořit v několika Apartment objekty. Abyste mohli využívat této podpory, odvozena EXE modul z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Objekty knihovny ATL normálně získat objekt třídy odvozené z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), který deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactoryAutoThread`, zadejte [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra v definici třídy objektu. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 `CComClassFactoryAutoThread`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="createinstance"></a>  CComClassFactoryAutoThread::CreateInstance  
 Vytvoří objekt zadaného CLSID a načte ukazatele rozhraní k tomuto objektu.  
  
```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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
 Pokud modul je odvozena z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` první vybere vlákno k vytvoření objektu v přidružené typu apartment.  
  
##  <a name="lockserver"></a>  CComClassFactoryAutoThread::LockServer  
 Zvýší a sníží počet zámek modulu voláním **_Module::Lock** a **_Module::Unlock**, v uvedeném pořadí.  
  
```
STDMETHODIMP LockServer(BOOL fLock);
```  
  
### <a name="parameters"></a>Parametry  
 `fLock`  
 [v] Pokud **TRUE**, počet zámků je zvýšena; jinak hodnota, se odečte počet zámků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Při použití `CComClassFactoryAutoThread`, **_Module** obvykle odkazuje na globální instance [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Volání metody `LockServer` umožňuje klienta tak, aby udržení na objekt pro vytváření tříd, aby více objektů můžete rychle vytvořit.  
  
## <a name="see-also"></a>Viz také  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 – třída](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactorySingleton – třída](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Přehled třídy](../../atl/atl-class-overview.md)
