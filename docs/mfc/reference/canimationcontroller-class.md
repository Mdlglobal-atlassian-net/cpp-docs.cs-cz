---
title: Třída CAnimationController
ms.date: 03/27/2019
f1_keywords:
- CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::AddAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::AddKeyframeToGroup
- AFXANIMATIONCONTROLLER/CAnimationController::AnimateGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CleanUpGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CreateKeyframe
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationManagerEvent
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnablePriorityComparisonHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnableStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::GetKeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionLibrary
- AFXANIMATIONCONTROLLER/CAnimationController::IsAnimationInProgress
- AFXANIMATIONCONTROLLER/CAnimationController::IsValid
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnBeforeAnimationStart
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCancel
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCompress
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityConclude
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityTrim
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAllAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationController::ScheduleGroup
- AFXANIMATIONCONTROLLER/CAnimationController::SetRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::UpdateAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::OnAfterSchedule
- AFXANIMATIONCONTROLLER/CAnimationController::gkeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::m_bIsValid
- AFXANIMATIONCONTROLLER/CAnimationController::m_lstAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::m_pRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionLibrary
helpviewer_keywords:
- CAnimationController [MFC], CAnimationController
- CAnimationController [MFC], AddAnimationObject
- CAnimationController [MFC], AddKeyframeToGroup
- CAnimationController [MFC], AnimateGroup
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], CreateKeyframe
- CAnimationController [MFC], EnableAnimationManagerEvent
- CAnimationController [MFC], EnableAnimationTimerEventHandler
- CAnimationController [MFC], EnablePriorityComparisonHandler
- CAnimationController [MFC], EnableStoryboardEventHandler
- CAnimationController [MFC], FindAnimationGroup
- CAnimationController [MFC], FindAnimationObject
- CAnimationController [MFC], GetKeyframeStoryboardStart
- CAnimationController [MFC], GetUIAnimationManager
- CAnimationController [MFC], GetUIAnimationTimer
- CAnimationController [MFC], GetUITransitionFactory
- CAnimationController [MFC], GetUITransitionLibrary
- CAnimationController [MFC], IsAnimationInProgress
- CAnimationController [MFC], IsValid
- CAnimationController [MFC], OnAnimationIntegerValueChanged
- CAnimationController [MFC], OnAnimationManagerStatusChanged
- CAnimationController [MFC], OnAnimationTimerPostUpdate
- CAnimationController [MFC], OnAnimationTimerPreUpdate
- CAnimationController [MFC], OnAnimationTimerRenderingTooSlow
- CAnimationController [MFC], OnAnimationValueChanged
- CAnimationController [MFC], OnBeforeAnimationStart
- CAnimationController [MFC], OnHasPriorityCancel
- CAnimationController [MFC], OnHasPriorityCompress
- CAnimationController [MFC], OnHasPriorityConclude
- CAnimationController [MFC], OnHasPriorityTrim
- CAnimationController [MFC], OnStoryboardStatusChanged
- CAnimationController [MFC], OnStoryboardUpdated
- CAnimationController [MFC], RemoveAllAnimationGroups
- CAnimationController [MFC], RemoveAnimationGroup
- CAnimationController [MFC], RemoveAnimationObject
- CAnimationController [MFC], RemoveTransitions
- CAnimationController [MFC], ScheduleGroup
- CAnimationController [MFC], SetRelatedWnd
- CAnimationController [MFC], UpdateAnimationManager
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], OnAfterSchedule
- CAnimationController [MFC], gkeyframeStoryboardStart
- CAnimationController [MFC], m_bIsValid
- CAnimationController [MFC], m_lstAnimationGroups
- CAnimationController [MFC], m_pAnimationManager
- CAnimationController [MFC], m_pAnimationTimer
- CAnimationController [MFC], m_pRelatedWnd
- CAnimationController [MFC], m_pTransitionFactory
- CAnimationController [MFC], m_pTransitionLibrary
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
ms.openlocfilehash: 489e931c4063e7bf06ace1cb130b9891253c94d4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750174"
---
# <a name="canimationcontroller-class"></a>Třída CAnimationController

Implementuje řadič animace, který poskytuje centrální rozhraní pro vytváření a správu animací.

## <a name="syntax"></a>Syntaxe

