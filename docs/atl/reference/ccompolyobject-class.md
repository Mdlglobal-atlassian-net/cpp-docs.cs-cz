---
title: "Třída CComPolyObject | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3518fd5936c4871e99eaf597f12fb3ab7cc8aff6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccompolyobject-class"></a>CComPolyObject – třída
Tato třída implementuje **IUnknown** pro agregovaná nebo neagregovaná objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class contained>  
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Parametry  
 `contained`  
 Vlastní třídy odvozené od [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře od dalších rozhraní, které chcete podporovat v objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Konstruktor|  
|[CComPolyObject:: ~ CComPolyObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComPolyObject::AddRef](#addref)|Zvýší počet odkazů objektu.|  
|[CComPolyObject::CreateInstance](#createinstance)|(Statické) Umožňuje vytvořit novou **CComPolyObject <** `contained`  **>**  objektu bez režie [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).|  
|[CComPolyObject::FinalConstruct](#finalconstruct)|Provede konečnou inicializaci `m_contained`.|  
|[CComPolyObject::FinalRelease](#finalrelease)|Provede konečnou zničení `m_contained`.|  
|[CComPolyObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|  
|[CComPolyObject::Release](#release)|Snižuje počet odkaz objekt.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComPolyObject::m_contained](#m_contained)|Delegáti **IUnknown** volá na vnější neznámý, pokud je objekt agregován nebo k **IUnknown** objektu, pokud objekt nejsou agregovány.|  
  
## <a name="remarks"></a>Poznámky  
 `CComPolyObject`implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pro agregovaná nebo neagregovaná objekt.  
  
 Pokud instance `CComPolyObject` je vytvořen, hodnota vnější je zaškrtnuta možnost neznámá. Pokud je **NULL**, **IUnknown** je implementována pro objekt neagregovaná. Pokud vnější Neznámý není **NULL**, **IUnknown** je implementována pro agregovaný objekt.  
  
 Výhodou použití `CComPolyObject` je vyhnout se nutnosti obě [CComAggObject](../../atl/reference/ccomaggobject-class.md) a [CComObject](../../atl/reference/ccomobject-class.md) v modulu pro zpracování agregované a neagregovaná případy. Jediný `CComPolyObject` objekt zpracovává obou případech. To znamená, že pouze jedna kopie tabulce vtable a jednu kopii funkce existují v modulu. Pokud vaše vtable velká, může to podstatně snížit velikost vašeho modulu. Ale pokud je vaše vtable malá, pomocí `CComPolyObject` může způsobit něco větší velikost modulu, protože není optimalizována pro agregovaná nebo neagregovaná objekt, jako jsou `CComAggObject` a `CComObject`.  
  
 Pokud `DECLARE_POLY_AGGREGATABLE` makro je zadaný v definici třídy objektu, `CComPolyObject` se použije k vytvoření objektu. `DECLARE_POLY_AGGREGATABLE`bude automaticky deklarovat Pokud použijete Průvodce projektem ATL k vytvoření úplné řízení nebo Internet Explorer ovládací prvek.  
  
 Pokud agregovány, `CComPolyObject` objekt má svou vlastní **IUnknown**samostatné z vnějšího objektu **IUnknown**a udržuje vlastní počet odkazů. `CComPolyObject`používá [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) delegovat na vnější neznámý.  
  
 Další informace o agregace, najdete v článku [základy objektů COM ATL](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>CComPolyObject::AddRef  
 Zvýší počet odkaz na objekt.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku nebo testování.  
  
##  <a name="ccompolyobject"></a>CComPolyObject::CComPolyObject  
 Konstruktor  
  
```
CComPolyObject(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 [v] Ukazatel na vnější neznámý, pokud objekt má být agregován, nebo **NULL** Pokud objekt, pokud objekt nejsou agregovány.  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje `CComContainedObject` – datový člen, [m_contained](#m_contained)a zvýší počet modulů zámku.  
  
 Destruktor snižuje počet zámek modulu.  
  
##  <a name="dtor"></a>CComPolyObject:: ~ CComPolyObject  
 Destruktor.  
  
```
~CComPolyObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky, volání [FinalRelease](#finalrelease), a snižuje počet zámek modulu.  
  
##  <a name="createinstance"></a>CComPolyObject::CreateInstance  
 Umožňuje vytvořit novou **CComPolyObject <** `contained`  **>**  objektu bez režie [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(  
    LPUNKNOWN pUnkOuter, 
    CComPolyObject<contained>** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `pp`  
 [out] Ukazatel **CComPolyObject <** `contained`  **>**  ukazatel. Pokud `CreateInstance` není úspěšné, `pp` je nastaven na **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Objekt vrácený má nulový počet odkaz, takže volání `AddRef` okamžitě, pak použít **verze** k bezplatným odkaz na objekt ukazatele, když jste hotovi.  
  
 Pokud není nutné přímý přístup k objektu, ale přesto chcete vytvořit nový objekt bez režie `CoCreateInstance`, použijte [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) místo.  
  
##  <a name="finalconstruct"></a>CComPolyObject::FinalConstruct  
 Volá se během poslední fáze vytváření objektů, tato metoda provádí všechny konečné inicializace [m_contained](#m_contained) – datový člen.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="finalrelease"></a>CComPolyObject::FinalRelease  
 Volá se při odstraňování objektu, tato metoda uvolní [m_contained](#m_contained) – datový člen.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComPolyObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objekt odvozen z vaší třídy.  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>Parametry  
 `contained`  
 [v] Vlastní třídy odvozené od [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře od dalších rozhraní, které chcete podporovat v objektu.  
  
### <a name="remarks"></a>Poznámky  
 **IUnknown** volá prostřednictvím `m_contained` jsou delegovanými na vnější neznámý, pokud je agregován objektu, nebo k **IUnknown** tohoto objektu, pokud objekt nejsou agregovány.  
  
##  <a name="queryinterface"></a>CComPolyObject::QueryInterface  
 Načte ukazatel na požadované rozhraní.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `Q`  
 Rozhraní COM.  
  
 `iid`  
 [v] Identifikátor rozhraní požadováno.  
  
 `ppvObject`  
 [out] Ukazatel na ukazatel rozhraní identifikovaný `iid`. Pokud objekt nepodporuje toto rozhraní `ppvObject` je nastaven na **NULL**.  
  
 `pp`  
 [out] Ukazatel rozhraní identifikovaný **__uuidof(Q)**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Pro agregovaný objekt, pokud je požadované rozhraní **IUnknown**, `QueryInterface` vrací ukazatel na agregovaného objektu vlastní **IUnknown** a zvýší počet odkazů. Jinak tato metoda dotazuje na rozhraní prostřednictvím `CComContainedObject` – datový člen, [m_contained](#m_contained).  
  
##  <a name="release"></a>CComPolyObject::Release  
 Snižuje počet odkaz na objekt.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení pro ladění **verze** vrátí hodnotu, která může být užitečné pro diagnostiku nebo testování. V sestavení pro nondebug **verze** vždy vrátí hodnotu 0.  
  
## <a name="see-also"></a>Viz také  
 [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)   
 [Přehled třídy](../../atl/atl-class-overview.md)
