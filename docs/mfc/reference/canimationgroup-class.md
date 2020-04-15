---
title: Třída CAnimationGroup
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
ms.openlocfilehash: 28d305e2107f7b9a8fd2164eb0ec9678d62ef8fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369747"
---
# <a name="canimationgroup-class"></a>Třída CAnimationGroup

Implementuje skupinu animace, která kombinuje scénáře animace, objekty animace a přechody k definování animace.

## <a name="syntax"></a>Syntaxe

```
class CAnimationGroup;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|Vytvoří skupinu animací.|
|[CAnimationGroup::~CAnimationGroup](#_dtorcanimationgroup)|Destruktor. Nazývá se při zničení skupiny animací.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationGroup::Animovat](#animate)|Animuje skupinu.|
|[CAnimationGroup::ApplyTransitions](#applytransitions)|Aplikuje přechody na objekty animace.|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Vyhledá objekt animace, který obsahuje zadanou proměnnou animace.|
|[CanimationGroup::GetGroupID](#getgroupid)|Vrátí GroupID.|
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|Odebere a volitelně zničí všechny klíčové snímky, které patří do skupiny animací.|
|[CAnimationGroup::RemoveTransitions](#removetransitions)|Odstraní přechody z animačních objektů, které patří do skupiny animací.|
|[CAnimationGroup::Plán](#schedule)|Naplánuje animaci v určený čas.|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Přesměruje všechny animační objekty, které patří do skupiny, automaticky zničí přechody.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Pomocník, který přidá klíčové snímky do scénáře.|
|[CAnimationGroup::AddTransitions](#addtransitions)|Pomocník, který přidá přechody do scénáře.|
|[CAnimationGroup::CreateTransitions](#createtransitions)|Pomocník, který vytváří objekty přechodu MODELU COM.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Určuje, jak vymazat přechody z objektů animace, které patří do skupiny. Pokud je tento člen TRUE, přechody jsou automaticky odebrány, když byla naplánována animace. V opačném případě je třeba odstranit přechody ručně.|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Určuje způsob zničení objektů animace. Pokud je tento parametr TRUE, objekty animace budou automaticky zničeny při zničení skupiny. V opačném případě musí být objekty animace zničeny ručně. Výchozí hodnota je FALSE. Tuto hodnotu nastavte na hodnotu PRAVDA pouze v případě, že všechny objekty animace, které patří do skupiny, jsou dynamicky přiděleny operátoru new.|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Určuje způsob zničení klíčových snímků. Pokud je tato hodnota TRUE, všechny klíčové snímky jsou odebrány a zničeny; v opačném případě budou odebrány pouze ze seznamu. Výchozí hodnota je TRUE.|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Obsahuje seznam animačních objektů.|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Obsahuje seznam klíčových snímků.|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Odkazuje na scénář animace. Tento ukazatel je platný pouze po volání na Animate.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Jedinečný identifikátor skupiny animací.|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Ukazatel na ovladač animace, do který tato skupina patří.|

## <a name="remarks"></a>Poznámky

Skupiny animací jsou vytvářeny automaticky řadičem animace (CAnimationController) při přidání objektů animace pomocí CAnimationController::AddAnimationObject. Skupina animací je identifikována GroupID, která se obvykle považuje za parametr pro manipulaci se skupinami animací. GroupID je převzatz první objekt animace, který je přidán do nové skupiny animací. Zapouzdřený scénář animace je vytvořen po volání CAnimationController::AnimateGroup a lze k němu přistupovat prostřednictvím veřejného m_pStoryboard.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CAnimationGroup`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationgroupcanimationgroup"></a><a name="_dtorcanimationgroup"></a>CAnimationGroup::~CAnimationGroup

Destruktor. Nazývá se při zničení skupiny animací.

```
~CAnimationGroup();
```

## <a name="canimationgroupaddkeyframes"></a><a name="addkeyframes"></a>CAnimationGroup::AddKeyframes

Pomocník, který přidá klíčové snímky do scénáře.

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na objekt com scénáře.

*bPřidatDeep*<br/>
Určuje, zda má tato metoda přidat do scénáře klíčové snímky, které závisí na jiných klíčových snímků.

## <a name="canimationgroupaddtransitions"></a><a name="addtransitions"></a>CAnimationGroup::AddTransitions

Pomocník, který přidá přechody do scénáře.

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na objekt com scénáře.

*bDependOnKeyframes*

## <a name="canimationgroupanimate"></a><a name="animate"></a>CAnimationGroup::Animovat

Animuje skupinu.

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>Parametry

*pManažer*<br/>
*pTimer*
*bScheduleNow*

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří vnitřní scénář, vytvoří a použije přechody a naplánuje animaci, pokud je bScheduleNow TRUE. Pokud bScheduleNow je FALSE, je třeba volat Plán spustit animaci v zadaném čase.

## <a name="canimationgroupapplytransitions"></a><a name="applytransitions"></a>CAnimationGroup::ApplyTransitions

Aplikuje přechody na objekty animace.

```
void ApplyTransitions();
```

### <a name="remarks"></a>Poznámky

Tato metoda ASSERTS v režimu ladění, pokud scénář nebyl vytvořen. Nejprve vytvoří všechny přechody, poté přidá "statické" klíčové snímky (klíčové snímky, které závisí na posunech), přidá přechody, které nezávisí na klíčových snímcích, přidá klíčové snímky v závislosti na přechodech a dalších klíčových snímcích a nakonec přidá přechody, které závisí na klíčových snímcích.

## <a name="canimationgroupcanimationgroup"></a><a name="canimationgroup"></a>CAnimationGroup::CAnimationGroup

Vytvoří skupinu animací.

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*pParentController*<br/>
Ukazatel na ovladač animace, který vytvoří skupinu.

