---
title: "Třída CAnimationController | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 79343615b633b583775a482f0a9d2155e79ede10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="canimationcontroller-class"></a>CAnimationController – třída
Implementuje animace řadiči, který poskytuje centrální rozhraní pro vytváření a správa animace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationController : public CObject;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationController::CAnimationController](#canimationcontroller)|Vytvoří řadič animace.|  
|[CAnimationController:: ~ CAnimationController](#canimationcontroller__~canimationcontroller)|Destruktor. Voláno, když je zničen objektu řadiče animace.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationController::AddAnimationObject](#addanimationobject)|Přidá objekt animace do skupiny, která patří do kontroleru animace.|  
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Klíčový přidá do skupiny.|  
|[CAnimationController::AnimateGroup](#animategroup)|Připraví skupinu pro spuštění animace a volitelně ji plány.|  
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Přetíženo. Voláno rámcem odstranit skupinu při bylo naplánováno animace.|  
|[CAnimationController::CreateKeyframe](#createkeyframe)|Přetíženo. Vytvoří klíčový snímek, který závisí na přechod a přidá ji do zadané skupiny.|  
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Nastaví nebo uvolní obslužná rutina volat při změně stavu animace správce.|  
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Nastaví nebo uvolní obslužnou rutinu pro časování události a obslužné rutiny pro časování aktualizace.|  
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Nastaví nebo obslužná rutina porovnání s prioritou volat k určení, zda naplánované storyboard může být zrušena, se dospělo k závěru, oříznut nebo komprimované verze.|  
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Nastaví nebo uvolní obslužnou rutinu události storyboard stavu a aktualizace.|  
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Přetíženo. Vyhledá skupinu animace podle jeho scénáře.|  
|[CAnimationController::FindAnimationObject](#findanimationobject)|Vyhledá animace objekt obsahující zadanou animace proměnné.|  
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Vrátí klíčový snímek, který identifikuje začátek storyboard.|  
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Poskytuje přístup k zapouzdřené IUIAnimationManager objektu.|  
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Poskytuje přístup k zapouzdřené IUIAnimationTimer objektu.|  
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Ukazatel rozhraní IUIAnimationTransitionFactory nebo hodnota NULL, pokud vytvoření přechodu knihovny se nezdařilo.|  
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Poskytuje přístup k zapouzdřené IUIAnimationTransitionLibrary objektu.|  
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Určuje, zda je alespoň jednu skupinu přehrávání animace.|  
|[CAnimationController::IsValid](#isvalid)|Určuje, zda je animace řadiče platný.|  
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Voláno rámcem, pokud došlo ke změně celočíselnou hodnotu proměnné animace.|  
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Voláno rámcem v reakci na StatusChanged události ze Správce animace.|  
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Voláno rámcem po dokončení aktualizace animace.|  
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Voláno rámcem před zahájením aktualizace animace.|  
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Voláno rámcem při vykreslování snímků za sekundu pro animace klesne pod minimální žádoucí obnovovací frekvence.|  
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Voláno rámcem, pokud došlo ke změně hodnoty proměnné animace.|  
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Voláno rámcem správné předtím, než je naplánováno animace.|  
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Voláno rámcem vyřešit konflikty v plánu.|  
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Voláno rámcem vyřešit konflikty v plánu.|  
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Voláno rámcem vyřešit konflikty v plánu.|  
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Voláno rámcem vyřešit konflikty v plánu.|  
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Voláno rámcem, pokud došlo ke změně stavu scénáře.|  
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|Voláno rámcem storyboard po aktualizaci.|  
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Odebere všechny skupiny animace z řadiče animace.|  
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Odebere skupinu animace se zadaným ID z řadiče animace.|  
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Odeberte objekt animace z řadiče animace.|  
|[CAnimationController::RemoveTransitions](#removetransitions)|Odebere přechody animace objektů, které patří do zadané skupiny.|  
|[CAnimationController::ScheduleGroup](#schedulegroup)|Naplánuje animace.|  
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Vytvoří vztah mezi animace řadiče a v okně.|  
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Určí, že správce animace a aktualizujte hodnoty všech proměnných animace.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Přetíženo. Pomocné rutiny vyčistí skupině.|  
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Voláno rámcem při animace pro zadanou skupinu pouze bylo naplánováno.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Klíčový snímek, který představuje začátek scénáře.|  
|[CAnimationController::m_bIsValid](#m_bisvalid)|Určuje, jestli řadič animace je platný, nebo ne. Tento člen je nastavena na hodnotu FALSE, pokud aktuální operační systém nepodporuje rozhraní API systému Windows animace.|  
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Seznam animace skupiny, které patří do tohoto řadiče animace.|  
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Ukládá ukazatel na objekt Manager animace COM.|  
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Ukládá ukazatel na objekt COM časovače animace.|  
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Ukazatel na související objekt CWnd můžete být automaticky překreslen, pokud došlo ke změně stavu animace manager nebo došlo k události aktualizace post. Může mít hodnotu NULL.|  
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Ukládá ukazatel na objekt Factory COM přechodu.|  
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Ukládá ukazatel na objekt COM knihovny přechodu.|  
  
## <a name="remarks"></a>Poznámky  
 Třída CAnimationController je klíčů třídě, která spravuje animace. Může vytvořit jeden nebo více instancí řadiče animace v aplikaci a volitelně připojení k objektu CWnd pomocí CAnimationController::SetRelatedWnd instance řadiče animace. Toto připojení je potřeba odesílat do okna související zprávy WM_PAINT automaticky při došlo ke změně stavu animace správce nebo časovače animace se aktualizovala. Pokud nepovolíte tento vztah, musí ho překreslit okno, které zobrazí animace ručně. Pro tento účel můžete odvození třídy z CAnimationController a přepsání OnAnimationManagerStatusChanged nebo OnAnimationTimerPostUpdate a zrušení platnosti jednoho nebo více windows, pokud je to nezbytné.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationController`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationcontroller"></a>CAnimationController:: ~ CAnimationController  
 Destruktor. Voláno, když je zničen objektu řadiče animace.  
  
```  
virtual ~CAnimationController(void);
```   
  
##  <a name="addanimationobject"></a>CAnimationController::AddAnimationObject  
 Přidá objekt animace do skupiny, která patří do kontroleru animace.  
  
```  
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pObject`  
 Ukazatel na objekt animace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatele na existující nebo nové skupiny animace, kde byla přidána pObject Pokud funkce úspěšně. Hodnota NULL, pokud pObject již byla přidána do skupiny, která patří do jiného řadiče animace.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem přidání objektu animace do řadiče animace. Objekt přidá do skupiny podle objektu GroupID (viz CAnimationBaseObject::SetID). Animace řadiče vytvoří novou skupinu, pokud je první objekt přidávané s zadané ID skupiny. Objekt animace můžete přidat do pouze jeden animace řadiče. Pokud potřebujete přidat objekt do jiného řadiče, volejte nejprve RemoveAnimationObject. Při volání ID sady s nové ID skupiny pro objekt, který byl již přidán do skupiny, bude objekt odebrána ze staré skupiny a přidat do jiné skupiny s určeným ID.  
  
##  <a name="addkeyframetogroup"></a>CAnimationController::AddKeyframeToGroup  
 Klíčový přidá do skupiny.  
  
```  
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,  
    CBaseKeyFrame* pKeyframe);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Určuje ID skupiny.  
  
 `pKeyframe`  
 Ukazatel na klíčový snímek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud funkci úspěšně. jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle nemusíte volat tuto metodu, použijte CAnimationController::CreateKeyframe místo toho, která vytvoří a automaticky přidá do skupiny vytvořené klíčový snímek.  
  
##  <a name="animategroup"></a>CAnimationController::AnimateGroup  
 Připraví skupinu pro spuštění animace a volitelně ji plány.  
  
```  
BOOL AnimateGroup(
    UINT32 nGroupID,  
    BOOL bScheduleNow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Určuje ID skupiny.  
  
 `bScheduleNow`  
 Určuje, zda chcete spustit hned animace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud animace byla úspěšně naplánovat a spustit.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda ve skutečnosti provádí zpracování vytváření storyboard, přidání animace proměnné, použití přechody a nastavení klíčových snímků. Je možné zpoždění před naplánování bScheduleNow nastaveného na hodnotu FALSE. Zadaná skupina v takovém případě bude obsahovat storyboard, která byla vytvořena pro animace. V tomto bodě se dá nastavit události pro proměnné scénáře a animace. Když ve skutečnosti musíte spustit volání animace CAnimationController::ScheduleGroup.  
  
##  <a name="canimationcontroller"></a>CAnimationController::CAnimationController  
 Vytvoří řadič animace.  
  
```  
CAnimationController(void);
```   
  
##  <a name="cleanupgroup"></a>CAnimationController::CleanUpGroup  
 Voláno rámcem odstranit skupinu při bylo naplánováno animace.  
  
```  
void CleanUpGroup(UINT32 nGroupID);  
void CleanUpGroup(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Určuje ID skupiny.  
  
 `pGroup`  
 Ukazatel na skupiny animace vyčistit.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odebere všechny přechody a klíčových snímků ze zadané skupiny, protože nejsou relevantní, po bylo naplánováno animace.  
  
##  <a name="createkeyframe"></a>CAnimationController::CreateKeyframe  
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
 `nGroupID`  
 Určuje ID skupiny, pro kterou je vytvořen klíčový snímek.  
  
 `pTransition`  
 Ukazatel na přechod. Klíčový snímek se vloží do scénáře po tento přechod.  
  
 `pKeyframe`  
 Ukazatel na základní klíčový snímek pro tento klíčový snímek.  
  
 `offset`  
 Posun v sekundách mezi základní jednotlivými určeného pKeyframe.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený klíčový snímek, je-li funkci úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Můžete ukládat Vrácený ukazatel a základní jiných klíčových snímků na nově vytvořený klíčový snímek (viz druhý přetížení). Je možné začít přechody na klíčové snímky – viz CBaseTransition::SetKeyframes. Nemusíte odstranit vytvořené v tomto případě klíčové snímky, protože se automaticky odstraní skupinami animace. Buďte opatrní při vytváření klíčových snímků na základě jiných klíčových snímků a přechody a vyhnout se cyklické odkazy.  
  
##  <a name="enableanimationmanagerevent"></a>CAnimationController::EnableAnimationManagerEvent  
 Nastaví nebo uvolní obslužná rutina volat při změně stavu animace správce.  
  
```  
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Určuje, zda nastavení nebo uvolnění obslužnou rutinu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud obslužná rutina byla úspěšně nastavena nebo vydání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud obslužná rutina nastavena (povoleno) Windows animace volá OnAnimationManagerStatusChanged při změně stavu animace správce.  
  
##  <a name="enableanimationtimereventhandler"></a>CAnimationController::EnableAnimationTimerEventHandler  
 Nastaví nebo uvolní obslužnou rutinu pro časování události a obslužné rutiny pro časování aktualizace.  
  
```  
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,  
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Určuje, zda nastavení nebo uvolnění obslužných rutin.  
  
 `idleBehavior`  
 Určuje chování při nečinnosti pro obslužnou rutinu aktualizace časovače.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud byly úspěšně nastavit nebo vydání; obslužné rutiny FALSE v případě, že tato metoda je volána při druhé stisknutým obslužných rutin, nebo pokud jakékoliv dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou obslužných rutin nastavíte (povoleno) volání rozhraní API systému Windows animace OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate, OnRenderingTooSlow metody. Budete muset povolit animace časovače umožňující scénářů aktualizace rozhraní API systému Windows animace. V opačném případě budete muset volat CAnimationController::UpdateAnimationManager aby bylo možné směrovat animace správce a aktualizujte hodnoty všech proměnných animace.  
  
##  <a name="enableprioritycomparisonhandler"></a>CAnimationController::EnablePriorityComparisonHandler  
 Nastaví nebo obslužná rutina porovnání s prioritou volat k určení, zda naplánované storyboard může být zrušena, se dospělo k závěru, oříznut nebo komprimované verze.  
  
```  
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```  
  
### <a name="parameters"></a>Parametry  
 `dwHandlerType`  
 Kombinace UI_ANIMATION_PHT_ příznaky (viz poznámky), která určuje, jaké obslužné rutiny nastavení nebo uvolnění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud obslužná rutina byla úspěšně nastavena nebo vydání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud obslužná rutina nastavena (povoleno) Windows animace volá následující virtuální metody, v závislosti na dwHandlerType: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler může být kombinací následující příznaky: UI_ANIMATION_PHT_NONE - verze všechny obslužné rutiny UI_ANIMATION_PHT_CANCEL - nastavit Storno porovnání obslužná rutina UI_ANIMATION_PHT_CONCLUDE - nastavit popisovač porovnání Conclude UI_ANIMATION_PHT_COMPRESS – nastavení Obslužná rutina porovnání compress UI_ANIMATION_PHT_TRIM - nastavit popisovač Trim porovnání UI_ANIMATION_PHT_CANCEL_REMOVE – porovnání Storno UI_ANIMATION_PHT_CONCLUDE_REMOVE – obslužné rutiny odebírání - odebrání porovnání Conclude UI_ANIMATION_PHT_COMPRESS_ – obslužné rutiny ODEBRAT – obslužné rutiny porovnání Compress UI_ANIMATION_PHT_TRIM_REMOVE - odebrat oříznutí porovnání obslužné rutiny odebírání  
  
##  <a name="enablestoryboardeventhandler"></a>CAnimationController::EnableStoryboardEventHandler  
 Nastaví nebo uvolní obslužnou rutinu události storyboard stavu a aktualizace.  
  
```  
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Určuje ID skupiny.  
  
 `bEnable`  
 Určuje, zda nastavení nebo uvolnění obslužnou rutinu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je obslužná rutina byl úspěšně nastaven nebo vydání; FALSE, pokud je nyní najít skupinu zadaný animace nebo nebyla inicializována animace pro zadanou skupinu a jeho vnitřní storyboard má hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 Pokud obslužná rutina nastavena (povoleno) rozhraní API systému Windows animace volá OnStoryboardStatusChanges a OnStoryboardUpdated virtuální metody. Obslužná rutina musí být nastaven po zavolání CAnimationController::Animate pro zadaný animace skupinu, protože se tím vytvoří zapouzdřené IUIAnimationStoryboard objektu.  
  
##  <a name="findanimationgroup"></a>CAnimationController::FindAnimationGroup  
 Vyhledá skupinu animace podle jeho ID skupiny.  
  
```  
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);  
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Určuje ID skupiny.  
  
 `pStoryboard`  
 Ukazatel na scénář.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na animace skupiny nebo hodnota NULL, pokud skupina se zadaným ID nebyla nalezena.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k vyhledání skupinu animace za běhu. Skupinu je vytvořen a přidán do seznamu interní skupin animace při první objekt animace s konkrétním ID skupiny je přidáván do řadiče animace.  
  
##  <a name="findanimationobject"></a>CAnimationController::FindAnimationObject  
 Vyhledá animace objekt obsahující zadanou animace proměnné.  
  
```  
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,  
    CAnimationBaseObject** ppObject,  
    CAnimationGroup** ppGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `pVariable`  
 Ukazatel na proměnnou animace.  
  
 `ppObject`  
 Výstup. Obsahuje ukazatel na objekt animace nebo hodnotu NULL.  
  
 `ppGroup`  
 Výstup. Obsahuje ukazatel na animace skupiny, která obsahuje objekt animace, nebo hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud byl nalezen objekt; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Volat z obslužné rutiny událostí, pokud je to požadováno, vyhledání objektu animace z příchozí proměnné animace.  
  
##  <a name="g_keyframestoryboardstart"></a>CAnimationController::gkeyframeStoryboardStart  
 Klíčový snímek, který představuje začátek scénáře.  
  
```  
static CBaseKeyFrame gkeyframeStoryboardStart;  
```  
  
##  <a name="getkeyframestoryboardstart"></a>CAnimationController::GetKeyframeStoryboardStart  
 Vrátí klíčový snímek, který identifikuje začátek storyboard.  
  
```  
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na základní klíčový snímek, který identifikuje začátek scénáře.  
  
### <a name="remarks"></a>Poznámky  
 Získáte tento klíčový snímek na základní ostatní klíčových snímků nebo přechody na okamžik v čase, při spuštění scénáře.  
  
##  <a name="getuianimationmanager"></a>CAnimationController::GetUIAnimationManager  
 Poskytuje přístup k zapouzdřené IUIAnimationManager objektu.  
  
```  
IUIAnimationManager* GetUIAnimationManager();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní IUIAnimationManager nebo hodnota NULL, pokud vytvoření manager animace se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Pokud aktuální operační systém nepodporuje rozhraní API systému Windows animace, tato metoda vrátí hodnotu NULL a potom všechny následující volání na CAnimationController::IsValid vrací hodnotu FALSE. Musíte pro přístup k IUIAnimationManager, aby bylo možné volat jeho metody rozhraní, které nejsou zabalené službou řadiče animace.  
  
##  <a name="getuianimationtimer"></a>CAnimationController::GetUIAnimationTimer  
 Poskytuje přístup k zapouzdřené IUIAnimationTimer objektu.  
  
```  
IUIAnimationTimer* GetUIAnimationTimer();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní IUIAnimationTimer nebo hodnota NULL, pokud vytvoření časovače animace se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Pokud aktuální operační systém nepodporuje rozhraní API systému Windows animace, tato metoda vrátí hodnotu NULL a potom všechny následující volání na CAnimationController::IsValid vrací hodnotu FALSE.  
  
##  <a name="getuitransitionfactory"></a>CAnimationController::GetUITransitionFactory  
 Ukazatel rozhraní IUIAnimationTransitionFactory nebo hodnota NULL, pokud vytvoření přechodu knihovny se nezdařilo.  
  
```  
IUIAnimationTransitionFactory* GetUITransitionFactory();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na IUIAnimationTransitionFactory nebo hodnota NULL, pokud vytvoření objektu pro vytváření přechod se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Pokud aktuální operační systém nepodporuje rozhraní API systému Windows animace, tato metoda vrátí hodnotu NULL a potom všechny následující volání na CAnimationController::IsValid vrací hodnotu FALSE.  
  
##  <a name="getuitransitionlibrary"></a>CAnimationController::GetUITransitionLibrary  
 Poskytuje přístup k zapouzdřené IUIAnimationTransitionLibrary objektu.  
  
```  
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní IUIAnimationTransitionLibrary nebo hodnota NULL, pokud vytvoření přechodu knihovny se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Pokud aktuální operační systém nepodporuje rozhraní API systému Windows animace, tato metoda vrátí hodnotu NULL a potom všechny následující volání na CAnimationController::IsValid vrací hodnotu FALSE.  
  
##  <a name="isanimationinprogress"></a>CAnimationController::IsAnimationInProgress  
 Určuje, zda je alespoň jednu skupinu přehrávání animace.  
  
```  
virtual BOOL IsAnimationInProgress();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je animace v průběhu pro tento kontroler animace; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Kontroluje stav manager animace a vrátí hodnotu TRUE, pokud je stav UI_ANIMATION_MANAGER_BUSY.  
  
##  <a name="isvalid"></a>CAnimationController::IsValid  
 Určuje, zda je animace řadiče platný.  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je animace řadič platný; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu FALSE pouze v případě, že rozhraní API systému Windows animace není podporována na aktuálního operačního systému a vytvoření animace manager se nezdařila, protože není zaregistrován. Je třeba volat GetUIAnimationManager alespoň jednou po inicializaci knihovny COM způsobí nastavení tohoto příznaku.  
  
##  <a name="m_bisvalid"></a>CAnimationController::m_bIsValid  
 Určuje, jestli řadič animace je platný, nebo ne. Tento člen je nastavena na hodnotu FALSE, pokud aktuální operační systém nepodporuje rozhraní API systému Windows animace.  
  
```  
BOOL m_bIsValid;  
```  
  
##  <a name="m_lstanimationgroups"></a>CAnimationController::m_lstAnimationGroups  
 Seznam animace skupiny, které patří do tohoto řadiče animace.  
  
```  
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;  
```  
  
##  <a name="m_panimationmanager"></a>CAnimationController::m_pAnimationManager  
 Ukládá ukazatel na objekt Manager animace COM.  
  
```  
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;  
```  
  
##  <a name="m_panimationtimer"></a>CAnimationController::m_pAnimationTimer  
 Ukládá ukazatel na objekt COM časovače animace.  
  
```  
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;  
```  
  
##  <a name="m_prelatedwnd"></a>CAnimationController::m_pRelatedWnd  
 Ukazatel na související objekt CWnd můžete být automaticky překreslen, pokud došlo ke změně stavu animace manager nebo došlo k události aktualizace post. Může mít hodnotu NULL.  
  
```  
CWnd* m_pRelatedWnd;  
```  
  
##  <a name="m_ptransitionfactory"></a>CAnimationController::m_pTransitionFactory  
 Ukládá ukazatel na objekt Factory COM přechodu.  
  
```  
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;  
```  
  
##  <a name="m_ptransitionlibrary"></a>CAnimationController::m_pTransitionLibrary  
 Ukládá ukazatel na objekt COM knihovny přechodu.  
  
```  
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;  
```  
  
##  <a name="onafterschedule"></a>CAnimationController::OnAfterSchedule  
 Voláno rámcem při animace pro zadanou skupinu pouze bylo naplánováno.  
  
```  
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Ukazatel na animace skupiny, které bylo naplánováno.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace klíčových snímků odebere zadané skupiny a přejde z animace proměnných, které patří do zadané skupiny. Lze přepsat v odvozené třídě a provádět žádné další akce po plán animace.  
  
##  <a name="onanimationintegervaluechanged"></a>CAnimationController::OnAnimationIntegerValueChanged  
 Voláno rámcem, pokud došlo ke změně celočíselnou hodnotu proměnné animace.  
  
```  
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,  
    CAnimationBaseObject* pObject,  
    IUIAnimationVariable* variable,  
    INT32 newValue,  
    INT32 prevValue);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Ukazatel na skupinu animace, která obsahuje objekt animace, jehož hodnota změnila.  
  
 `pObject`  
 Ukazatel na animace objekt, který obsahuje proměnnou animace, jehož hodnota změněna.  
  
 `variable`  
 Ukazatel na proměnnou animace.  
  
 `newValue`  
 Udává novou hodnotu.  
  
 `prevValue`  
 Určuje předchozí hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte animace proměnné události s EnableIntegerValueChangedEvent volat pro konkrétní animace proměnnou nebo objekt animace. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci.  
  
##  <a name="onanimationmanagerstatuschanged"></a>CAnimationController::OnAnimationManagerStatusChanged  
 Voláno rámcem v reakci na StatusChanged události ze Správce animace.  
  
```  
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,  
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Parametry  
 `newStatus`  
 Nový stav manager animace.  
  
 `previousStatus`  
 Předchozí stav manager animace.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte události manager animace s EnableAnimationManagerEvent. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci. Výchozí implementace aktualizuje související okno, pokud je nastavená s SetRelatedWnd.  
  
##  <a name="onanimationtimerpostupdate"></a>CAnimationController::OnAnimationTimerPostUpdate  
 Voláno rámcem po dokončení aktualizace animace.  
  
```  
virtual void OnAnimationTimerPostUpdate();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte obslužné rutiny událostí časovače pomocí EnableAnimationTimerEventHandler. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci.  
  
##  <a name="onanimationtimerpreupdate"></a>CAnimationController::OnAnimationTimerPreUpdate  
 Voláno rámcem před zahájením aktualizace animace.  
  
```  
virtual void OnAnimationTimerPreUpdate();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte obslužné rutiny událostí časovače pomocí EnableAnimationTimerEventHandler. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci.  
  
##  <a name="onanimationtimerrenderingtooslow"></a>CAnimationController::OnAnimationTimerRenderingTooSlow  
 Voláno rámcem při vykreslování snímků za sekundu pro animace klesne pod minimální žádoucí obnovovací frekvence.  
  
```  
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```  
  
### <a name="parameters"></a>Parametry  
 `fps`  
 Aktuální rychlost rámce v snímků za sekundu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte obslužné rutiny událostí časovače pomocí EnableAnimationTimerEventHandler. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci. Volání metody IUIAnimationTimer::SetFrameRateThreshold je zadána minimální žádoucí snímků za sekundu.  
  
##  <a name="onanimationvaluechanged"></a>CAnimationController::OnAnimationValueChanged  
 Voláno rámcem, pokud došlo ke změně hodnoty proměnné animace.  
  
```  
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,  
    CAnimationBaseObject* pObject,  
    IUIAnimationVariable* variable,  
    DOUBLE newValue,  
    DOUBLE prevValue);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Ukazatel na skupinu animace, která obsahuje objekt animace, jehož hodnota změnila.  
  
 `pObject`  
 Ukazatel na animace objekt, který obsahuje proměnnou animace, jehož hodnota změněna.  
  
 `variable`  
 Ukazatel na proměnnou animace.  
  
 `newValue`  
 Udává novou hodnotu.  
  
 `prevValue`  
 Určuje předchozí hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte animace proměnné události s EnableValueChangedEvent volat pro konkrétní animace proměnnou nebo objekt animace. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci.  
  
##  <a name="onbeforeanimationstart"></a>CAnimationController::OnBeforeAnimationStart  
 Voláno rámcem správné předtím, než je naplánováno animace.  
  
```  
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Ukazatel na skupinu animace jejichž animace se chystá spuštění.  
  
### <a name="remarks"></a>Poznámky  
 Toto volání se směruje na související CWnd a může být přepsána nastaveními v odvozené třídě a provádět žádné další akce před spuštěním animace pro zadanou skupinu.  
  
##  <a name="onhasprioritycancel"></a>CAnimationController::OnHasPriorityCancel  
 Voláno rámcem vyřešit konflikty v plánu.  
  
```  
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroupScheduled`  
 Skupinu, která je vlastníkem aktuálně naplánované scénáře.  
  
 `pGroupNew`  
 Skupinu, která je vlastníkem nové scénáře, který je v konfliktu s naplánované storyboard vlastníkem pGroupScheduled plánování.  
  
 `priorityEffect`  
 Potenciální vliv na pGroupNew Pokud pGroupScheduled má vyšší prioritu.  
  
### <a name="return-value"></a>Návratová hodnota  
 By měl vrátit hodnotu TRUE, pokud storyboard vlastníkem pGroupNew má prioritu. By měl vrátit hodnotu FALSE, pokud storyboard vlastníkem pGroupScheduled má prioritu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte událostí porovnání s prioritou pomocí CAnimationController::EnablePriorityComparisonHandler a zadáte UI_ANIMATION_PHT_CANCEL. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci. Dokumentace rozhraní API animace systému Windows pro čtení pro další informace o správě konflikt (http://msdn.microsoft.com/library/dd371759 (VS.85).aspx).  
  
##  <a name="onhasprioritycompress"></a>CAnimationController::OnHasPriorityCompress  
 Voláno rámcem vyřešit konflikty v plánu.  
  
```  
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroupScheduled`  
 Skupinu, která je vlastníkem aktuálně naplánované scénáře.  
  
 `pGroupNew`  
 Skupinu, která je vlastníkem nové scénáře, který je v konfliktu s naplánované storyboard vlastníkem pGroupScheduled plánování.  
  
 `priorityEffect`  
 Potenciální vliv na pGroupNew Pokud pGroupScheduled má vyšší prioritu.  
  
### <a name="return-value"></a>Návratová hodnota  
 By měl vrátit hodnotu TRUE, pokud storyboard vlastníkem pGroupNew má prioritu. By měl vrátit hodnotu FALSE, pokud storyboard vlastníkem pGroupScheduled má prioritu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte událostí porovnání s prioritou pomocí CAnimationController::EnablePriorityComparisonHandler a zadáte UI_ANIMATION_PHT_COMPRESS. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci. Dokumentace rozhraní API animace systému Windows pro čtení pro další informace o správě konflikt (http://msdn.microsoft.com/library/dd371759 (VS.85).aspx).  
  
##  <a name="onhaspriorityconclude"></a>CAnimationController::OnHasPriorityConclude  
 Voláno rámcem vyřešit konflikty v plánu.  
  
```  
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroupScheduled`  
 Skupinu, která je vlastníkem aktuálně naplánované scénáře.  
  
 `pGroupNew`  
 Skupinu, která je vlastníkem nové scénáře, který je v konfliktu s naplánované storyboard vlastníkem pGroupScheduled plánování.  
  
 `priorityEffect`  
 Potenciální vliv na pGroupNew Pokud pGroupScheduled má vyšší prioritu.  
  
### <a name="return-value"></a>Návratová hodnota  
 By měl vrátit hodnotu TRUE, pokud storyboard vlastníkem pGroupNew má prioritu. By měl vrátit hodnotu FALSE, pokud storyboard vlastníkem pGroupScheduled má prioritu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte událostí porovnání s prioritou pomocí CAnimationController::EnablePriorityComparisonHandler a zadáte UI_ANIMATION_PHT_CONCLUDE. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci. Dokumentace rozhraní API animace systému Windows pro čtení pro další informace o správě konflikt (http://msdn.microsoft.com/library/dd371759 (VS.85).aspx).  
  
##  <a name="onhasprioritytrim"></a>CAnimationController::OnHasPriorityTrim  
 Voláno rámcem vyřešit konflikty v plánu.  
  
```  
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroupScheduled`  
 Skupinu, která je vlastníkem aktuálně naplánované scénáře.  
  
 `pGroupNew`  
 Skupinu, která je vlastníkem nové scénáře, který je v konfliktu s naplánované storyboard vlastníkem pGroupScheduled plánování.  
  
 `priorityEffect`  
 Potenciální vliv na pGroupNew Pokud pGroupScheduled má vyšší prioritu.  
  
### <a name="return-value"></a>Návratová hodnota  
 By měl vrátit hodnotu TRUE, pokud storyboard vlastníkem pGroupNew má prioritu. By měl vrátit hodnotu FALSE, pokud storyboard vlastníkem pGroupScheduled má prioritu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte událostí porovnání s prioritou pomocí CAnimationController::EnablePriorityComparisonHandler a zadáte UI_ANIMATION_PHT_TRIM. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci. Dokumentace rozhraní API animace systému Windows pro čtení pro další informace o správě konflikt (http://msdn.microsoft.com/library/dd371759 (VS.85).aspx).  
  
##  <a name="onstoryboardstatuschanged"></a>CAnimationController::OnStoryboardStatusChanged  
 Voláno rámcem, pokud došlo ke změně stavu scénáře.  
  
```  
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,  
    UI_ANIMATION_STORYBOARD_STATUS newStatus,  
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Ukazatel na skupinu animace vlastnící scénáři, jejichž stav se změnil.  
  
 `newStatus`  
 Určuje nový stav.  
  
 `previousStatus`  
 Určuje předchozího stavu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte storyboard událostí pomocí CAnimationController::EnableStoryboardEventHandler. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci.  
  
##  <a name="onstoryboardupdated"></a>CAnimationController::OnStoryboardUpdated  
 Voláno rámcem storyboard po aktualizaci.  
  
```  
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Ukazatel na skupinu, která je vlastníkem scénáři.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, pokud povolíte storyboard událostí pomocí CAnimationController::EnableStoryboardEventHandler. Můžete být přepsání v odvozené třídě a provádět akce specifické pro aplikaci.  
  
##  <a name="removeallanimationgroups"></a>CAnimationController::RemoveAllAnimationGroups  
 Odebere všechny skupiny animace z řadiče animace.  
  
```  
void RemoveAllAnimationGroups();
```  
  
### <a name="remarks"></a>Poznámky  
 Všechny skupiny bude odstranit, jejich ukazatel Pokud uložené na úrovni aplikace, musí být zrušena. Pokud CAnimationGroup::m_bAutodestroyAnimationObjects pro skupinu odstraňuje hodnotu PRAVDA, se odstraní všechny animace objekty, které patří do dané skupiny; v opačném případě jejich odkazy na rodičovský ovladač animace bude nastavena na hodnotu NULL a mohou být přidány do jiného řadiče.  
  
##  <a name="removeanimationgroup"></a>CAnimationController::RemoveAnimationGroup  
 Odebere skupinu animace se zadaným ID z řadiče animace.  
  
```  
void RemoveAnimationGroup(UINT32 nGroupID);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Určuje ID animace skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda Odebere skupinu animace z interní seznam skupin a neodstraní, proto pokud jste uložili ukazatel do této skupiny animace, se musí být zrušena. Pokud CAnimationGroup::m_bAutodestroyAnimationObjects hodnotu PRAVDA, se odstraní všechny animace objekty, které patří do dané skupiny; v opačném případě jejich odkazy na rodičovský ovladač animace bude nastavena na hodnotu NULL a mohou být přidány do jiného řadiče.  
  
##  <a name="removeanimationobject"></a>CAnimationController::RemoveAnimationObject  
 Odeberte objekt animace z řadiče animace.  
  
```  
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,  
    BOOL bNoDelete = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `pObject`  
 Ukazatel na objekt animace.  
  
 `bNoDelete`  
 Pokud tento parametr je TRUE objekt nebudou odstraněna po odebrání.  
  
### <a name="remarks"></a>Poznámky  
 Odebere objekt animace z animace řadiče a skupiny animace. Pokud už by neměl být animovaný určitého objektu nebo pokud potřebujete přesunout objekt na jiný řadič animace volání této funkce. V posledních případu bNoDelete musí být TRUE.  
  
##  <a name="removetransitions"></a>CAnimationController::RemoveTransitions  
 Odebere přechody animace objektů, které patří do zadané skupiny.  
  
```  
void RemoveTransitions(UINT32 nGroupID);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Určuje ID skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Skupina cyklicky prochází přes jeho animace objektů a volá ClearTransitions(FALSE) pro každý objekt animace. Tato metoda je volána rámcem po bylo naplánováno animace.  
  
##  <a name="schedulegroup"></a>CAnimationController::ScheduleGroup  
 Naplánuje animace.  
  
```  
BOOL ScheduleGroup(
    UINT32 nGroupID,  
    UI_ANIMATION_SECONDS time = 0.0);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Určuje ID skupiny při plánování animace.  
  
 `time`  
 Určuje čas při plánování.  
  
### <a name="return-value"></a>Návratová hodnota  
 TRUE, pokud byla úspěšně naplánována animace. FALSE, pokud nebyl vytvořen storyboard nebo dojde k další chybě.  
  
### <a name="remarks"></a>Poznámky  
 AnimateGroup musí volat pomocí parametru bScheduleNow nastavena na hodnotu FALSE předchozí ScheduleGroup. Můžete zadat časový požadované animace získané z IUIAnimationTimer::GetTime. Pokud je parametr čas 0,0, animace naplánován aktuální čas.  
  
##  <a name="setrelatedwnd"></a>CAnimationController::SetRelatedWnd  
 Vytvoří vztah mezi animace řadiče a v okně.  
  
```  
void SetRelatedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Ukazatel na okno objekt, který chcete nastavit.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je související objekt CWnd nastavená, řadičem animace můžete automaticky aktualizovat (Odeslat zprávu WM_PAINT) při došlo ke změně stavu animace manager nebo časovače post aktualizace události.  
  
##  <a name="updateanimationmanager"></a>CAnimationController::UpdateAnimationManager  
 Určí, že správce animace a aktualizujte hodnoty všech proměnných animace.  
  
```  
virtual void UpdateAnimationManager();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání, které tato metoda přejde správce animace aktuální čas, změna stavy scénářů podle potřeby a aktualizace žádné proměnné animace příslušné interpolované hodnoty. Interně tato metoda volá IUIAnimationTimer::GetTime(timeNow) a IUIAnimationManager::Update(timeNow). Potlačí tuto metodu v odvozené třídě přizpůsobit toto chování.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
