---
title: Ccomtearoffobject – třída
ms.date: 11/04/2016
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
ms.openlocfilehash: 78e9bda9c21ce53fa5b775b83be5c978c3fa1431
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555256"
---
# <a name="ccomtearoffobject-class"></a>Ccomtearoffobject – třída

Tato třída implementuje rozhraní s odnímatelnými nabídkami.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>Parametry

*základ*<br/>
Vaše odtržených třída odvozena od `CComTearOffObjectBase` a rozhraní chcete, aby váš objekt odtržených pro podporu.

ATL – implementuje jeho odtržených rozhraní ve dvou fázích – `CComTearOffObjectBase` metody zpracovávají počet odkazů a `QueryInterface`, zatímco `CComTearOffObject` implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|Konstruktor|
|[Ccomtearoffobject –:: ~ ccomtearoffobject –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComTearOffObject::AddRef](#addref)|Zvýší počet odkazů `CComTearOffObject` objektu.|
|[CComTearOffObject::QueryInterface](#queryinterface)|Vrací ukazatel na požadované rozhraní na vaší třídy odtržených nebo třída vlastníka.|
|[CComTearOffObject::Release](#release)|Sníží počet odkaz pro `CComTearOffObject` objektu a odstraní jej.|

### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase metody

|||
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Konstruktor|

### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase datové členy

|||
|-|-|
|[m_pOwner](#m_powner)|Ukazatel `CComObject` odvozené od třídy vlastníka.|

## <a name="remarks"></a>Poznámky

`CComTearOffObject` implementuje rozhraní s odnímatelnými nabídkami jako samostatný objekt, jehož instance je vytvořena pouze v případě, že toto rozhraní se dotazují pro. Odtrhnout se odstraní při jeho počet odkazů klesne na nulu. Obvykle vytvoříte rozhraní odtržených rozhraní, který se používá jen občas, protože použití odnímatelnými nabídkami ukládá ukazatel vtable ve všech instancích hlavním objektem.

By měla být odvozena třída implementace odtržených z `CComTearOffObjectBase` a z toho rozhraní má objekt odtržených na podporu. `CComTearOffObjectBase` je založena na třídě vlastníka a modelu vláken. Třída vlastníka je třídu objektu, pro kterou odnímatelnými nabídkami se implementuje. Pokud model vláken nezadáte, použije se výchozí model vláken.

Třídy odtržených byste měli vytvořit mapu COM. Když odtrhnout vytvoří instanci ATL, vytvoří `CComTearOffObject<CYourTearOffClass>` nebo `CComCachedTearOffObject<CYourTearOffClass>`.

Například v ukázce BEEPER `CBeeper2` třídy je třída odnímatelnými nabídkami a `CBeeper` třídy je třída vlastníka:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComTearOffObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="addref"></a>  CComTearOffObject::AddRef

Zvýší počet odkazů `CComTearOffObject` objekt o jednu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečné pro diagnostiku a testování.

##  <a name="ccomtearoffobject"></a>  CComTearOffObject::CComTearOffObject

Konstruktor

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
[in] Ukazatel, který bude převeden na ukazatel `CComObject<Owner>` objektu.

### <a name="remarks"></a>Poznámky

Zvýší počet odkazů vlastníka o jednu.

##  <a name="dtor"></a>  Ccomtearoffobject –:: ~ ccomtearoffobject –

Destruktor.

```
~CComTearOffObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, volání modulu FinalRelease a sníží počet uzamčení.

##  <a name="ccomtearoffobjectbase"></a>  CComTearOffObject::CComTearOffObjectBase

Konstruktor

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Poznámky

Inicializuje [m_pOwner](#m_powner) člena na hodnotu NULL.

##  <a name="m_powner"></a>  CComTearOffObject::m_pOwner

Ukazatel [CComObject](../../atl/reference/ccomobject-class.md) objekt odvozený od *vlastníka*.

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>Parametry

*Vlastník*<br/>
[in] Třída, pro kterou odnímatelnými nabídkami se implementuje.

### <a name="remarks"></a>Poznámky

Během konstrukce je inicializován ukazatel na hodnotu NULL.

##  <a name="queryinterface"></a>  CComTearOffObject::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*identifikátor IID*<br/>
[in] Identifikátor IID rozhraní žádá.

*ppvObject*<br/>
[out] Ukazatel na ukazatel rozhraní, který je identifikován *iid*, nebo hodnota NULL, pokud se nenajde rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Dotazy pro rozhraní na třídě odnímatelnými nabídkami. Pokud rozhraní není, dotazy na rozhraní objektu vlastníka. Pokud je požadovaná rozhraní `IUnknown`, vrátí `IUnknown` vlastníka.

##  <a name="release"></a>  CComTearOffObject::Release

Sníží počet referenční jednou a je-li počet odkazů nuly, odstraní `CComTearOffObject`.

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>Návratová hodnota

V sestaveních bez ladění vždy vrátí hodnotu 0. V sestavení ladění vrátí hodnotu, která může být užitečné pro diagnostiku a testování.

## <a name="see-also"></a>Viz také

[CComCachedTearOffObject – třída](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
