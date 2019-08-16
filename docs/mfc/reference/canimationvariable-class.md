---
title: CAnimationVariable – třída
ms.date: 03/27/2019
f1_keywords:
- CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationVariable::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::Create
- AFXANIMATIONCONTROLLER/CAnimationVariable::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_dblDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_lstTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_pParentObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_variable
helpviewer_keywords:
- CAnimationVariable [MFC], CAnimationVariable
- CAnimationVariable [MFC], AddTransition
- CAnimationVariable [MFC], ApplyTransitions
- CAnimationVariable [MFC], ClearTransitions
- CAnimationVariable [MFC], Create
- CAnimationVariable [MFC], CreateTransitions
- CAnimationVariable [MFC], EnableIntegerValueChangedEvent
- CAnimationVariable [MFC], EnableValueChangedEvent
- CAnimationVariable [MFC], GetDefaultValue
- CAnimationVariable [MFC], GetParentAnimationObject
- CAnimationVariable [MFC], GetValue
- CAnimationVariable [MFC], GetVariable
- CAnimationVariable [MFC], SetDefaultValue
- CAnimationVariable [MFC], SetParentAnimationObject
- CAnimationVariable [MFC], m_bAutodestroyTransitions
- CAnimationVariable [MFC], m_dblDefaultValue
- CAnimationVariable [MFC], m_lstTransitions
- CAnimationVariable [MFC], m_pParentObject
- CAnimationVariable [MFC], m_variable
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
ms.openlocfilehash: b6767ed42d66aff467ef36bd2a7b5234ad181ced
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507542"
---
# <a name="canimationvariable-class"></a>CAnimationVariable – třída

Představuje proměnnou animace.

## <a name="syntax"></a>Syntaxe

```
class CAnimationVariable;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|Vytvoří objekt proměnné animace.|
|[CAnimationVariable:: ~ CAnimationVariable](#_dtorcanimationvariable)|Destruktor. Volána, když je zničen objekt CAnimationVariable.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAnimationVariable::AddTransition](#addtransition)|Přidá přechod.|
|[CAnimationVariable::ApplyTransitions](#applytransitions)|Přidá přechody z interního seznamu do scénáře.|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|Vymaže přechody.|
|[CAnimationVariable:: Create](#create)|Vytvoří základní objekt proměnné animace objektu COM.|
|[CAnimationVariable::CreateTransitions](#createtransitions)|Vytvoří všechny přechody, které mají být aplikovány na tuto proměnnou animace.|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Povolí nebo zakáže událost IntegerValueChanged.|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|Povolí nebo zakáže událost ValueChanged.|
|[CAnimationVariable:: getdefaultvalue](#getdefaultvalue)|Vrátí výchozí hodnotu.|
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|Vrátí nadřazený objekt animace.|
|[CAnimationVariable:: GetValue](#getvalue)|Přetíženo. Vrátí aktuální hodnotu proměnné animace.|
|[CAnimationVariable:: getvariable](#getvariable)|Vrátí ukazatel na objekt COM IUIAnimationVariable.|
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu a uvolní objekt COM IUIAnimationVariable.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|Nastaví vztah mezi proměnnou animace a objektem animace.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Určuje, zda se mají odstranit související objekty přechodu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|Určuje výchozí hodnotu, která je šířena do IUIAnimationVariable.|
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|Obsahuje seznam přechodů, které tuto proměnnou animace animuje.|
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|Ukazatel na objekt animace, který zapouzdřuje tuto proměnnou animace.|
|[CAnimationVariable::m_variable](#m_variable)|Ukládá ukazatel na objekt COM IUIAnimationVariable. Hodnota NULL, pokud objekt COM ještě nebyl vytvořen, nebo pokud vytvoření se nezdařilo.|

## <a name="remarks"></a>Poznámky

Třída CAnimationVariable zapouzdřuje objekt IUIAnimationVariable COM. Obsahuje také seznam přechodů, které mají být aplikovány na proměnnou animace ve scénáři. Objekty CAnimationVariable jsou vloženy do objektů animace, které mohou představovat v aplikaci animovanou hodnotu, bod, velikost, barvu a obdélník.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CAnimationVariable`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller. h

##  <a name="_dtorcanimationvariable"></a>CAnimationVariable:: ~ CAnimationVariable

Destruktor. Volána, když je zničen objekt CAnimationVariable.

