---
title: "Třída CComObjectNoLock | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a85a238d17fe279359a73d3c740406c15b92c34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock – třída
Tato třída implementuje **IUnknown** neagregovaná objektu, ale nemá není přírůstek zámek modulu počet v konstruktoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>  
class CComObjectNoLock : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Vlastní třídy odvozené od [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře kvůli další rozhraní, které chcete podporovat v objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Konstruktor|  
|[CComObjectNoLock:: ~ CComObjectNoLock](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectNoLock::AddRef](#addref)|Zvýší počet odkaz na objekt.|  
|[CComObjectNoLock::QueryInterface](#queryinterface)|Vrací ukazatel na požadované rozhraní.|  
|[CComObjectNoLock::Release](#release)|Snižuje počet odkaz na objekt.|  
  
## <a name="remarks"></a>Poznámky  
 `CComObjectNoLock`je podobná [CComObject](../../atl/reference/ccomobject-class.md) v tom, že implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pro objekt neagregovaná; však `CComObjectNoLock` nemá přírůstek zámek modulu počet v konstruktoru.  
  
 ATL používá `CComObjectNoLock` interně pro vytváření tříd. Obecně platí nebude tato třída používat přímo.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `CComObjectNoLock`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>CComObjectNoLock::AddRef  
 Zvýší počet odkaz na objekt.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku nebo testování.  
  
##  <a name="ccomobjectnolock"></a>CComObjectNoLock::CComObjectNoLock  
 Konstruktor Na rozdíl od [CComObject](../../atl/reference/ccomobject-class.md), nezvyšuje počet modulů zámku.  
  
```
CComObjectNoLock(void* = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 **void\***  
 [v] Tento nepojmenovaný parametr se nepoužívá. Existuje pro symetrie s jinými **CCom***XXX*`Object`*XXX* konstruktory.  
  
##  <a name="dtor"></a>CComObjectNoLock:: ~ CComObjectNoLock  
 Destruktor.  
  
```
~CComObjectNoLock();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky a volání [FinalRelease](ccomobjectrootex-class.md#finalrelease).  

  
##  <a name="queryinterface"></a>CComObjectNoLock::QueryInterface  
 Načte ukazatel na požadované rozhraní.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor rozhraní požadováno.  
  
 `ppvObject`  
 [out] Ukazatel na ukazatel rozhraní identifikovaný `iid`. Pokud objekt nepodporuje toto rozhraní `ppvObject` je nastaven na **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="release"></a>CComObjectNoLock::Release  
 Snižuje počet odkaz na objekt.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení pro ladění **verze** vrátí hodnotu, která může být užitečné pro diagnostiku nebo testování. V sestavení pro bez ladění **verze** vždy vrátí hodnotu 0.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
