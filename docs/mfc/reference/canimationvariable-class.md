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
ms.openlocfilehash: 51cc4732ee8ad5f954e5bd758484cec74cf00fe6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377054"
---
# <a name="canimationvariable-class"></a>CAnimationVariable – třída

Představuje proměnnou animace.

## <a name="syntax"></a>Syntaxe

```
class CAnimationVariable;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationVariable::Proměnná CAnimation](#canimationvariable)|Vytvoří objekt proměnné animace.|
|[CAnimationVariable::~CAnimationVariable](#_dtorcanimationvariable)|Destruktor. Volána při zničení objektu CAnimationVariable.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationVariable::AddTransition](#addtransition)|Přidá přechod.|
|[CAnimationVariable::ApplyTransitions](#applytransitions)|Přidá přechody z vnitřního seznamu do scénáře.|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|Vymaže přechody.|
|[CAnimationVariable::Vytvořit](#create)|Vytvoří základní objekt COM proměnné animace.|
|[CAnimationVariable::CreateTransitions](#createtransitions)|Vytvoří všechny přechody, které mají být použity pro tuto proměnnou animace.|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Povolí nebo zakáže událost IntegerValueChanged.|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|Povolí nebo zakáže událost ValueChanged.|
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnotu.|
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|Vrátí nadřazený objekt animace.|
|[CAnimationVariable::Hodnota GetValue](#getvalue)|Přetíženo. Vrátí aktuální hodnotu proměnné animace.|
|[CAnimationVariable::GetVariable](#getvariable)|Vrátí ukazatel na objekt COM IUIAnimationVariable.|
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu a uvolní objekt COM IUIAnimationVariable.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|Nastaví vztah mezi proměnnou animace a objektem animace.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[Proměnná CAnimation::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Určuje, zda mají být odstraněny související objekty přechodu.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[Proměnná CAnimation::m_dblDefaultValue](#m_dbldefaultvalue)|Určuje výchozí hodnotu, která je šířena na proměnnou IUIAnimationVariable.|
|[Proměnná CAnimation::m_lstTransitions](#m_lsttransitions)|Obsahuje seznam přechodů, které animují tuto proměnnou animace.|
|[Proměnná canimation::m_pParentObject](#m_pparentobject)|Ukazatel na objekt animace, který zapouzdřuje tuto proměnnou animace.|
|[Proměnná canimation::m_variable](#m_variable)|Ukládá ukazatel na objekt COM IUIAnimationVariable. Null, pokud objekt COM ještě nebyl vytvořen nebo pokud se vytvoření nezdařilo.|

## <a name="remarks"></a>Poznámky

Třída CAnimationVariable zapouzdřuje objekt COM IUIAnimationVariable. Obsahuje také seznam přechodů, které mají být použity na proměnnou animace ve scénáři. CAnimationVariable objekty jsou vloženy do animační objekty, které mohou představovat v aplikaci animovanou hodnotu, bod, velikost, barvu a obdélník.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CAnimationVariable`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationvariablecanimationvariable"></a><a name="_dtorcanimationvariable"></a>CAnimationVariable::~CAnimationVariable

Destruktor. Volána při zničení objektu CAnimationVariable.

```
virtual ~CAnimationVariable();
```

## <a name="canimationvariableaddtransition"></a><a name="addtransition"></a>CAnimationVariable::AddTransition

Přidá přechod.

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parametry

*pPřechod*<br/>
Ukazatel na přechod, který chcete přidat.

### <a name="remarks"></a>Poznámky

Tato metoda je volána přidat přechod do vnitřního seznamu přechodů, které mají být použity na proměnnou animace. Tento seznam by měl být vymazán, pokud byla naplánována animace.

## <a name="canimationvariableapplytransitions"></a><a name="applytransitions"></a>CAnimationVariable::ApplyTransitions

Přidá přechody z vnitřního seznamu do scénáře.

