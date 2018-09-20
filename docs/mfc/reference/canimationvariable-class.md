---
title: Canimationvariable – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fdf35381efb5f6d017b3238f4630929fb1d9ebbe
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447853"
---
# <a name="canimationvariable-class"></a>Canimationvariable – třída

Představuje proměnnou animace.

## <a name="syntax"></a>Syntaxe

```
class CAnimationVariable;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|Vytvoří objekt proměnné animace.|
|[Canimationvariable –:: ~ canimationvariable –](#canimationvariable__~canimationvariable)|Destruktor. Volá se, když se likviduje canimationvariable – objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationVariable::AddTransition](#addtransition)|Přidá přechod.|
|[CAnimationVariable::ApplyTransitions](#applytransitions)|Přidá přechody ze seznamu interní do scénáře.|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|Vymaže přechodů.|
|[CAnimationVariable::Create](#create)|Vytvoří základní objekt modelu COM proměnné animace.|
|[CAnimationVariable::CreateTransitions](#createtransitions)|Vytvoří všechny přechody u této proměnné animace.|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Povolí nebo zakáže IntegerValueChanged událostí.|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|Povolí nebo zakáže ValueChanged události.|
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnotu.|
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|Vrátí nadřazený objekt animace.|
|[CAnimationVariable::GetValue](#getvalue)|Přetíženo. Vrátí aktuální hodnotu proměnné animace.|
|[CAnimationVariable::GetVariable](#getvariable)|Vrací ukazatel na objekt modelu COM IUIAnimationVariable.|
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnoty a uvolní objekt modelu COM IUIAnimationVariable.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|Nastaví vztah mezi proměnnou animace a objekt animace.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Určuje, zda mají být odstraněny přechod související objekty.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|Určuje výchozí hodnotu, která se šíří do IUIAnimationVariable.|
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|Obsahuje seznam přechody, která animovat tuto proměnnou animace.|
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|Ukazatel na objekt animace, který zapouzdřuje této proměnné animace.|
|[CAnimationVariable::m_variable](#m_variable)|Uchovává ukazatel na objekt modelu COM IUIAnimationVariable. Pokud ještě nebyl vytvořen objekt modelu COM, nebo pokud se nepovedlo s hodnotou NULL.|

## <a name="remarks"></a>Poznámky

Canimationvariable – třída zapouzdří objekt modelu COM IUIAnimationVariable. Obsahuje také seznam přechody má použít u proměnné animace ve scénáři. Canimationvariable – objekty jsou vloženy do animace objekty, které mohou reprezentovat v aplikaci hodnotou animované, bod, velikost, barvu a obdélník.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CAnimationVariable`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="_dtorcanimationvariable"></a>  Canimationvariable –:: ~ canimationvariable –

Destruktor. Volá se, když se likviduje canimationvariable – objektu.

```
virtual ~CAnimationVariable();
```

##  <a name="addtransition"></a>  CAnimationVariable::AddTransition

Přidá přechod.

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parametry

*pTransition*<br/>
Ukazatel na přechod na Přidat.

### <a name="remarks"></a>Poznámky

Tato metoda je volána přidáte přechod na vnitřní seznam přechody má použít u proměnné animace. Tento seznam by měla zůstat nezaškrtnutá, když je naplánovaná animace.

##  <a name="applytransitions"></a>  CAnimationVariable::ApplyTransitions

Přidá přechody ze seznamu interní do scénáře.

```
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Ukazatel na rodičovský ovladač animace.

*pStoryboard*<br/>
Ukazatel na scénáře.

*bDependOnKeyframes*<br/>
Hodnota TRUE, pokud tato metoda by měla přidat přechody, které jsou závislé na klíčové snímky.

### <a name="remarks"></a>Poznámky

Tato metoda přidá přechody ze seznamu interní do scénáře. Je volána z kódu nejvyšší úrovně několikrát přidat přechodů, které nemají závisí na klíčové snímky a přidání přechodů, které jsou závislé na klíčové snímky. Pokud nebyla vytvořena základní proměnné animace objektu COM, tato metoda se vytvoří v této fázi.

##  <a name="canimationvariable"></a>  CAnimationVariable::CAnimationVariable

Vytvoří objekt proměnné animace.

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Určuje výchozí hodnotu.

### <a name="remarks"></a>Poznámky

Vytvoří objekt proměnné animace a nastaví výchozí hodnotu. Pokud proměnná není animovat, nebo nelze animovat, použije se výchozí hodnota.

##  <a name="cleartransitions"></a>  CAnimationVariable::ClearTransitions

Vymaže přechodů.

```
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parametry

*bAutodestroy*<br/>
Určuje, zda tato metoda by měla odstranit objekty přechodu.

### <a name="remarks"></a>Poznámky

Tato metoda odebere všechny přechody ze seznamu vnitřních přechodů. Pokud bAutodestroy má hodnotu TRUE nebo m_bAutodestroyTransitions má hodnotu TRUE, jsou odstraněny přechodů. V opačném případě volající by měl uvolnit objekty přechodu.

##  <a name="create"></a>  CAnimationVariable::Create

Vytvoří základní objekt modelu COM proměnné animace.

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>Parametry

*pManager*<br/>
Ukazatel na správce animace.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byl úspěšně vytvořen proměnné animace; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří základní proměnnou animace objekt modelu COM a nastaví výchozí hodnotu.

##  <a name="createtransitions"></a>  CAnimationVariable::CreateTransitions

Vytvoří všechny přechody u této proměnné animace.

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Ukazatel na [IUIAnimationTransitionLibrary rozhraní](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), která definuje knihovnu standardní přechodů.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud úspěšně; vytvořily přechody v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když je nutné vytvořit přechody, které byly přidány do seznamu interní proměnné přechodů.