```
class CAnimationController : public CObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAnimationController::CAnimationController](#canimationcontroller)|Vytvoří animační řadič.|
|[CAnimationController::~CAnimationController](#_dtorcanimationcontroller)|Destruktor. Volána při zničení objektu řadiče animace.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|Přidá objekt animace do skupiny, která patří do ovladače animace.|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Přidá klíčový snímek do skupiny.|
|[CAnimationController::AnimovatSkupina](#animategroup)|Připraví skupinu ke spuštění animace a volitelně ji naplánuje.|
|[CanimationController::CleanUpGroup](#cleanupgroup)|Přetíženo. Volat rámci vyčistit skupinu, když animace byla naplánována.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|Přetíženo. Vytvoří klíčový snímek, který závisí na přechodu, a přidá jej do zadané skupiny.|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Nastaví nebo uvolní obslužnou rutinu, která bude volat, když se změní stav správce animací.|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Nastaví nebo uvolní obslužnou rutinu pro události časování a obslužnou rutinu pro aktualizace časování.|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Nastaví nebo uvolní obslužnou rutinu porovnání priorit k volání k určení, zda naplánované scénáře lze zrušit, uzavřít, oříznuté nebo komprimované.|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Nastaví nebo uvolní obslužnou rutinu pro stav scénáře a aktualizovat události.|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Přetíženo. Najde skupinu animací podle scénáře.|
|[CAnimationController::FindAnimationObject](#findanimationobject)|Najde objekt animace obsahující zadanou proměnnou animace.|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Vrátí klíčový snímek, který identifikuje začátek scénáře.|
|[CAnimationController::GetUiAnimationManager](#getuianimationmanager)|Poskytuje přístup k zapouzdřené IUIAnimationManager objektu.|
|[CanimationController::GetUiAnimationTimer](#getuianimationtimer)|Poskytuje přístup k zapouzdřený objekt IUIAnimationTimer.|
|[CanimationController::GetUiTransitionFactory](#getuitransitionfactory)|Ukazatel na rozhraní IUIAnimationTransitionFactory nebo NULL, pokud se nezdařilo vytvoření knihovny přechodu.|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Poskytuje přístup k zapouzdřený IUIAnimationTransitionLibrary objektu.|
|[CanimationController::IsAnimationInProgress](#isanimationinprogress)|Určuje, zda alespoň jedna skupina přehrává animaci.|
|[CAnimationController::IsValid](#isvalid)|Určuje, zda je řadič animace platný.|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Volat rámci při nezměnila celá hodnota proměnné animace.|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Volat rámci v reakci na StatusChanged událost ze správce animací.|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Volat rámci po dokončení aktualizace animace.|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Volat rámci před zahájením aktualizace animace.|
|[CanimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Volat rámci při vykreslování kmitočet snímků pro animaci klesne pod minimální žádoucí kmitočet snímků.|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Volat rámci při změně hodnoty proměnné animace.|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Volat rámci těsně před naplánované animace.|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Volat v rámci k řešení konfliktů plánování.|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Volat v rámci k řešení konfliktů plánování.|
|[CanimationController::OnHasPriorityUzavřít](#onhaspriorityconclude)|Volat v rámci k řešení konfliktů plánování.|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Volat v rámci k řešení konfliktů plánování.|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Volat rámci při změně stavu scénáře.|
|[CAnimationController::OnStoryboardAktualizováno](#onstoryboardupdated)|Volat rámci při scénář i aktualizace scénáře.|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Odebere všechny skupiny animací z ovladače animace.|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Odebere skupinu animací se zadaným ID z ovladače animace.|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Odeberte objekt animace z ovladače animace.|
|[CAnimationController::RemoveTransitions](#removetransitions)|Odebere přechody z animačních objektů, které patří do zadané skupiny.|
|[CAnimationController::ScheduleGroup](#schedulegroup)|Naplánuje animaci.|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Vytvoří vztah mezi ovladačem animace a oknem.|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Přesměruje správce animací k aktualizaci hodnot všech proměnných animace.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CanimationController::CleanUpGroup](#cleanupgroup)|Přetíženo. Pomocník, který uklidí skupinu.|
|[CanimationController::OnAfterSchedule](#onafterschedule)|Volat rámci při animace pro zadanou skupinu byla právě naplánována.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Klíčový snímek, který představuje začátek scénáře.|
|[CAnimationController::m_bIsValid](#m_bisvalid)|Určuje, zda je řadič animace platný nebo ne. Tento člen je nastaven na hodnotu FALSE, pokud aktuální operační systém nepodporuje rozhraní API pro animaci systému Windows.|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Seznam animačních skupin, které patří do tohoto animačního kontroléru.|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Uloží ukazatel na objekt COM Správce animací.|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Uloží ukazatel na objekt COM časovače animace.|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Ukazatel na související cwnd objekt, který lze automaticky překreslit, když se změní stav správce animací nebo dojde k události po aktualizaci. Může být NULL.|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Uloží ukazatel na objekt COM z továrny přechodu.|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Uloží ukazatel na objekt COM knihovny přechodu.|

## <a name="remarks"></a>Poznámky

Třída CAnimationController je třída klíče, která spravuje animace. Můžete vytvořit jednu nebo více instancí řadiče animace v aplikaci a volitelně připojit instanci řadiče animace k objektu CWnd pomocí CAnimationController::SetRelatedWnd. Toto připojení je nutné automaticky odesílat WM_PAINT zprávy do souvisejícího okna, pokud se změní stav správce animací nebo dojde k aktualizaci časovače animace. Pokud tento vztah nepovolíte, je nutné překreslit okno, které zobrazuje animaci ručně. Pro tento účel můžete odvodit třídu z CAnimationController a přepsat OnAnimationManagerStatusChanged a/nebo OnAnimationTimerPostUpdate a v případě potřeby zneplatnit jedno nebo více oken.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationcontrollercanimationcontroller"></a><a name="_dtorcanimationcontroller"></a>CAnimationController::~CAnimationController

Destruktor. Volána při zničení objektu řadiče animace.

```
virtual ~CAnimationController(void);
```

## <a name="canimationcontrolleraddanimationobject"></a><a name="addanimationobject"></a>CAnimationController::AddAnimationObject

Přidá objekt animace do skupiny, která patří do ovladače animace.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Parametry

*pObjekt*<br/>
Ukazatel na objekt animace.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na existující nebo novou skupinu animací, kde byl přidán objekt pObject, pokud je funkce úspěšná; NULL, pokud pObject již byla přidána do skupiny, která patří do jiného řadiče animace.

### <a name="remarks"></a>Poznámky

Volání této metody přidat objekt animace do ovladače animace. Objekt bude přidán do skupiny podle GroupID objektu (viz CAnimationBaseObject::SetID). Kontroler animace vytvoří novou skupinu, pokud se jedná o první objekt, který je přidán se zadaným GroupID. Objekt animace lze přidat pouze do jednoho ovladače animace. Pokud potřebujete přidat objekt do jiného řadiče, nejprve zavolejte RemoveAnimationObject. Pokud zavoláte SetID s novým GroupID pro objekt, který již byl přidán do skupiny, objekt bude odebrán ze staré skupiny a přidán do jiné skupiny se zadaným ID.

## <a name="canimationcontrolleraddkeyframetogroup"></a><a name="addkeyframetogroup"></a>CAnimationController::AddKeyframeToGroup

Přidá klíčový snímek do skupiny.

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>Parametry

*nID skupiny*<br/>
Určuje ID skupiny.

*pKlíč*<br/>
Ukazatel na klíčový snímek.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je funkce úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Obvykle není nutné volat tuto metodu, použijte CAnimationController::CreateKeyframe místo, který vytvoří a přidá vytvořený klíčový snímek do skupiny automaticky.

## <a name="canimationcontrolleranimategroup"></a><a name="animategroup"></a>CAnimationController::AnimovatSkupina

Připraví skupinu ke spuštění animace a volitelně ji naplánuje.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>Parametry

*nID skupiny*<br/>
Určuje GroupID.

*bScheduleNow*<br/>
Určuje, zda má být animace spuštěna ihned.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud animace byla úspěšně naplánována a spuštěna.

### <a name="remarks"></a>Poznámky

Tato metoda provádí skutečnou práci vytváření scénáře, přidávání proměnných animace, použití přechodů a nastavení klíčových snímků. Je možné odložit plánování, pokud nastavíte bScheduleNow na FALSE. V takovém případě zadaná skupina bude obsahovat scénář, který byl nastaven pro animaci. V tomto okamžiku můžete nastavit události pro proměnné scénáře a animace. Když skutečně potřebujete spustit volání animace CAnimationController::ScheduleGroup.

## <a name="canimationcontrollercanimationcontroller"></a><a name="canimationcontroller"></a>CAnimationController::CAnimationController

Vytvoří animační řadič.

```
CAnimationController(void);
```

## <a name="canimationcontrollercleanupgroup"></a><a name="cleanupgroup"></a>CanimationController::CleanUpGroup

Volat rámci vyčistit skupinu, když animace byla naplánována.

```cpp
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*nID skupiny*<br/>
Určuje GroupID.

