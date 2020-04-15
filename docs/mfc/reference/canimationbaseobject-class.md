---
title: CAnimationBaseObject – třída
ms.date: 03/27/2019
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
ms.openlocfilehash: 9581ea142c6f87ae12665374a483abc00763ad97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371125"
---
# <a name="canimationbaseobject-class"></a>CAnimationBaseObject – třída

Základní třída pro všechny objekty animace.

## <a name="syntax"></a>Syntaxe

```
class CAnimationBaseObject : public CObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|Přetíženo. Vytvoří objekt animace.|
|[CAnimationBaseObject::~CAnimationBaseObject](#_dtorcanimationbaseobject)|Destruktor. Nazývá se při zničení objektu animace.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|Přidá přechody do scénáře s zapouzdřenou proměnnou animace.|
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Odebere všechny související přechody.|
|[CanimationBaseObject::Obsahuje proměnnou](#containsvariable)|Určuje, zda objekt animace obsahuje určitou proměnnou animace.|
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Vytvoří přechody přidružené k objektu animace.|
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|Odpojí objekt animace od nadřazeného animačního kontroléru.|
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Nastaví obslužnou rutinu události Integer Value Changed.|
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Nastaví obslužnou rutinu události Value Changed.|
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Určuje, zda jsou související přechody automaticky zničeny.|
|[CanimationBaseObject::GetGroupID](#getgroupid)|Vrátí aktuální ID skupiny.|
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Vrátí aktuální ID objektu.|
|[CAnimationBaseObject::GetUserData](#getuserdata)|Vrátí uživatelem definovaná data.|
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Nastaví příznak, který automaticky zničí přechody.|
|[CanimationBaseObject::SetID](#setid)|Nastaví nová ID.|
|[CAnimationBaseObject::SetUserData](#setuserdata)|Nastaví uživatelem definovaná data.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Shromažďuje ukazatele na obsažené proměnné animace.|
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Vytvoří vztah mezi proměnné animace obsažené v objektu animace a jejich kontejneru.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Určuje, zda mají být související přechody automaticky zničeny.|
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Ukládá uživatelem definovaná data.|
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Určuje ID skupiny objektu animace.|
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Určuje ID objektu animace.|
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Ukazatel na nadřazený ovladač animace.|

## <a name="remarks"></a>Poznámky

Tato třída implementuje základní metody pro všechny objekty animace. Objekt animace může představovat hodnotu, bod, velikost, obdélník nebo barvu v aplikaci, stejně jako všechny vlastní entity. Objekty animace jsou uloženy ve skupinách animací (viz CAnimationGroup). Každá skupina může být animována samostatně a může být považována za analogový scénář. Objekt animace zapouzdřuje jednu nebo více proměnných animace (viz CAnimationVariable), v závislosti na jeho logické reprezentaci. Například CAnimationRect obsahuje čtyři proměnné animace - jednu proměnnou pro každou stranu obdélníku. Každá třída objektu animace zveřejňuje přetížené AddTransition metoda, která by měla být použita k použití přechody zapouzdřené proměnné animace. Objekt animace lze identifikovat podle ID objektu (volitelně) a Podle ID skupiny. ID skupiny je nezbytné k umístění objektu animace pro opravu skupiny, ale pokud není zadáno ID skupiny, je objekt umístěn do výchozí skupiny s ID 0. Pokud zavoláte SetID s jiným GroupID, objekt animace bude přesunut do jiné skupiny (v případě potřeby se vytvoří nová skupina).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="_dtorcanimationbaseobject"></a>CAnimationBaseObject::~CAnimationBaseObject

Destruktor. Nazývá se při zničení objektu animace.

```
virtual ~CAnimationBaseObject();
```

## <a name="canimationbaseobjectapplytransitions"></a><a name="applytransitions"></a>CAnimationBaseObject::ApplyTransitions

Přidá přechody do scénáře s zapouzdřenou proměnnou animace.

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénář.

*bDependOnKeyframes*<br/>
Pokud false, tato metoda přidá pouze ty přechody, které nejsou závislé na klíčových snímků.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byly přechody úspěšně přidány.

### <a name="remarks"></a>Poznámky

Přidá související přechody, které byly přidány s AddTransition (přetížené metody v odvozených třídách), do scénáře.

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="canimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject

Vytvoří objekt animace.

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*nID skupiny*<br/>
Určuje ID skupiny.

*nID objektu*<br/>
Určuje ID objektu.

*dwUserData*<br/>
Uživatelem definovaná data, která mohou být přidružena k objektu animace a načtena později za běhu.

### <a name="remarks"></a>Poznámky

Vytvoří objekty animace a přiřadí výchozí ID objektu (0) a ID skupiny (0).

## <a name="canimationbaseobjectcleartransitions"></a><a name="cleartransitions"></a>CAnimationBaseObject::ClearTransitions

Odebere všechny související přechody.

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parametry

*bAutodestroy*<br/>
Určuje, zda mají být objekty přechodu automaticky zničte nebo je pouze odeberete ze souvisejícího seznamu.

### <a name="remarks"></a>Poznámky

Odebere všechny související přechody a zničí je, pokud bAutodestroy nebo m_bAutodestroyTransitions příznak je PRAVDA. Přechody by měly být zničeny automaticky pouze v případě, že nejsou přiděleny v zásobníku. Pokud jsou výše uvedené příznaky FALSE, přechody jsou právě odebrány z vnitřního seznamu souvisejících přechodů.

## <a name="canimationbaseobjectcontainsvariable"></a><a name="containsvariable"></a>CanimationBaseObject::Obsahuje proměnnou

Určuje, zda objekt animace obsahuje určitou proměnnou animace.

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pProměnná proměnná*<br/>
Ukazatel na proměnnou animace.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je proměnná animace obsažena v objektu animace; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu lze použít k určení, zda je proměnná animace určená parametrem pVariable obsažena v objektu animace. Objekt animace, v závislosti na jeho typu, může obsahovat několik proměnných animace. Například CAnimationColor obsahuje tři proměnné, jednu pro každou barevnou složku (červenou, zelenou a modrou). Pokud se hodnota proměnné animace změnila, rozhraní API animace systému Windows odešle události ValueChanged nebo IntegerValueChanged (pokud je povoleno) a parametr této události je ukazatelem proměnné animace IUIAnimationVariable rozhraní. Tato metoda pomáhá získat ukazatel na animaci z ukazatele obsaženého objektu COM.

## <a name="canimationbaseobjectcreatetransitions"></a><a name="createtransitions"></a>CAnimationBaseObject::CreateTransitions

Vytvoří přechody přidružené k objektu animace.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byly přechody úspěšně vytvořeny; jinak FALSE.

### <a name="remarks"></a>Poznámky

Smyčky přes seznam proměnných animace zapouzdřené v odvozené matné objektu a vytvoří přechody spojené s každou proměnnou animace.

## <a name="canimationbaseobjectdetachfromcontroller"></a><a name="detachfromcontroller"></a>CAnimationBaseObject::DetachFromController

Odpojí objekt animace od nadřazeného animačního kontroléru.

```
void DetachFromController();
```

### <a name="remarks"></a>Poznámky

Tato metoda se používá interně.

## <a name="canimationbaseobjectenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>CAnimationBaseObject::EnableIntegerValueChangedEvent

Nastaví obslužnou rutinu události Integer Value Changed.

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pKontrolér*<br/>
Ukazatel na nadřazený řadič.

*bEnable*<br/>
Určuje, zda má být povolena nebo zakázána událost Integer Value Changed.

### <a name="remarks"></a>Poznámky

Pokud je povolena obslužná rutina události Integer Value Changed, můžete tuto událost zpracovat v metodě CAnimationController::OnAnimationIntegerValueChanged, která by měla být přepsána ve třídě odvozené odvozenou z CAnimationController. Tato metoda se nazývá při každé změně hodnoty celého čísla animace.

## <a name="canimationbaseobjectenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>CAnimationBaseObject::EnableValueChangedEvent

Nastaví obslužnou rutinu události Value Changed.

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pKontrolér*<br/>
Ukazatel na nadřazený řadič.

*bEnable*<br/>
Určuje, zda má být povolena nebo zakázána událost Změna hodnoty.

### <a name="remarks"></a>Poznámky

Pokud je povolena obslužná rutina události Value Changed, můžete zpracovat tuto událost v metodě CAnimationController::OnAnimationValueChanged, která by měla být přepsána v třídě odvozené od CAnimationController. Tato metoda se nazývá pokaždé, když se změnila hodnota animace.

## <a name="canimationbaseobjectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationBaseObject::GetAnimationVariableList

Shromažďuje ukazatele na obsažené proměnné animace.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& list) = 0;
```

