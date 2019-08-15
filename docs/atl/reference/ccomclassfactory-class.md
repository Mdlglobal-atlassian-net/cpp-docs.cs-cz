---
title: CComClassFactory – třída
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 892153e47ac4e9dd45d5dfc01b76f1ce29d23938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497453"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory – třída

Tato třída implementuje rozhraní [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .

## <a name="syntax"></a>Syntaxe

```
class CComClassFactory
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComClassFactory::CreateInstance](#createinstance)|Vytvoří objekt zadaného objektu CLSID.|
|[CComClassFactory::LockServer](#lockserver)|Zamkne objekt pro vytváření tříd v paměti.|

## <a name="remarks"></a>Poznámky

`CComClassFactory`implementuje rozhraní [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) , které obsahuje metody pro vytvoření objektu KONKRÉTNÍho identifikátoru CLSID, a také uzamykání objektu pro vytváření tříd v paměti, aby bylo možné rychle vytvořit nové objekty. `IClassFactory`je nutné implementovat pro každou třídu, kterou zaregistrujete do systémového registru a ke kterému přiřadíte CLSID.

Objekty ATL normálně získávají objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje makro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), které deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete-li přepsat toto výchozí nastavení, zadejte `DECLARE_CLASSFACTORY`jedno z maker *xxx* v definici třídy. Například makro [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) používá určenou třídu pro objekt pro vytváření tříd:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

Definice výše uvedené třídy určuje, `CMyClassFactory` který se použije jako výchozí objekt pro vytváření tříd. `CMyClassFactory`musí odvozovat `CComClassFactory` od a `CreateInstance`přepsat.

Knihovna ATL poskytuje tři další makra, která deklaruje objekt pro vytváření tříd:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) Používá [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), které řídí vytváření prostřednictvím licence.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) Používá [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), který vytváří objekty ve více objektech Apartment.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) Používá [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), který vytvoří jeden objekt [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="createinstance"></a>CComClassFactory:: CreateInstance

Vytvoří objekt zadaného identifikátoru CLSID a načte ukazatel rozhraní na tento objekt.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
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

##  <a name="lockserver"></a>  CComClassFactory::LockServer

Zvýší a sníží počet zámků modulu voláním `_Module::Lock` a `_Module::Unlock`v uvedeném pořadí.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*stád*<br/>
pro Při hodnotě TRUE se zvýší počet zámků; v opačném případě se počet zámků sníží.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`_Module`odkazuje na globální instanci [CComModule](../../atl/reference/ccommodule-class.md) nebo z ní odvozené třídy.

Volání `LockServer` umožňuje klientovi umístit se do objektu pro vytváření tříd, aby bylo možné rychle vytvořit více objektů.

## <a name="see-also"></a>Viz také:

[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