##  <a name="enableintegervaluechangedevent"></a>  CAnimationVariable::EnableIntegerValueChangedEvent

Povolí nebo zakáže IntegerValueChanged událostí.

```
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Ukazatel na rodičovský ovladač.

*bEnable*<br/>
TRUE – povolit událostí, FALSE, zakažte události.

### <a name="remarks"></a>Poznámky

Když je povolené ValueChanged události, volá framework virtuální metoda CAnimationController::OnAnimationIntegerValueChanged. Je nutné přepsat ve třídě odvozené z canimationcontroller – aby bylo možné zpracování této události. Tato metoda je volána pokaždé, když se změní celočíselnou hodnotu proměnné animace.

##  <a name="enablevaluechangedevent"></a>  CAnimationVariable::EnableValueChangedEvent

Povolí nebo zakáže ValueChanged události.

```
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Ukazatel na rodičovský ovladač.

*bEnable*<br/>
TRUE – povolit událostí, FALSE, zakažte události.

### <a name="remarks"></a>Poznámky

Když je povolené ValueChanged události, volá framework virtuální metoda CAnimationController::OnAnimationValueChanged. Je nutné přepsat ve třídě odvozené z canimationcontroller – aby bylo možné zpracování této události. Tato metoda je volána pokaždé, když se změní hodnota proměnné animace.

##  <a name="getdefaultvalue"></a>  CAnimationVariable::GetDefaultValue

Vrátí výchozí hodnotu.

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>Návratová hodnota

Výchozí hodnota.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k získání výchozí hodnotu proměnné animace. V konstruktoru nebo metodou SetDefaultValue můžete nastavit výchozí hodnotu.

##  <a name="getparentanimationobject"></a>  CAnimationVariable::GetParentAnimationObject

Vrátí nadřazený objekt animace.

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nadřazený objekt animace, pokud se vytvořila relace, jinak hodnota NULL.

### <a name="remarks"></a>Poznámky

Tuto metodu lze volat pro načtení ukazatel na nadřazený objekt animace (kontejner).

##  <a name="getvalue"></a>  CAnimationVariable::GetValue

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

S_OK, pokud byl úspěšně získán hodnotu nebo nebyla vytvořena základní proměnné animace. Jinak kód chyby HRESULT.

### <a name="remarks"></a>Poznámky

Tuto metodu lze volat pro načtení aktuální hodnota proměnné animace. Pokud nebyl vytvořen na základní objekt modelu COM, dblValue bude obsahovat výchozí hodnotu, pokud funkce vrátí.

##  <a name="getvariable"></a>  CAnimationVariable::GetVariable

Vrací ukazatel na objekt modelu COM IUIAnimationVariable.

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na objekt modelu COM IUIAnimationVariable nebo hodnota NULL, pokud nebyl vytvořen proměnné animace, nebo nelze vytvořit.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte pro přístup k základní objekt modelu COM IUIAnimationVariable a volat jeho metody přímo v případě potřeby.

##  <a name="m_bautodestroytransitions"></a>  CAnimationVariable::m_bAutodestroyTransitions

Určuje, zda mají být odstraněny přechod související objekty.

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>Poznámky

Když budou odebrány z interní seznam přechody, nastavte tuto hodnotu na true Vynutit odstranění objektů přechodu. Pokud je tato hodnota FALSE, neodstraní se pomocí volání aplikace přechodů. Seznam přechody je vždy vymazána po animaci je naplánovaná. Výchozí hodnota je FALSE.

##  <a name="m_dbldefaultvalue"></a>  CAnimationVariable::m_dblDefaultValue

Určuje výchozí hodnotu, která se šíří do IUIAnimationVariable.

```
DOUBLE m_dblDefaultValue;
```

##  <a name="m_lsttransitions"></a>  CAnimationVariable::m_lstTransitions

Obsahuje seznam přechody, která animovat tuto proměnnou animace.

```
CObList m_lstTransitions;
```

##  <a name="m_pparentobject"></a>  CAnimationVariable::m_pParentObject

Ukazatel na objekt animace, který zapouzdřuje této proměnné animace.

```
CAnimationBaseObject* m_pParentObject;
```

##  <a name="m_variable"></a>  CAnimationVariable::m_variable

Uchovává ukazatel na objekt modelu COM IUIAnimationVariable. Pokud ještě nebyl vytvořen objekt modelu COM, nebo pokud se nepovedlo s hodnotou NULL.

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

##  <a name="setdefaultvalue"></a>  CAnimationVariable::SetDefaultValue

Nastaví výchozí hodnoty a uvolní objekt modelu COM IUIAnimationVariable.

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Určuje nová výchozí hodnota.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li obnovit výchozí hodnotu. Tato metoda uvolní vnitřní objekt IUIAnimationVariable COM, proto když se znovu vytvoří proměnné animace, základní objekt modelu COM získá nový výchozí hodnotu. Výchozí hodnota je vrácený GetValue, pokud nevytvoříte objekt COM, který představuje proměnnou animace, nebo pokud proměnnou nebyl animovat.

##  <a name="setparentanimationobject"></a>  CAnimationVariable::SetParentAnimationObject

Nastaví vztah mezi proměnnou animace a objekt animace.

```
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>Parametry

*pParentObject*<br/>
Ukazatel na objekt animace, která obsahuje tuto proměnnou.

### <a name="remarks"></a>Poznámky

Tato metoda je volána interně k navázání relace 1: 1 mezi proměnnou animace a animace objektu, který zapouzdřuje ho.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
