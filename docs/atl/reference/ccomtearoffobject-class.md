---
title: "Třída CComTearOffObject | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
dev_langs:
- C++
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80be7d80af5a6c8fa2c47bc0e853020663f2ceae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject – třída
Tato třída implementuje rozhraní úplné vypnutí.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>
class CComTearOffObject : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Vaše úplné vypnutí třída odvozena od `CComTearOffObjectBase` a rozhraní chcete objektu úplné vypnutí pro podporu.  
  
 ATL implementuje rozhraní jeho úplné vypnutí ve dvou fázích – `CComTearOffObjectBase` metody zpracování počet odkazů a `QueryInterface`, zatímco `CComTearOffObject` implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509).  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|Konstruktor|  
|[CComTearOffObject:: ~ CComTearOffObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComTearOffObject::AddRef](#addref)|Zvýší počet odkazů pro `CComTearOffObject` objektu.|  
|[CComTearOffObject::QueryInterface](#queryinterface)|Vrací ukazatel na požadované rozhraní na třídě úplné vypnutí nebo třída vlastníka.|  
|[CComTearOffObject::Release](#release)|Snižuje počet odkaz `CComTearOffObject` objektu a ukončuje se.|  
  
### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase metody  
  
|||  
|-|-|  
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Konstruktor|  
  
### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase datové členy  
  
|||  
|-|-|  
|[m_pOwner](#m_powner)|Ukazatel na `CComObject` odvozena od třídy vlastníka.|  
  
## <a name="remarks"></a>Poznámky  
 `CComTearOffObject`implementuje rozhraní úplné vypnutí jako samostatný objekt, který je vytvořena instance jenom v případě, že rozhraní je dotazován na. Úplné vypnutí se odstraní při jeho počet odkazů klesne na nulu. Obvykle vytvoříte rozhraní úplné vypnutí pro rozhraní, které se používá jen občas, protože ukazatel vtable pomocí úplné vypnutí uloží ve všech instancích vašeho hlavní objektu.  
  
 By měl být odvozen třída implementace úplné – vypnuté z `CComTearOffObjectBase` a z libovolného rozhraní má objektu úplné vypnutí pro podporu. `CComTearOffObjectBase`je převést na šablonu pro třídu vlastníka a model vláken. Třída vlastníka je třídu objektu, pro který úplné vypnutí se implementuje. Pokud model vláken nezadáte, použije se výchozí model vláken.  
  
 Měli byste vytvořit mapu COM pro třídu úplné vypnutí. Když ATL vytvoří úplné vypnutí, vytvoří **CComTearOffObject\<CYourTearOffClass >** nebo **CComCachedTearOffObject\<CYourTearOffClass >**.  
  
 Například v ukázce BEEPER `CBeeper2` třídy je třída úplné vypnutí a `CBeeper` třídy je třída vlastníka:  
  
 [!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `CComTearOffObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>CComTearOffObject::AddRef  
 Zvýší počet odkazů `CComTearOffObject` objekt o jednu.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku a testování.  
  
##  <a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject  
 Konstruktor  
  
```
CComTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 [v] Ukazatele, který text bude převeden na odkazy **CComObject\<vlastníka >** objektu.  
  
### <a name="remarks"></a>Poznámky  
 Zvýší počet odkazů vlastníka o jednu.  
  
##  <a name="dtor"></a>CComTearOffObject:: ~ CComTearOffObject  
 Destruktor.  
  
```
~CComTearOffObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky, vyvolá modul FinalRelease a snižuje počet zamknout.  
  
##  <a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase  
 Konstruktor  
  
```
CComTearOffObjectBase();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje [m_pOwner](#m_powner) člena **NULL**.  
  
##  <a name="m_powner"></a>CComTearOffObject::m_pOwner  
 Ukazatel [CComObject](../../atl/reference/ccomobject-class.md) objekt odvozen od *vlastníka*.  
  
```
CComObject<Owner>* m_pOwner;
```  
  
### <a name="parameters"></a>Parametry  
 *Vlastník*  
 [v] Třída, pro který úplné vypnutí se implementuje.  
  
### <a name="remarks"></a>Poznámky  
 Je inicializováno ukazatele **NULL** během vytváření.  
  
##  <a name="queryinterface"></a>CComTearOffObject::QueryInterface  
 Načte ukazatel na požadované rozhraní.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátory IID rozhraní požadováno.  
  
 `ppvObject`  
 [out] Ukazatel na ukazatel rozhraní identifikovaný `iid`, nebo **NULL** Pokud rozhraní nebyl nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Dotazy nejprve pro rozhraní na vaší třídě úplné vypnutí. Pokud rozhraní není, dotazy pro rozhraní objektu vlastníka. Pokud je požadované rozhraní **IUnknown**, vrátí **IUnknown** vlastníka.  
  
##  <a name="release"></a>CComTearOffObject::Release  
 Snižuje počet reference o jednu a, pokud počet odkazů nula, odstraní `CComTearOffObject`.  
  
```
STDMETHOD_ULONG Release();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení pro bez ladění vždy vrátí hodnotu nula. V sestavení pro ladění vrátí hodnotu, která může být užitečné pro diagnostiku nebo testování.  
  
## <a name="see-also"></a>Viz také  
 [CComCachedTearOffObject – třída](../../atl/reference/ccomcachedtearoffobject-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
