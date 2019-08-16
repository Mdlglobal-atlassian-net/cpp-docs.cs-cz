---
title: CComEnumImpl – třída
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
ms.openlocfilehash: 7d26c59a38bfe43e49215fbb6108453e10ca6dea
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497176"
---
# <a name="ccomenumimpl-class"></a>CComEnumImpl – třída

Tato třída poskytuje implementaci rozhraní enumerátoru modelu COM, kde jsou položky výčtové v poli uloženy.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Parametry

*Základ*<br/>
Rozhraní enumerátoru COM. Příklad najdete v tématu [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

*piid*<br/>
Ukazatel na ID rozhraní rozhraní enumerátoru.

*T*<br/>
Typ položky vystavený rozhraním enumerátoru.

*kopírování*<br/>
[Třída zásad](../../atl/atl-copy-policy-classes.md)pro homogenní kopírování.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Konstruktor|
|[CComEnumImpl::~CComEnumImpl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComEnumImpl:: Clone](#clone)|Implementace metody rozhraní výčtu **klonování** .|
|[CComEnumImpl:: init](#init)|Inicializuje enumerátor.|
|[CComEnumImpl::Next](#next)|Implementace **Next**.|
|[CComEnumImpl:: Reset](#reset)|Implementace resetu.|
|[CComEnumImpl::Skip](#skip)|Implementace **Skip**.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComEnumImpl::m_begin](#m_begin)|Ukazatel na první položku v poli.|
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Příznaky kopírování předané `Init`.|
|[CComEnumImpl::m_end](#m_end)|Ukazatel na umístění hned za poslední položkou v poli.|
|[CComEnumImpl::m_iter](#m_iter)|Ukazatel na aktuální položku v poli.|
|[CComEnumImpl::m_spUnk](#m_spunk)|`IUnknown` Ukazatel objektu, který poskytuje výčet kolekce.|

## <a name="remarks"></a>Poznámky

Příklad implementace metod naleznete v tématu [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) . `CComEnumImpl`poskytuje implementaci pro rozhraní enumerátoru modelu COM, kde jsou výčtové položky uloženy v poli. Tato třída je analogická `IEnumOnSTLImpl` třídě, která poskytuje implementaci rozhraní enumerátoru na základě C++ standardního kontejneru knihovny.

> [!NOTE]
>  Podrobnosti o dalších rozdílech mezi `CComEnumImpl` a `IEnumOnSTLImpl`naleznete v tématu [CComEnumImpl:: init](#init).

Obvykle nebudete muset vytvářet vlastní třídu enumerátoru odvozením z této implementace rozhraní. Pokud chcete použít enumerátor dodaný ATL na základě pole, je obvyklejší vytvořit instanci třídy [CComEnum](../../atl/reference/ccomenum-class.md).

Pokud však potřebujete zadat vlastní enumerátor (například jeden, který zveřejňuje rozhraní kromě rozhraní enumerátor), můžete z této třídy odvodit. V této situaci je pravděpodobně nutné přepsat metodu [CComEnumImpl:: Clone](#clone) k poskytnutí vlastní implementace.

Další informace naleznete v tématu [kolekce a čítače ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl

Konstruktor

```
CComEnumImpl();
```

##  <a name="dtor"></a>CComEnumImpl:: ~ CComEnumImpl

Destruktor.

```
~CComEnumImpl();
```

##  <a name="init"></a>CComEnumImpl:: init

Tato metoda musí být volána před předáním ukazatele na rozhraní enumerátoru zpátky na všechny klienty.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Parametry

*ifunctiondiscovery*<br/>
Ukazatel na první prvek pole obsahujícího položky, které mají být vyčísleny.

*účelu*<br/>
Ukazatel na umístění hned za posledním prvkem pole obsahujícího položky, které mají být vyčísleny.

*pUnk*<br/>
pro `IUnknown` Ukazatel objektu, který musí být během životnosti čítače udržován v aktivním stavu. Pokud žádný takový objekt neexistuje, předejte hodnotu NULL.

*Flag*<br/>
Příznaky určující, zda má enumerátor převzít vlastnictví pole nebo vytvořit jeho kopii. Možné hodnoty jsou popsány níže.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tuto metodu volejte jenom jednou – inicializujte enumerátor, použijte ho a pak ho vyvolejte.

Pokud předáte ukazatele na položky v poli, které jsou uloženy v jiném objektu (a nepožadujete enumerátor ke zkopírování dat), můžete použít parametr *punk* a zajistit tak, že objekt a pole, které jsou uchovávány, jsou k dispozici, dokud je enumerátor vyžaduje. Enumerátor jednoduše drží odkaz COM na objekt, aby zůstal aktivní. Odkaz COM je automaticky uvolněn při zničení enumerátoru.

Parametr *Flags* umožňuje určit, jak má enumerátor považovat prvky pole, které jsou předány. *příznaky* mohou převzít jednu z hodnot z `CComEnumFlags` výčtu uvedeného níže:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`znamená, že enumerátor neřídí životní cyklus pole. V takovém případě bude pole buď statické, nebo objekt identifikovaný pomocí *punk* bude zodpovědný za uvolnění pole, když už ho nepotřebujete.

`AtlFlagTakeOwnership`znamená, že zničení pole má být řízeno enumerátorem. V tomto případě musí být pole dynamicky přiděleno pomocí **New**. Enumerátor odstraní pole ve svém destruktoru. Obvykle byste předávali hodnotu NULL pro *punk*, i když je třeba předávat platný ukazatel, pokud potřebujete být upozorněni na zničení výčtu z nějakého důvodu.

`AtlFlagCopy`znamená, že nové pole se má vytvořit zkopírováním pole předaného `Init`. Doba života nového pole je řízena enumerátorem. Enumerátor odstraní pole ve svém destruktoru. Obvykle byste předávali hodnotu NULL pro *punk*, i když je třeba předávat platný ukazatel, pokud potřebujete být upozorněni na zničení výčtu z nějakého důvodu.

> [!NOTE]
>  Prototyp této metody určuje prvky pole jako typ `T`, kde `T` byl definován jako parametr šablony třídy. Toto je stejný typ, který je vystavený prostřednictvím metody rozhraní COM [CComEnumImpl:: Next](#next). Důvodem je, že na rozdíl od [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)Tato třída nepodporuje jiné úložiště a exponované datové typy. Datový typ prvků v poli musí být stejný jako datový typ vydaný prostřednictvím rozhraní COM.

##  <a name="clone"></a>CComEnumImpl:: Clone

Tato metoda poskytuje implementaci metody klonování vytvořením objektu typu `CComEnum`, jeho inicializací se stejným polem a iterátorem použitým aktuálním objektem a vrácením rozhraní u nově vytvořeného objektu.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parametry

*ppEnum*<br/>
mimo Rozhraní enumerátoru u nově vytvořeného objektu naklonované z aktuálního enumerátoru.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Všimněte si, že klonované výčty nikdy nevytvářejí vlastní kopii (nebo přebírají vlastnictví) dat, která používá původní enumerátor. V případě potřeby budou klonované výčty zůstat původní enumerátor aktivní (pomocí odkazu modelu COM), aby bylo zajištěno, že data budou k dispozici po dobu, po kterou ji potřebují.

##  <a name="m_spunk"></a>  CComEnumImpl::m_spUnk

Tento inteligentní ukazatel udržuje odkaz na objekt předaný do [CComEnumImpl:: init](#init)a zajišťuje tak, že zůstane aktivní během životnosti enumerátoru.

```
CComPtr<IUnknown> m_spUnk;
```

##  <a name="m_begin"></a>  CComEnumImpl::m_begin

Ukazatel na umístění hned za posledním prvkem pole obsahujícího položky, které mají být vyčísleny.

```
T* m_begin;
```

##  <a name="m_end"></a>  CComEnumImpl::m_end

Ukazatel na první prvek pole obsahujícího položky, které mají být vyčísleny.

```
T* m_end;
```

##  <a name="m_iter"></a>  CComEnumImpl::m_iter

Ukazatel na aktuální prvek pole obsahujícího položky, které mají být vyčísleny.

```
T* m_iter;
```

##  <a name="m_dwflags"></a>  CComEnumImpl::m_dwFlags

Příznaky předané do [CComEnumImpl:: init](#init).

```
DWORD m_dwFlags;
```

##  <a name="next"></a>CComEnumImpl:: Next

Tato metoda poskytuje implementaci **Další** metody.

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
pro Počet požadovaných prvků.

*rgelt*<br/>
mimo Pole, které má být vyplněno prvky.

*pceltFetched*<br/>
mimo Počet prvků skutečně vrácených v *rgelt*. To může být menší než *celt* , pokud v seznamu zůstalo méně než *celt* prvky.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="reset"></a>CComEnumImpl:: Reset

Tato metoda poskytuje implementaci metody resetování .

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="skip"></a>CComEnumImpl:: Skip

Tato metoda poskytuje implementaci metody **Skip** .

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parametry

*celt*<br/>
pro Počet prvků, které se mají přeskočit

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vrátí E_INVALIDARG, pokud *celt* je nula, vrátí S_FALSE, pokud jsou vraceny méně než *celt* prvky, vrátí S_OK jinak.

## <a name="see-also"></a>Viz také:

[IEnumOnSTLImpl – třída](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum – třída](../../atl/reference/ccomenum-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
