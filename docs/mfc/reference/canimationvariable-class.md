---
title: "Třída CAnimationVariable | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a90db931ca53687c42263df6a4112eb478059227
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="canimationvariable-class"></a>CAnimationVariable – třída
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
|[CAnimationVariable:: ~ CAnimationVariable](#canimationvariable__~canimationvariable)|Destruktor. Voláno, když je objekt CAnimationVariable zničen.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationVariable::AddTransition](#addtransition)|Přidá přechod.|  
|[CAnimationVariable::ApplyTransitions](#applytransitions)|Přidá přechody ze seznamu interní do scénáře.|  
|[CAnimationVariable::ClearTransitions](#cleartransitions)|Vymaže přechody.|  
|[CAnimationVariable::Create](#create)|Vytvoří základní objekt COM proměnné animace.|  
|[CAnimationVariable::CreateTransitions](#createtransitions)|Vytvoří všechny přechody má být použita pro tuto proměnnou animace.|  
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Povolí nebo zakáže IntegerValueChanged události.|  
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|Povolí nebo zakáže událost ValueChanged.|  
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnotu.|  
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|Vrací nadřazeného objektu animace.|  
|[CAnimationVariable::GetValue](#getvalue)|Přetíženo. Vrací aktuální hodnotu proměnné animace.|  
|[CAnimationVariable::GetVariable](#getvariable)|Vrátí objekt IUIAnimationVariable COM ukazatel.|  
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu a uvolní objekt IUIAnimationVariable COM.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|Nastaví vztah mezi proměnná animace a objekt animace.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Určuje, zda mají být odstraněny přechod související objekty.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|Určuje výchozí hodnotu, která je rozšířena do IUIAnimationVariable.|  
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|Obsahuje seznam přechody, které tato proměnná animace animace.|  
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|Ukazatel na animace objekt, který zapouzdří Tato proměnná animace.|  
|[CAnimationVariable::m_variable](#m_variable)|Ukládá ukazatel na objekt IUIAnimationVariable COM. Hodnota NULL, pokud ještě nebyl vytvořen objekt COM nebo pokud vytvoření se nezdařilo.|  
  
## <a name="remarks"></a>Poznámky  
 CAnimationVariable třída zapouzdří objekt IUIAnimationVariable COM. Obsahuje také seznam přechody, která má být použita pro proměnnou animace v scénáře. Animace objektů, které můžete v aplikaci animovaný hodnotu, bod, velikost, barvu a obdélníku představují jsou vloženy CAnimationVariable objekty.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CAnimationVariable`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationvariable"></a>CAnimationVariable:: ~ CAnimationVariable  
 Destruktor. Voláno, když je objekt CAnimationVariable zničen.  
  
```  
virtual ~CAnimationVariable();
```  
  
##  <a name="addtransition"></a>CAnimationVariable::AddTransition  
 Přidá přechod.  
  
```  
void AddTransition(CBaseTransition* pTransition);
```  
  
### <a name="parameters"></a>Parametry  
 `pTransition`  
 Ukazatel na přechod k přidání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána pro přidání přechod do interní seznam přechody, která má být použita pro proměnnou animace. Tento seznam vymazání, jakmile bylo naplánováno animace.  
  
##  <a name="applytransitions"></a>CAnimationVariable::ApplyTransitions  
 Přidá přechody ze seznamu interní do scénáře.  
  
```  
void ApplyTransitions(
    CAnimationController* pController,  
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>Parametry  
 `pController`  
 Ukazatel na rodičovský ovladač animace.  
  
 `pStoryboard`  
 Ukazatel do scénáře.  
  
 `bDependOnKeyframes`  
 Hodnota TRUE, pokud tato metoda by měla přidat přechody, které jsou závislé na klíčových snímků.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá přechody ze seznamu interní do scénáře. Volání z kódu nejvyšší úrovně několikrát k přidání přechody, které nemají závisí na klíčových snímků a přidat přechody, které jsou závislé na klíčových snímků. Pokud nebyla vytvořena základní animace proměnné objektu COM, tato metoda se vytvoří v této fázi.  
  
##  <a name="canimationvariable"></a>CAnimationVariable::CAnimationVariable  
 Vytvoří objekt proměnné animace.  
  
```  
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```  
  
### <a name="parameters"></a>Parametry  
 `dblDefaultValue`  
 Určuje výchozí hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří objekt animace proměnnou a nastaví výchozí hodnota. Výchozí hodnota se používá při proměnné není animovaný nebo nelze animovaný.  
  
##  <a name="cleartransitions"></a>CAnimationVariable::ClearTransitions  
 Vymaže přechody.  
  
```  
void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>Parametry  
 `bAutodestroy`  
 Určuje, zda tato metoda by měla odstranit objekty přechodu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odebere všechny přechody ze seznamu interní přechodů. Pokud má hodnotu TRUE, bAutodestroy nebo m_bAutodestroyTransitions má hodnotu TRUE, jsou odstraněny přechody. Volající by jinak navrácení objekty přechodu.  
  
##  <a name="create"></a>CAnimationVariable::Create  
 Vytvoří základní objekt COM proměnné animace.  
  
```  
virtual BOOL Create(IUIAnimationManager* pManager);
```  
  
### <a name="parameters"></a>Parametry  
 `pManager`  
 Ukazatel na manager animace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud byla úspěšně vytvořena proměnná animace; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří základní proměnnou animace objektu COM a nastaví výchozí hodnota.  
  
##  <a name="createtransitions"></a>CAnimationVariable::CreateTransitions  
 Vytvoří všechny přechody má být použita pro tuto proměnnou animace.  
  
```  
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parametry  
`pLibrary`  
 Ukazatel na [IUIAnimationTransitionLibrary rozhraní](https://msdn.microsoft.com/library/windows/desktop/dd371897), která definuje knihovnu standardní přechodů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud přechody byly vytvořeny úspěšně; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rozhraním framework, když potřebuje k vytvoření přechody, které byly přidány do seznamu interní proměnné přechodů.  
  
##  <a name="enableintegervaluechangedevent"></a>CAnimationVariable::EnableIntegerValueChangedEvent  
 Povolí nebo zakáže IntegerValueChanged události.  
  
```  
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `pController`  
 Ukazatel na rodičovský ovladač.  
  
 `bEnable`  
 TRUE – povolit událostí, FALSE, zakažte událostí.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je povoleno událost ValueChanged, volá framework virtuální metoda CAnimationController::OnAnimationIntegerValueChanged. Je nutné přepsat v třídy odvozené od CAnimationController, aby bylo možné zpracovat tuto událost. Tato metoda je volána pokaždé, když se změní celočíselná hodnota proměnné animace.  
  
##  <a name="enablevaluechangedevent"></a>CAnimationVariable::EnableValueChangedEvent  
 Povolí nebo zakáže událost ValueChanged.  
  
```  
void EnableValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `pController`  
 Ukazatel na rodičovský ovladač.  
  
 `bEnable`  
 TRUE – povolit událostí, FALSE, zakažte událostí.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je povoleno událost ValueChanged, volá framework virtuální metoda CAnimationController::OnAnimationValueChanged. Je nutné přepsat v třídy odvozené od CAnimationController, aby bylo možné zpracovat tuto událost. Tato metoda je volána pokaždé, když se změní hodnota proměnné animace.  
  
##  <a name="getdefaultvalue"></a>CAnimationVariable::GetDefaultValue  
 Vrátí výchozí hodnotu.  
  
```  
DOUBLE GetDefaultValue() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete získat výchozí hodnota proměnné animace. Výchozí hodnota lze nastavit v konstruktoru nebo SetDefaultValue metodou.  
  
##  <a name="getparentanimationobject"></a>CAnimationVariable::GetParentAnimationObject  
 Vrací nadřazeného objektu animace.  
  
```  
CAnimationBaseObject* GetParentAnimationObject();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nadřazený objekt animace, pokud bylo vytvořeno relace, jinak hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze volat pro získání ukazatele na nadřazený objekt animace (kontejner).  
  
##  <a name="getvalue"></a>CAnimationVariable::GetValue  
 Vrací aktuální hodnotu proměnné animace.  
  
```  
HRESULT GetValue(DOUBLE& dblValue);  
HRESULT GetValue(INT32& nValue);
```  
  
### <a name="parameters"></a>Parametry  
 `dblValue`  
 Aktuální hodnota proměnné animace.  
  
 `nValue`  
 Aktuální hodnota proměnné animace.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud byla úspěšně získána hodnota nebo proměnná základní animace nebyl vytvořen. Jinak hodnota HRESULT kódu chyby.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze volat pro načtení aktuální hodnotu proměnné animace. Pokud nebyla vytvořena základní objekt COM, dblValue bude obsahovat výchozí hodnotu, pokud funkce vrátí hodnotu.  
  
##  <a name="getvariable"></a>CAnimationVariable::GetVariable  
 Vrátí objekt IUIAnimationVariable COM ukazatel.  
  
```  
IUIAnimationVariable* GetVariable();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Neplatný ukazatel na objektu IUIAnimationVariable COM nebo hodnota NULL, pokud nebyla vytvořena proměnná animace, nebo nelze vytvořit.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci použijte pro přístup k základní objekt IUIAnimationVariable COM a její metody volat přímo v případě potřeby.  
  
##  <a name="m_bautodestroytransitions"></a>CAnimationVariable::m_bAutodestroyTransitions  
 Určuje, zda mají být odstraněny přechod související objekty.  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud se se odeberou ze seznamu interní přechody, nastavte hodnotu na hodnotu PRAVDA, aby Vynutit odstranění objektů přechod. Pokud tato hodnota je FALSE je potřeba odstranit přechodů voláním aplikace. Seznam přechody je vždy vymazán poté, co bylo naplánováno animace. Výchozí hodnota je FALSE.  
  
##  <a name="m_dbldefaultvalue"></a>CAnimationVariable::m_dblDefaultValue  
 Určuje výchozí hodnotu, která je rozšířena do IUIAnimationVariable.  
  
```  
DOUBLE m_dblDefaultValue;  
```  
  
##  <a name="m_lsttransitions"></a>CAnimationVariable::m_lstTransitions  
 Obsahuje seznam přechody, které tato proměnná animace animace.  
  
```  
CObList m_lstTransitions;  
```  
  
##  <a name="m_pparentobject"></a>CAnimationVariable::m_pParentObject  
 Ukazatel na animace objekt, který zapouzdří Tato proměnná animace.  
  
```  
CAnimationBaseObject* m_pParentObject;  
```  
  
##  <a name="m_variable"></a>CAnimationVariable::m_variable  
 Ukládá ukazatel na objekt IUIAnimationVariable COM. Hodnota NULL, pokud ještě nebyl vytvořen objekt COM nebo pokud vytvoření se nezdařilo.  
  
```  
ATL::CComPtr<IUIAnimationVariable> m_variable;  
```  
  
##  <a name="setdefaultvalue"></a>CAnimationVariable::SetDefaultValue  
 Nastaví výchozí hodnotu a uvolní objekt IUIAnimationVariable COM.  
  
```  
void SetDefaultValue(DOUBLE dblDefaultValue);
```  
  
### <a name="parameters"></a>Parametry  
 `dblDefaultValue`  
 Určuje nová výchozí hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li obnovit výchozí hodnota. Tato metoda uvolní vnitřní objekt IUIAnimationVariable COM, proto když se znovu vytvoří animace proměnné, základní objekt COM získá nový výchozí hodnotu. Výchozí hodnota je vrácený GetValue, pokud objekt COM představující proměnnou animace není vytvořen, nebo pokud nebyla byla animovaný proměnnou.  
  
##  <a name="setparentanimationobject"></a>CAnimationVariable::SetParentAnimationObject  
 Nastaví vztah mezi proměnná animace a objekt animace.  
  
```  
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentObject`  
 Ukazatel na animace objekt, který obsahuje tuto proměnnou.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána interně k vytvoření relace mezi proměnná animace a animace objekt, který zapouzdří ho.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
