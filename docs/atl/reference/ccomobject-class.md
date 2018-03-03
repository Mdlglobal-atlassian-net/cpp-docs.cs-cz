---
title: "Třída CComObject | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27da00e09ca88cc06b8bafed8f8601dac756fd34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomobject-class"></a>CComObject – třída
Tato třída implementuje **IUnknown** neagregovaná objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>  
class CComObject : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Vlastní třídy odvozené od [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře od dalších rozhraní, které chcete podporovat v objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObject::CComObject](#ccomobject)|Konstruktor|  
|[CComObject:: ~ CComObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObject::AddRef](#addref)|Zvýší počet odkaz na objekt.|  
|[CComObject::CreateInstance](#createinstance)|(Statické) Vytvoří nový `CComObject` objektu.|  
|[CComObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|  
|[CComObject::Release](#release)|Snižuje počet odkaz na objekt.|  
  
## <a name="remarks"></a>Poznámky  
 `CComObject`implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) neagregovaná objektu. Ale volání `QueryInterface`, `AddRef`, a **verze** jsou přeneseny na `CComObjectRootEx`.  
  
 Další informace o používání `CComObject`, najdete v článku [základy objektů COM ATL](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `CComObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>CComObject::AddRef  
 Zvýší počet odkaz na objekt.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato funkce vrátí počet nových zvýšena odkaz na objekt. Tato hodnota může být užitečná pro diagnostiku a testování.  
  
##  <a name="ccomobject"></a>CComObject::CComObject  
 Konstruktor zvýší počet modulů zámku.  
  
```
CComObject(void* = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 **void\***  
 [v] Tento nepojmenovaný parametr se nepoužívá. Existuje pro symetrie s jinými **CCom***XXX*`Object`*XXX* konstruktory.  
  
### <a name="remarks"></a>Poznámky  
 Snižuje destruktor ho.  
  
 Pokud `CComObject`-odvozené objektu je úspěšně vytvořená pomocí **nové** operátor, počet počáteční odkaz na hodnotu 0. Nastavit počet odkazů na správnou hodnotu (1), ujistěte se, volání [addref –](#addref) funkce.  
  
##  <a name="dtor"></a>CComObject:: ~ CComObject  
 Destruktor.  
  
```
CComObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky, volání [FinalRelease](ccomobjectrootex-class.md#finalrelease), a snižuje počet zámek modulu.  

  
##  <a name="createinstance"></a>CComObject::CreateInstance  
 Tato statická funkce vám umožní vytvořit nový **CComObject <** `Base`  **>**  objekt, bez nutnosti [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `pp`  
 [out] Ukazatel **CComObject <** `Base`  **>**  ukazatel. Pokud `CreateInstance` není úspěšné, `pp` je nastaven na **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Objekt vrácený má nulový počet odkaz, takže volání `AddRef` okamžitě, pak použít **verze** k bezplatným odkaz na objekt ukazatele, když jste hotovi.  
  
 Pokud není nutné přímý přístup k objektu, ale přesto chcete vytvořit nový objekt bez režie `CoCreateInstance`, použijte [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) místo.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]  
  
 [!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]  
  
##  <a name="queryinterface"></a>CComObject::QueryInterface  
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
  
##  <a name="release"></a>CComObject::Release  
 Snižuje počet odkaz na objekt.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato funkce vrátí počet nových odečte odkaz na objekt. V sestavení pro ladění může být návratovou hodnotu užitečné pro diagnostiku nebo testování. V sestavení pro bez ladění **verze** vždy vrátí hodnotu 0.  
  
## <a name="see-also"></a>Viz také  
 [CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)   
 [CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [Přehled třídy](../../atl/atl-class-overview.md)
