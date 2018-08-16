---
title: CComObject – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89a909b715633488cff37fa87ea5950681e208cd
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881838"
---
# <a name="ccomobject-class"></a>CComObject – třída
Tato třída implementuje `IUnknown` pro neagregovaná objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>  
class CComObject : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 *základ*  
 Vaše třída odvozena od [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře jako z jiných rozhraní, které chcete podporovat na objekt.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObject::CComObject](#ccomobject)|Konstruktor|  
|[CComObject:: ~ CComObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObject::AddRef](#addref)|Zvýší počet odkazů na objekt.|  
|[CComObject::CreateInstance](#createinstance)|(Statické) Vytvoří novou `CComObject` objektu.|  
|[CComObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|  
|[CComObject::Release](#release)|Sníží počet odkaz na objekt.|  
  
## <a name="remarks"></a>Poznámky  
 `CComObject` implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pro neagregovaná objekt. Nicméně volání `QueryInterface`, `AddRef`, a `Release` se deleguje na `CComObjectRootEx`.  
  
 Další informace o používání `CComObject`, najdete v článku [základy ATL COM objekty](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `CComObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>  CComObject::AddRef  
 Zvýší počet odkazů na objekt.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato funkce vrací nový počet odkazů zvýšena na objekt. Tato hodnota může být užitečné pro diagnostiku a testování.  
  
##  <a name="ccomobject"></a>  CComObject::CComObject  
 Konstruktor inkrementuje počet zámků modulů.  
  
```
CComObject(void* = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 **Typ void\***  
 [in] Tento nepojmenovaný parametr se nepoužívá. Existuje pro symetrie s jinými **CCom***XXX*`Object`*XXX* konstruktory.  
  
### <a name="remarks"></a>Poznámky  
 Sníží destruktor ho.  
  
 Pokud `CComObject`-odvozeného objektu je úspěšně vytvořený **nové** operátor, počet počáteční odkazů je 0. Pokud chcete nastavit počet odkazů na správnou hodnotu (1), ujistěte se, volání [AddRef](#addref) funkce.  
  
##  <a name="dtor"></a>  CComObject:: ~ CComObject  
 Destruktor.  
  
```
CComObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky, volání [FinalRelease](ccomobjectrootex-class.md#finalrelease), a sníží počet modul zámku.  

  
##  <a name="createinstance"></a>  CComObject::CreateInstance  
 Tato statická funkce vám umožní vytvořit nový **CComObject <** `Base` **>** objekt, bez režie [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```  
  
### <a name="parameters"></a>Parametry  
 *str*  
 [out] Ukazatel **CComObject <** `Base` **>** ukazatele. Pokud `CreateInstance` neproběhne úspěšně, *pp* nastaven na hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Objekt vrácený má nulový počet odkaz, takže volání `AddRef` okamžitě, pak použijte `Release` uvolnit odkaz na ukazatel objektu, až budete hotovi.  
  
 Pokud není nutné přímý přístup k objektu, ale přesto chcete vytvořit nový objekt bez režie `CoCreateInstance`, použijte [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) místo.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]  
  
 [!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]  
  
##  <a name="queryinterface"></a>  CComObject::QueryInterface  
 Načte ukazatel na požadované rozhraní.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor IID*  
 [in] Identifikátor se požadované rozhraní.  
  
 *ppvObject*  
 [out] Ukazatel na ukazatel rozhraní, který je identifikován *iid*. Pokud objekt nepodporuje toto rozhraní *ppvObject* nastaven na hodnotu NULL.  
  
 *str*  
 [out] Ukazatel na ukazatel rozhraní, které jsou určeny podle typu `Q`. Pokud objekt nepodporuje toto rozhraní *pp* nastaven na hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
##  <a name="release"></a>  CComObject::Release  
 Sníží počet odkaz na objekt.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato funkce vrací nový počet odkazů sníží na objekt. V sestavení pro ladění může být vrácenou hodnotu užitečné pro diagnostiku a testování. V sestaveních bez ladění `Release` vždy vrátí hodnotu 0.  
  
## <a name="see-also"></a>Viz také  
 [CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)   
 [CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [Přehled tříd](../../atl/atl-class-overview.md)