```
virtual ~CAnimationVariable();
```

##  <a name="addtransition"></a>CAnimationVariable::AddTransition

Přidá přechod.

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parametry

*pTransition*<br/>
Ukazatel na přechod, který má být přidán.

### <a name="remarks"></a>Poznámky

Tato metoda je volána pro přidání přechodu do interního seznamu přechodů, které mají být aplikovány na proměnnou animace. Tento seznam by měl být po naplánování animace vymazán.

##  <a name="applytransitions"></a>CAnimationVariable::ApplyTransitions

Přidá přechody z interního seznamu do scénáře.

```
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Ukazatel na nadřazený kontroler animací.

*pStoryboard*<br/>
Ukazatel na scénář.

*bDependOnKeyframes*<br/>
TRUE, pokud by tato metoda měla přidat přechody závislé na klíčových snímcích.

### <a name="remarks"></a>Poznámky

Tato metoda přidá přechody z interního seznamu do scénáře. Je volána z kódu nejvyšší úrovně několikrát k přidání přechodů, které nejsou závislé na klíčových snímcích, a přidání přechodů, které jsou závislé na klíčových snímcích. Pokud se objekt COM proměnné animace nevytvořil, vytvoří tato metoda v této fázi.

##  <a name="canimationvariable"></a>CAnimationVariable::CAnimationVariable

Vytvoří objekt proměnné animace.

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Určuje výchozí hodnotu.

### <a name="remarks"></a>Poznámky

Vytvoří objekt proměnné animace a nastaví jeho výchozí hodnotu. Výchozí hodnota se použije, když proměnná není animovaná, nebo ji nejde animovat.

##  <a name="cleartransitions"></a>CAnimationVariable::ClearTransitions

Vymaže přechody.

```
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parametry

*bAutodestroy*<br/>
Určuje, zda tato metoda má odstranit objekty přechodu.

### <a name="remarks"></a>Poznámky

Tato metoda odebere všechny přechody z interního seznamu přechodů. Pokud má bAutodestroy hodnotu TRUE nebo má m_bAutodestroyTransitions hodnotu TRUE, přechody se odstraní. V opačném případě by volající měl zrušit přidělení objektů přechodu.

##  <a name="create"></a>CAnimationVariable:: Create

Vytvoří základní objekt proměnné animace objektu COM.

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>Parametry

*pManager*<br/>
Ukazatel na správce animací.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla proměnná animace úspěšně vytvořena; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří podkladovou proměnnou animace objektu COM a nastaví její výchozí hodnotu.

##  <a name="createtransitions"></a>CAnimationVariable::CreateTransitions

Vytvoří všechny přechody, které mají být aplikovány na tuto proměnnou animace.

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Ukazatel na [rozhraní IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), které definuje knihovnu standardních přechodů.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byly přechody úspěšně vytvořeny; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když je potřeba vytvořit přechody, které byly přidány do interního seznamu přechodů proměnné.

##  <a name="enableintegervaluechangedevent"></a>CAnimationVariable::EnableIntegerValueChangedEvent

Povolí nebo zakáže událost IntegerValueChanged.

```
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Ukazatel na nadřazený kontroler.

*bEnable*<br/>
TRUE – povolit událost, FALSE – zakázat událost.

### <a name="remarks"></a>Poznámky

Když je povolená událost ValueChanged, rozhraní volá virtuální metodu CAnimationController:: OnAnimationIntegerValueChanged. Je nutné jej přepsat ve třídě odvozené z CAnimationController, aby bylo možné tuto událost zpracovat. Tato metoda je volána pokaždé, když se změní celočíselná hodnota proměnné animace.

##  <a name="enablevaluechangedevent"></a>CAnimationVariable::EnableValueChangedEvent

Povolí nebo zakáže událost ValueChanged.

```
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Ukazatel na nadřazený kontroler.

*bEnable*<br/>
TRUE – povolit událost, FALSE – zakázat událost.

### <a name="remarks"></a>Poznámky

Když je povolená událost ValueChanged, rozhraní volá virtuální metodu CAnimationController:: OnAnimationValueChanged. Je nutné jej přepsat ve třídě odvozené z CAnimationController, aby bylo možné tuto událost zpracovat. Tato metoda je volána pokaždé, když se změní hodnota proměnné animace.

##  <a name="getdefaultvalue"></a>CAnimationVariable:: getdefaultvalue