### <a name="parameters"></a>Parametry

*list*<br/>
Seznam, který musí být vyplněn proměnnými animace obsaženými v objektu animace.

### <a name="remarks"></a>Poznámky

Tato čistě virtuální metoda musí být přepsána v odvozené třídě. Objekt animace v závislosti na jeho typu obsahuje jednu nebo více proměnných animace. Například CAnimationPoint obsahuje dvě proměnné pro souřadnice X a Y. Základní třída CAnimationBaseObject implementuje některé obecné metody, které působí na seznamu proměnných animace: ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Tyto metody volání GetAnimationVariableList, který je vyplněn v odvozené třídy s aktuální proměnné animace obsažené v konkrétní objekt animace, potom smyčka přes seznam a provést nezbytné akce. Pokud vytvoříte vlastní objekt animace, musíte přidat do *seznamu* všechny proměnné animace obsažené v tomto objektu.

## <a name="canimationbaseobjectgetautodestroytransitions"></a><a name="getautodestroytransitions"></a>CAnimationBaseObject::GetAutodestroyTransitions

Určuje, zda jsou související přechody automaticky zničeny.

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud true, související přechody jsou zničeny automaticky; pokud false, přechod objekty by měly být deallocated voláním aplikace.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je tento příznak TRUE. Nastavte tento příznak pouze v případě, že jste přidělili přechod v zásobníku nebo přechody by měly být přiděleny volající aplikace.

