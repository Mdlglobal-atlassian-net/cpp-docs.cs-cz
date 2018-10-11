---
title: Canimationcontroller – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ce23acf1988e88954279f3b8cdbc8fc3c9001af
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083642"
---
# <a name="canimationcontroller-class"></a>Canimationcontroller – třída

Implementuje řadič animace, který poskytuje centrální rozhraní pro vytváření a správu animací.

## <a name="syntax"></a>Syntaxe

```
class CAnimationController : public CObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAnimationController::CAnimationController](#canimationcontroller)|Vytvoří řadič animace.|
|[Canimationcontroller –:: ~ canimationcontroller –](#canimationcontroller__~canimationcontroller)|Destruktor. Volá se, když se likviduje objektu řadiče animace.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|Animace objektu přidá do skupiny, které patří do kontroleru animace.|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Klíčový snímek přidá do skupiny.|
|[CAnimationController::AnimateGroup](#animategroup)|Připraví skupiny ke spuštění animace a volitelně plány.|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Přetíženo. Volá se rozhraním vyčistit skupiny, když je naplánovaná animace.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|Přetíženo. Vytvoří klíčový snímek, který závisí na přechod a přidá ji do zadané skupiny.|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Nastaví nebo uvolní obslužné rutiny má volat při změně stavu Správce animace.|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Nastaví nebo uvolní obslužnou rutinu události časování a obslužné rutiny pro časování aktualizací.|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Nastaví nebo uvolní obslužná rutina porovnání priority volání za účelem určení, zda naplánované scénáře může být zrušena, dospělo k závěru, oříznut nebo komprimované.|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Nastaví nebo uvolní obslužnou rutinu události stavu a aktualizaci scénáře.|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Přetíženo. Vyhledá skupinu animace podle jeho scénáře.|
|[CAnimationController::FindAnimationObject](#findanimationobject)|Vyhledá objekt animace, který obsahuje proměnné zadané animace.|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Vrátí klíčový snímek, který označuje začátek scénáře.|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Poskytuje přístup k zapouzdřenému IUIAnimationManager objektu.|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Poskytuje přístup k zapouzdřenému IUIAnimationTimer objektu.|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Ukazatel na rozhraní IUIAnimationTransitionFactory nebo hodnota NULL, pokud vytvoření přechodu knihovny se nezdařilo.|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Poskytuje přístup k zapouzdřenému IUIAnimationTransitionLibrary objektu.|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Určuje, zda je alespoň jednu skupinu přehrávat animace.|
|[CAnimationController::IsValid](#isvalid)|Určuje, zda je řadič animace platný.|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Volá se rozhraním při změně hodnoty proměnné animace celé číslo.|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Volá se rozhraním v reakci na události StatusChanged ze Správce animace.|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Volá se rozhraním po dokončení aktualizace animace.|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Volá se rozhraním před zahájením aktualizace animace.|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Volá se rozhraním, když snímkovou frekvenci vykreslování animace klesne pod minimální žádoucí snímkovou frekvenci.|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Volá se rozhraním, se při změně hodnoty proměnné animace.|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Volá se rozhraním správné před naplánovaným animace.|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Volá se rozhraním, k řešení konfliktů při plánování.|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Volá se rozhraním, k řešení konfliktů při plánování.|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Volá se rozhraním, k řešení konfliktů při plánování.|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Volá se rozhraním, k řešení konfliktů při plánování.|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Volá se rozhraním při změně stavu scénáře.|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|Volá se rozhraním, když scénáře se aktualizovala.|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Odebere všechny skupiny animace z řadič animace.|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Odebere skupinu animace se zadaným ID z řadič animace.|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Animace objektu odeberte řadič animace.|
|[CAnimationController::RemoveTransitions](#removetransitions)|Odebere přechody z animace objektů, které patří do zadané skupiny.|
|[CAnimationController::ScheduleGroup](#schedulegroup)|Naplánuje animace.|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Vytvoří vztah mezi řadič animace a v okně.|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Přesměruje Správce animací aktualizovat hodnoty všechny proměnné animace.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Přetíženo. Pomocné rutiny, která vyčistí skupině.|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Volá se rozhraním, když právě byla plánována animace pro zadanou skupinu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Klíčový snímek, který reprezentuje začátek scénáře.|
|[CAnimationController::m_bIsValid](#m_bisvalid)|Určuje, zda je řadič animace platná nebo ne. Tento člen je nastavený na hodnotu FALSE, pokud aktuální operační systém nepodporuje rozhraní API animace Windows.|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Seznam skupin animace, které patří do tohoto kontroleru animace.|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Uchovává ukazatel na objekt modelu COM správce animace.|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Uchovává ukazatel na objekt modelu COM časovače animace.|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Ukazatel na související objektu CWnd, který může automaticky překreslení při změnu stavu Správce animace, nebo došlo k události update příspěvku. Může mít hodnotu NULL.|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Uchovává ukazatel na objekt Factory COM přechodu.|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Uchovává ukazatel na objekt knihovny COM přechodu.|

## <a name="remarks"></a>Poznámky

Canimationcontroller – třída je klíč třídy, která spravuje animace. Může vytvořit jeden nebo víc instancí řadič animace v aplikaci a volitelné připojení k objektu CWnd pomocí CAnimationController::SetRelatedWnd instance řadič animace. Toto připojení je potřeba WM_PAINT při odeslání zprávy do příslušné okno automaticky změnu stavu Správce animace nebo časovače animace se aktualizovala. Pokud nepovolíte tento vztah, musí ho překreslit okno, které zobrazí animace ručně. Za tímto účelem lze odvodit třídu z canimationcontroller – a přepsat OnAnimationManagerStatusChanged a/nebo OnAnimationTimerPostUpdate a zneplatnit jedno nebo více oken, pokud je to nezbytné.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="_dtorcanimationcontroller"></a>  Canimationcontroller –:: ~ canimationcontroller –

Destruktor. Volá se, když se likviduje objektu řadiče animace.

```
virtual ~CAnimationController(void);
```

##  <a name="addanimationobject"></a>  CAnimationController::AddAnimationObject

Animace objektu přidá do skupiny, které patří do kontroleru animace.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Parametry

*odstraněný objekt*<br/>
Ukazatel na objekt animace.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na existující nebo nové skupiny animace, kde byl odstraněný objekt přidán Pokud funkce uspěje; Hodnota NULL, pokud odstraněný objekt již byla přidána do skupiny, který patří do jiného řadič animace.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem přidání objektu animace řadič animace. Objekt se přidají do skupiny podle ID objektu skupiny (viz CAnimationBaseObject::SetID). Řadič animace vytvoří novou skupinu, pokud je první objekt, který přidává se zadaným ID skupiny. Animace objektu lze přidat pouze řadič animace. Pokud je potřeba přidat k jinému objektu, nejprve volejte RemoveAnimationObject. Při volání ID sady se nové ID skupiny pro objekt, který již byla přidána do skupiny, objekt bude odebrán ze staré skupiny a přidat do jiné skupiny s určeným ID.

##  <a name="addkeyframetogroup"></a>  CAnimationController::AddKeyframeToGroup

Klíčový snímek přidá do skupiny.

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID skupiny.

*pKeyframe*<br/>
Ukazatel na klíčový snímek.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud funkce uspěje; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Obvykle není nutné volat tuto metodu, místo toho použijte CAnimationController::CreateKeyframe vytvoří a automaticky přidá do skupiny vytvořené klíčový snímek.

##  <a name="animategroup"></a>  CAnimationController::AnimateGroup

Připraví skupiny ke spuštění animace a volitelně plány.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID skupiny.

*bScheduleNow*<br/>
Určuje, jestli se má spustit hned animace.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud animace byla úspěšně naplánovat a spustit.

### <a name="remarks"></a>Poznámky

Tato metoda ve skutečnosti provádí scénáře vytváření, přidávání proměnné animace, použití přechody a nastavování klíčových snímků. Je možné ke zpoždění plánování bScheduleNow nastavíte na hodnotu FALSE. V tomto případě zadaná skupina bude obsahovat storyboardem, který je nastavený pro animaci. V tomto okamžiku můžete nastavit události pro scénáře a animace proměnné. Když skutečně potřebujete ke spuštění animace volání CAnimationController::ScheduleGroup.

##  <a name="canimationcontroller"></a>  CAnimationController::CAnimationController

Vytvoří řadič animace.

```
CAnimationController(void);
```

##  <a name="cleanupgroup"></a>  CAnimationController::CleanUpGroup

Volá se rozhraním vyčistit skupiny, když je naplánovaná animace.

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID skupiny.

*pGroup*<br/>
Ukazatel na skupiny animace k vyčištění.

### <a name="remarks"></a>Poznámky

Tato metoda odebere všechny přechody a klíčové snímky ze zadané skupiny, protože nejsou relevantní, poté, co je naplánovaná animace.

##  <a name="createkeyframe"></a>  CAnimationController::CreateKeyframe

Vytvoří klíčový snímek, který závisí na přechod a přidá ji do zadané skupiny.

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

*nGroupID*<br/>
Určuje ID skupiny, pro který je vytvořen klíčový snímek.

*pTransition*<br/>
Ukazatel na přechod. Klíčový snímek bude vložen do scénáře po tomto přechodu.

*pKeyframe*<br/>
Ukazatel na základní klíčový snímek pro tento klíčový snímek.

*Posun*<br/>
Posun v řádu sekund z určeného pKeyframe základní klíčový snímek.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený klíčový snímek, pokud je funkce úspěšná.

### <a name="remarks"></a>Poznámky

Můžete ukládat vrácenému ukazateli a základní ostatních klíčových snímků na nově vytvořený klíčový snímek (viz druhé přetížení). Je možné začít přechody na klíčové snímky – viz CBaseTransition::SetKeyframes. Není nutné odstranit klíčové snímky vytvořené tímto způsobem, protože se odstraní automaticky podle skupin animace. Buďte opatrní při vytváření klíčových snímků na základě jiné klíčové snímky a přechody a vyhnout se cyklické odkazy.

##  <a name="enableanimationmanagerevent"></a>  CAnimationController::EnableAnimationManagerEvent

Nastaví nebo uvolní obslužné rutiny má volat při změně stavu Správce animace.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda nastavení nebo uvolnění obslužnou rutinu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud obslužná rutina byla úspěšně nastavena nebo vydání.

### <a name="remarks"></a>Poznámky

Pokud je nastavena obslužná rutina (povoleno) animace Windows volá OnAnimationManagerStatusChanged při změně stavu Správce animace.

##  <a name="enableanimationtimereventhandler"></a>  CAnimationController::EnableAnimationTimerEventHandler

Nastaví nebo uvolní obslužnou rutinu události časování a obslužné rutiny pro časování aktualizací.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda nastavení nebo uvolnění obslužné rutiny.

*idleBehavior*<br/>
Určuje chování při nečinnosti o obslužnou rutinu aktualizace časovače.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byly obslužné rutiny úspěšně nastavit nebo vydání; FALSE, pokud tato metoda je volána pro podruhé stisknutým obslužných rutin, nebo pokud jakýkoli jiný dojde k chybě.

### <a name="remarks"></a>Poznámky

Když obslužné rutiny jsou nastaveny (povoleno) volání API animace Windows OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate OnRenderingTooSlow metody. Je potřeba povolit animace časovače povolit scénáře API animace Windows update. Jinak budete muset volat CAnimationController::UpdateAnimationManager, aby bylo možné směrovat animace správce k aktualizaci hodnoty všechny proměnné animace.

##  <a name="enableprioritycomparisonhandler"></a>  CAnimationController::EnablePriorityComparisonHandler

Nastaví nebo uvolní obslužná rutina porovnání priority volání za účelem určení, zda naplánované scénáře může být zrušena, dospělo k závěru, oříznut nebo komprimované.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Parametry

*dwHandlerType*<br/>
Kombinace UI_ANIMATION_PHT_ příznaky (viz poznámky), která určuje, jaké rutiny k nastavení nebo uvolnění.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud obslužná rutina byla úspěšně nastavena nebo vydání.

### <a name="remarks"></a>Poznámky

Pokud je nastavena obslužná rutina (povoleno) animace Windows volá následující virtuální metody v závislosti na dwHandlerType: OnHasPriorityCancel OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler může obsahovat kombinaci následující příznaky: UI_ANIMATION_PHT_NONE – verze všechny obslužné rutiny UI_ANIMATION_PHT_CANCEL - nastavit Storno nastavena obslužná rutina porovnání UI_ANIMATION_PHT_CONCLUDE – obslužná rutina porovnání Conclude UI_ANIMATION_PHT_COMPRESS – nastavení Obslužná rutina porovnání komprimovat UI_ANIMATION_PHT_TRIM - nastavování obslužné rutiny uvolnění dočasné paměti porovnání UI_ANIMATION_PHT_CANCEL_REMOVE - odebrat porovnání obslužný podproces příkazu Storno UI_ANIMATION_PHT_CONCLUDE_REMOVE - odebrat obslužnou rutinu porovnání Conclude UI_ANIMATION_PHT_COMPRESS_ Odebrat – odebrat obslužnou rutinu porovnání komprimovat UI_ANIMATION_PHT_TRIM_REMOVE - Trim porovnání odebrat obslužnou rutinu

##  <a name="enablestoryboardeventhandler"></a>  CAnimationController::EnableStoryboardEventHandler

Nastaví nebo uvolní obslužnou rutinu události stavu a aktualizaci scénáře.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID skupiny.

*bEnable*<br/>
Určuje, zda nastavení nebo uvolnění obslužnou rutinu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud obslužná rutina byla úspěšně nastavena nebo vydání; FALSE, pokud skupina zadaná animace teď nalezena nebo nebyla inicializována animace pro zadanou skupinu a jeho vnitřní scénář má hodnotu NULL.

### <a name="remarks"></a>Poznámky

Pokud je nastavena obslužná rutina zavolá API animace (povoleno) Windows OnStoryboardStatusChanges a OnStoryboardUpdated virtuální metody. Obslužná rutina musí být nastavena po CAnimationController::Animate byla volána pro zadaný animace skupinu, protože tak vzniká zapouzdřený objekt IUIAnimationStoryboard.

##  <a name="findanimationgroup"></a>  CAnimationController::FindAnimationGroup

Vyhledá skupinu animace pomocí jeho ID skupiny.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje, ID skupiny.

*pStoryboard*<br/>
Ukazatel na scénáře.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na animace skupiny nebo hodnota NULL, pokud skupina se zadaným ID nebyla nalezena.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete najít skupinu animace v době běhu. Skupina je vytvořen a přidán do vnitřní seznam skupin animace při první animace objekt s ID konkrétní skupiny se přidává na řadič animace.

##  <a name="findanimationobject"></a>  CAnimationController::FindAnimationObject

Vyhledá objekt animace, který obsahuje proměnné zadané animace.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>Parametry

*pVariable*<br/>
Ukazatel na proměnnou animace.

*ppObject*<br/>
Výstup. Obsahuje ukazatel na objekt animace nebo hodnota NULL.

*ppGroup*<br/>
Výstup. Obsahuje ukazatel na animace skupiny, který obsahuje objekt animace, nebo hodnota NULL.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byl nalezen objekt; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Volá se z obslužné rutiny událostí, když je potřeba najít objekt animace z příchozí proměnné animace.

##  <a name="g_keyframestoryboardstart"></a>  CAnimationController::gkeyframeStoryboardStart

Klíčový snímek, který reprezentuje začátek scénáře.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>  CAnimationController::GetKeyframeStoryboardStart

Vrátí klíčový snímek, který označuje začátek scénáře.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na základní klíčový snímek, který označuje začátek scénáře.

### <a name="remarks"></a>Poznámky

Získáte tuto klíčový snímek na základní žádné další klíčové snímky nebo přechody na okamžik v čase, při spuštění scénáře.

##  <a name="getuianimationmanager"></a>  CAnimationController::GetUIAnimationManager

Poskytuje přístup k zapouzdřenému IUIAnimationManager objektu.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IUIAnimationManager nebo hodnota NULL, pokud vytvoření správce animace se nezdařilo.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje Windows API animace, tato metoda vrátí hodnotu NULL a pak všechny následné volání na CAnimationController::IsValid vracet hodnotu FALSE. Budete muset přístup IUIAnimationManager pro volání obsažených metod rozhraní, které nejsou zabalené službou řadič animace.

##  <a name="getuianimationtimer"></a>  CAnimationController::GetUIAnimationTimer

Poskytuje přístup k zapouzdřenému IUIAnimationTimer objektu.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IUIAnimationTimer nebo hodnota NULL, pokud vytvoření časovače animace se nezdařilo.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje Windows API animace, tato metoda vrátí hodnotu NULL a pak všechny následné volání na CAnimationController::IsValid vracet hodnotu FALSE.

##  <a name="getuitransitionfactory"></a>  CAnimationController::GetUITransitionFactory

Ukazatel na rozhraní IUIAnimationTransitionFactory nebo hodnota NULL, pokud vytvoření přechodu knihovny se nezdařilo.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na IUIAnimationTransitionFactory nebo hodnota NULL, pokud vytvoření objektu pro vytváření přechodu se nezdařilo.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje Windows API animace, tato metoda vrátí hodnotu NULL a pak všechny následné volání na CAnimationController::IsValid vracet hodnotu FALSE.

##  <a name="getuitransitionlibrary"></a>  CAnimationController::GetUITransitionLibrary

Poskytuje přístup k zapouzdřenému IUIAnimationTransitionLibrary objektu.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IUIAnimationTransitionLibrary nebo hodnota NULL, pokud vytvoření přechodu knihovny se nezdařilo.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje Windows API animace, tato metoda vrátí hodnotu NULL a pak všechny následné volání na CAnimationController::IsValid vracet hodnotu FALSE.

##  <a name="isanimationinprogress"></a>  CAnimationController::IsAnimationInProgress

Určuje, zda je alespoň jednu skupinu přehrávat animace.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je pro tento řadič animace; probíhá animace v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Kontroly stavu Správce animace a vrátí TRUE, pokud je stav UI_ANIMATION_MANAGER_BUSY.

##  <a name="isvalid"></a>  CAnimationController::IsValid

Určuje, zda je řadič animace platný.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je platná řadič animace v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu FALSE, pouze pokud API animace Windows nepodporuje aktuální operačního systému a zřízení správce animace se nezdařilo, protože není zaregistrován. Je třeba volat GetUIAnimationManager alespoň jednou po inicializaci knihovny modelu COM způsobit nastavení tohoto příznaku.

##  <a name="m_bisvalid"></a>  CAnimationController::m_bIsValid

Určuje, zda je řadič animace platná nebo ne. Tento člen je nastavený na hodnotu FALSE, pokud aktuální operační systém nepodporuje rozhraní API animace Windows.

```
BOOL m_bIsValid;
```

##  <a name="m_lstanimationgroups"></a>  CAnimationController::m_lstAnimationGroups

Seznam skupin animace, které patří do tohoto kontroleru animace.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

##  <a name="m_panimationmanager"></a>  CAnimationController::m_pAnimationManager

Uchovává ukazatel na objekt modelu COM správce animace.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>  CAnimationController::m_pAnimationTimer

Uchovává ukazatel na objekt modelu COM časovače animace.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>  CAnimationController::m_pRelatedWnd

Ukazatel na související objektu CWnd, který může automaticky překreslení při změnu stavu Správce animace, nebo došlo k události update příspěvku. Může mít hodnotu NULL.

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory

Uchovává ukazatel na objekt Factory COM přechodu.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>  CAnimationController::m_pTransitionLibrary

Uchovává ukazatel na objekt knihovny COM přechodu.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>  CAnimationController::OnAfterSchedule

Volá se rozhraním, když právě byla plánována animace pro zadanou skupinu.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Ukazatel na skupinu animace, která má naplánované.

### <a name="remarks"></a>Poznámky

Výchozí implementace odebere zadané skupině klíčové snímky a změní z proměnné animace, které patří do zadané skupiny. Můžete přepsat v odvozené třídě žádné další akce na plán animace.

##  <a name="onanimationintegervaluechanged"></a>  CAnimationController::OnAnimationIntegerValueChanged

Volá se rozhraním při změně hodnoty proměnné animace celé číslo.

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Ukazatel na skupinu animace, která obsahuje objekt animace, jehož hodnota se změnila.

*odstraněný objekt*<br/>
Ukazatel na objekt animace, který obsahuje proměnnou animace, jehož hodnota se změnila.

*Proměnná*<br/>
Ukazatel na proměnnou animace.

*newValue*<br/>
Určuje novou hodnotu.

*prevValue*<br/>
Určuje předchozí hodnotu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte s názvem pro konkrétní animace proměnné nebo objektu animace EnableIntegerValueChangedEvent události proměnné animace. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci.

##  <a name="onanimationmanagerstatuschanged"></a>  CAnimationController::OnAnimationManagerStatusChanged

Volá se rozhraním v reakci na události StatusChanged ze Správce animace.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*newStatus*<br/>
Nové stavu Správce animace.

*previousStatus*<br/>
Předchozí stavu Správce animace.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události Správce animace s EnableAnimationManagerEvent. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci. Výchozí implementace aktualizuje související okno, pokud byl nastaven s SetRelatedWnd.

##  <a name="onanimationtimerpostupdate"></a>  CAnimationController::OnAnimationTimerPostUpdate

Volá se rozhraním po dokončení aktualizace animace.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte pomocí EnableAnimationTimerEventHandler obslužné rutiny události časovače. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci.

##  <a name="onanimationtimerpreupdate"></a>  CAnimationController::OnAnimationTimerPreUpdate

Volá se rozhraním před zahájením aktualizace animace.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte pomocí EnableAnimationTimerEventHandler obslužné rutiny události časovače. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci.

##  <a name="onanimationtimerrenderingtooslow"></a>  CAnimationController::OnAnimationTimerRenderingTooSlow

Volá se rozhraním, když snímkovou frekvenci vykreslování animace klesne pod minimální žádoucí snímkovou frekvenci.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Parametry

*snímků za sekundu*<br/>
Aktuální frekvenci snímků v snímků za sekundu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte pomocí EnableAnimationTimerEventHandler obslužné rutiny události časovače. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci. Minimální kmitočet žádoucí určena voláním IUIAnimationTimer::SetFrameRateThreshold.

##  <a name="onanimationvaluechanged"></a>  CAnimationController::OnAnimationValueChanged

Volá se rozhraním, se při změně hodnoty proměnné animace.

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Ukazatel na skupinu animace, která obsahuje objekt animace, jehož hodnota se změnila.

*odstraněný objekt*<br/>
Ukazatel na objekt animace, který obsahuje proměnnou animace, jehož hodnota se změnila.

*Proměnná*<br/>
Ukazatel na proměnnou animace.

*newValue*<br/>
Určuje novou hodnotu.

*prevValue*<br/>
Určuje předchozí hodnotu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte s názvem pro konkrétní animace proměnné nebo objektu animace EnableValueChangedEvent události proměnné animace. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci.

##  <a name="onbeforeanimationstart"></a>  CAnimationController::OnBeforeAnimationStart

Volá se rozhraním správné před naplánovaným animace.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Ukazatel na skupinu animace, jehož animaci je začít.

### <a name="remarks"></a>Poznámky

Toto volání se směruje na související CWnd a je možné přepsat v odvozené třídě provádět žádné další akce před spuštěním animace softwaru pro zadané skupiny.

##  <a name="onhasprioritycancel"></a>  CAnimationController::OnHasPriorityCancel

Volá se rozhraním, k řešení konfliktů při plánování.

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Skupině, vlastnící aktuálně naplánované scénáře.

*pGroupNew*<br/>
Skupině, vlastnící nový scénář, který je v konfliktu plánování s naplánovanou scénáře vlastněné pGroupScheduled.

*priorityEffect*<br/>
Nežádoucí vliv na pGroupNew Pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měl vrací TRUE, pokud scénář vlastněné pGroupNew má prioritu. By měl vrátit hodnotu FALSE, pokud scénář vlastněné pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte Priorita porovnávání události pomocí CAnimationController::EnablePriorityComparisonHandler a zadejte UI_ANIMATION_PHT_CANCEL. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci. Dokumentace k API animace Windows ke čtení pro další informace o [konflikt správu](https://msdn.microsoft.com/library/dd371759).

##  <a name="onhasprioritycompress"></a>  CAnimationController::OnHasPriorityCompress

Volá se rozhraním, k řešení konfliktů při plánování.

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Skupině, vlastnící aktuálně naplánované scénáře.

*pGroupNew*<br/>
Skupině, vlastnící nový scénář, který je v konfliktu plánování s naplánovanou scénáře vlastněné pGroupScheduled.

*priorityEffect*<br/>
Nežádoucí vliv na pGroupNew Pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měl vrací TRUE, pokud scénář vlastněné pGroupNew má prioritu. By měl vrátit hodnotu FALSE, pokud scénář vlastněné pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte Priorita porovnávání události pomocí CAnimationController::EnablePriorityComparisonHandler a zadejte UI_ANIMATION_PHT_COMPRESS. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci. Dokumentace k API animace Windows ke čtení pro další informace o [konflikt správu](https://msdn.microsoft.com/library/dd371759).

##  <a name="onhaspriorityconclude"></a>  CAnimationController::OnHasPriorityConclude

Volá se rozhraním, k řešení konfliktů při plánování.

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Skupině, vlastnící aktuálně naplánované scénáře.

*pGroupNew*<br/>
Skupině, vlastnící nový scénář, který je v konfliktu plánování s naplánovanou scénáře vlastněné pGroupScheduled.

*priorityEffect*<br/>
Nežádoucí vliv na pGroupNew Pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měl vrací TRUE, pokud scénář vlastněné pGroupNew má prioritu. By měl vrátit hodnotu FALSE, pokud scénář vlastněné pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte Priorita porovnávání události pomocí CAnimationController::EnablePriorityComparisonHandler a zadejte UI_ANIMATION_PHT_CONCLUDE. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci. Dokumentace k API animace Windows ke čtení pro další informace o [konflikt správu](https://msdn.microsoft.com/library/dd371759).

##  <a name="onhasprioritytrim"></a>  CAnimationController::OnHasPriorityTrim

Volá se rozhraním, k řešení konfliktů při plánování.

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Skupině, vlastnící aktuálně naplánované scénáře.

*pGroupNew*<br/>
Skupině, vlastnící nový scénář, který je v konfliktu plánování s naplánovanou scénáře vlastněné pGroupScheduled.

*priorityEffect*<br/>
Nežádoucí vliv na pGroupNew Pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měl vrací TRUE, pokud scénář vlastněné pGroupNew má prioritu. By měl vrátit hodnotu FALSE, pokud scénář vlastněné pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte Priorita porovnávání události pomocí CAnimationController::EnablePriorityComparisonHandler a zadejte UI_ANIMATION_PHT_TRIM. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci. Dokumentace k API animace Windows ke čtení pro další informace o [konflikt správu](https://msdn.microsoft.com/library/dd371759).

##  <a name="onstoryboardstatuschanged"></a>  CAnimationController::OnStoryboardStatusChanged

Volá se rozhraním při změně stavu scénáře.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Ukazatel na skupinu animace, který vlastní scénáře stavem se změnila.

*newStatus*<br/>
Určuje nový stav.

*previousStatus*<br/>
Určuje předchozí stav.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte pomocí CAnimationController::EnableStoryboardEventHandler události scénáře. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci.

##  <a name="onstoryboardupdated"></a>  CAnimationController::OnStoryboardUpdated

Volá se rozhraním, když scénáře se aktualizovala.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Ukazatel na skupinu, která vlastní scénáře.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte pomocí CAnimationController::EnableStoryboardEventHandler události scénáře. Ho bude možné přepsat v odvozené třídě akce specifické pro aplikaci.

##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups

Odebere všechny skupiny animace z řadič animace.

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Poznámky

Všechny skupiny budou odstraněna, ukazatele, pokud je uložen na úrovni aplikace, musí ukončit platnost. Pokud CAnimationGroup::m_bAutodestroyAnimationObjects pro skupinu odstranit hodnotu TRUE, odstraní se všechny objekty animace, které patří do této skupiny; v opačném případě jejich odkazů na rodičovský ovladač animace se nastaví na hodnotu NULL a je možné je přidat k jinému.

##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup

Odebere skupinu animace se zadaným ID z řadič animace.

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID animace skupiny.

### <a name="remarks"></a>Poznámky

Tato metoda Odebere skupinu animace ze seznamu interní skupin a odstraní ji, pokud jste si uložili ukazatel do této skupiny animace, se musí být nezneplatnil. Pokud CAnimationGroup::m_bAutodestroyAnimationObjects hodnotu TRUE, odstraní se všechny objekty animace, které patří do této skupiny; v opačném případě jejich odkazů na rodičovský ovladač animace se nastaví na hodnotu NULL a je možné je přidat k jinému.

##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject

Animace objektu odeberte řadič animace.

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Parametry

*odstraněný objekt*<br/>
Ukazatel na objekt animace.

*bNoDelete*<br/>
Pokud tento parametr má hodnotu TRUE objektu se neodstraní po odebrání.

### <a name="remarks"></a>Poznámky

Odebere objekt animace z řadič animace a animace skupiny. Voláním této funkce, pokud konkrétního objektu by neměla už animovat, nebo pokud potřebujete přesunout objekt na jiný řadič animace. Za posledních případu bNoDelete musí být nastavena na možnost PRAVDA.

##  <a name="removetransitions"></a>  CAnimationController::RemoveTransitions

Odebere přechody z animace objektů, které patří do zadané skupiny.

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID skupiny.

### <a name="remarks"></a>Poznámky

Skupina cyklickému své objekty animace a volá ClearTransitions(FALSE) pro každý objekt animace. Tato metoda je volána rozhraním, poté, co je naplánovaná animace.

##  <a name="schedulegroup"></a>  CAnimationController::ScheduleGroup

Naplánuje animace.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID skupiny plánování animace.

*čas*<br/>
Určuje čas, naplánovat.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se úspěšně naplánovala animace. FALSE, pokud nebyl vytvořen scénáře nebo dojde k chybě.

### <a name="remarks"></a>Poznámky

AnimateGroup musí volat s parametrem bScheduleNow nastavena na hodnotu FALSE předchozí schedulegroup –. Můžete zadat čas požadovaného animace získané z IUIAnimationTimer::GetTime. Pokud parametr času je 0,0, animace naplánován pro aktuální čas.

##  <a name="setrelatedwnd"></a>  CAnimationController::SetRelatedWnd

Vytvoří vztah mezi řadič animace a v okně.

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na objekt okna nastavení.

### <a name="remarks"></a>Poznámky

Pokud je nastavena souvisejícího objektu CWnd, řadič animace automaticky ho mohli aktualizovat (Odeslat zprávu WM_PAINT) při změnu stavu Správce animace nebo došlo k události časovače příspěvek aktualizace.

##  <a name="updateanimationmanager"></a>  CAnimationController::UpdateAnimationManager

Přesměruje Správce animací aktualizovat hodnoty všechny proměnné animace.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Poznámky

Volání funkce, které tato metoda přejde Správce animací na aktuální čas, mění stav scénáře podle potřeby a aktualizuje všechny proměnné animace příslušné interpolovaných hodnoty. Interně tato metoda volá IUIAnimationTimer::GetTime(timeNow) a IUIAnimationManager::Update(timeNow). Potlačí tuto metodu v odvozené třídě k přizpůsobení tohoto chování.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
