---
title: IEnumOnSTLImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
ms.openlocfilehash: 7cf777f3ff0d298f224157735a06bf57a2c10cf5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495863"
---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl – třída

Tato třída definuje rozhraní enumerátoru na základě C++ standardní kolekce knihoven.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>Parametry

*Základ*<br/>
Enumerátor COM. Příklad najdete v tématu [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

*piid*<br/>
Ukazatel na ID rozhraní rozhraní enumerátoru.

*T*<br/>
Typ položky vystavený rozhraním enumerátoru.

*kopírování*<br/>
[Třída zásad kopírování](../../atl/atl-copy-policy-classes.md).

*CollType*<br/>
Třída C++ kontejneru standardní knihovny.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IEnumOnSTLImpl::Clone](#clone)|Implementace klonu.|
|[IEnumOnSTLImpl::Init](#init)|Inicializuje enumerátor.|
|[IEnumOnSTLImpl::Next](#next)|Implementace **Next**.|
|[IEnumOnSTLImpl:: Reset](#reset)|Implementace resetu.|
|[IEnumOnSTLImpl:: Skip](#skip)|Implementace **Skip**.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|Iterátor, který představuje aktuální pozici čítače výčtu v rámci kolekce.|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Ukazatel na C++ standardní kontejner knihovny, který uchovává položky, které mají být vyčísleny.|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|`IUnknown` Ukazatel objektu, který poskytuje kolekci.|

## <a name="remarks"></a>Poznámky

`IEnumOnSTLImpl`poskytuje implementaci rozhraní enumerátoru modelu COM, kde jsou položky výčtové, uloženy ve C++ standardním kontejneru kompatibilním s knihovnou. Tato třída je podobná třídě [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) , která poskytuje implementaci rozhraní enumerátoru založeného na poli.

> [!NOTE]
>  Podrobnosti o dalších rozdílech mezi `CComEnumImpl` a `IEnumOnSTLImpl`získáte v tématu [CComEnumImpl:: init](../../atl/reference/ccomenumimpl-class.md#init) .

Obvykle nebudete muset vytvářet vlastní třídu enumerátoru odvozením z této implementace rozhraní. Pokud chcete použít enumerátor dodaný ATL na základě C++ standardního kontejneru knihovny, je obvyklejší vytvořit instanci [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)nebo vytvořit třídu kolekce, která vrací enumerátor odvozením z [ICollectionOnSTLImpl ](../../atl/reference/icollectiononstlimpl-class.md).

Pokud však potřebujete zadat vlastní enumerátor (například jeden, který zveřejňuje rozhraní kromě rozhraní enumerátor), můžete z této třídy odvodit. V této situaci je pravděpodobně nutné přepsat metodu klonování, aby byla [](#clone) zajištěna vaše vlastní implementace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="init"></a>IEnumOnSTLImpl:: init

Inicializuje enumerátor.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>Parametry

*pUnkForRelease*<br/>
pro `IUnknown` Ukazatel objektu, který musí být během životnosti čítače udržován v aktivním stavu. Pokud žádný takový objekt neexistuje, předejte hodnotu NULL.

*kolekce*<br/>
Odkaz na C++ standardní kontejner knihovny, který obsahuje položky, které mají být vyčísleny.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud předáte `Init` odkaz na kolekci uloženou v jiném objektu, můžete použít parametr *pUnkForRelease* a zajistit tak, že objekt a kolekce, které jsou v něm uloženy, jsou k dispozici, dokud je enumerátor vyžaduje.

Tato metoda musí být volána před předáním ukazatele na rozhraní enumerátoru zpátky na všechny klienty.

##  <a name="clone"></a>IEnumOnSTLImpl:: Clone

Tato metoda poskytuje implementaci metody klonování vytvořením objektu typu `CComEnumOnSTL`, inicializací se stejnou kolekcí a iterátorem použitým aktuálním objektem a vrácením rozhraní u nově vytvořeného objektu.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parametry

*ppEnum*<br/>
mimo Rozhraní enumerátoru u nově vytvořeného objektu naklonované z aktuálního enumerátoru.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="m_spunk"></a>  IEnumOnSTLImpl::m_spUnk

`IUnknown` Ukazatel objektu, který poskytuje kolekci.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Poznámky

Tento inteligentní ukazatel udržuje odkaz na objekt předaný do [IEnumOnSTLImpl:: init](#init)a zajišťuje tak, že zůstane aktivní během životnosti enumerátoru.

##  <a name="m_pcollection"></a>  IEnumOnSTLImpl::m_pcollection

Tento člen odkazuje na kolekci, která poskytuje data, která řídí implementaci rozhraní enumerátoru.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Poznámky

Tento člen je inicializován voláním metody [IEnumOnSTLImpl:: init](#init).

##  <a name="m_iter"></a>  IEnumOnSTLImpl::m_iter

Tento člen obsahuje iterátor, který slouží k označení aktuální pozice v rámci kolekce a přechodu na následné prvky.

```
CollType::iterator m_iter;
```

##  <a name="next"></a>IEnumOnSTLImpl:: Next

Tato metoda poskytuje implementaci **Další** metody.

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
pro Počet požadovaných prvků.

*rgelt*<br/>
mimo Pole, které se má vyplnit prvky.

*pceltFetched*<br/>
mimo Počet prvků skutečně vrácených v *rgelt*. To může být menší než *celt* , pokud v seznamu zůstane méně než *celt* prvky.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="reset"></a>IEnumOnSTLImpl:: Reset

Tato metoda poskytuje implementaci metody resetování .

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="skip"></a>IEnumOnSTLImpl:: Skip

Tato metoda poskytuje implementaci metody **Skip** .

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
pro Počet prvků, které se mají přeskočit

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
