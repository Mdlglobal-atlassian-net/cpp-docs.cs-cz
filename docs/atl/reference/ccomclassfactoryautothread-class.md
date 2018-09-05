---
title: Ccomclassfactoryautothread – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 476edd2a199ca21a9067a72cac82a6ac7b608112
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757375"
---
# <a name="ccomclassfactoryautothread-class"></a>Ccomclassfactoryautothread – třída

Tato třída implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) rozhraní a umožňuje objektů bude vytvořena ve více objekty apartment.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComClassFactoryAutoThread 
   : public IClassFactory, 
     public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|Vytvoří objekt zadaným identifikátorem CLSID.|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Zamkne objekt pro vytváření tříd v paměti.|

## <a name="remarks"></a>Poznámky

`CComClassFactoryAutoThread` je podobný [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md), ale umožňuje objektů bude vytvořena ve více objekty apartment. Využít této podpory, jsou odvozeny z modulu EXE [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Objekty knihovny ATL obvykle získat objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), který deklaruje [ccomclassfactory –](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete-li použít `CComClassFactoryAutoThread`, zadejte [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra v definici třídy objektu. Příklad:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="createinstance"></a>  CComClassFactoryAutoThread::CreateInstance

Vytvoří objekt zadaným identifikátorem CLSID a načte ukazatel rozhraní k tomuto objektu.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*  
[in] Pokud se objekt vytváří jako součást agregace, pak *pUnkOuter* musí být vnější neznámá. V opačném případě *pUnkOuter* musí mít hodnotu NULL.

*riid*  
[in] Identifikátor IID požadované rozhraní. Pokud *pUnkOuter* je jiná než NULL, *riid* musí být `IID_IUnknown`.

*ppvObj*  
[out] Ukazatel na ukazatel rozhraní, který je identifikován *riid*. Pokud objekt nepodporuje toto rozhraní *ppvObj* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pokud modul je odvozena z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` nejprve vybere vlákno k vytvoření objektu v přidružené objektu apartment.

##  <a name="lockserver"></a>  CComClassFactoryAutoThread::LockServer

Inkrementuje a dekrementuje počet zámků modulů voláním `_Module::Lock` a `_Module::Unlock`v uvedeném pořadí.

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*hejna*  
[in] Při hodnotě TRUE se zvýší počet zámků; v opačném případě je snížen počet zámků.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Při použití `CComClassFactoryAutoThread`, `_Module` obvykle odkazuje na globální instanci [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Volání `LockServer` umožňuje klientovi opřete se o objekt pro vytváření tříd tak, aby více objektů lze rychle vytvořit.

## <a name="see-also"></a>Viz také

[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)   
[Ccomclassfactory2 – třída](../../atl/reference/ccomclassfactory2-class.md)   
[Ccomclassfactorysingleton – třída](../../atl/reference/ccomclassfactorysingleton-class.md)   
[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)   
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
[Přehled tříd](../../atl/atl-class-overview.md)
