---
title: "Třída CComObjectStack | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
dev_langs: C++
helpviewer_keywords: CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b7fa9d14a27277d4c26fc6e7589400e19ef1395
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomobjectstack-class"></a>CComObjectStack – třída
Tato třída vytvoří dočasný objekt COM a poskytne mu kosterního provádění **IUnknown**.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class  Base>  
class CComObjectStack
 : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Vlastní třídy odvozené od [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře kvůli další rozhraní, které chcete podporovat v objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|Konstruktor|  
|[CComObjectStack:: ~ CComObjectStack](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectStack::AddRef](#addref)|Vrátí hodnotu nula. V režimu ladění, volá `_ASSERTE`.|  
|[CComObjectStack::QueryInterface](#queryinterface)|Vrátí **E_NOINTERFACE**. V režimu ladění, volá `_ASSERTE`.|  
|[CComObjectStack::Release](#release)|Vrátí hodnotu nula. V režimu ladění, volá `_ASSERTE`. ~|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Obsahuje **HRESULT** vrátil během vytváření `CComObjectStack` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CComObjectStack`slouží k vytvoření dočasného objektu COM a zadat objekt kosterního provádění **IUnknown**. Objekt se obvykle používá jako místní proměnné v rámci jedné funkce (který se instaluje do zásobníku). Vzhledem k tomu, že objekt je zrušen po dokončení funkce, počítání odkazů neprovádí zvýšit efektivitu.  
  
 Následující příklad ukazuje, jak vytvořit objekt COM použít uvnitř funkce:  
  
 [!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]  
  
 Dočasný objekt `Tempobj` je vloženy do zásobníku a automaticky zmizí po dokončení funkce.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `CComObjectStack`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>CComObjectStack::AddRef  
 Vrátí hodnotu nula.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu nula.  
  
### <a name="remarks"></a>Poznámky  
 V režimu ladění, volá `_ASSERTE`.  
  
##  <a name="ccomobjectstack"></a>CComObjectStack::CComObjectStack  
 Konstruktor  
  
```
CComObjectStack(void* = NULL);
```  
  
### <a name="remarks"></a>Poznámky  
 Volání `FinalConstruct` a nastaví [m_hResFinalConstruct](#m_hresfinalconstruct) k `HRESULT` vrácený `FinalConstruct`. Pokud nebyly odvozené ze základní třídu [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), je nutné zadat vlastní `FinalConstruct` metoda. Volání destruktoru `FinalRelease`.  
  
##  <a name="dtor"></a>CComObjectStack:: ~ CComObjectStack  
 Destruktor.  
  
```
CComObjectStack();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky a volání [FinalRelease](ccomobjectrootex-class.md#finalrelease).  
  
##  <a name="m_hresfinalconstruct"></a>CComObjectStack::m_hResFinalConstruct  
 Obsahuje `HRESULT` vrácená z volání `FinalConstruct` během vytváření `CComObjectStack` objektu.  
  
```
HRESULT    m_hResFinalConstruct;
```  
  
##  <a name="queryinterface"></a>CComObjectStack::QueryInterface  
 Vrátí **E_NOINTERFACE**.  
  
```
HRESULT    QueryInterface(REFIID, void**)
 ;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOINTERFACE**.  
  
### <a name="remarks"></a>Poznámky  
 V režimu ladění, volá `_ASSERTE`.  
  
##  <a name="release"></a>CComObjectStack::Release  
 Vrátí hodnotu nula.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu nula.  
  
### <a name="remarks"></a>Poznámky  
 V režimu ladění, volá `_ASSERTE`.  
  
## <a name="see-also"></a>Viz také  
 [CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)   
 [CComObject – třída](../../atl/reference/ccomobject-class.md)   
 [CComObjectGlobal – třída](../../atl/reference/ccomobjectglobal-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