*pSkupina*<br/>
Ukazatel na skupinu animací k čištění.

### <a name="remarks"></a>Poznámky

Tato metoda odebere všechny přechody a klíčové snímky ze zadané skupiny, protože nejsou relevantní po naplánování animace.

## <a name="canimationcontrollercreatekeyframe"></a><a name="createkeyframe"></a>CAnimationController::CreateKeyframe

Vytvoří klíčový snímek, který závisí na přechodu, a přidá jej do zadané skupiny.

```
CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseTransition* pTransition);

CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parametry

*nID skupiny*<br/>
Určuje ID skupiny, pro které je vytvořen klíčový snímek.

*pPřechod*<br/>
Ukazatel přechodu. Klíčový snímek bude vložen do scénáře po tomto přechodu.

*pKlíč*<br/>
Ukazatel na základní klíčový snímek pro tento klíčový snímek.

*Posun*<br/>
Posun v sekundách od základního klíčového snímku určeného pKeyframe.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený klíčový snímek, pokud je funkce úspěšná.

### <a name="remarks"></a>Poznámky

Vrácený ukazatel a další klíčové snímky můžete uložit na nově vytvořený klíčový snímek (viz druhé přetížení). Je možné zahájit přechody na klíčové snímky - viz CBaseTransition::SetKeyframes. Není nutné odstraňovat klíčové snímky vytvořené tímto způsobem, protože jsou automaticky odstraněny skupinami animací. Při vytváření klíčových snímků založených na jiných klíčových snímcích a přechodech buďte opatrní a vyhněte se cyklické odkazy.

## <a name="canimationcontrollerenableanimationmanagerevent"></a><a name="enableanimationmanagerevent"></a>CAnimationController::EnableAnimationManagerEvent

Nastaví nebo uvolní obslužnou rutinu, která bude volat, když se změní stav správce animací.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda má být obslužná rutina nastavena nebo vydána.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla obslužná rutina úspěšně nastavena nebo vydána.

### <a name="remarks"></a>Poznámky

Pokud je nastavena (povolena) Animace systému Windows volá OnAnimationManagerStatusChanged při změně stavu správce animací.

## <a name="canimationcontrollerenableanimationtimereventhandler"></a><a name="enableanimationtimereventhandler"></a>CAnimationController::EnableAnimationTimerEventHandler

Nastaví nebo uvolní obslužnou rutinu pro události časování a obslužnou rutinu pro aktualizace časování.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda mají být obslužné rutiny nastaveny nebo vydány.

*idleBehavior*<br/>
Určuje chování nečinnosti pro obslužnou rutinu aktualizace časovače.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byly obslužné rutiny úspěšně nastaveny nebo uvolněny; FALSE, pokud je tato metoda volána podruhé bez uvolnění obslužné rutiny první nebo pokud dojde k jiné chybě.

### <a name="remarks"></a>Poznámky

Když jsou nastaveny (povoleny) Windows Animation API volání OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate, OnRenderingTooSlow metody. Je třeba povolit časovače animace povolit windows animace rozhraní API aktualizovat scénáře. V opačném případě budete muset volat CAnimationController::UpdateAnimationManager, abyste nasměrovali správce animací na aktualizaci hodnot všech proměnných animace.

## <a name="canimationcontrollerenableprioritycomparisonhandler"></a><a name="enableprioritycomparisonhandler"></a>CAnimationController::EnablePriorityComparisonHandler

Nastaví nebo uvolní obslužnou rutinu porovnání priorit k volání k určení, zda naplánované scénáře lze zrušit, uzavřít, oříznuté nebo komprimované.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Parametry

*dwHandlerType*<br/>
Kombinace příznaků UI_ANIMATION_PHT_ (viz poznámky), která určuje, jaké obslužné rutiny mají být nastaveny nebo vydány.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla obslužná rutina úspěšně nastavena nebo vydána.

### <a name="remarks"></a>Poznámky

Pokud je nastavena obslužná rutina (povolena) Animace systému Windows volá následující virtuální metody v závislosti na dwHandlerType: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler může být kombinací následujících příznaků: UI_ANIMATION_PHT_NONE - uvolnit všechny obslužné rutiny UI_ANIMATION_PHT_CANCEL - nastavit zrušit porovnávácí obslužnou rutinu UI_ANIMATION_PHT_CONCLUDE - nastavit obslužnou rutinu porovnání UI_ANIMATION_PHT_COMPRESS - nastavit obslužnou rutinu porovnání komprese UI_ANIMATION_PHT_TRIM - nastavit obslužnou rutinu porovnání trim UI_ANIMATION_PHT_CANCEL_REMOVE - odebrat obslužnou rutinu porovnání storno UI_ANIMATION_PHT_CONCLUDE_REMOVE - odebrat obslužnou rutinu porovnání UI_ANIMATION_PHT_COMPRESS_REMOVE - Odstranit porovnání obslužnou rutinu UI_ANIMATION_PHT_TRIM_REMOVE - odebrat obslužnou rutinu porovnání oříznutí

## <a name="canimationcontrollerenablestoryboardeventhandler"></a><a name="enablestoryboardeventhandler"></a>CAnimationController::EnableStoryboardEventHandler

Nastaví nebo uvolní obslužnou rutinu pro stav scénáře a aktualizovat události.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*nID skupiny*<br/>
Určuje ID skupiny.

*bEnable*<br/>
Určuje, zda má být obslužná rutina nastavena nebo vydána.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla obslužná rutina úspěšně nastavena nebo vydána; FALSE, pokud je nyní nalezena zadaná skupina animací nebo animace pro zadanou skupinu nebyla inicializována a její vnitřní scénář je NULL.

### <a name="remarks"></a>Poznámky

Když je nastavena obslužná rutina (povolena) Rozhraní API animace systému Windows volá OnStoryboardStatusChanges a OnStoryboardUpdated virtuální metody. Obslužná rutina musí být nastavena po CAnimationController::Animate byla volána pro zadanou skupinu animací, protože vytvoří zapouzdřený iUIAnimationStoryboard objekt.

## <a name="canimationcontrollerfindanimationgroup"></a><a name="findanimationgroup"></a>CAnimationController::FindAnimationGroup

Vyhledá animační skupinu podle ID skupiny.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*nID skupiny*<br/>
Určuje GroupID.

*pStoryboard*<br/>
Ukazatel na scénář.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na skupinu animací nebo hodnotu NULL, pokud není nalezena skupina se zadaným ID.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete najít skupinu animací za běhu. Skupina je vytvořena a přidána do interního seznamu skupin animací, když je do řadiče animace přidán první objekt animace s určitým GroupID.

## <a name="canimationcontrollerfindanimationobject"></a><a name="findanimationobject"></a>CAnimationController::FindAnimationObject

Najde objekt animace obsahující zadanou proměnnou animace.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>Parametry

*pProměnná proměnná*<br/>
Ukazatel na proměnnou animace.

*ppObject*<br/>
Výstup. Obsahuje ukazatel na objekt animace nebo NULL.

*ppSkupina*<br/>
Výstup. Obsahuje ukazatel na skupinu animace, která obsahuje objekt animace nebo NULL.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl nalezen objekt; jinak FALSE.

### <a name="remarks"></a>Poznámky

Volána z obslužné rutiny událostí, když je nutné najít objekt animace z příchozí proměnné animace.

## <a name="canimationcontrollergkeyframestoryboardstart"></a><a name="g_keyframestoryboardstart"></a>CAnimationController::gkeyframeStoryboardStart

Klíčový snímek, který představuje začátek scénáře.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

## <a name="canimationcontrollergetkeyframestoryboardstart"></a><a name="getkeyframestoryboardstart"></a>CAnimationController::GetKeyframeStoryboardStart

Vrátí klíčový snímek, který identifikuje začátek scénáře.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na základní klíčový snímek, který identifikuje začátek scénáře.

### <a name="remarks"></a>Poznámky

Získejte tento klíčový snímek založit všechny ostatní klíčové snímky nebo přechody v okamžiku, kdy se spustí scénář.

## <a name="canimationcontrollergetuianimationmanager"></a><a name="getuianimationmanager"></a>CAnimationController::GetUiAnimationManager

Poskytuje přístup k zapouzdřené IUIAnimationManager objektu.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IUIAnimationManager nebo NULL, pokud se nezdařilo vytvoření správce animací.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje rozhraní API animace systému Windows, vrátí tato metoda hodnotu NULL a poté všechna následná volání na CAnimationController::IsValid return FALSE. Možná budete muset získat přístup k IUIAnimationManager, aby bylo možné volat jeho metody rozhraní, které nejsou zabaleny do řadiče animace.

## <a name="canimationcontrollergetuianimationtimer"></a><a name="getuianimationtimer"></a>CanimationController::GetUiAnimationTimer

Poskytuje přístup k zapouzdřený objekt IUIAnimationTimer.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IUIAnimationTimer nebo NULL, pokud se nezdařilo vytvoření časovače animace.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje rozhraní API animace systému Windows, vrátí tato metoda hodnotu NULL a poté všechna následná volání na CAnimationController::IsValid return FALSE.

## <a name="canimationcontrollergetuitransitionfactory"></a><a name="getuitransitionfactory"></a>CanimationController::GetUiTransitionFactory

Ukazatel na rozhraní IUIAnimationTransitionFactory nebo NULL, pokud se nezdařilo vytvoření knihovny přechodu.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na IUIAnimationTransitionFactory nebo NULL, pokud se nezdařilo vytvoření továrny přechodu.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje rozhraní API animace systému Windows, vrátí tato metoda hodnotu NULL a poté všechna následná volání na CAnimationController::IsValid return FALSE.

## <a name="canimationcontrollergetuitransitionlibrary"></a><a name="getuitransitionlibrary"></a>CAnimationController::GetUITransitionLibrary

Poskytuje přístup k zapouzdřený IUIAnimationTransitionLibrary objektu.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IUIAnimationTransitionLibrary nebo NULL, pokud se nezdařilo vytvoření knihovny přechodu.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje rozhraní API animace systému Windows, vrátí tato metoda hodnotu NULL a poté všechna následná volání na CAnimationController::IsValid return FALSE.

## <a name="canimationcontrollerisanimationinprogress"></a><a name="isanimationinprogress"></a>CanimationController::IsAnimationInProgress

Určuje, zda alespoň jedna skupina přehrává animaci.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud pro tento ovladač animace probíhá animace; jinak FALSE.

### <a name="remarks"></a>Poznámky

Zkontroluje stav správce animací a vrátí hodnotu PRAVDA, pokud je stav UI_ANIMATION_MANAGER_BUSY.

## <a name="canimationcontrollerisvalid"></a><a name="isvalid"></a>CAnimationController::IsValid

Určuje, zda je řadič animace platný.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je řadič animace platný; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí false pouze v případě, že rozhraní API animace systému Windows není podporováno v aktuálním osu a vytvoření správce animací se nezdařilo, protože není registrováno. Musíte volat GetUIAnimationManager alespoň jednou po inicializaci knihoven COM způsobit nastavení tohoto příznaku.

## <a name="canimationcontrollerm_bisvalid"></a><a name="m_bisvalid"></a>CAnimationController::m_bIsValid

Určuje, zda je řadič animace platný nebo ne. Tento člen je nastaven na hodnotu FALSE, pokud aktuální operační systém nepodporuje rozhraní API pro animaci systému Windows.

```
BOOL m_bIsValid;
```

## <a name="canimationcontrollerm_lstanimationgroups"></a><a name="m_lstanimationgroups"></a>CAnimationController::m_lstAnimationGroups

Seznam animačních skupin, které patří do tohoto animačního kontroléru.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

## <a name="canimationcontrollerm_panimationmanager"></a><a name="m_panimationmanager"></a>CAnimationController::m_pAnimationManager

Uloží ukazatel na objekt COM Správce animací.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

## <a name="canimationcontrollerm_panimationtimer"></a><a name="m_panimationtimer"></a>CAnimationController::m_pAnimationTimer

Uloží ukazatel na objekt COM časovače animace.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

## <a name="canimationcontrollerm_prelatedwnd"></a><a name="m_prelatedwnd"></a>CAnimationController::m_pRelatedWnd

Ukazatel na související cwnd objekt, který lze automaticky překreslit, když se změní stav správce animací nebo dojde k události po aktualizaci. Může být NULL.

```
CWnd* m_pRelatedWnd;
```

## <a name="canimationcontrollerm_ptransitionfactory"></a><a name="m_ptransitionfactory"></a>CAnimationController::m_pTransitionFactory

Uloží ukazatel na objekt COM z továrny přechodu.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

## <a name="canimationcontrollerm_ptransitionlibrary"></a><a name="m_ptransitionlibrary"></a>CAnimationController::m_pTransitionLibrary

Uloží ukazatel na objekt COM knihovny přechodu.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

## <a name="canimationcontrolleronafterschedule"></a><a name="onafterschedule"></a>CanimationController::OnAfterSchedule

Volat rámci při animace pro zadanou skupinu byla právě naplánována.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pSkupina*<br/>
Ukazatel na skupinu animací, která byla naplánována.

### <a name="remarks"></a>Poznámky

Výchozí implementace odebere klíčové snímky ze zadané skupiny a přechází z proměnných animace, které patří do zadané skupiny. Může být přepsána v odvozené třídě provést jakékoli další akce na plán animace.

## <a name="canimationcontrolleronanimationintegervaluechanged"></a><a name="onanimationintegervaluechanged"></a>CAnimationController::OnAnimationIntegerValueChanged

Volat rámci při nezměnila celá hodnota proměnné animace.

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>Parametry

*pSkupina*<br/>
Ukazatel na skupinu animací, která obsahuje objekt animace, jehož hodnota se změnila.

*pObjekt*<br/>
Ukazatel na objekt animace, který obsahuje proměnnou animace, jejíž hodnota se změnila.

*Proměnné*<br/>
Ukazatel na proměnnou animace.

*Newvalue*<br/>
Určuje novou hodnotu.

*prevValue*<br/>
Určuje předchozí hodnotu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události proměnné animace s EnableIntegerValueChangedEvent volaným pro konkrétní proměnnou animace nebo objekt animace. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci.

## <a name="canimationcontrolleronanimationmanagerstatuschanged"></a><a name="onanimationmanagerstatuschanged"></a>CAnimationController::OnAnimationManagerStatusChanged

Volat rámci v reakci na StatusChanged událost ze správce animací.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*newStatus*<br/>
Nový stav správce animací.

*previousStatus*<br/>
Předchozí stav správce animací.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události správce animací s EnableAnimationManagerEvent. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci. Výchozí implementace aktualizuje související okno, pokud byla nastavena s SetRelatedWnd.

## <a name="canimationcontrolleronanimationtimerpostupdate"></a><a name="onanimationtimerpostupdate"></a>CAnimationController::OnAnimationTimerPostUpdate

Volat rámci po dokončení aktualizace animace.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte obslužné rutiny událostí časovače pomocí EnableAnimationTimerEventHandler. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci.

## <a name="canimationcontrolleronanimationtimerpreupdate"></a><a name="onanimationtimerpreupdate"></a>CAnimationController::OnAnimationTimerPreUpdate

Volat rámci před zahájením aktualizace animace.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte obslužné rutiny událostí časovače pomocí EnableAnimationTimerEventHandler. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci.

## <a name="canimationcontrolleronanimationtimerrenderingtooslow"></a><a name="onanimationtimerrenderingtooslow"></a>CanimationController::OnAnimationTimerRenderingTooSlow

Volat rámci při vykreslování kmitočet snímků pro animaci klesne pod minimální žádoucí kmitočet snímků.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Parametry

*Fps*<br/>
Aktuální kmitočet snímků v snímcích za sekundu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte obslužné rutiny událostí časovače pomocí EnableAnimationTimerEventHandler. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci. Minimální žádoucí kmitočet snímků je určen voláním IUIAnimationTimer::SetFrameRateThreshold.

## <a name="canimationcontrolleronanimationvaluechanged"></a><a name="onanimationvaluechanged"></a>CAnimationController::OnAnimationValueChanged

Volat rámci při změně hodnoty proměnné animace.

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>Parametry

*pSkupina*<br/>
Ukazatel na skupinu animací, která obsahuje objekt animace, jehož hodnota se změnila.

*pObjekt*<br/>
Ukazatel na objekt animace, který obsahuje proměnnou animace, jejíž hodnota se změnila.

*Proměnné*<br/>
Ukazatel na proměnnou animace.

*Newvalue*<br/>
Určuje novou hodnotu.

*prevValue*<br/>
Určuje předchozí hodnotu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události proměnné animace s EnableValueChangedEvent volaným pro konkrétní proměnnou animace nebo objekt animace. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci.

## <a name="canimationcontrolleronbeforeanimationstart"></a><a name="onbeforeanimationstart"></a>CAnimationController::OnBeforeAnimationStart

Volat rámci těsně před naplánované animace.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pSkupina*<br/>
Ukazatel na skupinu animací, jejíž animace se chystá spustit.

### <a name="remarks"></a>Poznámky

Toto volání je směrováno na související CWnd a může být přepsáno v odvozené třídě k provedení dalších akcí před zahájením animace pro zadanou skupinu.

## <a name="canimationcontrolleronhasprioritycancel"></a><a name="onhasprioritycancel"></a>CAnimationController::OnHasPriorityCancel

Volat v rámci k řešení konfliktů plánování.

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupNaplánované*<br/>
Skupina, která vlastní aktuálně naplánovaný scénář.

*pGroupNew*<br/>
Skupina, která vlastní nový scénář, který je v plánování v konfliktu s naplánovaným scénářem vlastněným pGroupScheduled.

*prioritaEfekt*<br/>
Potenciální vliv na pGroupNew pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měl vrátit TRUE, pokud scénář vlastněný pGroupNew má prioritu. By měl vrátit FALSE, pokud scénář vlastněný pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události porovnání priorit pomocí CAnimationController::EnablePriorityComparisonHandler a určíte UI_ANIMATION_PHT_CANCEL. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci. Další informace o [správě konfliktů](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)naleznete v dokumentaci k rozhraní API pro animaci systému Windows .

## <a name="canimationcontrolleronhasprioritycompress"></a><a name="onhasprioritycompress"></a>CAnimationController::OnHasPriorityCompress

Volat v rámci k řešení konfliktů plánování.

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupNaplánované*<br/>
Skupina, která vlastní aktuálně naplánovaný scénář.

*pGroupNew*<br/>
Skupina, která vlastní nový scénář, který je v plánování v konfliktu s naplánovaným scénářem vlastněným pGroupScheduled.

*prioritaEfekt*<br/>
Potenciální vliv na pGroupNew pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měl vrátit TRUE, pokud scénář vlastněný pGroupNew má prioritu. By měl vrátit FALSE, pokud scénář vlastněný pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události porovnání priorit pomocí CAnimationController::EnablePriorityComparisonHandler a zadáte UI_ANIMATION_PHT_COMPRESS. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci. Další informace o [správě konfliktů](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)naleznete v dokumentaci k rozhraní API pro animaci systému Windows .

## <a name="canimationcontrolleronhaspriorityconclude"></a><a name="onhaspriorityconclude"></a>CanimationController::OnHasPriorityUzavřít

Volat v rámci k řešení konfliktů plánování.

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupNaplánované*<br/>
Skupina, která vlastní aktuálně naplánovaný scénář.

*pGroupNew*<br/>
Skupina, která vlastní nový scénář, který je v plánování v konfliktu s naplánovaným scénářem vlastněným pGroupScheduled.

*prioritaEfekt*<br/>
Potenciální vliv na pGroupNew pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měl vrátit TRUE, pokud scénář vlastněný pGroupNew má prioritu. By měl vrátit FALSE, pokud scénář vlastněný pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události porovnání priorit pomocí CAnimationController::EnablePriorityComparisonHandler a určíte UI_ANIMATION_PHT_CONCLUDE. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci. Další informace o [správě konfliktů](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)naleznete v dokumentaci k rozhraní API pro animaci systému Windows .

## <a name="canimationcontrolleronhasprioritytrim"></a><a name="onhasprioritytrim"></a>CAnimationController::OnHasPriorityTrim

Volat v rámci k řešení konfliktů plánování.

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupNaplánované*<br/>
Skupina, která vlastní aktuálně naplánovaný scénář.

*pGroupNew*<br/>
Skupina, která vlastní nový scénář, který je v plánování v konfliktu s naplánovaným scénářem vlastněným pGroupScheduled.

*prioritaEfekt*<br/>
Potenciální vliv na pGroupNew pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měl vrátit TRUE, pokud scénář vlastněný pGroupNew má prioritu. By měl vrátit FALSE, pokud scénář vlastněný pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události porovnání priorit pomocí CAnimationController::EnablePriorityComparisonHandler a určíte UI_ANIMATION_PHT_TRIM. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci. Další informace o [správě konfliktů](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)naleznete v dokumentaci k rozhraní API pro animaci systému Windows .

## <a name="canimationcontrolleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>CAnimationController::OnStoryboardStatusChanged

Volat rámci při změně stavu scénáře.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*pSkupina*<br/>
Ukazatel na skupinu animací, která vlastní scénář, jehož stav se změnil.

*newStatus*<br/>
Určuje nový stav.

*previousStatus*<br/>
Určuje předchozí stav.

### <a name="remarks"></a>Poznámky

Tato metoda se nazývá, pokud povolíte události scénáře pomocí CAnimationController::EnableStoryboardEventHandler. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci.

## <a name="canimationcontrolleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>CAnimationController::OnStoryboardAktualizováno

Volat rámci při scénář i aktualizace scénáře.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pSkupina*<br/>
Ukazatel na skupinu, která vlastní scénář.

### <a name="remarks"></a>Poznámky

Tato metoda se nazývá, pokud povolíte události scénáře pomocí CAnimationController::EnableStoryboardEventHandler. Může být přepsána v odvozené třídě, aby se akce specifické pro aplikaci.

## <a name="canimationcontrollerremoveallanimationgroups"></a><a name="removeallanimationgroups"></a>CAnimationController::RemoveAllAnimationGroups

Odebere všechny skupiny animací z ovladače animace.

```cpp
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Poznámky

