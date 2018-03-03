---
title: "Třída CAnimationBaseObject | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35af11c38c70513cb2225bbeb8e74c4ab61c8cc5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="canimationbaseobject-class"></a>CAnimationBaseObject – třída
Základní třída pro všechny objekty animace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationBaseObject : public CObject;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|Přetíženo. Vytvoří objekt animace.|  
|[CAnimationBaseObject:: ~ CAnimationBaseObject](#canimationbaseobject__~canimationbaseobject)|Destruktor. Voláno, když je zničen objekt animace.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|Přidá přechody do scénáře s proměnnou zapouzdřené animace.|  
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Odebere všechny související přechody.|  
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|Určuje, zda objekt animace obsahuje proměnnou konkrétní animace.|  
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Vytvoří přechody přidružená k objektu animace.|  
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|Umožňuje odpojit objekt animace z nadřazené animace řadiče.|  
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Nastaví obslužnou rutinu události celočíselnou hodnotu změnit.|  
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Nastaví hodnotu změnit obslužné rutiny události.|  
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Určuje, zda jsou související přechodu zničen automaticky.|  
|[CAnimationBaseObject::GetGroupID](#getgroupid)|Vrátí aktuální ID skupiny.|  
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Vrátí aktuální ID objektu.|  
|[CAnimationBaseObject::GetUserData](#getuserdata)|Vrátí data o definované uživatelem.|  
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Nastaví příznak, který řadí automaticky zrušení přechody.|  
|[CAnimationBaseObject::SetID](#setid)|Nastaví nové ID.|  
|[CAnimationBaseObject::SetUserData](#setuserdata)|Uživatelem definované datové sady.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Shromažďuje ukazatele do proměnné obsažené animace.|  
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Vytvoří vztah mezi animace proměnné, obsažené v objektu animace a jejich kontejneru.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Určuje, zda související přechody by měl být automaticky způsobem zničena.|  
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Uživatelem definované datové úložiště.|  
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Určuje ID skupiny objektu animace.|  
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Určuje Identifikátor objektu objektu animace.|  
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Ukazatel na rodičovský ovladač animace.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída implementuje základní metody pro všechny objekty animace. Objekt animace může představovat hodnotu, bod, velikost, obdélníku nebo barvy v aplikaci, jakož i vlastní entitu. Animace objektů jsou uloženy ve skupinách animace (viz CAnimationGroup). Každá skupina může být animovaný samostatně a lze zacházet jako analogovým scénáře. Zapouzdří objekt animace jeden nebo více animace proměnné (viz CAnimationVariable), v závislosti na jeho logické zastoupení. Například CAnimationRect obsahuje čtyři proměnné animace – pro každé straně obdélníku jednu proměnnou. Každá třída objektu animace zpřístupní přetížené AddTransition metoda, která se má použít pro použití přechody zapouzdřené animace proměnné. Objekt animace lze identifikovat podle ID objektu (volitelně) a ID skupiny. ID skupiny je nezbytné, aby se umístit objekt animace do správné skupiny, ale pokud není zadán ID skupiny, objekt je umístěn ve výchozí skupině s ID 0. Při volání ID sady s jinou GroupID, přesunou se objekt animace do jiné skupiny (nové skupiny se vytvoří v případě potřeby).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationBaseObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationbaseobject"></a>CAnimationBaseObject:: ~ CAnimationBaseObject  
 Destruktor. Voláno, když je zničen objekt animace.  
  
```  
virtual ~CAnimationBaseObject();
```  
  
##  <a name="applytransitions"></a>CAnimationBaseObject::ApplyTransitions  
 Přidá přechody do scénáře s proměnnou zapouzdřené animace.  
  
```  
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Ukazatel na scénář.  
  
 `bDependOnKeyframes`  
 Tato metoda s FALSE přidá jenom přechody, které jsou nezávislé na klíčových snímků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud přechody bylo úspěšně přidáno.  
  
### <a name="remarks"></a>Poznámky  
 Přidá související přechody, které byly přidány s AddTransition (přetížené metody v odvozených třídách), do scénáře.  
  
##  <a name="canimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject  
 Vytvoří objekt animace.  
  
```  
CAnimationBaseObject();

 
CAnimationBaseObject(
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Určuje ID skupiny.  
  
 `nObjectID`  
 Určuje ID objektu.  
  
 `dwUserData`  
 Uživatelem definované datové, kterému může být přidružené k objektu animace a načíst později za běhu.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří stavu animace objekty a přiřadí výchozí ID objektu (0) a ID skupiny (0).  
  
##  <a name="cleartransitions"></a>CAnimationBaseObject::ClearTransitions  
 Odebere všechny související přechody.  
  
```  
virtual void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>Parametry  
 `bAutodestroy`  
 Určuje, jestli zničit přechod objekty automaticky, nebo je odeberte ze seznamu související.  
  
### <a name="remarks"></a>Poznámky  
 Odebere všechny související přechody a zničí, je-li bAutodestroy nebo m_bAutodestroyTransitions příznak hodnotu PRAVDA. Přechody by měl být zničený automaticky pouze v případě, že jsou přiděleny v zásobníku. Pokud jsou výše příznaky hodnotu FALSE, jsou přechody právě odebrat ze seznamu interní související přechodů.  
  
##  <a name="containsvariable"></a>CAnimationBaseObject::ContainsVariable  
 Určuje, zda objekt animace obsahuje proměnnou konkrétní animace.  
  
```  
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>Parametry  
 `pVariable`  
 Ukazatel na proměnnou animace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je proměnná animace obsažené v objektu animace; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda slouží k určení, zda je proměnná animace určeného pVariable obsažené v objektu animace. Objekt animace, v závislosti na jeho typu může obsahovat několik proměnné animace. Například CAnimationColor obsahuje tři proměnné, jeden pro každou součást barvy (červená, zelená a modré). Při změně hodnoty proměnné animace, rozhraní API systému Windows animace odešle ValueChanged nebo IntegerValueChanged události (Pokud je povoleno) a parametr Tato událost je ukazatel na rozhraní IUIAnimationVariable proměnné animace. Tato metoda pomáhá získat ukazatel k animace z ukazatel na obsažený objekt COM.  
  
##  <a name="createtransitions"></a>CAnimationBaseObject::CreateTransitions  
 Vytvoří přechody přidružená k objektu animace.  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud přechody byly vytvořeny úspěšně; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Cyklicky prochází přes seznam proměnných animace zapouzdřené v objektu odvozené animace a vytvoří přechody spojené s každou proměnnou animace.  
  
##  <a name="detachfromcontroller"></a>CAnimationBaseObject::DetachFromController  
 Umožňuje odpojit objekt animace z nadřazené animace řadiče.  
  
```  
void DetachFromController();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se používá interně.  
  
##  <a name="enableintegervaluechangedevent"></a>CAnimationBaseObject::EnableIntegerValueChangedEvent  
 Nastaví obslužnou rutinu události celočíselnou hodnotu změnit.  
  
```  
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `pController`  
 Ukazatel na rodičovský ovladač.  
  
 `bEnable`  
 Určuje, jestli chcete povolit nebo zakázat událostí celočíselnou hodnotu změnit.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je povoleno obslužné rutiny události celočíselnou hodnotu změnit, může zpracovávat Tato událost CAnimationController::OnAnimationIntegerValueChanged metoda, která by měla být potlačena do CAnimationController odvozené třídy. Tato metoda je volána pokaždé, když došlo ke změně animace celočíselnou hodnotu.  
  
##  <a name="enablevaluechangedevent"></a>CAnimationBaseObject::EnableValueChangedEvent  
 Nastaví hodnotu změnit obslužné rutiny události.  
  
```  
virtual void EnableValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `pController`  
 Ukazatel na rodičovský ovladač.  
  
 `bEnable`  
 Určuje, jestli chcete povolit nebo zakázat událostí hodnotu změnit.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je hodnota změněna obslužné rutiny události je povoleno, může zpracovávat Tato událost CAnimationController::OnAnimationValueChanged metoda, která by měla být potlačena do CAnimationController odvozené třídy. Tato metoda je volána pokaždé, když došlo ke změně hodnoty animace.  
  
##  <a name="getanimationvariablelist"></a>CAnimationBaseObject::GetAnimationVariableList  
 Shromažďuje ukazatele do proměnné obsažené animace.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `lst`  
 Seznam, který musí být vyplněn animace proměnné obsažená v objektu animace.  
  
### <a name="remarks"></a>Poznámky  
 Toto je čistě virtuální metodu, která musí být přepsána nastaveními v odvozené třídě. Objekt animace, v závislosti na jeho typu, obsahuje jeden nebo více proměnných animace. Například CAnimationPoint obsahuje dvě proměnné pro X a Y koordinuje v uvedeném pořadí. Základní třída CAnimationBaseObject implementuje některé obecné metody, které jednají na seznam proměnných animace: ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Tyto metody volání GetAnimationVariableList, který je vyplněn v odvozené třídě skutečné animace proměnné obsažené v objektu konkrétní animace, potom smyčku seznamu a provádět potřebné akce. Pokud vytvoříte vlastní animace objektu, musíte přidat do obrázků všechny proměnné animace obsažené v objektu.  
  
##  <a name="getautodestroytransitions"></a>CAnimationBaseObject::GetAutodestroyTransitions  
 Určuje, zda jsou související přechodu zničen automaticky.  
  
```  
BOOL GetAutodestroyTransitions() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě hodnoty TRUE, jsou automaticky; zničen související přechody Když má hodnotu FALSE, přechod objekty by měl být navrácena voláním aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tento příznak má hodnotu TRUE. Tento příznak nastavte jenom v případě, že jste přidělili přechod v zásobníku a přechody by měl být navrácena volající aplikací.  
  
##  <a name="getgroupid"></a>CAnimationBaseObject::GetGroupID  
 Vrátí aktuální ID skupiny.  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 ID aktuální skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k načtení ID skupiny. Je-li ID skupiny není explicitně nastavena v konstruktoru nebo s ID sady je 0.  
  
##  <a name="getobjectid"></a>CAnimationBaseObject::GetObjectID  
 Vrátí aktuální ID objektu.  
  
```  
UINT32 GetObjectID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální ID objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k načtení ID objektu. To je 0, pokud ID objektu nebyl nastaven explicitně v konstruktoru nebo s ID sady.  
  
##  <a name="getuserdata"></a>CAnimationBaseObject::GetUserData  
 Vrátí data o definované uživatelem.  
  
```  
DWORD GetUserData() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota vlastní data.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem načtení vlastních dat za běhu. Vrácená hodnota bude 0, pokud nebyl inicializován jako explicitně v konstruktoru nebo s SetUserData.  
  
##  <a name="m_bautodestroytransitions"></a>CAnimationBaseObject::m_bAutodestroyTransitions  
 Určuje, zda související přechody by měl být automaticky způsobem zničena.  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
##  <a name="m_dwuserdata"></a>CAnimationBaseObject::m_dwUserData  
 Uživatelem definované datové úložiště.  
  
```  
DWORD m_dwUserData;  
```  
  
##  <a name="m_ngroupid"></a>CAnimationBaseObject::m_nGroupID  
 Určuje ID skupiny objektu animace.  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_nobjectid"></a>CAnimationBaseObject::m_nObjectID  
 Určuje Identifikátor objektu objektu animace.  
  
```  
UINT32 m_nObjectID;  
```  
  
##  <a name="m_pparentcontroller"></a>CAnimationBaseObject::m_pParentController  
 Ukazatel na rodičovský ovladač animace.  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="setautodestroytransitions"></a>CAnimationBaseObject::SetAutodestroyTransitions  
 Nastaví příznak, který řadí automaticky zrušení přechody.  
  
```  
void SetAutodestroyTransitions(BOOL bValue);
```  
  
### <a name="parameters"></a>Parametry  
 `bValue`  
 Určuje automatického destroy příznak.  
  
### <a name="remarks"></a>Poznámky  
 Tento příznak nastavte jenom v případě, že jste přidělili přechod objektů pomocí operátoru nové. Pokud z nějakého důvodu přechodu objekty jsou přidělené v zásobníku, automatické zrušení příznak by měl být FALSE. Ve výchozím nastavení tento příznak má hodnotu TRUE.  
  
##  <a name="setid"></a>CAnimationBaseObject::SetID  
 Nastaví nové ID.  
  
```  
void SetID(
    UINT32 nObjectID,  
    UINT32 nGroupID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nObjectID`  
 Určuje ID nového objektu.  
  
 `nGroupID`  
 Určuje ID nové skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Umožňuje změnit ID objektu a ID skupiny. Pokud toto nové ID skupiny se liší od aktuální ID, objekt animace je přesunout do jiné skupiny (Nová skupina bude vytvořena, v případě potřeby).  
  
##  <a name="setparentanimationobjects"></a>CAnimationBaseObject::SetParentAnimationObjects  
 Vytvoří vztah mezi animace proměnné, obsažené v objektu animace a jejich kontejneru.  
  
```  
virtual void SetParentAnimationObjects();
```  
  
### <a name="remarks"></a>Poznámky  
 Toto je pomocná, který slouží k navázání vztahu mezi animace proměnné, obsažené v objektu animace a jejich kontejneru. To cyklicky prochází přes animace proměnné a nastaví zpětný ukazatel na nadřazeného objektu animace pro každou proměnnou animace. V aktuální implementace, které skutečný vztah se nastavuje CAnimationBaseObject::ApplyTransitions proto back ukazatele nejsou nastavená, dokud volání CAnimationGroup::Animate. Znalost relace může být užitečné, když jste zpracování události a potřeba získat animace nadřazený objekt z CAnimationVariable (použijte CAnimationVariable::GetParentAnimationObject).  
  
##  <a name="setuserdata"></a>CAnimationBaseObject::SetUserData  
 Uživatelem definované datové sady.  
  
```  
void SetUserData (DWORD dwUserData);
```  
  
### <a name="parameters"></a>Parametry  
 `dwUserData`  
 Určuje vlastní data.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k přidružení vlastních dat k objektu animace. Tato data může být později načíst za běhu pomocí metody GetUserData.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
