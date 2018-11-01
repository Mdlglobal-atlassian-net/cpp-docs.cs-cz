---
title: Ccomenumimpl – třída
ms.date: 11/04/2016
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
helpviewer_keywords:
- CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
ms.openlocfilehash: 2104d98cbc068eb5d8f1408cdda0898fd55c9473
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467142"
---
# <a name="ccomenumimpl-class"></a>Ccomenumimpl – třída

Tato třída poskytuje implementaci pro uložení položky výčtu v poli rozhraní modelu COM enumerátor.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Parametry

*základ*<br/>
Enumerátor rozhraní modelu COM. Zobrazit [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) příklad.

*piid*<br/>
Ukazatel na Identifikátor rozhraní rozhraní enumerátor.

*T*<br/>
Typ položky, které jsou vystavené rozhraní enumerátor.

*kopírování*<br/>
Homogenní [třídy zásady kopírování](../../atl/atl-copy-policy-classes.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Konstruktor|
|[Ccomenumimpl –:: ~ ccomenumimpl –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComEnumImpl::Clone](#clone)|Provádění **klonování** výčtu rozhraní metodu.|
|[CComEnumImpl::Init](#init)|Inicializuje čítače výčtu.|
|[CComEnumImpl::Next](#next)|Provádění **Další**.|
|[CComEnumImpl::Reset](#reset)|Provádění **resetování**.|
|[CComEnumImpl::Skip](#skip)|Provádění **přeskočit**.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComEnumImpl::m_begin](#m_begin)|Ukazatel na první položku v poli.|
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Zkopírujte příznaky předává `Init`.|
|[CComEnumImpl::m_end](#m_end)|Ukazatel na umístění hned za poslední položku v poli.|
|[CComEnumImpl::m_iter](#m_iter)|Ukazatel na aktuální položku v poli.|
|[CComEnumImpl::m_spUnk](#m_spunk)|`IUnknown` Ukazatel objektu, který poskytuje kolekci výčtu.|

## <a name="remarks"></a>Poznámky

Zobrazit [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) příklad implementace metody. `CComEnumImpl` poskytuje implementaci pro uložení položky výčtu v poli rozhraní modelu COM enumerátor. Tato třída je obdobou `IEnumOnSTLImpl` třídu, která poskytuje implementaci rozhraní enumerátor podle kontejneru standardní knihovny C++.

> [!NOTE]
>  Podrobnosti o další rozdíly mezi `CComEnumImpl` a `IEnumOnSTLImpl`, naleznete v tématu [CComEnumImpl::Init](#init).

Obvykle bude *není* muset vytvořit vlastní čítač třídy odvozené z implementace tohoto rozhraní. Pokud chcete použít enumerátor ATL poskytované na základě pole, je běžné vytvořit instanci [ccomenum –](../../atl/reference/ccomenum-class.md).

Ale pokud potřebujete poskytovat vlastní čítače výčtu (například jeden, který zpřístupňuje rozhraní kromě rozhraní enumerátor), můžete odvozovat z této třídy. V takovém případě je pravděpodobné, že bude nutné přepsat [CComEnumImpl::Clone](#clone) metodu a zadejte vlastní implementaci.

Další informace najdete v tématu [ATL – kolekce a enumerátory](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="ccomenumimpl"></a>  CComEnumImpl::CComEnumImpl

Konstruktor

```
CComEnumImpl();
```

##  <a name="dtor"></a>  Ccomenumimpl –:: ~ ccomenumimpl –

Destruktor.

```
~CComEnumImpl();
```

##  <a name="init"></a>  CComEnumImpl::Init

Tato metoda musí volat před předáním ukazatel rozhraní enumerátor zpět na všechny klienty.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Parametry

*začít*<br/>
Ukazatel na první prvek pole obsahující položky, které chcete vytvořit výčet.

*ukončení*<br/>
Ukazatel na umístění hned za poslední prvek pole obsahující položky, které chcete vytvořit výčet.

*pUnk*<br/>
[in] `IUnknown` Ukazatel objektu, který musí být zachováno po celou dobu životnosti enumerátor. Předejte hodnotu NULL, pokud žádný takový objekt neexistuje.

*příznaky*<br/>
Příznaky určující, zda by měl čítač převzít vlastnictví pole nebo vytvořte jeho kopii. Možné hodnoty jsou popsané níže.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pouze po volání této metody – inicializovat čítač, použijte ho a pak se zbavovat.

Pokud předáte ukazatele na položky v poli nachází v jiném objektu (a neptat enumerátor ke zkopírování dat), můžete použít *pUnk* parametr ujistit, že jsou k dispozici, dokud je enumerátor pro objekt a pole obsahuje je potřebuje. Enumerátor jednoduše uchovává odkaz modelu COM na objekt, který chcete udržovat aktivní. Odkaz modelu COM je automaticky uvolněn, pokud je zničen enumerátor.

*Příznaky* parametr umožňuje určit, jak enumerátor by měly zpracovávat do něho předaný prvků pole. *příznaky* můžete provést jednu z hodnot `CComEnumFlags` výčtu je uvedeno níže:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy` znamená, že doba platnosti tohoto pole není řízen enumerátor. V takovém případě buď pole bude statické nebo objekt identifikovaný *pUnk* bude zodpovědná za uvolnění pole, pokud už je nepotřebujete.

`AtlFlagTakeOwnership` znamená, že odstranění pole je kontrolován enumerátor. V tomto případě pole musí být dynamicky přidělený pomocí **nové**. Enumerátor odstraní pole ve svém destruktoru. Obvykle by předat hodnotu NULL pro *pUnk*, i když stále můžete předat platný ukazatel Pokud potřebujete upozornit zničení enumerátor z nějakého důvodu.

`AtlFlagCopy` znamená, že nové pole má být vytvořen tak, že zkopírujete pole předána `Init`. Nové pole životnost je kontrolován enumerátor. Enumerátor odstraní pole ve svém destruktoru. Obvykle by předat hodnotu NULL pro *pUnk*, i když stále můžete předat platný ukazatel Pokud potřebujete upozornit zničení enumerátor z nějakého důvodu.

> [!NOTE]
>  Prototyp této metody určuje jako typ prvků pole `T`, kde `T` byl definován jako parametr šablony třídy. Jedná se o stejný typ, který je zveřejněný prostřednictvím metody rozhraní COM [CComEnumImpl::Next](#next). Důsledkem tohoto je, že na rozdíl od [ienumonstlimpl –](../../atl/reference/ienumonstlimpl-class.md), tato třída nepodporuje jiného úložiště a vystavený datové typy. Datový typ prvků v poli musí být stejný jako datový typ vystavené prostřednictvím rozhraní modelu COM.

##  <a name="clone"></a>  CComEnumImpl::Clone

Tato metoda poskytuje implementaci **klonování** metodu tak, že vytvoříte objekt typu `CComEnum`, inicializuje se stejnými pole a používá aktuální objekt iterátoru a vrací rozhraní na nově vytvořený objekt.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parametry

*ppEnum*<br/>
[out] Enumerátor rozhraní na nově vytvořený objekt naklonovali z aktuální enumerátor.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Nezapomeňte, že klonovaný enumerátory nikdy vytvořit své vlastní kopii (nebo převzít vlastnictví) dat používaných původní enumerátor. V případě potřeby naklonované enumerátory se zachování původního enumerátor (pomocí odkaz modelu COM) k zajištění, že data jsou k dispozici pro za předpokladu, které potřebují.

##  <a name="m_spunk"></a>  CComEnumImpl::m_spUnk

Inteligentní ukazatele this udržuje odkaz na objekt předaný [CComEnumImpl::Init](#init), zajištění, že zůstane aktivní po dobu životnosti enumerátor.

```
CComPtr<IUnknown> m_spUnk;
```

##  <a name="m_begin"></a>  CComEnumImpl::m_begin

Ukazatel na umístění hned za poslední prvek pole obsahující položky, které chcete vytvořit výčet.

```
T* m_begin;
```

##  <a name="m_end"></a>  CComEnumImpl::m_end

Ukazatel na první prvek pole obsahující položky, které chcete vytvořit výčet.

```
T* m_end;
```

##  <a name="m_iter"></a>  CComEnumImpl::m_iter

Ukazatel na aktuální prvek pole obsahující položky, které chcete vytvořit výčet.

```
T* m_iter;
```

##  <a name="m_dwflags"></a>  CComEnumImpl::m_dwFlags

Příznaky předán [CComEnumImpl::Init](#init).

```
DWORD m_dwFlags;
```

##  <a name="next"></a>  CComEnumImpl::Next

Tato metoda poskytuje implementaci **Další** metody.

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
[in] Počet prvků požadavku.

*rgelt*<br/>
[out] Pole pro vyplnění s prvky.

*pceltFetched*<br/>
[out] Počet prvků ve skutečnosti vrátí v *rgelt*. To může být kratší než *celt* Pokud méně než *celt* prvků zůstávaly v seznamu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="reset"></a>  CComEnumImpl::Reset

Tato metoda poskytuje implementaci **resetování** metody.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="skip"></a>  CComEnumImpl::Skip

Tato metoda poskytuje implementaci **přeskočit** metody.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
[in] Počet prvků, které mají přeskočit.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pokud vrátí E_INVALIDARG *celt* je nula, vrátí S_FALSE, je-li menší než *celt* prvky jsou vráceny, v opačném případě vrátí hodnotu S_OK.

## <a name="see-also"></a>Viz také

[IEnumOnSTLImpl – třída](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum – třída](../../atl/reference/ccomenum-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
