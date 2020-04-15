---
title: Třída CComEnumImpl
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
ms.openlocfilehash: 965e0a8bf6c890882754b60e2785832933d1c52c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327867"
---
# <a name="ccomenumimpl-class"></a>Třída CComEnumImpl

Tato třída poskytuje implementaci pro rozhraní výčtu COM, kde jsou položky, které jsou výčtovány, uloženy v poli.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Parametry

*Základní*<br/>
Rozhraní čítače výčtu COM. Viz [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) pro příklad.

*piid*<br/>
Ukazatel na ID rozhraní rozhraní čítače.

*T*<br/>
Typ položky vystavené rozhraní množek.

*Kopírovat*<br/>
Homogenní třída [zásad kopírování](../../atl/atl-copy-policy-classes.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Konstruktor|
|[CComEnumImpl::~CComEnumImpl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComEnumImpl::Klonování](#clone)|Implementace metody rozhraní **clone** výčtu.|
|[CComEnumImpl::Init](#init)|Inicializuje čítač výčtu.|
|[CComEnumImpl::Další](#next)|Implementace **Next**.|
|[CComEnumImpl::Obnovit](#reset)|Implementace **reset**.|
|[CComEnumImpl::Přeskočit](#skip)|Implementace **Skip**.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComEnumImpl::m_begin](#m_begin)|Ukazatel na první položku v poli.|
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Kopírovat příznaky `Init`prošel .|
|[CComEnumImpl::m_end](#m_end)|Ukazatel na umístění těsně za poslední položku v poli.|
|[CComEnumImpl::m_iter](#m_iter)|Ukazatel na aktuální položku v poli.|
|[CComEnumImpl::m_spUnk](#m_spunk)|Ukazatel `IUnknown` objektu, který poskytuje kolekci, která je výčtována.|

## <a name="remarks"></a>Poznámky

Viz [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) příklad implementace metody. `CComEnumImpl`poskytuje implementaci pro rozhraní výčtu COM, kde jsou položky, které jsou výčty uloženy v poli. Tato třída je obdobou `IEnumOnSTLImpl` třídy, která poskytuje implementaci rozhraní výčtu založené na kontejneru standardní knihovny Jazyka C++.

> [!NOTE]
> Podrobnosti o dalších `CComEnumImpl` `IEnumOnSTLImpl`rozdílech mezi písmenem a ) naleznete v [tématu CComEnumImpl::Init](#init).

Obvykle *nebudete* muset vytvořit vlastní třídu čítače odvozením z této implementace rozhraní. Pokud chcete použít čítač dodaný atl na základě pole, je běžnější vytvořit instanci [CComEnum](../../atl/reference/ccomenum-class.md).

Však pokud je třeba zadat vlastní čítač výčtu (například ten, který zpřístupňuje rozhraní kromě rozhraní čítače), můžete odvodit z této třídy. V takovém případě je pravděpodobné, že budete muset přepsat [CComEnumImpl::Clone](#clone) metoda poskytnout vlastní implementaci.

Další informace naleznete v tématu [kolekce atl a čítače výčtu](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl

Konstruktor

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>CComEnumImpl::~CComEnumImpl

Destruktor.

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>CComEnumImpl::Init

Tuto metodu je nutné volat před předáním ukazatele rozhraní enumerator zpět všem klientům.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Parametry

*Začít*<br/>
Ukazatel na první prvek pole obsahující položky, které mají být výčtu.

*Konec*<br/>
Ukazatel na umístění těsně za poslední prvek pole obsahující položky, které mají být výčtu.

*Punk*<br/>
[v] Ukazatel `IUnknown` objektu, který musí zůstat naživu během životnosti čítače výčtu. Předat hodnotu NULL, pokud žádný takový objekt neexistuje.

*příznaky*<br/>
Příznaky určující, zda má čítač výčtu převzít vlastnictví pole nebo vytvořit jeho kopii. Možné hodnoty jsou popsány níže.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pouze volání této metody jednou – inicializovat čítač výčtu, použijte jej, pak vyhodit.

Pokud předáte ukazatele na položky v poli držené v jiném objektu (a nepožádáte čítače výčtu ke kopírování dat), můžete použít parametr *pUnk* k zajištění, že objekt a pole, které drží, jsou k dispozici tak dlouho, dokud je čítač enumerator potřebuje. Čítač výčtu jednoduše obsahuje odkaz COM na objekt, aby jej udrželi naživu. Odkaz COM je automaticky uvolněna při zničení čítače výčtu.

Parametr *flags* umožňuje určit, jak by měl čítač enumerator zacházet s prvky pole, které mu byly předány. *příznaky* mohou mít jednu `CComEnumFlags` z hodnot z výčtu uvedeného níže:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`znamená, že životnost pole není řízena čítatelem výčtu. V takovém případě bude pole statické nebo objekt identifikovaný *pomocí pUnk* bude zodpovědný za uvolnění pole, když již není potřeba.

`AtlFlagTakeOwnership`znamená, že zničení pole má být řízeno čítatelem výčtu. V tomto případě musí být pole dynamicky přiděleno pomocí **nového**. Čítač výčtu odstraní pole v jeho destruktoru. Obvykle by předat NULL pro *pUnk*, i když stále můžete předat platný ukazatel, pokud potřebujete být upozorněni na zničení čítače výčtu z nějakého důvodu.

`AtlFlagCopy`znamená, že nové pole má být vytvořeno zkopírováním pole předaným společnosti `Init`. Životnost nového pole má být řízena čítatelem výčtu. Čítač výčtu odstraní pole v jeho destruktoru. Obvykle by předat NULL pro *pUnk*, i když stále můžete předat platný ukazatel, pokud potřebujete být upozorněni na zničení čítače výčtu z nějakého důvodu.

> [!NOTE]
> Prototyp této metody určuje prvky pole jako `T`typ `T` , kde byl definován jako parametr šablony pro třídu. Jedná se o stejný typ, který je vystaven pomocí metody rozhraní COM [CComEnumImpl::Next](#next). Důsledkem je, že na rozdíl od [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), tato třída nepodporuje různé úložiště a vystavené datové typy. Datový typ prvků v poli musí být stejný jako datový typ vystavený pomocí rozhraní COM.

## <a name="ccomenumimplclone"></a><a name="clone"></a>CComEnumImpl::Klonování

Tato metoda poskytuje implementaci **Metody Clone** vytvořením `CComEnum`objektu typu , inicializací se stejným polem a iterátorem používaným aktuálním objektem a vrácením rozhraní nově vytvořeného objektu.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parametry

*ppEnum*<br/>
[out] Rozhraní čítače na nově vytvořený objekt klonovaný z aktuálního čítače výčtu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Všimněte si, že klonované čítače výčtu nikdy vytvořit vlastní kopii (nebo převzít vlastnictví) dat používaných původní čítač výčtu. V případě potřeby klonované čítače výčtu zachovávají původní čítač enumeratoru aktivní (pomocí odkazu COM), aby bylo zajištěno, že data budou k dispozici tak dlouho, jak je potřebují.

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>CComEnumImpl::m_spUnk

Tento inteligentní ukazatel udržuje odkaz na objekt předán [CComEnumImpl::Init](#init), zajištění, že zůstane naživu po dobu životnosti čítače výčtu.

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>CComEnumImpl::m_begin

Ukazatel na umístění těsně za poslední prvek pole obsahující položky, které mají být výčtu.

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>CComEnumImpl::m_end

Ukazatel na první prvek pole obsahující položky, které mají být výčtu.

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>CComEnumImpl::m_iter

Ukazatel na aktuální prvek pole obsahující položky, které mají být výčtu.

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>CComEnumImpl::m_dwFlags

Příznaky předané [CComEnumImpl::Init](#init).

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>CComEnumImpl::Další

Tato metoda poskytuje implementaci **Next** metoda.

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
[v] Počet požadovaných prvků.

*rgelt (Rgelt)*<br/>
[out] Pole, které má být vyplněno prvky.

*pceltnačten*<br/>
[out] Počet prvků skutečně vrácených v *rgelt*. To může být menší než *celt,* pokud v seznamu zůstalo méně než *keltové* prvky.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ccomenumimplreset"></a><a name="reset"></a>CComEnumImpl::Obnovit

Tato metoda poskytuje implementaci **Reset** metoda.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ccomenumimplskip"></a><a name="skip"></a>CComEnumImpl::Přeskočit

Tato metoda poskytuje implementaci **Skip** metoda.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
[v] Počet prvků přeskočit.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vrátí E_INVALIDARG pokud je *celt nula,* vrátí S_FALSE pokud jsou vráceny méně než *keltové* prvky, vrátí S_OK jinak.

## <a name="see-also"></a>Viz také

[Třída IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Třída CComEnum](../../atl/reference/ccomenum-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