```
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pKontrolér*<br/>
Ukazatel na nadřazený ovladač animace.

*pStoryboard*<br/>
Ukazatel na scénář.

*bDependOnKeyframes*<br/>
PRAVDA, pokud tato metoda by měla přidat přechody, které závisí na klíčových snímků.

### <a name="remarks"></a>Poznámky

Tato metoda přidá přechody z vnitřního seznamu do scénáře. Je volána z kódu nejvyšší úrovně několikrát přidat přechody, které nejsou závislé na klíčových snímků a přidat přechody, které závisí na klíčových snímků. Pokud základní proměnná animace COM objekt nebyl vytvořen, tato metoda ji vytvoří v této fázi.

## <a name="canimationvariablecanimationvariable"></a><a name="canimationvariable"></a>CAnimationVariable::Proměnná CAnimation

Vytvoří objekt proměnné animace.

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Určuje výchozí hodnotu.

### <a name="remarks"></a>Poznámky

Vytvoří objekt proměnné animace a nastaví jeho výchozí hodnotu. Výchozí hodnota se používá, když proměnná není animovaná nebo animovaná.

## <a name="canimationvariablecleartransitions"></a><a name="cleartransitions"></a>CAnimationVariable::ClearTransitions

Vymaže přechody.

```
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parametry

*bAutodestroy*<br/>
Určuje, zda má tato metoda odstranit přechodové objekty.

### <a name="remarks"></a>Poznámky

Tato metoda odebere všechny přechody z vnitřního seznamu přechodů. Pokud bAutodestroy je PRAVDA nebo m_bAutodestroyTransitions je PRAVDA, pak přechody jsou odstraněny. V opačném případě by volající měl navrátit objekty přechodu.

## <a name="canimationvariablecreate"></a><a name="create"></a>CAnimationVariable::Vytvořit

Vytvoří základní objekt COM proměnné animace.

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>Parametry

*pManažer*<br/>
Ukazatel na správce animací.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla proměnná animace úspěšně vytvořena; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří základní objekt COM proměnné animace a nastaví výchozí hodnotu.

## <a name="canimationvariablecreatetransitions"></a><a name="createtransitions"></a>CAnimationVariable::CreateTransitions

Vytvoří všechny přechody, které mají být použity pro tuto proměnnou animace.

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pKnihovna*<br/>
Ukazatel na [rozhraní IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), které definuje knihovnu standardních přechodů.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byly přechody úspěšně vytvořeny; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda je volána v rámci, když potřebuje vytvořit přechody, které byly přidány do vnitřního seznamu přechodů proměnné.

## <a name="canimationvariableenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>CAnimationVariable::EnableIntegerValueChangedEvent

Povolí nebo zakáže událost IntegerValueChanged.

```
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pKontrolér*<br/>
Ukazatel na nadřazený řadič.

*bEnable*<br/>
TRUE - povolit událost, FALSE - zakázat událost.

### <a name="remarks"></a>Poznámky

Pokud je povolena událost ValueChanged, framework volá virtuální metodu CAnimationController::OnAnimationIntegerValueChanged. Je třeba přepsat ve třídě odvozené z CAnimationController za účelem zpracování této události. Tato metoda je volána při každé změně celé hodnoty proměnné animace.

## <a name="canimationvariableenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>CAnimationVariable::EnableValueChangedEvent

Povolí nebo zakáže událost ValueChanged.

```
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pKontrolér*<br/>
Ukazatel na nadřazený řadič.

*bEnable*<br/>
TRUE - povolit událost, FALSE - zakázat událost.

### <a name="remarks"></a>Poznámky

Pokud je povolena událost ValueChanged, framework volá virtuální metodu CAnimationController::OnAnimationValueChanged. Je třeba přepsat ve třídě odvozené z CAnimationController za účelem zpracování této události. Tato metoda je volána při každé změně hodnoty proměnné animace.

## <a name="canimationvariablegetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationVariable::GetDefaultValue

Vrátí výchozí hodnotu.

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>Návratová hodnota

Výchozí hodnota.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k získání výchozí hodnoty proměnné animace. Výchozí hodnotu lze nastavit v konstruktoru nebo metodou SetDefaultValue.

## <a name="canimationvariablegetparentanimationobject"></a><a name="getparentanimationobject"></a>CAnimationVariable::GetParentAnimationObject

Vrátí nadřazený objekt animace.

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nadřazený objekt animace, pokud byl vytvořen vztah, jinak NULL.

