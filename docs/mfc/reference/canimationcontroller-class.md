---
title: CAnimationController – třída
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
ms.openlocfilehash: 9039d44d9ef36a47c11b3ecaddf232ad427727c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507642"
---
# <a name="canimationcontroller-class"></a>CAnimationController – třída

Implementuje kontroler animace, který poskytuje centrální rozhraní pro vytváření a správu animací.

## <a name="syntax"></a>Syntaxe

```
class CAnimationController : public CObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAnimationController::CAnimationController](#canimationcontroller)|Vytvoří kontroler animace.|
|[CAnimationController:: ~ CAnimationController](#_dtorcanimationcontroller)|Destruktor. Volá se při zničení objektu animačního kontroleru.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|Přidá objekt animace do skupiny, která patří k řadiči animace.|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Přidá klíčový snímek do skupiny.|
|[CAnimationController::AnimateGroup](#animategroup)|Připraví skupinu na spuštění animace a volitelně ji naplánuje.|
|[CAnimationController:: CleanUp](#cleanupgroup)|Přetíženo. Volá se rozhraním, aby se vyčistila skupina, když se naplánovala animace.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|Přetíženo. Vytvoří klíčový snímek, který závisí na přechodu a přidá ho do zadané skupiny.|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Nastaví nebo uvolní obslužnou rutinu, která má být volána, když se změní stav manažera animace.|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Nastaví nebo uvolní obslužnou rutinu pro události časování a obslužné rutiny pro aktualizace časování.|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Nastaví nebo uvolní obslužnou rutinu porovnání priority, která má zavolat, aby bylo možné určit, zda lze plánovaný scénář zrušit, uzavřít, oříznout nebo komprimovat.|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Nastaví nebo uvolní obslužnou rutinu pro stav scénáře a události aktualizace.|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Přetíženo. Vyhledá animační skupinu podle scénáře.|
|[CAnimationController::FindAnimationObject](#findanimationobject)|Najde objekt animace obsahující zadanou proměnnou animace.|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Vrátí klíčový snímek, který identifikuje začátek scénáře.|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Poskytuje přístup k zapouzdřenému objektu IUIAnimationManager.|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Poskytuje přístup k zapouzdřenému objektu IUIAnimationTimer.|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Ukazatel na rozhraní IUIAnimationTransitionFactory nebo NULL, pokud se nepovedlo vytvořit knihovnu přechodu.|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Poskytuje přístup k zapouzdřenému objektu IUIAnimationTransitionLibrary.|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Určuje, zda nejméně jedna skupina přehrává animaci.|
|[CAnimationController::IsValid](#isvalid)|Informuje o tom, zda je řadič animace platný.|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Volá se rozhraním, když se změnila celočíselná hodnota proměnné animace.|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Volá se rozhraním v reakci na událost StatusChanged ze Správce animací.|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Volá se rozhraním po dokončení aktualizace animace.|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Volá se rozhraním, než začne aktualizace animace.|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Volá se rozhraním, když míra vykreslování snímků pro animaci klesne pod minimální požadovanou snímkovou sazbu.|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Volá se rozhraním, když se změnila hodnota proměnné animace.|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Volá se rozhraním přímo předtím, než se naplánuje animace.|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Volá se rozhraním, aby se vyřešily konflikty plánování.|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Volá se rozhraním, aby se vyřešily konflikty plánování.|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Volá se rozhraním, aby se vyřešily konflikty plánování.|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Volá se rozhraním, aby se vyřešily konflikty plánování.|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Volá se rozhraním, když se změní stav scénáře.|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|Volá se rozhraním, když se aktualizuje scénář.|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Odebere všechny animační skupiny z kontroleru animací.|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Odebere ze kontroleru animací skupinu animace se zadaným ID.|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Odebere objekt animace z kontroleru animací.|
|[CAnimationController::RemoveTransitions](#removetransitions)|Odebere přechody z objektů animace, které patří do zadané skupiny.|
|[CAnimationController::ScheduleGroup](#schedulegroup)|Naplánuje animaci.|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Vytvoří vztah mezi animačním kontrolérem a oknem.|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Nasměruje Správce animací, aby aktualizoval hodnoty všech proměnných animace.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CAnimationController:: CleanUp](#cleanupgroup)|Přetíženo. Pomocná skupina, která vyčistí skupinu.|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Volá se rozhraním, když se právě naplánovala animace pro zadanou skupinu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Klíčový snímek, který představuje začátek scénáře.|
|[CAnimationController::m_bIsValid](#m_bisvalid)|Určuje, jestli je kontroler animace platný, nebo ne. Tento člen je nastaven na hodnotu FALSE, pokud aktuální operační systém nepodporuje rozhraní API Windows Animation.|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Seznam skupin animací, které patří k tomuto řadiči animací|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Ukládá ukazatel na objekt modelu COM Správce animací.|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Ukládá ukazatel na objekt modelu COM časovače animace.|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Ukazatel na související objekt CWnd, který lze automaticky překreslit při změně stavu správce animace nebo při události po aktualizaci. Může mít hodnotu NULL.|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Ukládá ukazatel na převod objektu COM továrny.|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Ukládá ukazatel na objekt modelu COM knihovny přechodu.|

## <a name="remarks"></a>Poznámky

Třída CAnimationController je klíčovou třídou, která spravuje animace. V aplikaci můžete vytvořit jednu nebo více instancí animačního kontroleru a volitelně připojit instanci animačního kontroleru k objektu CWnd pomocí CAnimationController:: SetRelatedWnd. Toto připojení je potřeba k automatickému posílání zpráv WM_PAINT do příslušného okna, když se změní stav manažera animace nebo když se aktualizuje časovač animace. Pokud tento vztah nepovolíte, musíte znovu nakreslit okno, které zobrazí animaci ručně. Pro tento účel můžete odvodit třídu z CAnimationController a přepsat OnAnimationManagerStatusChanged a/nebo OnAnimationTimerPostUpdate a v případě potřeby zrušit platnost jednoho nebo více oken.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller. h

##  <a name="_dtorcanimationcontroller"></a>CAnimationController:: ~ CAnimationController

Destruktor. Volá se při zničení objektu animačního kontroleru.

```
virtual ~CAnimationController(void);
```

##  <a name="addanimationobject"></a>CAnimationController::AddAnimationObject

Přidá objekt animace do skupiny, která patří k řadiči animace.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Parametry

*pObject*<br/>
Ukazatel na objekt animace.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na existující nebo novou skupinu animace, do které byl přidán pObject, pokud je funkce úspěšná; Hodnota NULL, pokud již byla pObject přidána do skupiny, která patří k jinému řadiči animace.

### <a name="remarks"></a>Poznámky

Voláním této metody přidáte objekt animace do kontroleru animací. Objekt se přidá do skupiny podle identifikátoru skupiny objektu (viz CAnimationBaseObject:: SetID). Řadič animace vytvoří novou skupinu, pokud se jedná o první objekt přidaný se zadaným identifikátorem skupiny. Objekt animace lze přidat pouze do jednoho řadiče animace. Pokud potřebujete přidat objekt na jiný kontroler, zavolejte RemoveAnimationObject jako první. Pokud voláte SetID s novým identifikátorem skupiny pro objekt, který již byl přidán do skupiny, objekt bude odebrán z původní skupiny a přidán do jiné skupiny se zadaným ID.

##  <a name="addkeyframetogroup"></a>CAnimationController::AddKeyframeToGroup

Přidá klíčový snímek do skupiny.

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

TRUE, pokud je funkce úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Obvykle nemusíte volat tuto metodu, místo toho použijte CAnimationController:: CreateKeyframe, která vytvoří a přidá automaticky vytvořený klíčový snímek do skupiny.

##  <a name="animategroup"></a>CAnimationController:: Animate

Připraví skupinu na spuštění animace a volitelně ji naplánuje.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje identifikátor GroupID.

*bScheduleNow*<br/>
Určuje, jestli se má okamžitě spustit animace.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se animace úspěšně naplánovala a spustila.

### <a name="remarks"></a>Poznámky

Tato metoda provádí skutečnou práci při vytváření scénáře, přidávání proměnných animace, použití přechodů a nastavení klíčových snímků. Je možné zpozdit plánování, pokud nastavíte bScheduleNow na FALSE. V tomto případě bude mít zadaná skupina scénář, který je nastavený pro animaci. V tomto okamžiku můžete nastavit události pro proměnné scénáře a animace. Pokud skutečně potřebujete spustit volání animace CAnimationController:: Schedule.

##  <a name="canimationcontroller"></a>CAnimationController::CAnimationController

Vytvoří kontroler animace.

```
CAnimationController(void);
```

##  <a name="cleanupgroup"></a>CAnimationController:: CleanUp

Volá se rozhraním, aby se vyčistila skupina, když se naplánovala animace.

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje identifikátor GroupID.

*pGroup*<br/>
Ukazatel na skupinu animace, která se má vyčistit

### <a name="remarks"></a>Poznámky

Tato metoda odebere všechny přechody a klíčové snímky ze zadané skupiny, protože nejsou relevantní po naplánování animace.

##  <a name="createkeyframe"></a>CAnimationController::CreateKeyframe

Vytvoří klíčový snímek, který závisí na přechodu a přidá ho do zadané skupiny.

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
Určuje ID skupiny, pro který se vytvoří klíčový snímek.

*pTransition*<br/>
Ukazatel na přechod. Klíčový snímek se po tomto přechodu vloží do scénáře.

*pKeyframe*<br/>
Ukazatel na základní klíčový snímek pro tento klíčový snímek.

*polohy*<br/>
Posun v sekundách od základního klíčového snímku zadaného parametrem pKeyframe.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený klíčový snímek, pokud je funkce úspěšná.

### <a name="remarks"></a>Poznámky

Vrácený ukazatel a základní další klíčové snímky můžete uložit do nově vytvořeného klíčového snímku (viz druhé přetížení). Je možné začít přechody na klíčové snímky – viz CBaseTransition:: SetKeyframes. Nemusíte odstraňovat klíčové snímky vytvořené tímto způsobem, protože jsou automaticky odstraněny pomocí skupin animací. Buďte opatrní při vytváření klíčových snímků na základě jiných klíčových snímků a přechodů a vyhněte se cyklickým odkazům.

##  <a name="enableanimationmanagerevent"></a>CAnimationController::EnableAnimationManagerEvent

Nastaví nebo uvolní obslužnou rutinu, která má být volána, když se změní stav manažera animace.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda má být obslužná rutina nastavena nebo vydána.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byla obslužná rutina úspěšně nastavena nebo vydána.

### <a name="remarks"></a>Poznámky

Když je nastavena obslužná rutina (Enabled), volání animace systému Windows OnAnimationManagerStatusChanged při změně stavu správce animace.

##  <a name="enableanimationtimereventhandler"></a>CAnimationController::EnableAnimationTimerEventHandler

Nastaví nebo uvolní obslužnou rutinu pro události časování a obslužné rutiny pro aktualizace časování.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda mají být obslužné rutiny nastaveny nebo vydány.

*idleBehavior*<br/>
Určuje chování při nečinnosti obslužné rutiny aktualizace časovače.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byly obslužné rutiny úspěšně nastaveny nebo vydány; FALSE, pokud je tato metoda volána pro druhý čas, aniž by nejprve uvolnila obslužné rutiny, nebo pokud dojde k jakékoli jiné chybě.

### <a name="remarks"></a>Poznámky

Když jsou obslužné rutiny nastavené (povolené), rozhraní API pro animace systému Windows volá metody OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate, OnRenderingTooSlow. Pokud chcete povolit scénáře aktualizace rozhraní API pro animaci Windows, musíte povolit časovače animací. Jinak budete muset volat CAnimationController:: UpdateAnimationManager, aby bylo možné nasměrovat Správce animací, aby aktualizoval hodnoty všech proměnných animace.

##  <a name="enableprioritycomparisonhandler"></a>CAnimationController::EnablePriorityComparisonHandler

Nastaví nebo uvolní obslužnou rutinu porovnání priority, která má zavolat, aby bylo možné určit, zda lze plánovaný scénář zrušit, uzavřít, oříznout nebo komprimovat.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Parametry

*dwHandlerType*<br/>
Kombinace příznaků UI_ANIMATION_PHT_ (viz poznámky), které určují obslužné rutiny pro nastavení nebo vydání.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byla obslužná rutina úspěšně nastavena nebo vydána.

### <a name="remarks"></a>Poznámky

Když je nastavená obslužná rutina (Enabled), zavolá animace Windows následující virtuální metody v závislosti na dwHandlerType: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler může být kombinací následujících příznaků: UI_ANIMATION_PHT_NONE – vydání všech obslužných rutin UI_ANIMATION_PHT_CANCEL – nastavte zrušit porovnávací popisovač UI_ANIMATION_PHT_CONCLUDE-set dokončit porovnávací obslužnou rutinu UI_ANIMATION_PHT_COMPRESS-nastavit komprimaci porovnávací obslužné rutiny UI_ANIMATION_PHT_TRIM-set Střih obslužné rutiny porovnání UI_ANIMATION_PHT_CANCEL_REMOVE-odebrat zrušit porovnávací popisovač UI_ANIMATION_PHT_CONCLUDE_REMOVE-odebrat uzavírání porovnávacích obslužných rutin UI_ANIMATION_PHT_COMPRESS_REMOVE – odebrat popisovač porovnání komprese UI_ANIMATION_PHT _TRIM_REMOVE-odebrat popisovač porovnání pro ořezávání

##  <a name="enablestoryboardeventhandler"></a>CAnimationController::EnableStoryboardEventHandler

Nastaví nebo uvolní obslužnou rutinu pro stav scénáře a události aktualizace.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID skupiny.

*bEnable*<br/>
Určuje, zda má být obslužná rutina nastavena nebo vydána.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla obslužná rutina úspěšně nastavena nebo uvolněna; FALSE, pokud je nyní nalezena zadaná animační skupina nebo animace pro zadanou skupinu nebyla inicializována a její vnitřní scénář je NULL.

### <a name="remarks"></a>Poznámky

Pokud je nastavená obslužná rutina (Enabled), rozhraní API pro animace systému Windows volá virtuální metody OnStoryboardStatusChanges a OnStoryboardUpdated. Obslužná rutina musí být nastavena po volání metody CAnimationController:: Animate pro zadanou skupinu animace, protože vytváří zapouzdřený objekt IUIAnimationStoryboard.

##  <a name="findanimationgroup"></a>CAnimationController::FindAnimationGroup

Vyhledá skupinu animace podle ID skupiny.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje identifikátor skupiny.

*pStoryboard*<br/>
Ukazatel na scénář.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na skupinu animace nebo hodnotu NULL, pokud nebyla nalezena skupina se zadaným ID.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li najít skupinu animace za běhu. Skupina je vytvořena a přidána do interního seznamu skupin animace, když je do řadiče animace přidán první objekt animace se specifickým identifikátorem skupiny.

##  <a name="findanimationobject"></a>CAnimationController::FindAnimationObject

Najde objekt animace obsahující zadanou proměnnou animace.

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
Výkonem. Obsahuje ukazatel na objekt animace nebo hodnotu NULL.

*ppGroup*<br/>
Výkonem. Obsahuje ukazatel na skupinu animace, která obsahuje objekt animace nebo hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byl objekt nalezen; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Volá se z obslužných rutin událostí, pokud je potřeba najít objekt animace z příchozí proměnné animace.

##  <a name="g_keyframestoryboardstart"></a>CAnimationController::gkeyframeStoryboardStart

Klíčový snímek, který představuje začátek scénáře.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>CAnimationController::GetKeyframeStoryboardStart

Vrátí klíčový snímek, který identifikuje začátek scénáře.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na základní klíčový snímek, který identifikuje začátek scénáře.

### <a name="remarks"></a>Poznámky

Získejte tento klíčový snímek, který bude základem všech dalších klíčových snímků nebo přechodů k časovému okamžiku, kdy se scénář spustí.

##  <a name="getuianimationmanager"></a>CAnimationController::GetUIAnimationManager

Poskytuje přístup k zapouzdřenému objektu IUIAnimationManager.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IUIAnimationManager nebo NULL, pokud se nepovedlo vytvořit Správce animací.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje rozhraní API animace systému Windows, vrátí tato metoda hodnotu NULL a poté, co všechna následující volání na CAnimationController:: IsValid vrací hodnotu FALSE. Pro volání metod rozhraní, které nejsou zabaleny řadičem animace, možná budete muset získat přístup k IUIAnimationManager.

##  <a name="getuianimationtimer"></a>CAnimationController::GetUIAnimationTimer

Poskytuje přístup k zapouzdřenému objektu IUIAnimationTimer.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IUIAnimationTimer nebo NULL, pokud se nepovedlo vytvořit časovač animace.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje rozhraní API animace systému Windows, vrátí tato metoda hodnotu NULL a poté, co všechna následující volání na CAnimationController:: IsValid vrací hodnotu FALSE.

##  <a name="getuitransitionfactory"></a>CAnimationController::GetUITransitionFactory

Ukazatel na rozhraní IUIAnimationTransitionFactory nebo NULL, pokud se nepovedlo vytvořit knihovnu přechodu.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na IUIAnimationTransitionFactory nebo NULL, pokud se nepovedlo vytvořit převod továrny.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje rozhraní API animace systému Windows, vrátí tato metoda hodnotu NULL a poté, co všechna následující volání na CAnimationController:: IsValid vrací hodnotu FALSE.

##  <a name="getuitransitionlibrary"></a>CAnimationController::GetUITransitionLibrary

Poskytuje přístup k zapouzdřenému objektu IUIAnimationTransitionLibrary.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IUIAnimationTransitionLibrary nebo NULL, pokud se nepovedlo vytvořit knihovnu přechodu.

### <a name="remarks"></a>Poznámky

Pokud aktuální operační systém nepodporuje rozhraní API animace systému Windows, vrátí tato metoda hodnotu NULL a poté, co všechna následující volání na CAnimationController:: IsValid vrací hodnotu FALSE.

##  <a name="isanimationinprogress"></a>CAnimationController::IsAnimationInProgress

Určuje, zda nejméně jedna skupina přehrává animaci.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud pro tento kontroler animací probíhá animace; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Zkontroluje stav Správce animací a vrátí hodnotu TRUE, pokud je stav UI_ANIMATION_MANAGER_BUSY.

##  <a name="isvalid"></a>CAnimationController:: IsValid

Informuje o tom, zda je řadič animace platný.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je řadič animace platný; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu FALSE pouze v případě, že rozhraní API animace systému Windows není v aktuálním operačním systému podporováno a vytvoření Správce animací se nezdařilo, protože není zaregistrováno. Pro nastavení tohoto příznaku je nutné volat GetUIAnimationManager alespoň jednou po inicializaci knihoven COM.

##  <a name="m_bisvalid"></a>  CAnimationController::m_bIsValid

Určuje, jestli je kontroler animace platný, nebo ne. Tento člen je nastaven na hodnotu FALSE, pokud aktuální operační systém nepodporuje rozhraní API Windows Animation.

```
BOOL m_bIsValid;
```

##  <a name="m_lstanimationgroups"></a>CAnimationController::m_lstAnimationGroups

Seznam skupin animací, které patří k tomuto řadiči animací

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

##  <a name="m_panimationmanager"></a>  CAnimationController::m_pAnimationManager

Ukládá ukazatel na objekt modelu COM Správce animací.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>CAnimationController::m_pAnimationTimer

Ukládá ukazatel na objekt modelu COM časovače animace.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>CAnimationController::m_pRelatedWnd

Ukazatel na související objekt CWnd, který lze automaticky překreslit při změně stavu správce animace nebo při události po aktualizaci. Může mít hodnotu NULL.

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory

Ukládá ukazatel na převod objektu COM továrny.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>  CAnimationController::m_pTransitionLibrary

Ukládá ukazatel na objekt modelu COM knihovny přechodu.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>CAnimationController::OnAfterSchedule

Volá se rozhraním, když se právě naplánovala animace pro zadanou skupinu.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Ukazatel na skupinu animace, která je naplánována.

### <a name="remarks"></a>Poznámky

Výchozí implementace odebere klíčové snímky ze zadané skupiny a přechody z proměnných animace, které patří do zadané skupiny. Může být přepsán v odvozené třídě, aby bylo možné provádět další akce v rámci plánu animace.

##  <a name="onanimationintegervaluechanged"></a>CAnimationController::OnAnimationIntegerValueChanged

Volá se rozhraním, když se změnila celočíselná hodnota proměnné animace.

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

*pObject*<br/>
Ukazatel na objekt animace, který obsahuje proměnnou animace, jejíž hodnota se změnila.

*variabilní*<br/>
Ukazatel na proměnnou animace.

*newValue*<br/>
Určuje novou hodnotu.

*prevValue*<br/>
Určuje předchozí hodnotu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události proměnných animace s voláním EnableIntegerValueChangedEvent pro konkrétní proměnnou animace nebo objekt animace. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci.

##  <a name="onanimationmanagerstatuschanged"></a>CAnimationController::OnAnimationManagerStatusChanged

Volá se rozhraním v reakci na událost StatusChanged ze Správce animací.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*newStatus*<br/>
Nový stav manažera animace

*previousStatus*<br/>
Stav předchozího Správce animací

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události Správce animací pomocí EnableAnimationManagerEvent. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci. Výchozí implementace aktualizuje související okno, pokud bylo nastaveno pomocí SetRelatedWnd.

##  <a name="onanimationtimerpostupdate"></a>CAnimationController::OnAnimationTimerPostUpdate

Volá se rozhraním po dokončení aktualizace animace.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte obslužné rutiny událostí časovače pomocí EnableAnimationTimerEventHandler. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci.

##  <a name="onanimationtimerpreupdate"></a>CAnimationController::OnAnimationTimerPreUpdate

Volá se rozhraním, než začne aktualizace animace.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte obslužné rutiny událostí časovače pomocí EnableAnimationTimerEventHandler. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci.

##  <a name="onanimationtimerrenderingtooslow"></a>CAnimationController::OnAnimationTimerRenderingTooSlow

Volá se rozhraním, když míra vykreslování snímků pro animaci klesne pod minimální požadovanou snímkovou sazbu.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Parametry

*snímků za sekundu*<br/>
Aktuální snímková frekvence v rámečcích za sekundu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte obslužné rutiny událostí časovače pomocí EnableAnimationTimerEventHandler. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci. Minimální žádoucí snímková frekvence je určena voláním IUIAnimationTimer:: SetFrameRateThreshold.

##  <a name="onanimationvaluechanged"></a>CAnimationController::OnAnimationValueChanged

Volá se rozhraním, když se změnila hodnota proměnné animace.

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

*pObject*<br/>
Ukazatel na objekt animace, který obsahuje proměnnou animace, jejíž hodnota se změnila.

*variabilní*<br/>
Ukazatel na proměnnou animace.

*newValue*<br/>
Určuje novou hodnotu.

*prevValue*<br/>
Určuje předchozí hodnotu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události proměnných animace s voláním EnableValueChangedEvent pro konkrétní proměnnou animace nebo objekt animace. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci.

##  <a name="onbeforeanimationstart"></a>CAnimationController::OnBeforeAnimationStart

Volá se rozhraním přímo předtím, než se naplánuje animace.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Ukazatel na skupinu animace, jejíž animace se chystá začít.

### <a name="remarks"></a>Poznámky

Toto volání je směrováno na související CWnd a může být přepsáno v odvozené třídě, aby provedla jakékoli další akce před začátkem animace zadané skupiny.

##  <a name="onhasprioritycancel"></a>CAnimationController::OnHasPriorityCancel

Volá se rozhraním, aby se vyřešily konflikty plánování.

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Skupina, která vlastní aktuálně naplánovaný scénář.

*pGroupNew*<br/>
Skupina, která je vlastníkem nového scénáře v plánování, je v konfliktu s plánovaným scénářem, který vlastní pGroupScheduled.

*priorityEffect*<br/>
Potenciální účinek na pGroupNew, pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měla vracet hodnotu TRUE, pokud má scénář ve vlastnictví pGroupNew prioritu. By měla vracet hodnotu FALSE, pokud scénář vlastněný nástrojem pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události porovnání priorit pomocí CAnimationController:: EnablePriorityComparisonHandler a zadáním UI_ANIMATION_PHT_CANCEL. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci. Další informace o [správě konfliktů](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)najdete v dokumentaci k rozhraní Windows Animation API.

##  <a name="onhasprioritycompress"></a>CAnimationController::OnHasPriorityCompress

Volá se rozhraním, aby se vyřešily konflikty plánování.

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Skupina, která vlastní aktuálně naplánovaný scénář.

*pGroupNew*<br/>
Skupina, která je vlastníkem nového scénáře v plánování, je v konfliktu s plánovaným scénářem, který vlastní pGroupScheduled.

*priorityEffect*<br/>
Potenciální účinek na pGroupNew, pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měla vracet hodnotu TRUE, pokud má scénář ve vlastnictví pGroupNew prioritu. By měla vracet hodnotu FALSE, pokud scénář vlastněný nástrojem pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události porovnání priorit pomocí CAnimationController:: EnablePriorityComparisonHandler a zadáním UI_ANIMATION_PHT_COMPRESS. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci. Další informace o [správě konfliktů](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)najdete v dokumentaci k rozhraní Windows Animation API.

##  <a name="onhaspriorityconclude"></a>CAnimationController::OnHasPriorityConclude

Volá se rozhraním, aby se vyřešily konflikty plánování.

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Skupina, která vlastní aktuálně naplánovaný scénář.

*pGroupNew*<br/>
Skupina, která je vlastníkem nového scénáře v plánování, je v konfliktu s plánovaným scénářem, který vlastní pGroupScheduled.

*priorityEffect*<br/>
Potenciální účinek na pGroupNew, pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měla vracet hodnotu TRUE, pokud má scénář ve vlastnictví pGroupNew prioritu. By měla vracet hodnotu FALSE, pokud scénář vlastněný nástrojem pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události porovnání priorit pomocí CAnimationController:: EnablePriorityComparisonHandler a zadáním UI_ANIMATION_PHT_CONCLUDE. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci. Další informace o [správě konfliktů](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)najdete v dokumentaci k rozhraní Windows Animation API.

##  <a name="onhasprioritytrim"></a>CAnimationController::OnHasPriorityTrim

Volá se rozhraním, aby se vyřešily konflikty plánování.

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Skupina, která vlastní aktuálně naplánovaný scénář.

*pGroupNew*<br/>
Skupina, která je vlastníkem nového scénáře v plánování, je v konfliktu s plánovaným scénářem, který vlastní pGroupScheduled.

*priorityEffect*<br/>
Potenciální účinek na pGroupNew, pokud pGroupScheduled má vyšší prioritu.

### <a name="return-value"></a>Návratová hodnota

By měla vracet hodnotu TRUE, pokud má scénář ve vlastnictví pGroupNew prioritu. By měla vracet hodnotu FALSE, pokud scénář vlastněný nástrojem pGroupScheduled má prioritu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události porovnání priorit pomocí CAnimationController:: EnablePriorityComparisonHandler a zadáním UI_ANIMATION_PHT_TRIM. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci. Další informace o [správě konfliktů](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)najdete v dokumentaci k rozhraní Windows Animation API.

##  <a name="onstoryboardstatuschanged"></a>CAnimationController::OnStoryboardStatusChanged

Volá se rozhraním, když se změní stav scénáře.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Ukazatel na skupinu animace, která vlastní scénář, jehož stav byl změněn.

*newStatus*<br/>
Určuje nový stav.

*previousStatus*<br/>
Určuje předchozí stav.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události scénáře pomocí CAnimationController:: EnableStoryboardEventHandler. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci.

##  <a name="onstoryboardupdated"></a>CAnimationController::OnStoryboardUpdated

Volá se rozhraním, když se aktualizuje scénář.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Ukazatel na skupinu, která vlastní scénář.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, pokud povolíte události scénáře pomocí CAnimationController:: EnableStoryboardEventHandler. Může být přepsán v odvozené třídě pro provedení akcí specifických pro aplikaci.

##  <a name="removeallanimationgroups"></a>CAnimationController::RemoveAllAnimationGroups

Odebere všechny animační skupiny z kontroleru animací.

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Poznámky

Odstraní se všechny skupiny, jejich ukazatel, pokud je uložený na úrovni aplikace, musí být zrušené. Pokud je CAnimationGroup:: m_bAutodestroyAnimationObjects pro skupinu, která je odstraněna, nastavena na hodnotu TRUE, odstraní se všechny objekty animace, které patří do této skupiny. v opačném případě se jejich odkazy na nadřazený kontroler animací nastaví na hodnotu NULL a dají se přidat na jiný kontroler.

##  <a name="removeanimationgroup"></a>CAnimationController::RemoveAnimationGroup

Odebere ze kontroleru animací skupinu animace se zadaným ID.

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID animační skupiny.

### <a name="remarks"></a>Poznámky

Tato metoda odebere skupinu animace z interního seznamu skupin a odstraní ji, takže pokud jste ukazatel na tuto skupinu animací uložili, je nutné, aby byla zrušena. Pokud CAnimationGroup:: m_bAutodestroyAnimationObjects má hodnotu TRUE, odstraní se všechny objekty animace, které patří do této skupiny. v opačném případě se jejich odkazy na nadřazený kontroler animací nastaví na hodnotu NULL a dají se přidat na jiný kontroler.

##  <a name="removeanimationobject"></a>CAnimationController::RemoveAnimationObject

Odebere objekt animace z kontroleru animací.

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Parametry

*pObject*<br/>
Ukazatel na objekt animace.

*bNoDelete*<br/>
Pokud má tento parametr hodnotu TRUE, objekt se po odebrání neodstraní.

### <a name="remarks"></a>Poznámky

Odebere objekt animace z kontroleru animace a skupiny animací. Tuto funkci volejte, pokud by příslušný objekt již neměl být animovaný, nebo pokud potřebujete objekt přesunout na jiný kontroler animace. V posledním případě bNoDelete musí mít hodnotu TRUE.

##  <a name="removetransitions"></a>CAnimationController::RemoveTransitions

Odebere přechody z objektů animace, které patří do zadané skupiny.

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID skupiny.

### <a name="remarks"></a>Poznámky

Skupina projde objekty animace a volá ClearTransitions (FALSE) pro každý objekt animace. Tato metoda je volána rozhraním po naplánování animace.

##  <a name="schedulegroup"></a>CAnimationController:: Schedule –

Naplánuje animaci.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID animační skupiny k naplánování.

*čas*<br/>
Určuje čas k naplánování.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se úspěšně naplánovala animace FALSE, pokud není vytvořen scénář nebo dojde k jiné chybě.

### <a name="remarks"></a>Poznámky

Je nutné volat vlastnost Animate. bScheduleNow nastavenou na hodnotu FALSE předchozí skupiny Schedule. Můžete určit požadovanou dobu animace získanou z IUIAnimationTimer:: GetTime. Pokud je parametr time 0,0, je pro aktuální čas naplánována animace.

##  <a name="setrelatedwnd"></a>CAnimationController::SetRelatedWnd

Vytvoří vztah mezi animačním kontrolérem a oknem.

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na objekt okna, který chcete nastavit.

### <a name="remarks"></a>Poznámky

Pokud je nastaven související objekt CWnd, může se řadič animace automaticky aktualizovat (Odeslat zprávu WM_PAINT), když došlo ke změně stavu Správce animací nebo k události po aktualizaci časovače.

##  <a name="updateanimationmanager"></a>CAnimationController::UpdateAnimationManager

Nasměruje Správce animací, aby aktualizoval hodnoty všech proměnných animace.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Poznámky

Volání této metody posune správce animace na aktuální čas, mění stavy scénářů podle potřeby a aktualizuje všechny proměnné animace na příslušné Interpolované hodnoty. Interně Tato metoda volá IUIAnimationTimer:: GetTime (timeNow) a IUIAnimationManager:: Update (timeNow). Tuto metodu přepište v odvozené třídě, aby se toto chování přizpůsobilo.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
