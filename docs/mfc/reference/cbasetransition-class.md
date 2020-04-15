---
title: CBaseTransition – třída
ms.date: 03/27/2019
f1_keywords:
- CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboardAtKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::Clear
- AFXANIMATIONCONTROLLER/CBaseTransition::Create
- AFXANIMATIONCONTROLLER/CBaseTransition::GetEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::GetStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::GetType
- AFXANIMATIONCONTROLLER/CBaseTransition::IsAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::SetKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::SetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_transition
- AFXANIMATIONCONTROLLER/CBaseTransition::m_type
helpviewer_keywords:
- CBaseTransition [MFC], CBaseTransition
- CBaseTransition [MFC], AddToStoryboard
- CBaseTransition [MFC], AddToStoryboardAtKeyframes
- CBaseTransition [MFC], Clear
- CBaseTransition [MFC], Create
- CBaseTransition [MFC], GetEndKeyframe
- CBaseTransition [MFC], GetRelatedVariable
- CBaseTransition [MFC], GetStartKeyframe
- CBaseTransition [MFC], GetTransition
- CBaseTransition [MFC], GetType
- CBaseTransition [MFC], IsAdded
- CBaseTransition [MFC], SetKeyframes
- CBaseTransition [MFC], SetRelatedVariable
- CBaseTransition [MFC], m_bAdded
- CBaseTransition [MFC], m_pEndKeyframe
- CBaseTransition [MFC], m_pRelatedVariable
- CBaseTransition [MFC], m_pStartKeyframe
- CBaseTransition [MFC], m_transition
- CBaseTransition [MFC], m_type
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
ms.openlocfilehash: 8339785fd10fa3dcef1c0fb573310762dc2d2405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352836"
---
# <a name="cbasetransition-class"></a>CBaseTransition – třída

Představuje základní přechod.

## <a name="syntax"></a>Syntaxe

```
class CBaseTransition : public CObject;
```

## <a name="members"></a>Členové

### <a name="public-enumerations"></a>Veřejné výčty

