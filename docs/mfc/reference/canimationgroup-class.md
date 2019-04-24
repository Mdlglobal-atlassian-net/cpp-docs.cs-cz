---
title: Canimationgroup – třída
ms.date: 03/27/2019
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
helpviewer_keywords:
- CAnimationGroup [MFC], CAnimationGroup
- CAnimationGroup [MFC], Animate
- CAnimationGroup [MFC], ApplyTransitions
- CAnimationGroup [MFC], FindAnimationObject
- CAnimationGroup [MFC], GetGroupID
- CAnimationGroup [MFC], RemoveKeyframes
- CAnimationGroup [MFC], RemoveTransitions
- CAnimationGroup [MFC], Schedule
- CAnimationGroup [MFC], SetAutodestroyTransitions
- CAnimationGroup [MFC], AddKeyframes
- CAnimationGroup [MFC], AddTransitions
- CAnimationGroup [MFC], CreateTransitions
- CAnimationGroup [MFC], m_bAutoclearTransitions
- CAnimationGroup [MFC], m_bAutodestroyAnimationObjects
- CAnimationGroup [MFC], m_bAutodestroyKeyframes
- CAnimationGroup [MFC], m_lstAnimationObjects
- CAnimationGroup [MFC], m_lstKeyFrames
- CAnimationGroup [MFC], m_pStoryboard
- CAnimationGroup [MFC], m_nGroupID
- CAnimationGroup [MFC], m_pParentController
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
ms.openlocfilehash: 32b2adfee2a36139a11caa12fa98bd240b0732dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152070"
---
# <a name="canimationgroup-class"></a>Canimationgroup – třída

Implementuje skupinu animace, která kombinuje scénáře animace, objekty animace a přechody definují animace.

## <a name="syntax"></a>Syntaxe

```
class CAnimationGroup;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|Vytvoří skupinu animace.|
|[CAnimationGroup::~CAnimationGroup](#_dtorcanimationgroup)|Destruktor. Volá se, když se likviduje skupinu animace.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationGroup::Animate](#animate)|Animuje skupinu.|
|[CAnimationGroup::ApplyTransitions](#applytransitions)|Přechody se vztahuje na objekty animace.|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Vyhledá objekt animace, který obsahuje proměnné zadané animace.|
|[CAnimationGroup::GetGroupID](#getgroupid)|Vrátí ID skupiny.|
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|Odebere a volitelně odstraní všechny klíčové snímky, které patří do skupiny animace.|
|[CAnimationGroup::RemoveTransitions](#removetransitions)|Odebere přechody z animace objektů, které patří do skupiny animace.|
|[CAnimationGroup::Schedule](#schedule)|Naplánuje animace v zadanou dobu.|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Dostává instrukci, že všechny objekty animace, které patří do skupiny automaticky zničit přechodů.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Pomocné rutiny, která přidá klíčové snímky na scénáře.|
|[CAnimationGroup::AddTransitions](#addtransitions)|Pomocné rutiny, která přidává přechody do scénáře.|
|[CAnimationGroup::CreateTransitions](#createtransitions)|Pomocné rutiny, která vytváří objekty modelu COM přechodu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Určuje, jak vymazat přechody ze animace objektů, které patří do skupiny. Pokud tato vlastnost hodnotu TRUE, se automaticky odeberou přechody, když je naplánovaná animace. Jinak budete muset ručně odebrat přechodů.|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Určuje, jak zničit objekty animace. Pokud tento parametr má hodnotu TRUE, objekty animace zničí automaticky při zničení skupině. Animace objektů v opačném případě musí být zničený ručně. Výchozí hodnota je FALSE. Nastavte tuto hodnotu na TRUE jenom v případě, že všechny objekty animace, které patří do skupiny se přidělují dynamicky pomocí operátoru new.|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Určuje, jak odstranit klíčové snímky. Pokud je tato hodnota TRUE, se odeberou a zničení; všechny klíčové snímky v opačném případě se odeberou ze seznamu pouze. Výchozí hodnota je TRUE.|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Obsahuje seznam objektů animace.|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Obsahuje seznam klíčových snímků.|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Body scénáře animace. Tento ukazatel je platný pouze po volání na animovat.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Jedinečný identifikátor skupiny animace.|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Ukazatel na řadič animace, do které tato skupina patří.|

## <a name="remarks"></a>Poznámky

Animace skupiny jsou vytvořené automaticky řadič animace (canimationcontroller –) přidáte pomocí CAnimationController::AddAnimationObject objekty animace. Skupinu animace je identifikován GroupID, které se obvykle považuje za parametr k manipulaci se skupinami animace. GroupID je převzata z první animace objekt přidávaný do nové skupiny animace. Zapouzdřenému animace scénáře je vytvořen po volání CAnimationController::AnimateGroup a je přístupný prostřednictvím m_pStoryboard veřejný člen.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CAnimationGroup`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="_dtorcanimationgroup"></a>  Canimationgroup –:: ~ canimationgroup –

