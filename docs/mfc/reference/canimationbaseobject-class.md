---
title: Canimationbaseobject – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6b1f9ebaa68538486d698204e6d09d39d0bfb0b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062248"
---
# <a name="canimationbaseobject-class"></a>Canimationbaseobject – třída

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
|[Canimationbaseobject –:: ~ canimationbaseobject –](#canimationbaseobject__~canimationbaseobject)|Destruktor. Volá se, když se likviduje objekt animace.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|Přidá přechody do scénáře s proměnnou zapouzdřený animace.|
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Odebere všechny související přechody.|
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|Určuje, zda objekt animace obsahuje proměnnou s konkrétní animace.|
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Vytvoří přechody přidružená k objektu animace.|
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|Odpojí animace objektu z nadřazené řadič animace.|
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Nastaví hodnota celé číslo změněna obslužné rutiny události.|
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Nastaví hodnotu změnit obslužnou rutinu události.|
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Určuje, zda jsou automaticky zničeny související přechodu.|
|[CAnimationBaseObject::GetGroupID](#getgroupid)|Vrátí ID aktuální skupiny.|
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Vrací ID aktuálního objektu.|
|[CAnimationBaseObject::GetUserData](#getuserdata)|Vrátí data definovaná uživatelem.|
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Nastaví příznak, který řadí automaticky zničit přechodů.|
|[CAnimationBaseObject::SetID](#setid)|Nastaví nové identifikátory.|
|[CAnimationBaseObject::SetUserData](#setuserdata)|Uživatelem definované datové sady.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Shromažďuje ukazatelů na proměnné omezením animace.|
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Vytvoří vztah mezi proměnné animace, obsažené v objektu animace a jejich kontejneru.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Určuje, zda související přechody by měl automaticky odstraní.|
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Uživatelem definované datové úložiště.|
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Určuje ID skupiny objektu animace.|
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Určuje ID objektu animace objektu.|
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Ukazatel na rodičovský ovladač animace.|

## <a name="remarks"></a>Poznámky

Tato třída implementuje základní metody pro všechny objekty animace. Animace objektu může představovat hodnotu, bod, velikost, obdélníku nebo barvy v aplikaci, stejně jako všechny vlastní entity. Animace objektů jsou uložené ve skupinách animace (viz canimationgroup –). Každá skupina lze animovat samostatně a lze považovat za analogové scénáře. Animace objektu zapouzdřuje jednu nebo více animace proměnných (viz canimationvariable –), v závislosti na jeho logický reprezentací. Canimationrect – například obsahuje čtyři proměnné animace – jednu proměnnou pro každé straně obdélník. Každá třída objektu animace zpřístupňuje přetěžované metody AddTransition, která se má použít přechody vyrovnat animace zapouzdřené proměnné. Animace objektu lze identifikovat podle ID objektu (volitelně) a ID skupiny. ID skupiny je nutné, aby umístit objekt animace ke správné skupině, ale pokud není zadané ID skupiny, je objekt umístěný ve výchozí skupině s ID 0. Při volání ID sady s jinou GroupID, objekt animace se přesune do jiné skupiny (Nová skupina se vytvoří v případě potřeby).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="_dtorcanimationbaseobject"></a>  Canimationbaseobject –:: ~ canimationbaseobject –

Destruktor. Volá se, když se likviduje objekt animace.

```
virtual ~CAnimationBaseObject();
```

##  <a name="applytransitions"></a>  CAnimationBaseObject::ApplyTransitions

Přidá přechody do scénáře s proměnnou zapouzdřený animace.

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénáře.

*bDependOnKeyframes*<br/>
Tato metoda přidá s FALSE pouze přechody, která nezávisí na klíčové snímky.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byly úspěšně přidány přechodů.

### <a name="remarks"></a>Poznámky

Přidá související přechody, které byly přidány s AddTransition (přetížené metody v odvozených třídách), do scénáře.

##  <a name="canimationbaseobject"></a>  CAnimationBaseObject::CAnimationBaseObject

Vytvoří objekt animace.

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Určuje ID skupiny.

*nObjectID*<br/>
Určuje ID objektu.

*dwUserData*<br/>
Data definovaná uživatelem, které mohou být přidružený k objektu animace a později načíst za běhu.

### <a name="remarks"></a>Poznámky

Vytvoří objekty animace a přiřadí výchozí ID objektu (0) a ID skupiny (0).

##  <a name="cleartransitions"></a>  CAnimationBaseObject::ClearTransitions

Odebere všechny související přechody.

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parametry

*bAutodestroy*<br/>
Určuje, jestli se má zničit objekty přechod automaticky, nebo je odebrat ze seznamu související.

### <a name="remarks"></a>Poznámky

Odebere všechny související přechody a odstraní je bAutodestroy nebo m_bAutodestroyTransitions příznak-li hodnotu TRUE. Přechody by měl automaticky zničeny, pouze v případě, že nejsou přiděleny v zásobníku. Pokud výše uvedené příznaky jsou FALSE, přechody se odeberou jenom z interní seznam souvisejících přechody.

##  <a name="containsvariable"></a>  CAnimationBaseObject::ContainsVariable

Určuje, zda objekt animace obsahuje proměnnou s konkrétní animace.

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pVariable*<br/>
Ukazatel na proměnnou animace.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je obsažen proměnné animace v objektu animace. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k určení, zda je proměnnou animace určené pVariable obsažené v objektu animace. Objekt animace, v závislosti na jeho typu, může obsahovat několik proměnné animace. Canimationcolor – například obsahuje tří proměnných, jedna pro každou složku barvy (červené, zelené a modré). Při změně hodnoty proměnné animace, rozhraní API animace Windows odešle ValueChanged nebo IntegerValueChanged událostí (je-li povoleno) a parametr této události je ukazatel na rozhraní IUIAnimationVariable proměnné animace. Tato metoda umožňuje získat ukazatel na animaci z ukazatele na obsaženého objektu modelu COM.

##  <a name="createtransitions"></a>  CAnimationBaseObject::CreateTransitions

Vytvoří přechody přidružená k objektu animace.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud úspěšně; vytvořily přechody v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Cyklickému seznam proměnných animace zapouzdřené v objektu odvozené animace a přechody spojené s každou proměnnou animace vytvoří.

##  <a name="detachfromcontroller"></a>  CAnimationBaseObject::DetachFromController

Odpojí animace objektu z nadřazené řadič animace.

```
void DetachFromController();
```

### <a name="remarks"></a>Poznámky

Tato metoda se používá interně.

##  <a name="enableintegervaluechangedevent"></a>  CAnimationBaseObject::EnableIntegerValueChangedEvent

Nastaví hodnota celé číslo změněna obslužné rutiny události.

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Ukazatel na rodičovský ovladač.

*bEnable*<br/>
Určuje, jestli se má povolit nebo zakázat událost celočíselnou hodnotu změnit.

### <a name="remarks"></a>Poznámky

Pokud je povolená hodnota celé číslo změněna obslužná rutina události, může zpracování této události v CAnimationController::OnAnimationIntegerValueChanged metodě, která by měla být potlačena ve třídě odvozené canimationcontroller –. Tato metoda je volána pokaždé, když se změní animace celočíselnou hodnotu.

##  <a name="enablevaluechangedevent"></a>  CAnimationBaseObject::EnableValueChangedEvent

Nastaví hodnotu změnit obslužnou rutinu události.

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Ukazatel na rodičovský ovladač.

*bEnable*<br/>
Určuje, zda chcete povolit nebo zakázat události hodnotu změnit.

### <a name="remarks"></a>Poznámky

Pokud je povolená hodnota změněna obslužná rutina události, může zpracování této události v CAnimationController::OnAnimationValueChanged metodě, která by měla být potlačena ve třídě odvozené canimationcontroller –. Tato metoda je volána pokaždé, když se změní hodnota animace.

##  <a name="getanimationvariablelist"></a>  CAnimationBaseObject::GetAnimationVariableList

Shromažďuje ukazatelů na proměnné omezením animace.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst) = 0;
```

### <a name="parameters"></a>Parametry

*obrázků*<br/>
Seznam, který musí být vyplněn proměnné animace obsažená v objektu animace.

### <a name="remarks"></a>Poznámky

To se čistě virtuální metody, které se musí přepsat v odvozené třídě. Objekt animace, v závislosti na jeho typu, obsahuje jeden nebo více proměnné animace. Canimationpoint – například obsahuje dvě proměnné, pro souřadnice v uvedeném pořadí X a Y. Canimationbaseobject – základní třída implementuje některé obecné metody, které fungují na seznam proměnné animace: ApplyTransitions ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Tyto metody volat GetAnimationVariableList, což je vyplněna v odvozené třídě skutečné animace proměnné obsažené v objektu konkrétní animace, pak v seznamu ve smyčce a provádět potřebné akce. Pokud vytvoříte vlastní animace objektu, musíte přidat do obrázků všechny proměnné animace obsažené v tomto objektu.

##  <a name="getautodestroytransitions"></a>  CAnimationBaseObject::GetAutodestroyTransitions

Určuje, zda jsou automaticky zničeny související přechodu.

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>Návratová hodnota

Při hodnotě TRUE se související přechody jsou zničeny automaticky. Pokud má hodnotu FALSE, přechod objektů by měl uvolnit voláním aplikace.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je tento příznak hodnotu TRUE. Tento příznak nastavte pouze v případě, že jste přidělili přechod do zásobníku a/nebo přechody by měla být odebrána volající aplikací.

##  <a name="getgroupid"></a>  CAnimationBaseObject::GetGroupID

Vrátí ID aktuální skupiny.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Návratová hodnota

ID aktuální skupiny.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k načtení ID skupiny. To je 0, pokud ID skupiny není nastavený explicitně v konstruktoru nebo ID sady.

##  <a name="getobjectid"></a>  CAnimationBaseObject::GetObjectID

Vrací ID aktuálního objektu.

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>Návratová hodnota

ID aktuálního objektu.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k získání ID objektu. To je 0, pokud je ID objektu není nastavený explicitně v konstruktoru nebo ID sady.

##  <a name="getuserdata"></a>  CAnimationBaseObject::GetUserData

Vrátí data definovaná uživatelem.

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota vlastní data.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem získání vlastních dat za běhu. Vrácená hodnota bude 0, pokud nebyl inicializován jako explicitně v konstruktoru nebo s SetUserData.

##  <a name="m_bautodestroytransitions"></a>  CAnimationBaseObject::m_bAutodestroyTransitions

Určuje, zda související přechody by měl automaticky odstraní.

```
BOOL m_bAutodestroyTransitions;
```

##  <a name="m_dwuserdata"></a>  CAnimationBaseObject::m_dwUserData

Uživatelem definované datové úložiště.

```
DWORD m_dwUserData;
```

##  <a name="m_ngroupid"></a>  CAnimationBaseObject::m_nGroupID

Určuje ID skupiny objektu animace.

```
UINT32 m_nGroupID;
```

##  <a name="m_nobjectid"></a>  CAnimationBaseObject::m_nObjectID

Určuje ID objektu animace objektu.

```
UINT32 m_nObjectID;
```

##  <a name="m_pparentcontroller"></a>  CAnimationBaseObject::m_pParentController

Ukazatel na rodičovský ovladač animace.

```
CAnimationController* m_pParentController;
```

##  <a name="setautodestroytransitions"></a>  CAnimationBaseObject::SetAutodestroyTransitions

Nastaví příznak, který řadí automaticky zničit přechodů.

```
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>Parametry

*bValue*<br/>
Určuje, automatické zničení příznak.

### <a name="remarks"></a>Poznámky

Tento příznak nastavte pouze v případě, že jste přidělili přechod objekty pomocí operátoru nové. Pokud z nějakého důvodu, které jsou přidělené objekty přechod do zásobníku, automatické zničení příznak by měl mít hodnotu FALSE. Ve výchozím nastavení je tento příznak hodnotu TRUE.

##  <a name="setid"></a>  CAnimationBaseObject::SetID

Nastaví nové identifikátory.

```
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>Parametry

*nObjectID*<br/>
Určuje ID nového objektu.

*nGroupID*<br/>
Určuje ID nové skupiny.

### <a name="remarks"></a>Poznámky

Umožňuje změnit ID objektu a ID skupiny. Pokud nové ID skupiny se liší od aktuální ID, je objekt animace přesunout do jiné skupiny (Nová skupina bude vytvořena, v případě potřeby).

##  <a name="setparentanimationobjects"></a>  CAnimationBaseObject::SetParentAnimationObjects

Vytvoří vztah mezi proměnné animace, obsažené v objektu animace a jejich kontejneru.

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>Poznámky

Toto je pomocné rutiny, který slouží k navázání vztahu mezi proměnné animace, obsažené v objektu animace a jejich kontejneru. Cyklickému proměnné animace a nastaví zpětný ukazatel na nadřazený objekt animace ke každé proměnné animace. V aktuální implementaci navazovat v CAnimationBaseObject::ApplyTransitions skutečný vztah proto back ukazatele nejsou nastavená, až do okamžiku volání CAnimationGroup::Animate. Znalost vztahů mohou být užitečné, když je zpracování událostí a nemusí, aby získali animace nadřazeného objektu z canimationvariable – (použijte CAnimationVariable::GetParentAnimationObject).

##  <a name="setuserdata"></a>  CAnimationBaseObject::SetUserData

Uživatelem definované datové sady.

```
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>Parametry

*dwUserData*<br/>
Určuje vlastní data.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k přidružení vlastních dat k objektu animace. Tato data mohou být později načíst za běhu pomocí metody GetUserData.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
