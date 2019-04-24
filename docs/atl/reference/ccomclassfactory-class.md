---
title: CComClassFactory Class
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 85ef287a905abc7b3151628c0f5dc29b9050b187
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246719"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory Class

Tato třída implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) rozhraní.

## <a name="syntax"></a>Syntaxe

```
class CComClassFactory
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComClassFactory::CreateInstance](#createinstance)|Vytvoří objekt zadaným identifikátorem CLSID.|
|[CComClassFactory::LockServer](#lockserver)|Zamkne objekt pro vytváření tříd v paměti.|

## <a name="remarks"></a>Poznámky

`CComClassFactory` implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) rozhraní, která obsahuje metody pro vytvoření objektu s konkrétní identifikátorem CLSID, jakož i uzamčení objekt pro vytváření tříd v paměti, abyste mohli rychleji vytvořit nové objekty. `IClassFactory` je nutné implementovat pro každou třídu, která zaregistrujete v systémovém registru a můžete přiřadit identifikátor CLSID.

Objekty knihovny ATL obvykle získat objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), který deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete-li přepsat toto výchozí nastavení, zadejte jeden z `DECLARE_CLASSFACTORY` *XXX* makra v definici třídy. Například [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) makro používá zadanou třídu pro objekt pro vytváření tříd:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

Výše uvedené definice třídy, která určuje `CMyClassFactory` se použije jako objekt pro vytváření tříd objektu výchozí. `CMyClassFactory` musí být odvozen od `CComClassFactory` a přepsat `CreateInstance`.

Knihovna ATL poskytuje tři makra, které deklarují objekt pro vytváření tříd:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) používá [ccomclassfactory2 –](../../atl/reference/ccomclassfactory2-class.md), který řídí vytváření prostřednictvím licenci.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) používá [ccomclassfactoryautothread –](../../atl/reference/ccomclassfactoryautothread-class.md), která vytváří objekty ve více objekty apartment.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) používá [ccomclassfactorysingleton –](../../atl/reference/ccomclassfactorysingleton-class.md), což vytvoří jeden [ccomobjectglobal –](../../atl/reference/ccomobjectglobal-class.md) objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="createinstance"></a>  CComClassFactory::CreateInstance

Vytvoří objekt zadaným identifikátorem CLSID a načte ukazatel rozhraní k tomuto objektu.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
[in] Pokud se objekt vytváří jako součást agregace, pak *pUnkOuter* musí být vnější neznámá. V opačném případě *pUnkOuter* musí mít hodnotu NULL.

*riid*<br/>
[in] Identifikátor IID požadované rozhraní. Pokud *pUnkOuter* je jiná než NULL, *riid* musí být `IID_IUnknown`.

*ppvObj*<br/>
[out] Ukazatel na ukazatel rozhraní, který je identifikován *riid*. Pokud objekt nepodporuje toto rozhraní *ppvObj* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="lockserver"></a>  CComClassFactory::LockServer

Inkrementuje a dekrementuje počet zámků modulů voláním `_Module::Lock` a `_Module::Unlock`v uvedeném pořadí.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*fLock*<br/>
[in] Při hodnotě TRUE se zvýší počet zámků; v opačném případě je snížen počet zámků.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

`_Module` odkazuje na globální instanci [ccommodule –](../../atl/reference/ccommodule-class.md) nebo z něj odvozenou třídu.

Volání `LockServer` umožňuje klientovi opřete se o objekt pro vytváření tříd tak, aby více objektů lze rychle vytvořit.

## <a name="see-also"></a>Viz také:

[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