Destruktor. Volá se, když se likviduje skupinu animace.

```
~CAnimationGroup();
```

##  <a name="addkeyframes"></a>  CAnimationGroup::AddKeyframes

Pomocné rutiny, která přidá klíčové snímky na scénáře.

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na objekt modelu COM scénáře.

*bAddDeep*<br/>
Určuje, zda tato metoda má přidat do scénáře klíčové snímky, které závisí na ostatních klíčových snímků.

##  <a name="addtransitions"></a>  CAnimationGroup::AddTransitions

Pomocné rutiny, která přidává přechody do scénáře.

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na objekt modelu COM scénáře.

*bDependOnKeyframes*

##  <a name="animate"></a>  CAnimationGroup::Animate

Animuje skupinu.

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>Parametry

*pManager*<br/>
*pTimer*
*bScheduleNow*

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud metoda uspěje; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří vnitřní scénář, vytvoří a použije přechody a naplánuje animace, pokud bScheduleNow má hodnotu TRUE. Pokud bScheduleNow hodnotu FALSE, je třeba volat plán spuštění animace v zadanou dobu.

##  <a name="applytransitions"></a>  CAnimationGroup::ApplyTransitions

Přechody se vztahuje na objekty animace.

```
void ApplyTransitions();
```

### <a name="remarks"></a>Poznámky

Tato metoda nepodmíněné výrazy v režimu ladění, pokud nebyl vytvořen scénáře. Nejprve vytvoří všechny přechody pak přidá "statických" klíčové snímky (klíčové snímky, které závisí na posuny), přidá přechody, která nezávisí na klíčové snímky, přidá klíčové snímky v závislosti na přechody a ostatních klíčových snímků a v poslední přidá přechody, které jsou závislé na klíčové snímky .

##  <a name="canimationgroup"></a>  CAnimationGroup::CAnimationGroup

Vytvoří skupinu animace.

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*pParentController*<br/>
Ukazatel na řadič animace, který vytvoří skupinu.

*nGroupID*<br/>
Určuje ID skupiny.

##  <a name="createtransitions"></a>  CAnimationGroup::CreateTransitions

Pomocné rutiny, která vytváří objekty modelu COM přechodu.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE je metoda úspěšná, jinak hodnota FALSE.

##  <a name="findanimationobject"></a>  CAnimationGroup::FindAnimationObject

Vyhledá objekt animace, který obsahuje proměnné zadané animace.

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pVariable*<br/>
Ukazatel na proměnnou animace.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt animace, nebo hodnota NULL, pokud objekt animace nebyl nalezen.

##  <a name="getgroupid"></a>  CAnimationGroup::GetGroupID

Vrátí ID skupiny.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor skupiny.

##  <a name="m_bautocleartransitions"></a>  CAnimationGroup::m_bAutoclearTransitions

Určuje, jak vymazat přechody ze animace objektů, které patří do skupiny. Pokud tato vlastnost hodnotu TRUE, se automaticky odeberou přechody, když je naplánovaná animace. Jinak budete muset ručně odebrat přechodů.