Vrátí výchozí hodnotu.

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>Návratová hodnota

Výchozí hodnota.

### <a name="remarks"></a>Poznámky

Pomocí této funkce lze získat výchozí hodnotu proměnné animace. Výchozí hodnotu lze nastavit v konstruktoru nebo metodou SetDefaultValue.

##  <a name="getparentanimationobject"></a>CAnimationVariable::GetParentAnimationObject

Vrátí nadřazený objekt animace.

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nadřazený objekt animace, pokud byl vytvořen vztah, jinak NULL.

### <a name="remarks"></a>Poznámky

Tuto metodu lze volat, aby načetla ukazatel na nadřazený objekt animace (kontejner).

##  <a name="getvalue"></a>CAnimationVariable:: GetValue

Vrátí aktuální hodnotu proměnné animace.

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parametry

*dblValue*<br/>
Aktuální hodnota proměnné animace.

*nHodnota*<br/>
Aktuální hodnota proměnné animace.

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud byla hodnota získána úspěšně, nebo nebyla vytvořena základní proměnná animace. Jinak kód chyby HRESULT.

### <a name="remarks"></a>Poznámky

Tuto metodu lze volat pro načtení aktuální hodnoty proměnné animace. Pokud se podkladový objekt modelu COM nevytvořil, dblValue bude při návratu funkce obsahovat výchozí hodnotu.

##  <a name="getvariable"></a>CAnimationVariable:: getvariable

Vrátí ukazatel na objekt COM IUIAnimationVariable.

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na objekt COM IUIAnimationVariable nebo hodnotu NULL, pokud nebyla vytvořena proměnná animace nebo nemůže být vytvořena.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte pro přístup k základnímu objektu IUIAnimationVariable COM a volejte jeho metody přímo v případě potřeby.

##  <a name="m_bautodestroytransitions"></a>CAnimationVariable::m_bAutodestroyTransitions

Určuje, zda se mají odstranit související objekty přechodu.

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>Poznámky

Nastavte tuto hodnotu na TRUE, pokud chcete vynutit odstranění přesouvaných objektů při jejich odebírání z interního seznamu přechodů. Pokud je tato hodnota FALSE, přechody by měly být odstraněny voláním aplikace. Seznam přechodů je po naplánování animace vždy vymazán. Výchozí hodnota je FALSE (NEPRAVDA).

##  <a name="m_dbldefaultvalue"></a>CAnimationVariable::m_dblDefaultValue

Určuje výchozí hodnotu, která je šířena do IUIAnimationVariable.

```
DOUBLE m_dblDefaultValue;
```

##  <a name="m_lsttransitions"></a>CAnimationVariable::m_lstTransitions

Obsahuje seznam přechodů, které tuto proměnnou animace animuje.

```
CObList m_lstTransitions;
```

##  <a name="m_pparentobject"></a>  CAnimationVariable::m_pParentObject

Ukazatel na objekt animace, který zapouzdřuje tuto proměnnou animace.

```
CAnimationBaseObject* m_pParentObject;
```

##  <a name="m_variable"></a>CAnimationVariable::m_variable

Ukládá ukazatel na objekt COM IUIAnimationVariable. Hodnota NULL, pokud objekt COM ještě nebyl vytvořen, nebo pokud vytvoření se nezdařilo.

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

##  <a name="setdefaultvalue"></a>CAnimationVariable::SetDefaultValue

Nastaví výchozí hodnotu a uvolní objekt COM IUIAnimationVariable.

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Určuje novou výchozí hodnotu.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li obnovit výchozí hodnotu. Tato metoda uvolní interní objekt modelu COM IUIAnimationVariable, proto když je znovu vytvořena proměnná animace, získá příslušný objekt COM novou výchozí hodnotu. Výchozí hodnota je vrácena pomocí GetValue, pokud objekt COM představující proměnnou animace není vytvořen, nebo pokud proměnná nebyla animována.

##  <a name="setparentanimationobject"></a>CAnimationVariable::SetParentAnimationObject

Nastaví vztah mezi proměnnou animace a objektem animace.

```
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>Parametry

*pParentObject*<br/>
Ukazatel na objekt animace, který obsahuje tuto proměnnou.

### <a name="remarks"></a>Poznámky

Tato metoda je volána interně pro vytvoření vztahu 1:1 mezi proměnnou animace a objektem animace, který ho zapouzdřuje.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
