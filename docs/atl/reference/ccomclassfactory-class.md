---
title: Třída CComClassFactory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a144f4ff9902a633933ae556df872a9d55a5409
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359242"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory – třída
Tato třída implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComClassFactory 
   : public IClassFactory,  
     public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComClassFactory::CreateInstance](#createinstance)|Vytvoří objekt zadaného CLSID.|  
|[CComClassFactory::LockServer](#lockserver)|Zamkne objektu pro vytváření tříd v paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `CComClassFactory` implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) rozhraní, která obsahuje metody pro vytvoření objektu konkrétní CLSID, jakož i zámek objektu pro vytváření tříd v paměti umožňuje rychleji vytvořit nové objekty. **IClassFactory** pro každou třídu, která zaregistrujete v registru systému a můžete přiřadit identifikátor CLSID, musí být implementována.  
  
 Objekty knihovny ATL normálně získat objekt třídy odvozené z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), který deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete-li přepsat toto výchozí nastavení, zadejte jednu z `DECLARE_CLASSFACTORY` *XXX* makra v definici vaší třídy. Například [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) makro používá pro zadanou třídu objektu pro vytváření tříd:  
  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]  
  
 Výše uvedené definice třídy určuje, že **CMyClassFactory** se použije jako zdroj tříd výchozí objektu. **CMyClassFactory** musí být odvozeny od `CComClassFactory` a přepsání `CreateInstance`.  
  
 ATL poskytuje tři makra s objekt třídy:  
  
- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) používá [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), který řídí vytváření prostřednictvím licenci.  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) používá [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), která vytvoří objekty v několika Apartment.  
  
- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) používá [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), který vytvoří jeden [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="createinstance"></a>  CComClassFactory::CreateInstance  
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
  
##  <a name="lockserver"></a>  CComClassFactory::LockServer  
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
  
 Volání metody `LockServer` umožňuje klienta tak, aby udržení na objekt pro vytváření tříd, aby více objektů lze rychle vytvořit.  
  
## <a name="see-also"></a>Viz také  
 [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Přehled třídy](../../atl/atl-class-overview.md)
