---
title: Ccomobjectglobal – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d96af29f03da472c8e9cc829c89b60d0eaa591c
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880632"
---
# <a name="ccomobjectglobal-class"></a>Ccomobjectglobal – třída
Tato třída spravuje počet odkazů na modul obsahující vaše `Base` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>
class CComObjectGlobal : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 *základ*  
 Vaše třída odvozena od [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře jako z jiných rozhraní, které chcete podporovat na objekt.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|Konstruktor|  
|[Ccomobjectglobal –:: ~ ccomobjectglobal –](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectGlobal::AddRef](#addref)|Implementuje globální `AddRef`.|  
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implementuje globální `QueryInterface`.|  
|[CComObjectGlobal::Release](#release)|Implementuje globální `Release`.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Obsahuje HRESULT vrátil během procesu vytváření `CComObjectGlobal` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CComObjectGlobal` spravuje počet odkazů na modul obsahující vaše `Base` objektu. `CComObjectGlobal` zajišťuje, že objekt se neodstraní, tak dlouho, dokud se neuvolní modulu. Objekt se odebrat pouze v případě, že počet odkazů na celý modul sníží na nulu.  
  
 Například použití `CComObjectGlobal`, objekt pro vytváření tříd může obsahovat běžné globální objekt, jež jsou sdílena ve všech svých klientů.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `CComObjectGlobal`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>  CComObjectGlobal::AddRef  
 Zvýší počet odkazů objektu 1.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku a testování.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `AddRef` volání `_Module::Lock`, kde `_Module` je globální instanci [ccommodule –](../../atl/reference/ccommodule-class.md) nebo z něj odvozenou třídu.  
  
##  <a name="ccomobjectglobal"></a>  CComObjectGlobal::CComObjectGlobal  
 Konstruktor Volání `FinalConstruct` a pak nastaví [m_hResFinalConstruct](#m_hresfinalconstruct) k `HRESULT` vrácený `FinalConstruct`.  
  
```
CComObjectGlobal(void* = NULL));
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud ještě odvozené ze základní třídy [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md), je nutné zadat vlastní `FinalConstruct` metody. Volání destruktoru `FinalRelease`.  
  
##  <a name="dtor"></a>  Ccomobjectglobal –:: ~ ccomobjectglobal –  
 Destruktor.  
  
```
CComObjectGlobal();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky a volání [FinalRelease](ccomobjectrootex-class.md#finalrelease).  
  
##  <a name="m_hresfinalconstruct"></a>  CComObjectGlobal::m_hResFinalConstruct  
 Obsahuje hodnotu HRESULT z volání `FinalConstruct` během procesu vytváření `CComObjectGlobal` objektu.  
  
```
HRESULT m_hResFinalConstruct;
```  
  
##  <a name="queryinterface"></a>  CComObjectGlobal::QueryInterface  
 Načte ukazatel na ukazatel požadované rozhraní.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor IID*  
 [in] Identifikátor GUID se požadované rozhraní.  
  
 *ppvObject*  
 [out] Ukazatel na ukazatel rozhraní, který je identifikován iid, nebo hodnota NULL, pokud se nenajde rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 `QueryInterface` zpracovává pouze v tabulce mapy modelu COM rozhraní.  
  
##  <a name="release"></a>  CComObjectGlobal::Release  
 Sníží počet odkaz na objekt o 1.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V ladicím buildu `Release` vrátí hodnotu, která může být užitečné pro diagnostiku a testování. V sestaveních bez ladění `Release` vždy vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `Release` volání `_Module::Unlock`, kde `_Module` je globální instanci [ccommodule –](../../atl/reference/ccommodule-class.md) nebo z něj odvozenou třídu.  
  
## <a name="see-also"></a>Viz také  
 [Ccomobjectstack – třída](../../atl/reference/ccomobjectstack-class.md)   
 [CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)   
 [CComObject – třída](../../atl/reference/ccomobject-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
