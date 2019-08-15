---
title: CComClassFactoryAutoThread – třída
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: 73879a73a48290e19d2a27307884953129826df7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497492"
---
# <a name="ccomclassfactoryautothread-class"></a>CComClassFactoryAutoThread – třída

Tato třída implementuje rozhraní [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) a umožňuje vytvářet objekty ve více objektech Apartment.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComClassFactoryAutoThread
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComClassFactoryAutoThread:: CreateInstance](#createinstance)|Vytvoří objekt zadaného objektu CLSID.|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Zamkne objekt pro vytváření tříd v paměti.|

## <a name="remarks"></a>Poznámky

`CComClassFactoryAutoThread`je podobný jako [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale umožňuje vytvářet objekty ve více objektech Apartment. Chcete-li využít výhod této podpory, odvodit modul EXE z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Objekty ATL normálně získávají objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje makro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), které deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete- `CComClassFactoryAutoThread`li použít, zadejte makro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) v definici třídy vašeho objektu. Příklad:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="createinstance"></a>CComClassFactoryAutoThread:: CreateInstance

Vytvoří objekt zadaného identifikátoru CLSID a načte ukazatel rozhraní na tento objekt.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
pro Pokud se objekt vytváří jako součást agregace, pak musí být *pUnkOuter* vnějším neznámý. V opačném případě *pUnkOuter* musí mít hodnotu null.

*riid*<br/>
pro IID požadovaného rozhraní. Pokud *pUnkOuter* je jiný než null, musí být `IID_IUnknown`riid.

*ppvObj*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný *riid*. Pokud objekt nepodporuje toto rozhraní, je *ppvObj* nastaveno na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je váš modul odvozen z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` nejdřív vybere vlákno pro vytvoření objektu v přidruženém prostředí Apartment.

##  <a name="lockserver"></a>  CComClassFactoryAutoThread::LockServer

Zvýší a sníží počet zámků modulu voláním `_Module::Lock` a `_Module::Unlock`v uvedeném pořadí.

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*stád*<br/>
pro Při hodnotě TRUE se zvýší počet zámků; v opačném případě se počet zámků sníží.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Při použití `CComClassFactoryAutoThread`se `_Module` obvykle odkazuje na globální instanci [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Volání `LockServer` umožňuje klientovi umístit se do objektu pro vytváření tříd, aby bylo možné rychle vytvořit více objektů.

## <a name="see-also"></a>Viz také:

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 – třída](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactorySingleton – třída](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