## <a name="canimationbaseobjectgetgroupid"></a><a name="getgroupid"></a>CanimationBaseObject::GetGroupID

Vrátí aktuální ID skupiny.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální ID skupiny.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k načtení ID skupiny. Je to 0, pokud ID skupiny nebyla nastavena explicitně v konstruktoru nebo s SetID.

## <a name="canimationbaseobjectgetobjectid"></a><a name="getobjectid"></a>CAnimationBaseObject::GetObjectID

Vrátí aktuální ID objektu.

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>Návratová hodnota

ID aktuálního objektu.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k načtení ID objektu. Je to 0, pokud ID objektu nebyla nastavena explicitně v konstruktoru nebo s SetID.

## <a name="canimationbaseobjectgetuserdata"></a><a name="getuserdata"></a>CAnimationBaseObject::GetUserData

Vrátí uživatelem definovaná data.

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota vlastních dat.

### <a name="remarks"></a>Poznámky

Volání této metody načíst vlastní data za běhu. Vrácená hodnota bude 0, pokud nebyla explicitně inicializována v konstruktoru nebo s SetUserData.

## <a name="canimationbaseobjectm_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>CAnimationBaseObject::m_bAutodestroyTransitions

Určuje, zda mají být související přechody automaticky zničeny.

```
BOOL m_bAutodestroyTransitions;
```

## <a name="canimationbaseobjectm_dwuserdata"></a><a name="m_dwuserdata"></a>CAnimationBaseObject::m_dwUserData

Ukládá uživatelem definovaná data.

```
DWORD m_dwUserData;
```

## <a name="canimationbaseobjectm_ngroupid"></a><a name="m_ngroupid"></a>CAnimationBaseObject::m_nGroupID

Určuje ID skupiny objektu animace.

```
UINT32 m_nGroupID;
```

## <a name="canimationbaseobjectm_nobjectid"></a><a name="m_nobjectid"></a>CAnimationBaseObject::m_nObjectID

Určuje ID objektu animace.

```
UINT32 m_nObjectID;
```

## <a name="canimationbaseobjectm_pparentcontroller"></a><a name="m_pparentcontroller"></a>CAnimationBaseObject::m_pParentController

Ukazatel na nadřazený ovladač animace.

```
CAnimationController* m_pParentController;
```

## <a name="canimationbaseobjectsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>CAnimationBaseObject::SetAutodestroyTransitions

Nastaví příznak, který automaticky zničí přechody.

```
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>Parametry

*bHodnota*<br/>
Určuje příznak automatického zničení.

### <a name="remarks"></a>Poznámky

Tento příznak nastavte pouze v případě, že jste přidělili objekty přechodu pomocí operátoru new. Pokud z nějakého důvodu přechod objekty jsou přiděleny v zásobníku, auto zničit příznak by měl být FALSE. Ve výchozím nastavení je tento příznak TRUE.

## <a name="canimationbaseobjectsetid"></a><a name="setid"></a>CanimationBaseObject::SetID

Nastaví nová ID.

```
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>Parametry

*nID objektu*<br/>
Určuje nové ID objektu.

*nID skupiny*<br/>
Určuje nové ID skupiny.

### <a name="remarks"></a>Poznámky

Umožňuje změnit ID objektu a ID skupiny. Pokud se nové ID skupiny liší od aktuálního ID, objekt animace se přesune do jiné skupiny (v případě potřeby bude vytvořena nová skupina).

## <a name="canimationbaseobjectsetparentanimationobjects"></a><a name="setparentanimationobjects"></a>CAnimationBaseObject::SetParentAnimationObjects

Vytvoří vztah mezi proměnné animace obsažené v objektu animace a jejich kontejneru.

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>Poznámky

Tento pomocník lze vytvořit vztah mezi proměnné animace obsažené v objektu animace a jejich kontejneru. To smyčky přes proměnné animace a nastaví ukazatel zpět na nadřazený objekt animace na každou proměnnou animace. V aktuální implementaci je skutečný vztah vytvořen v CAnimationBaseObject::ApplyTransitions, proto nejsou nastaveny ukazatele zpět, dokud nezavoláte CAnimationGroup::Animate. Znalost vztahu může být užitečné při zpracování událostí a je třeba získat nadřazený objekt animace z CAnimationVariable. Použijte Proměnnou CAnimation::GetParentAnimationObject.

## <a name="canimationbaseobjectsetuserdata"></a><a name="setuserdata"></a>CAnimationBaseObject::SetUserData

Nastaví uživatelem definovaná data.

```
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>Parametry

*dwUserData*<br/>
Určuje vlastní data.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete přidružit vlastní data k objektu animace. Tato data mohou být načteny později za běhu GetUserData.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