|Name (Název)|Popis|
|----------|-----------------|
|[CBaseTransition::TRANSITION_TYPE Výčet](#transition_type_enumeration)|Definuje typy přechodů, které aktuálně podporuje implementace knihovny MFC rozhraní API pro animaci systému Windows.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CBaseTransition::CBaseTransition](#cbasetransition)|Vytvoří základní přechodový objekt.|
|[CBaseTransition::~CBaseTransition](#_dtorcbasetransition)|Destruktor. Nazývá se při zničení objektu přechodu.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|Přidá přechod do scénáře.|
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Přidá přechod do scénáře.|
|[CBaseTransition::Vymazat](#clear)|Uvolňuje zapouzdřený objekt Com IUIAnimationTransition.|
|[CBaseTransition::Vytvořit](#create)|Vytvoří přechod com.|
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|Vrátí počáteční klíčový snímek.|
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|Vrátí ukazatel na související proměnnou.|
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|Vrátí počáteční klíčový snímek.|
|[CBaseTransition::GetTransition](#gettransition)|Přetíženo. Vrátí ukazatel na základní objekt přechodu COM.|
|[CBaseTransition::GetType](#gettype)|Vrátí typ přechodu.|
|[CBaseTransition::Jepřidán](#isadded)|Určuje, zda byl přechod přidán do scénáře.|
|[CBaseTransition::SetKeyframes](#setkeyframes)|Nastaví klíčové snímky pro přechod.|
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|Vytvoří vztah mezi proměnnou animace a přechodem.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CBaseTransition::m_bAdded](#m_badded)|Určuje, zda byl přechod přidán do scénáře.|
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|Uloží ukazatel na klíčový snímek, který určuje konec přechodu.|
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|Ukazatel na proměnnou animace, která je animována s přechodem uloženým v m_transition.|
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|Uloží ukazatel na klíčový snímek, který určuje začátek přechodu.|
|[CBaseTransition::m_transition](#m_transition)|Ukládá ukazatel na IUIAnimationTransition. Null, pokud objekt přechodu COM nebyl vytvořen.|
|[CBaseTransition::m_type](#m_type)|Ukládá typ přechodu.|

## <a name="remarks"></a>Poznámky

Tato třída zapouzdřuje rozhraní IUIAnimationTransition a slouží jako základní třída pro všechny přechody.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="cbasetransitioncbasetransition"></a><a name="_dtorcbasetransition"></a>CBaseTransition::~CBaseTransition

Destruktor. Nazývá se při zničení objektu přechodu.

```
virtual ~CBaseTransition();
```

## <a name="cbasetransitionaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseTransition::AddToStoryboard

Přidá přechod do scénáře.

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénář, který animuje související proměnnou.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud přechod byl úspěšně přidán do scénáře.

### <a name="remarks"></a>Poznámky

Aplikuje přechod na související proměnnou ve scénáři. Pokud se jedná o první přechod použitý na tuto proměnnou v tomto scénáři, přechod začíná na začátku scénáře. V opačném případě je přechod připojen k přechodu, který byl naposledy přidán do proměnné.

## <a name="cbasetransitionaddtostoryboardatkeyframes"></a><a name="addtostoryboardatkeyframes"></a>CBaseTransition::AddToStoryboardAtKeyframes

Přidá přechod do scénáře.

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénář, který animuje související proměnnou.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud přechod byl úspěšně přidán do scénáře.

### <a name="remarks"></a>Poznámky

Aplikuje přechod na související proměnnou ve scénáři. Pokud byl zadán počáteční klíčový snímek, přechod začíná v tomto klíčovém snímku. Pokud byl zadán koncový klíčový snímek, přechod začíná na počátečním klíčovém snímku a zastaví se na koncovém klíčovém snímku. Pokud byl přechod vytvořen se zadaným parametrem doby trvání, je tato doba trvání přepsána dobou mezi počátečním a koncovým klíčovým snímky. Pokud nebyl zadán žádný klíčový snímek, je přechod připojen k přechodu, který byl naposledy přidán do proměnné.

## <a name="cbasetransitioncbasetransition"></a><a name="cbasetransition"></a>CBaseTransition::CBaseTransition

Vytvoří základní přechodový objekt.

```
CBaseTransition();
```

## <a name="cbasetransitionclear"></a><a name="clear"></a>CBaseTransition::Vymazat

Uvolňuje zapouzdřený objekt Com IUIAnimationTransition.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

Tato metoda by měla být volána z metody Create odvozené třídy, aby se zabránilo nevracení rozhraní IUITransition.

## <a name="cbasetransitioncreate"></a><a name="create"></a>CBaseTransition::Vytvořit

Vytvoří přechod com.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>Parametry

*pKnihovna*<br/>
Ukazatel na knihovnu přechodů, která vytváří standardní přechody. Může být NULL pro vlastní přechody.

*pFactory*<br/>
Ukazatel na továrnu přechodu, která vytváří vlastní přechody. Může být NULL pro standardní přechody.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl objekt com přechodu úspěšně vytvořen; jinak FALSE.

### <a name="remarks"></a>Poznámky

Toto je čistě virtuální funkce, která musí být přepsána v odvozené třídě. Je volána rámci k vytvoření instance základní objekt přechodu COM.

## <a name="cbasetransitiongetendkeyframe"></a><a name="getendkeyframe"></a>CBaseTransition::GetEndKeyframe

Vrátí počáteční klíčový snímek.

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na klíčový snímek nebo null, pokud přechod by neměl být vložen mezi klíčové snímky.

### <a name="remarks"></a>Poznámky

Tuto metodu lze použít pro přístup k objektu klíčového snímku, který byl dříve nastaven SetKeyframes. Je volána kódnejvyšší úrovně při přechody jsou přidávány do scénáře.

## <a name="cbasetransitiongetrelatedvariable"></a><a name="getrelatedvariable"></a>CBaseTransition::GetRelatedVariable

Vrátí ukazatel na související proměnnou.

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na proměnnou animace nebo NULL, pokud proměnná animace nebyla nastavena hodnotou SetRelatedVariable.

### <a name="remarks"></a>Poznámky

Toto je přistupující objekt k související proměnné animace.

## <a name="cbasetransitiongetstartkeyframe"></a><a name="getstartkeyframe"></a>CBaseTransition::GetStartKeyframe

Vrátí počáteční klíčový snímek.

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na klíčový snímek nebo NULL, pokud přechod by neměl začít po klíčový snímek.

### <a name="remarks"></a>Poznámky

Tuto metodu lze použít pro přístup k objektu klíčového snímku, který byl dříve nastaven SetKeyframes. Je volána kódnejvyšší úrovně při přechody jsou přidávány do scénáře.

## <a name="cbasetransitiongettransition"></a><a name="gettransition"></a>CBaseTransition::GetTransition

Vrátí ukazatel na základní objekt přechodu COM.

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>Parametry

*pKnihovna*<br/>
Ukazatel na knihovnu přechodů, která vytváří standardní přechody. Může být NULL pro vlastní přechody.

*pFactory*<br/>
Ukazatel na továrnu přechodu, která vytváří vlastní přechody. Může být NULL pro standardní přechody.

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na IUIAnimationTransition nebo NULL, pokud základní přechod nelze vytvořit.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí ukazatel na základní objekt přechodu COM a v případě potřeby jej vytvoří.

## <a name="cbasetransitiongettype"></a><a name="gettype"></a>CBaseTransition::GetType

Vrátí typ přechodu.

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>Návratová hodnota

Jedna z TRANSITION_TYPE vyčíslených hodnot.

### <a name="remarks"></a>Poznámky

Tuto metodu lze použít k identifikaci objektu přechodu podle jeho typu. Typ je nastaven v konstruktoru v odvozené třídě.

## <a name="cbasetransitionisadded"></a><a name="isadded"></a>CBaseTransition::Jepřidán

Určuje, zda byl přechod přidán do scénáře.

```
BOOL IsAdded();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byl do scénáře přidán přechod, jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tento příznak je nastaven interně při kódu nejvyšší úrovně přidá přechody do scénáře.

## <a name="cbasetransitionm_badded"></a><a name="m_badded"></a>CBaseTransition::m_bAdded

Určuje, zda byl přechod přidán do scénáře.

```
BOOL m_bAdded;
```

## <a name="cbasetransitionm_pendkeyframe"></a><a name="m_pendkeyframe"></a>CBaseTransition::m_pEndKeyframe

Uloží ukazatel na klíčový snímek, který určuje konec přechodu.

```
CBaseKeyFrame* m_pEndKeyframe;
```

## <a name="cbasetransitionm_prelatedvariable"></a><a name="m_prelatedvariable"></a>CBaseTransition::m_pRelatedVariable

Ukazatel na proměnnou animace, která je animována s přechodem uloženým v m_transition.

```
CAnimationVariable* m_pRelatedVariable;
```

## <a name="cbasetransitionm_pstartkeyframe"></a><a name="m_pstartkeyframe"></a>CBaseTransition::m_pStartKeyframe

Uloží ukazatel na klíčový snímek, který určuje začátek přechodu.

```
CBaseKeyFrame* m_pStartKeyframe;
```

## <a name="cbasetransitionm_transition"></a><a name="m_transition"></a>CBaseTransition::m_transition

Ukládá ukazatel na IUIAnimationTransition. Null, pokud objekt přechodu COM nebyl vytvořen.

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

## <a name="cbasetransitionm_type"></a><a name="m_type"></a>CBaseTransition::m_type

Ukládá typ přechodu.

```
TRANSITION_TYPE m_type;
```

## <a name="cbasetransitionsetkeyframes"></a><a name="setkeyframes"></a>CBaseTransition::SetKeyframes

Nastaví klíčové snímky pro přechod.

```
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>Parametry

*pStart*<br/>
Klíčový snímek, který určuje začátek přechodu.

*pEnd*<br/>
Klíčový snímek, který určuje konec přechodu.

### <a name="remarks"></a>Poznámky

Tato metoda říká přechod začít po zadaném klíčovém snímku a volitelně, pokud pEnd není NULL, konec před zadaný klíčový snímek. Pokud byl přechod vytvořen se zadaným parametrem doby trvání, je tato doba trvání přepsána dobou mezi počátečním a koncovým klíčovým snímky.

## <a name="cbasetransitionsetrelatedvariable"></a><a name="setrelatedvariable"></a>CBaseTransition::SetRelatedVariable

Vytvoří vztah mezi proměnnou animace a přechodem.

```
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pProměnná proměnná*<br/>
Ukazatel na související proměnnou animace.

### <a name="remarks"></a>Poznámky

Vytvoří vztah mezi proměnnou animace a přechodem. Přechod lze použít pouze na jednu proměnnou.

## <a name="cbasetransitiontransition_type-enumeration"></a><a name="transition_type_enumeration"></a>CBaseTransition::TRANSITION_TYPE Výčet

Definuje typy přechodů, které aktuálně podporuje implementace knihovny MFC rozhraní API pro animaci systému Windows.

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>Poznámky

Typ přechodu je nastaven v konstruktoru konkrétního přechodu. Například CSinusoidalTransitionFromRange nastaví jeho typ na SINUSOIDAL_FROM_RANGE.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
