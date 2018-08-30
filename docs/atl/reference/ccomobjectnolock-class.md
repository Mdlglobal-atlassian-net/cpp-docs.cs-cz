---
title: Třída ccomobjectnolock – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85332341e1a229ce5110153c0ad6195ef0ad42c4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208172"
---
# <a name="ccomobjectnolock-class"></a>Ccomobjectnolock – třída
Tato třída implementuje `IUnknown` pro neagregovaná objektu, ale nemá není přírůstek počet zámků modulů v konstruktoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>  
class CComObjectNoLock : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 *základ*  
 Vaše třída odvozena od [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře jako z jiných rozhraní, které chcete podporovat na objekt.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Konstruktor|  
|[CComObjectNoLock::~CComObjectNoLock](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectNoLock::AddRef](#addref)|Zvýší počet odkazů na objekt.|  
|[CComObjectNoLock::QueryInterface](#queryinterface)|Vrací ukazatel na požadované rozhraní.|  
|[CComObjectNoLock::Release](#release)|Sníží počet odkaz na objekt.|  
  
## <a name="remarks"></a>Poznámky  
 `CComObjectNoLock` je podobný [CComObject](../../atl/reference/ccomobject-class.md) v tom, že implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pro neagregovaná objekt; však `CComObjectNoLock` nepodporuje počet přírůstek modul zámku v konstruktoru.  
  
 ATL – používá `CComObjectNoLock` interně pro objekty pro vytváření tříd. Tato třída obecně nebude používat přímo.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `CComObjectNoLock`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>  CComObjectNoLock::AddRef  
 Zvýší počet odkazů na objekt.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku a testování.  
  
##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock  
 Konstruktor Na rozdíl od [CComObject](../../atl/reference/ccomobject-class.md), se nezvyšuje počet zámků modulů.  
  
```
CComObjectNoLock(void* = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 <em>Typ void\*</em>  
 [in] Tento nepojmenovaný parametr se nepoužívá. Existuje symetrie s jinými `CComXXXObjectXXX` konstruktory.  
  
##  <a name="dtor"></a>  Ccomobjectnolock –:: ~ ccomobjectnolock –  
 Destruktor.  
  
```
~CComObjectNoLock();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky a volání [FinalRelease](ccomobjectrootex-class.md#finalrelease).  

  
##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface  
 Načte ukazatel na požadované rozhraní.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor IID*  
 [in] Identifikátor se požadované rozhraní.  
  
 *ppvObject*  
 [out] Ukazatel na ukazatel rozhraní, který je identifikován *iid*. Pokud objekt nepodporuje toto rozhraní *ppvObject* nastaven na hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
##  <a name="release"></a>  CComObjectNoLock::Release  
 Sníží počet odkaz na objekt.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V ladicím buildu `Release` vrátí hodnotu, která může být užitečné pro diagnostiku a testování. V sestaveních bez ladění `Release` vždy vrátí hodnotu 0.  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)
