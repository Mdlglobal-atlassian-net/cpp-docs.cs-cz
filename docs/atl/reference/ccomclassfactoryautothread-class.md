---
title: Třída CComClassFactoryAutoThread
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: e997d92adfa9df46c82dacbd297db495b037c6e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320906"
---
# <a name="ccomclassfactoryautothread-class"></a>Třída CComClassFactoryAutoThread

Tato třída implementuje rozhraní [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) a umožňuje objekty, které mají být vytvořeny ve více bytech.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComClassFactoryAutoThread
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|Vytvoří objekt zadaného identifikátoru CLSID.|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Zamkne továrnu třídy v paměti.|

## <a name="remarks"></a>Poznámky

`CComClassFactoryAutoThread`je podobný [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale umožňuje objekty, které mají být vytvořeny ve více bytech. Chcete-li využít této podpory, odvodit modul EXE z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Objekty ATL obvykle získávají třídu odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)maker , který deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí třídy factory. Chcete-li použít `CComClassFactoryAutoThread`, zadejte [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makro v definici třídy objektu. Příklad:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomclassfactoryautothreadcreateinstance"></a><a name="createinstance"></a>CComClassFactoryAutoThread::CreateInstance

Vytvoří objekt zadaného identifikátoru CLSID a načte k tomuto objektu ukazatel rozhraní.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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

### <a name="remarks"></a>Poznámky

Pokud váš modul pochází z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` nejprve vybere vlákno k vytvoření objektu v přidružené matné matné.

## <a name="ccomclassfactoryautothreadlockserver"></a><a name="lockserver"></a>CComClassFactoryAutoThread::LockServer

Přírůstky a snížení počet zámek modulu `_Module::Lock` voláním `_Module::Unlock`a , v uvedeném pořadí.

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Stádo*<br/>
[v] Pokud true, počet zámků se zpřísňuje; v opačném případě je snížen počet zámků.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Při `CComClassFactoryAutoThread`použití `_Module` , obvykle odkazuje na globální instance [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Volání `LockServer` umožňuje klientovi podržet továrnu třídy tak, aby bylo možné rychle vytvořit více objektů.

## <a name="see-also"></a>Viz také

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[Třída CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)<br/>
[Třída CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[Třída CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
