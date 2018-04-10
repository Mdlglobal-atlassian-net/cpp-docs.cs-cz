---
title: Třída CComObjectGlobal | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d5264a2ab8e1bbc4c3f4eac4d83d096d91e8846
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal – třída
Tato třída spravuje počet odkazů na modul obsahující vaše `Base` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>
class CComObjectGlobal : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Vlastní třídy odvozené od [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře kvůli další rozhraní, které chcete podporovat v objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|Konstruktor|  
|[CComObjectGlobal:: ~ CComObjectGlobal](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectGlobal::AddRef](#addref)|Implementuje globální konfiguraci `AddRef`.|  
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implementuje globální konfiguraci `QueryInterface`.|  
|[CComObjectGlobal::Release](#release)|Implementuje globální konfiguraci **verze**.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Obsahuje **HRESULT** vrátil během vytváření `CComObjectGlobal` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CComObjectGlobal`spravuje počet odkazů na modul obsahující vaše `Base` objektu. `CComObjectGlobal`zajišťuje, že objektu se neodstraní, dokud se modul neuvolní. Objekt se odebere pouze, když počet odkaz na modul celý přejde na hodnotu nula.  
  
 Například pomocí `CComObjectGlobal`, vytváření třídy mohou být uloženy běžné globální objekt, který je sdílen svým klientům.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `CComObjectGlobal`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>CComObjectGlobal::AddRef  
 Počet odkazů objektu zvýší o 1.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku a testování.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `AddRef` volání **_Module::Lock**, kde **_Module** je globální instance [CComModule](../../atl/reference/ccommodule-class.md) nebo z něj odvozenou třídu.  
  
##  <a name="ccomobjectglobal"></a>CComObjectGlobal::CComObjectGlobal  
 Konstruktor Volání `FinalConstruct` a nastaví [m_hResFinalConstruct](#m_hresfinalconstruct) k `HRESULT` vrácený `FinalConstruct`.  
  
```
CComObjectGlobal(void* = NULL));
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud nebyly odvozené ze základní třídu [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), je nutné zadat vlastní `FinalConstruct` metoda. Volání destruktoru `FinalRelease`.  
  
##  <a name="dtor"></a>CComObjectGlobal:: ~ CComObjectGlobal  
 Destruktor.  
  
```
CComObjectGlobal();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky a volání [FinalRelease](ccomobjectrootex-class.md#finalrelease).  
  
##  <a name="m_hresfinalconstruct"></a>CComObjectGlobal::m_hResFinalConstruct  
 Obsahuje `HRESULT` z volání `FinalConstruct` během vytváření `CComObjectGlobal` objektu.  
  
```
HRESULT m_hResFinalConstruct;
```  
  
##  <a name="queryinterface"></a>CComObjectGlobal::QueryInterface  
 Načte ukazatel na ukazatel požadované rozhraní.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor GUID se požadované rozhraní.  
  
 `ppvObject`  
 [out] Ukazatel na ukazatel rozhraní identifikovaný iid, nebo **NULL** Pokud rozhraní nebyl nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 `QueryInterface`zpracovává jenom rozhraní v tabulce COM mapy.  
  
##  <a name="release"></a>CComObjectGlobal::Release  
 Snižuje počet odkaz na objekt o 1.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení pro ladění **verze** vrátí hodnotu, která může být užitečné pro diagnostiku a testování. V sestavení pro bez ladění **verze** vždy vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení **verze** volání **_Module::Unlock**, kde **_Module** je globální instance [CComModule](../../atl/reference/ccommodule-class.md) nebo z něj odvozenou třídu.  
  
## <a name="see-also"></a>Viz také  
 [CComObjectStack – třída](../../atl/reference/ccomobjectstack-class.md)   
 [CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)   
 [CComObject – třída](../../atl/reference/ccomobject-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
