---
title: Třída IEnumOnSTLImpl
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
ms.openlocfilehash: 2fbe6ccfbea2836c42a054da7ea9ebeac4e1555d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329715"
---
# <a name="ienumonstlimpl-class"></a>Třída IEnumOnSTLImpl

Tato třída definuje rozhraní výčtu založené na kolekci standardní knihovny jazyka C++.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>Parametry

*Základní*<br/>
Čítač výčtu COM. Viz [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) pro příklad.

*piid*<br/>
Ukazatel na ID rozhraní rozhraní čítače.

*T*<br/>
Typ položky vystavené rozhraní množek.

*Kopírovat*<br/>
Třída [zásad kopírování](../../atl/atl-copy-policy-classes.md).

*CollType*<br/>
Třída kontejneru standardní knihovny jazyka C++.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IEnumOnSTLImpl::Klonovat](#clone)|Implementace **Clone**.|
|[IEnumOnSTLImpl::Init](#init)|Inicializuje čítač výčtu.|
|[IEnumOnSTLImpl::Další](#next)|Implementace **Next**.|
|[IEnumOnSTLImpl::Obnovit](#reset)|Implementace **reset**.|
|[IEnumOnSTLImpl::Přeskočit](#skip)|Implementace **Skip**.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|Iterátor, který představuje aktuální pozici čítače v rámci kolekce.|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Ukazatel na kontejner standardní knihovny jazyka C++, který obsahuje položky, které mají být výčtovány.|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|Ukazatel `IUnknown` objektu dodávající kolekce.|

## <a name="remarks"></a>Poznámky

`IEnumOnSTLImpl`poskytuje implementaci pro rozhraní výčtu modelu COM, kde jsou položky, které jsou výčty uloženy v kontejneru kompatibilním se standardní knihovnou c++. Tato třída je obdobou [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) třídy, která poskytuje implementaci pro rozhraní výčtu založené na pole.

> [!NOTE]
> [Podrobnosti](../../atl/reference/ccomenumimpl-class.md#init) o dalších rozdílech mezi `CComEnumImpl` a `IEnumOnSTLImpl`.

Obvykle *nebudete* muset vytvořit vlastní třídu čítače odvozením z této implementace rozhraní. Pokud chcete použít čítač dodaný knihovnou ATL na základě kontejneru standardní knihovny jazyka C++, je běžnější vytvořit instanci [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)nebo vytvořit třídu kolekce, která vrací čítač podle odvození z [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).

Však pokud je třeba zadat vlastní čítač výčtu (například ten, který zpřístupňuje rozhraní kromě rozhraní čítače), můžete odvodit z této třídy. V takovém případě je pravděpodobné, že budete muset přepsat [Clone](#clone) metodu poskytnout vlastní implementaci.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ienumonstlimplinit"></a><a name="init"></a>IEnumOnSTLImpl::Init

Inicializuje čítač výčtu.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>Parametry

*pUnkForRelease*<br/>
[v] Ukazatel `IUnknown` objektu, který musí zůstat naživu během životnosti čítače výčtu. Předat hodnotu NULL, pokud žádný takový objekt neexistuje.

*Kolekce*<br/>
Odkaz na kontejner standardní knihovny Jazyka C++, který obsahuje položky, které mají být výčtovány.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud předáte `Init` odkaz na kolekci držené v jiném objektu, můžete použít parametr *pUnkForRelease* k zajištění, že objekt a kolekce, kterou obsahuje, je k dispozici tak dlouho, dokud to čítač výčtu potřebuje.

Tuto metodu je nutné volat před předáním ukazatele rozhraní enumerator zpět všem klientům.

## <a name="ienumonstlimplclone"></a><a name="clone"></a>IEnumOnSTLImpl::Klonovat

Tato metoda poskytuje implementaci **Clone** metoda vytvořením `CComEnumOnSTL`objektu typu , inicializace se stejnou kolekci a iterátor používaný aktuální objekt a vrácení rozhraní na nově vytvořený objekt.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parametry

*ppEnum*<br/>
[out] Rozhraní čítače na nově vytvořený objekt klonovaný z aktuálního čítače výčtu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ienumonstlimplm_spunk"></a><a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk

Ukazatel `IUnknown` objektu dodávající kolekce.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Poznámky

Tento inteligentní ukazatel udržuje odkaz na objekt předán [IEnumOnSTLImpl::Init](#init), zajištění, že zůstane naživu po dobu životnosti čítače výčtu.

## <a name="ienumonstlimplm_pcollection"></a><a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection

Tento člen odkazuje na kolekci, která poskytuje data řízení implementace rozhraní čítače výčtu.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Poznámky

Tento člen je inicializován voláním [IEnumOnSTLImpl::Init](#init).

## <a name="ienumonstlimplm_iter"></a><a name="m_iter"></a>IEnumOnSTLImpl::m_iter

Tento člen drží iterátor slouží k označení aktuální pozici v rámci kolekce a přejděte na další prvky.

```
CollType::iterator m_iter;
```

## <a name="ienumonstlimplnext"></a><a name="next"></a>IEnumOnSTLImpl::Další

Tato metoda poskytuje implementaci **Next** metoda.

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
[v] Počet požadovaných prvků.

*rgelt (Rgelt)*<br/>
[out] Pole, které má být vyplněno prvky.

*pceltnačten*<br/>
[out] Počet prvků skutečně vrácených v *rgelt*. To může být menší než *celt,* pokud v seznamu zůstane méně než *keltové* prvky.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ienumonstlimplreset"></a><a name="reset"></a>IEnumOnSTLImpl::Obnovit

Tato metoda poskytuje implementaci **Reset** metoda.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ienumonstlimplskip"></a><a name="skip"></a>IEnumOnSTLImpl::Přeskočit

Tato metoda poskytuje implementaci **Skip** metoda.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
[v] Počet prvků přeskočit.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