Všechny skupiny budou odstraněny, jejich ukazatel, pokud je uložen na úrovni aplikace, musí být zrušen. Pokud cAnimationGroup::m_bAutodestroyAnimationObjects pro skupinu, která je odstraněna, je PRAVDA, budou odstraněny všechny objekty animace, které patří do této skupiny; v opačném případě budou jejich odkazy na nadřazený ovladač animace nastavenna na hodnotu NULL a mohou být přidány do jiného řadiče.

## <a name="canimationcontrollerremoveanimationgroup"></a><a name="removeanimationgroup"></a>CAnimationController::RemoveAnimationGroup

Odebere skupinu animací se zadaným ID z ovladače animace.

```cpp
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*nID skupiny*<br/>
Určuje ID skupiny animací.

### <a name="remarks"></a>Poznámky

Tato metoda odebere skupinu animací z vnitřního seznamu skupin a odstraní ji, proto pokud jste uložili ukazatel na tuto skupinu animací, musí být zrušena. Pokud cAnimationGroup::m_bAutodestroyAnimationObjects je PRAVDA, budou odstraněny všechny objekty animace, které patří do této skupiny; v opačném případě budou jejich odkazy na nadřazený ovladač animace nastavenna na hodnotu NULL a mohou být přidány do jiného řadiče.

## <a name="canimationcontrollerremoveanimationobject"></a><a name="removeanimationobject"></a>CAnimationController::RemoveAnimationObject

Odeberte objekt animace z ovladače animace.

```cpp
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Parametry

