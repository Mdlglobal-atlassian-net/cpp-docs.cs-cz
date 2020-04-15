---
title: Třída CComClassFactory
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 041575339906b83488697f1db5a7f8b08b53070e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321026"
---
# <a name="ccomclassfactory-class"></a>Třída CComClassFactory

Tato třída implementuje rozhraní [IClassFactory.](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)

## <a name="syntax"></a>Syntaxe

```
class CComClassFactory
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComClassFactory::CreateInstance](#createinstance)|Vytvoří objekt zadaného identifikátoru CLSID.|
|[CComClassFactory::LockServer](#lockserver)|Zamkne továrnu třídy v paměti.|

## <a name="remarks"></a>Poznámky

`CComClassFactory`implementuje rozhraní [IClassFactory,](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) které obsahuje metody pro vytvoření objektu určitého identifikátoru CLSID, stejně jako uzamčení factory třídy v paměti, aby bylo možné rychleji vytvářet nové objekty. `IClassFactory`musí být implementována pro každou třídu, kterou zaregistrujete v systémovém registru a ke které přiřadíte CLSID.

Objekty ATL obvykle získávají třídu odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje [makro DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) `CComClassFactory` , který deklaruje jako výchozí třídy factory. Chcete-li toto výchozí nastavení `DECLARE_CLASSFACTORY`přepsat, zadejte jedno z maker *XXX* v definici třídy. Například [makro DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) používá zadanou třídu pro třídu factory:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

Výše uvedená definice `CMyClassFactory` třídy určuje, že bude použit jako objekt u výchozí třídy factory. `CMyClassFactory`musí odvodit a `CComClassFactory` přepsat `CreateInstance`.

Atl poskytuje tři další makra, která deklarují třídy:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) Používá [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), který řídí vytváření prostřednictvím licence.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) Používá [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), který vytváří objekty ve více bytech.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) Používá [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), který vytvoří jeden [cComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objekt.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomclassfactorycreateinstance"></a><a name="createinstance"></a>CComClassFactory::CreateInstance

Vytvoří objekt zadaného identifikátoru CLSID a načte k tomuto objektu ukazatel rozhraní.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
[v] Pokud je objekt vytvářen jako součást agregace, pak *pUnkOuter* musí být vnější neznámý. V opačném případě *pUnkOuter* musí být NULL.

*riid řekl:*<br/>
[v] IID požadovanérozhraní. Pokud *pUnkOuter* není null, *riid* musí být `IID_IUnknown`.

*ppvObj*<br/>
[out] Ukazatel rozhraní určený *riid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppvObj* nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ccomclassfactorylockserver"></a><a name="lockserver"></a>CComClassFactory::LockServer

Přírůstky a snížení počet zámek modulu `_Module::Lock` voláním `_Module::Unlock`a , v uvedeném pořadí.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Stádo*<br/>
[v] Pokud true, počet zámků se zpřísňuje; v opačném případě je snížen počet zámků.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`_Module`odkazuje na globální instanci [CComModule](../../atl/reference/ccommodule-class.md) nebo třídy odvozené z něj.

Volání `LockServer` umožňuje klientovi podržet továrnu třídy tak, aby bylo možné rychle vytvořit více objektů.

## <a name="see-also"></a>Viz také

[Třída CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