### <a name="remarks"></a>Poznámky

Tato metoda může být volána k načtení ukazatele na nadřazený objekt animace (kontejner).

## <a name="canimationvariablegetvalue"></a><a name="getvalue"></a>CAnimationVariable::Hodnota GetValue

Vrátí aktuální hodnotu proměnné animace.

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parametry

*hodnota dblValue*<br/>
Aktuální hodnota proměnné animace.

*nHodnota*<br/>
Aktuální hodnota proměnné animace.

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud byla hodnota získána úspěšně nebo základní animační proměnná nebyla vytvořena. V opačném případě hresult kód chyby.

### <a name="remarks"></a>Poznámky

Tato metoda může být volána k načtení aktuální hodnoty proměnné animace. Pokud základní objekt COM nebyl vytvořen, dblValue bude obsahovat výchozí hodnotu, když funkce vrátí.

## <a name="canimationvariablegetvariable"></a><a name="getvariable"></a>CAnimationVariable::GetVariable

Vrátí ukazatel na objekt COM IUIAnimationVariable.

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na objekt COM IUIAnimationVariable nebo NULL, pokud proměnná animace nebyla vytvořena nebo ji nelze vytvořit.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte pro přístup k podkladovému objektu Com IUIAnimationVariable a v případě potřeby přímo zavolejte jeho metody.

## <a name="canimationvariablem_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>Proměnná CAnimation::m_bAutodestroyTransitions

Určuje, zda mají být odstraněny související objekty přechodu.

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>Poznámky

Nastavte tuto hodnotu na HODNOTU TRUE, aby bylo vynuceno odstranění přechodových objektů při jejich odebírání z vnitřního seznamu přechodů. Pokud je tato hodnota FALSE, přechody by měly být odstraněny voláním aplikace. Seznam přechodů je vždy vymazána po animace byla naplánována. Výchozí hodnota je FALSE.

## <a name="canimationvariablem_dbldefaultvalue"></a><a name="m_dbldefaultvalue"></a>Proměnná CAnimation::m_dblDefaultValue

Určuje výchozí hodnotu, která je šířena na proměnnou IUIAnimationVariable.

```
DOUBLE m_dblDefaultValue;
```

## <a name="canimationvariablem_lsttransitions"></a><a name="m_lsttransitions"></a>Proměnná CAnimation::m_lstTransitions

Obsahuje seznam přechodů, které animují tuto proměnnou animace.

```
CObList m_lstTransitions;
```

## <a name="canimationvariablem_pparentobject"></a><a name="m_pparentobject"></a>Proměnná canimation::m_pParentObject

Ukazatel na objekt animace, který zapouzdřuje tuto proměnnou animace.

```
CAnimationBaseObject* m_pParentObject;
```

## <a name="canimationvariablem_variable"></a><a name="m_variable"></a>Proměnná canimation::m_variable

Ukládá ukazatel na objekt COM IUIAnimationVariable. Null, pokud objekt COM ještě nebyl vytvořen nebo pokud se vytvoření nezdařilo.

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

## <a name="canimationvariablesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationVariable::SetDefaultValue

Nastaví výchozí hodnotu a uvolní objekt COM IUIAnimationVariable.

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Určuje novou výchozí hodnotu.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k obnovení výchozí hodnoty. Tato metoda uvolní vnitřní Objekt COM IUIAnimationVariable, proto při znovu vytvoření proměnné animace získá základní objekt COM novou výchozí hodnotu. Výchozí hodnota je vrácena GetValue, pokud není vytvořen objekt COM představující proměnnou animace nebo pokud proměnná nebyla animována.

## <a name="canimationvariablesetparentanimationobject"></a><a name="setparentanimationobject"></a>CAnimationVariable::SetParentAnimationObject

Nastaví vztah mezi proměnnou animace a objektem animace.

```
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>Parametry

*pParentObject*<br/>
Ukazatel na objekt animace, který obsahuje tuto proměnnou.

### <a name="remarks"></a>Poznámky

Tato metoda se nazývá interně vytvořit vztah 1:1 mezi proměnnou animace a objekt animace, který zapouzdřuje ji.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