*pObjekt*<br/>
Ukazatel na objekt animace.

*bNoDelete*<br/>
Pokud je tento parametr TRUE, objekt nebude při odebrání odstraněn.

### <a name="remarks"></a>Poznámky

Odebere objekt animace z ovladače animace a skupiny animací. Tuto funkci zavolejte, pokud by konkrétní objekt již neměl být animován, nebo pokud potřebujete objekt přesunout do jiného ovladače animace. V posledním případě bNoDelete musí být TRUE.

## <a name="canimationcontrollerremovetransitions"></a><a name="removetransitions"></a>CAnimationController::RemoveTransitions

Odebere přechody z animačních objektů, které patří do zadané skupiny.

```cpp
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*nID skupiny*<br/>
Určuje ID skupiny.

### <a name="remarks"></a>Poznámky

Skupina smyčky přes jeho objekty animace a volá ClearTransitions(FALSE) pro každý objekt animace. Tato metoda je volána rámci po animace byla naplánována.

## <a name="canimationcontrollerschedulegroup"></a><a name="schedulegroup"></a>CAnimationController::ScheduleGroup

Naplánuje animaci.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Parametry

*nID skupiny*<br/>
Určuje id animace, které má být naplánováno.

*Čas*<br/>
Určuje čas plánování.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla animace úspěšně naplánována. FALSE, pokud scénář nebyl vytvořen nebo dojde k jiné chybě.

### <a name="remarks"></a>Poznámky

Musíte volat AnimateGroup s parametrem bScheduleNow nastaveným na FALSE předchozí ScheduleGroup. Můžete určit požadovanou dobu animace získanou z IUIAnimationTimer::GetTime. Pokud je parametr time 0.0, animace je naplánována na aktuální čas.

## <a name="canimationcontrollersetrelatedwnd"></a><a name="setrelatedwnd"></a>CAnimationController::SetRelatedWnd

Vytvoří vztah mezi ovladačem animace a oknem.

```cpp
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na objekt okna, který chcete nastavit.

### <a name="remarks"></a>Poznámky

Pokud je nastaven související cwnd objekt, regulátor animace můžete automaticky aktualizovat (odeslat WM_PAINT zprávu) při změně stavu správce animací nebo dojde k události aktualizace časovače.

## <a name="canimationcontrollerupdateanimationmanager"></a><a name="updateanimationmanager"></a>CAnimationController::UpdateAnimationManager

Přesměruje správce animací k aktualizaci hodnot všech proměnných animace.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Poznámky

Volání této metody posune správce animace na aktuální čas, změna stavů scénářů podle potřeby a aktualizace všech proměnných animace na příslušné interpolované hodnoty. Interně tato metoda volá IUIAnimationTimer::GetTime(timeNow) a IUIAnimationManager::Update(timeNow). Přepsat tuto metodu v odvozené třídě přizpůsobit toto chování.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