*nID skupiny*<br/>
Určuje GroupID.

## <a name="canimationgroupcreatetransitions"></a><a name="createtransitions"></a>CAnimationGroup::CreateTransitions

Pomocník, který vytváří objekty přechodu MODELU COM.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Návratová hodnota

TRUE je metoda úspěšná, jinak FALSE.

## <a name="canimationgroupfindanimationobject"></a><a name="findanimationobject"></a>CAnimationGroup::FindAnimationObject

Vyhledá objekt animace, který obsahuje zadanou proměnnou animace.

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pProměnná proměnná*<br/>
Ukazatel na proměnnou animace.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt animace nebo NULL, pokud objekt animace nebyl nalezen.

## <a name="canimationgroupgetgroupid"></a><a name="getgroupid"></a>CanimationGroup::GetGroupID

Vrátí GroupID.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor skupiny.

## <a name="canimationgroupm_bautocleartransitions"></a><a name="m_bautocleartransitions"></a>CAnimationGroup::m_bAutoclearTransitions

Určuje, jak vymazat přechody z objektů animace, které patří do skupiny. Pokud je tento člen TRUE, přechody jsou automaticky odebrány, když byla naplánována animace. V opačném případě je třeba odstranit přechody ručně.

```
BOOL m_bAutoclearTransitions;
```

## <a name="canimationgroupm_bautodestroyanimationobjects"></a><a name="m_bautodestroyanimationobjects"></a>CAnimationGroup::m_bAutodestroyAnimationObjects

Určuje způsob zničení objektů animace. Pokud je tento parametr TRUE, objekty animace budou automaticky zničeny při zničení skupiny. V opačném případě musí být objekty animace zničeny ručně. Výchozí hodnota je FALSE. Tuto hodnotu nastavte na hodnotu PRAVDA pouze v případě, že všechny objekty animace, které patří do skupiny, jsou dynamicky přiděleny operátoru new.

```
BOOL m_bAutodestroyAnimationObjects;
```

## <a name="canimationgroupm_bautodestroykeyframes"></a><a name="m_bautodestroykeyframes"></a>CAnimationGroup::m_bAutodestroyKeyframes

Určuje způsob zničení klíčových snímků. Pokud je tato hodnota TRUE, všechny klíčové snímky jsou odebrány a zničeny; v opačném případě budou odebrány pouze ze seznamu. Výchozí hodnota je TRUE.

```
BOOL m_bAutodestroyKeyframes;
```

## <a name="canimationgroupm_lstanimationobjects"></a><a name="m_lstanimationobjects"></a>CAnimationGroup::m_lstAnimationObjects

Obsahuje seznam animačních objektů.

```
CObList m_lstAnimationObjects;
```

## <a name="canimationgroupm_lstkeyframes"></a><a name="m_lstkeyframes"></a>CAnimationGroup::m_lstKeyFrames

Obsahuje seznam klíčových snímků.

```
CObList m_lstKeyFrames;
```

## <a name="canimationgroupm_ngroupid"></a><a name="m_ngroupid"></a>CAnimationGroup::m_nGroupID

Jedinečný identifikátor skupiny animací.

```
UINT32 m_nGroupID;
```

## <a name="canimationgroupm_pparentcontroller"></a><a name="m_pparentcontroller"></a>CAnimationGroup::m_pParentController

Ukazatel na ovladač animace, do který tato skupina patří.

```
CAnimationController* m_pParentController;
```

## <a name="canimationgroupm_pstoryboard"></a><a name="m_pstoryboard"></a>CAnimationGroup::m_pStoryboard

Odkazuje na scénář animace. Tento ukazatel je platný pouze po volání na Animate.

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

## <a name="canimationgroupremovekeyframes"></a><a name="removekeyframes"></a>CAnimationGroup::RemoveKeyframes

Odebere a volitelně zničí všechny klíčové snímky, které patří do skupiny animací.

```
void RemoveKeyframes();
```

### <a name="remarks"></a>Poznámky

Pokud je m_bAutodestroyKeyframes člen true, jsou klíčové snímky odebrány a zničeny, jinak jsou klíčové snímky právě odebrány z interního seznamu klíčových snímků.

## <a name="canimationgroupremovetransitions"></a><a name="removetransitions"></a>CAnimationGroup::RemoveTransitions

Odstraní přechody z animačních objektů, které patří do skupiny animací.

```
void RemoveTransitions();
```

### <a name="remarks"></a>Poznámky

Pokud je příznak m_bAutoclearTransitions nastaven na hodnotu TRUE, tato metoda se smyčkuje přes všechny objekty animace, které patří do skupiny a volá CAnimationObject::ClearTransitions(FALSE).

## <a name="canimationgroupschedule"></a><a name="schedule"></a>CAnimationGroup::Plán

Naplánuje animaci v určený čas.

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>Parametry

*pČasovač*<br/>
Ukazatel na časovač animace.

*Čas*<br/>
Určuje čas naplánování animace.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; FALSE, pokud metoda selže nebo pokud animate nebyla volána s bScheduleNow nastavena na hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Volání této funkce naplánovat animaci v zadaném čase. Musíte nejprve zavolat Animate s bScheduleNow nastaveným na HODNOTU FALSE.

## <a name="canimationgroupsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>CAnimationGroup::SetAutodestroyTransitions

Přesměruje všechny animační objekty, které patří do skupiny, automaticky zničí přechody.

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
Určuje způsob zničení přechodů.

### <a name="remarks"></a>Poznámky

Tuto hodnotu nastavte na hodnotu FALSE pouze v případě, že přidělujete přechody v zásobníku. Výchozí hodnota je TRUE, proto se důrazně doporučuje přidělit objekty přechodu pomocí operátoru new.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
