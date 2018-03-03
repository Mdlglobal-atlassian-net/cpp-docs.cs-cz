---
title: "Třída CComClassFactorySingleton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 165bc85a0b00ac8186e5a145a75c4478335b5e0e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton – třída
Tato třída odvozená z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class CComClassFactorySingleton : public CComClassFactory
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy.  
  
 `CComClassFactorySingleton`odvozená z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu. Každé volání `CreateInstance` metoda jednoduše dotazuje tohoto objektu pro ukazatele rozhraní.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Dotazy `m_spObj` pro ukazatele rozhraní.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComClassFactorySingleton::m_spObj](#m_spobj)|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objekt vytvořený pomocí `CComClassFactorySingleton`.|  
  
## <a name="remarks"></a>Poznámky  
 Objekty knihovny ATL normálně získat objekt třídy odvozené z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), který deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactorySingleton`, zadejte [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) makra v definici třídy objektu. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)  
  
 `CComClassFactorySingleton`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="createinstance"></a>CComClassFactorySingleton::CreateInstance  
 Volání `QueryInterface` prostřednictvím [m_spObj](#m_spobj) načíst ukazatele rozhraní.  
  
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
  
##  <a name="m_spobj"></a>CComClassFactorySingleton::m_spObj  
 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objekt vytvořený pomocí `CComClassFactorySingleton`.  
  
```
CComPtr<IUnknown> m_spObj;
```  
  
### <a name="remarks"></a>Poznámky  
 Každé volání [CreateInstance](#createinstance) metoda jednoduše dotazuje tohoto objektu pro ukazatele rozhraní.  
  
 Všimněte si, že aktuální formu `m_spObj` uvede narušující změně z způsob, `CComClassFactorySingleton` práce na incidentu v předchozích verzích ATL. V předchozích verzích `CComClassFactorySingleton` objekt byl vytvořen ve stejnou dobu jako objekt pro vytváření tříd, během inicializace serveru. V jazyce Visual C++ .NET 2003 je objekt líné, vytvořen při prvním požadavku. Tato změna může způsobit chyby v programech, které spoléhají na včasné inicializace.  
  
## <a name="see-also"></a>Viz také  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 – třída](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactoryAutoThread – třída](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Přehled třídy](../../atl/atl-class-overview.md)
