---
title: "Třída CComAggObject | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
dev_langs: C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0af699e61f487ba8af836a4f544ed4c338d70b4b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomaggobject-class"></a>CComAggObject – třída
Tato třída implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) rozhraní pro agregovaný objekt. Podle definice je agregovaný objekt obsažený v rámci vnějšího objekt. `CComAggObject` Třídy je podobná [CComObject třída](../../atl/reference/ccomobject-class.md)kromě toho, že zpřístupňuje rozhraní, které je přímo přístupný externím klientům.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class contained>  
class CComAggObject : public IUnknown, 
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Parametry  
 `contained`  
 Vlastní třídy odvozené od [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře od dalších rozhraní, které chcete podporovat v objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComAggObject::CComAggObject](#ccomaggobject)|Konstruktor|  
|[CComAggObject:: ~ CComAggObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComAggObject::AddRef](#addref)|Zvýší počet odkazů na agregovaný objekt.|  
|[CComAggObject::CreateInstance](#createinstance)|Tato statická funkce vám umožní vytvořit nový **CComAggObject <** `contained`  **>**  objektu bez režie [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).|  
|[CComAggObject::FinalConstruct](#finalconstruct)|Provede konečnou inicializaci `m_contained`.|  
|[CComAggObject::FinalRelease](#finalrelease)|Provede konečnou zničení `m_contained`.|  
|[CComAggObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|  
|[CComAggObject::Release](#release)|Snižuje počet odkaz na agregovaný objekt.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComAggObject::m_contained](#m_contained)|Delegáti `IUnknown` volání na vnější neznámý.|  
  
## <a name="remarks"></a>Poznámky  
 `CComAggObject`implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) agregovaného objektu. `CComAggObject`má svou vlastní **IUnknown** rozhraní, které jsou oddělené od vnější objekt **IUnknown** rozhraní a udržuje vlastní počet odkazů.  
  
 Další informace o agregace, najdete v článku [základy objektů COM ATL](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComAggObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>CComAggObject::AddRef  
 Zvýší počet odkazů na agregovaný objekt.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku nebo testování.  
  
##  <a name="ccomaggobject"></a>CComAggObject::CComAggObject  
 Konstruktor  
  
```
CComAggObject(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 [v] Vnější neznámý.  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje `CComContainedObject` člen [m_contained](#m_contained)a zvýší počet modulů zámku.  
  
 Destruktor snižuje počet zámek modulu.  
  
##  <a name="dtor"></a>CComAggObject:: ~ CComAggObject  
 Destruktor.  
  
```
~CComAggObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky, volání [FinalRelease](#finalrelease), a snižuje počet zámek modulu.  
  
##  <a name="createinstance"></a>CComAggObject::CreateInstance  
 Tato statická funkce vám umožní vytvořit nový **CComAggObject <** `contained`  **>**  objektu bez režie [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `pp`  
 [out] Ukazatel **CComAggObject\<***obsažené*  **>**  ukazatel. Pokud `CreateInstance` není úspěšné, `pp` je nastaven na **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Objekt vrácený má nulový počet odkaz, takže volání `AddRef` okamžitě, pak použít **verze** k bezplatným odkaz na objekt ukazatele, když jste hotovi.  
  
 Pokud není nutné přímý přístup k objektu, ale přesto chcete vytvořit nový objekt bez režie `CoCreateInstance`, použijte [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) místo.  
  
##  <a name="finalconstruct"></a>CComAggObject::FinalConstruct  
 Volá se během poslední fáze vytváření objektů, tato metoda provádí všechny konečné inicializace [m_contained](#m_contained) člen.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="finalrelease"></a>CComAggObject::FinalRelease  
 Volá se při odstraňování objektu, tato metoda uvolní [m_contained](#m_contained) člen.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComAggObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objekt odvozen z vaší třídy.  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>Parametry  
 `contained`  
 [v] Vlastní třídy odvozené od [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře od dalších rozhraní, které chcete podporovat v objektu.  
  
### <a name="remarks"></a>Poznámky  
 Všechny **IUnknown** volá prostřednictvím `m_contained` jsou delegovanými na vnější neznámý.  
  
##  <a name="queryinterface"></a>CComAggObject::QueryInterface  
 Načte ukazatel na požadované rozhraní.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor rozhraní požadováno.  
  
 `ppvObject`  
 [out] Ukazatel na ukazatel rozhraní identifikovaný `iid`. Pokud objekt nepodporuje toto rozhraní `ppvObject` je nastaven na **NULL**.  
  
 `pp`  
 [out] Ukazatel na ukazatel rozhraní typ identifikovat `Q`. Pokud objekt nepodporuje toto rozhraní `pp` je nastaven na **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je požadované rozhraní **IUnknown**, `QueryInterface` vrací ukazatel na agregovaného objektu vlastní **IUnknown** a zvýší počet odkazů. Jinak tato metoda dotazuje na rozhraní prostřednictvím `CComContainedObject` člen [m_contained](#m_contained).  
  
##  <a name="release"></a>CComAggObject::Release  
 Snižuje počet odkaz na agregovaný objekt.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení pro ladění **verze** vrátí hodnotu, která může být užitečné pro diagnostiku nebo testování. V sestavení pro bez ladění **verze** vždy vrátí hodnotu 0.  
  
## <a name="see-also"></a>Viz také  
 [CComObject – třída](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [Přehled třídy](../../atl/atl-class-overview.md)