```
BOOL m_bAutoclearTransitions;
```

##  <a name="m_bautodestroyanimationobjects"></a>  CAnimationGroup::m_bAutodestroyAnimationObjects

Určuje, jak zničit objekty animace. Pokud tento parametr má hodnotu TRUE, objekty animace zničí automaticky při zničení skupině. Animace objektů v opačném případě musí být zničený ručně. Výchozí hodnota je FALSE. Nastavte tuto hodnotu na TRUE jenom v případě, že všechny objekty animace, které patří do skupiny se přidělují dynamicky pomocí operátoru new.

```
BOOL m_bAutodestroyAnimationObjects;
```

##  <a name="m_bautodestroykeyframes"></a>  CAnimationGroup::m_bAutodestroyKeyframes

Určuje, jak odstranit klíčové snímky. Pokud je tato hodnota TRUE, se odeberou a zničení; všechny klíčové snímky v opačném případě se odeberou ze seznamu pouze. Výchozí hodnota je TRUE.

```
BOOL m_bAutodestroyKeyframes;
```

##  <a name="m_lstanimationobjects"></a>  CAnimationGroup::m_lstAnimationObjects

Obsahuje seznam objektů animace.

```
CObList m_lstAnimationObjects;
```

##  <a name="m_lstkeyframes"></a>  CAnimationGroup::m_lstKeyFrames

Obsahuje seznam klíčových snímků.

```
CObList m_lstKeyFrames;
```

##  <a name="m_ngroupid"></a>  CAnimationGroup::m_nGroupID

Jedinečný identifikátor skupiny animace.

```
UINT32 m_nGroupID;
```

##  <a name="m_pparentcontroller"></a>  CAnimationGroup::m_pParentController

Ukazatel na řadič animace, do které tato skupina patří.

```
CAnimationController* m_pParentController;
```

##  <a name="m_pstoryboard"></a>  CAnimationGroup::m_pStoryboard

Body scénáře animace. Tento ukazatel je platný pouze po volání na animovat.

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

##  <a name="removekeyframes"></a>  CAnimationGroup::RemoveKeyframes

Odebere a volitelně odstraní všechny klíčové snímky, které patří do skupiny animace.

```
void RemoveKeyframes();
```

### <a name="remarks"></a>Poznámky

Pokud člen m_bAutodestroyKeyframes je TRUE, pak klíčové snímky se odeberou a zničen, jinak jsou klíčové snímky právě odebrali z interní seznam klíčových snímků.

##  <a name="removetransitions"></a>  CAnimationGroup::RemoveTransitions

Odebere přechody z animace objektů, které patří do skupiny animace.

```
void RemoveTransitions();
```

### <a name="remarks"></a>Poznámky

Pokud m_bAutoclearTransitions příznak nastaven na hodnotu TRUE, tato metoda cyklicky prochází přes všechny objekty animace, které patří do skupiny a volá CAnimationObject::ClearTransitions(FALSE).

##  <a name="schedule"></a>  CAnimationGroup::Schedule

Naplánuje animace v zadanou dobu.

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>Parametry

*pTimer*<br/>
Ukazatel na časovač animace.

*čas*<br/>
Určuje dobu naplánování animace.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud metoda uspěje; FALSE Jestliže metoda selže nebo pokud animovat nebyla volána s bScheduleNow nastavena na hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Voláním této funkce naplánování animace v zadanou dobu. Animate musí volat s bScheduleNow nejprve nastavit na hodnotu FALSE.

##  <a name="setautodestroytransitions"></a>  CAnimationGroup::SetAutodestroyTransitions

Dostává instrukci, že všechny objekty animace, které patří do skupiny automaticky zničit přechodů.

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
Určuje, jak odstranit přechodů.

### <a name="remarks"></a>Poznámky

Nastavte tuto hodnotu na hodnotu FALSE, pouze pokud přidělíte přechody do zásobníku. Výchozí hodnota je TRUE, proto se důrazně doporučujeme k přidělení paměti pro přechod objekty pomocí operátoru nové.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
