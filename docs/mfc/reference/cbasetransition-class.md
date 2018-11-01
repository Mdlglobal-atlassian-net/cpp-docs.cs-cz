---
title: Cbasetransition – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: b4c15be574700730e847bce06aaa4a6f82aed4b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539123"
---
# <a name="cbasetransition-class"></a>Cbasetransition – třída

Představuje základní přechod.

## <a name="syntax"></a>Syntaxe

```
class CBaseTransition : public CObject;
```

## <a name="members"></a>Členové

### <a name="public-enumerations"></a>Veřejné výčty

|Název|Popis|
|----------|-----------------|
|[Výčet CBaseTransition::TRANSITION_TYPE](#transition_type_enumeration)|Definuje typy přechod aktuálně podporováno implementací MFC rozhraní Windows API animace.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CBaseTransition::CBaseTransition](#cbasetransition)|Vytvoří základní transtion objekt.|
|[Cbasetransition –:: ~ cbasetransition –](#cbasetransition__~cbasetransition)|Destruktor. Volá se při přechodu objekt je zničen.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|Přidá přechod do scénáře.|
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Přidá přechod do scénáře.|
|[CBaseTransition::Clear](#clear)|Verze zapouzdřený objekt modelu COM IUIAnimationTransition.|
|[CBaseTransition::Create](#create)|Vytvoří COM přechod.|
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|Vrátí start klíčový snímek.|
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|Vrací ukazatel na související proměnné.|
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|Vrátí start klíčový snímek.|
|[CBaseTransition::GetTransition](#gettransition)|Přetíženo. Vrací ukazatel na základní objekt modelu COM přechodu.|
|[CBaseTransition::GetType](#gettype)|Vrátí typ přechodu.|
|[CBaseTransition::IsAdded](#isadded)|Informuje, zda přechodu je přidaný do scénáře.|
|[CBaseTransition::SetKeyframes](#setkeyframes)|Nastaví klíčové snímky pro přechod.|
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|Vytvoří vztah mezi proměnné animace a přechod.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CBaseTransition::m_bAdded](#m_badded)|Určuje, zda přechodu je přidaný do scénáře.|
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|Uchovává ukazatel na klíčový snímek, který určuje konci přechodu.|
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|Ukazatel na proměnnou animace, který je animovaný přechodu uložené v m_transition.|
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|Uchovává ukazatel na klíčový snímek, který určuje začátek přechodu.|
|[CBaseTransition::m_transition](#m_transition)|Uchovává ukazatel na IUIAnimationTransition. Hodnota NULL, pokud nebyl vytvořen objekt modelu COM přechodu.|
|[CBaseTransition::m_type](#m_type)|Ukládá typ přechodu.|

## <a name="remarks"></a>Poznámky

Tato třída zapouzdří IUIAnimationTransition rozhraní a slouží jako základní třída pro všechny přechody.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="_dtorcbasetransition"></a>  Cbasetransition –:: ~ cbasetransition –

Destruktor. Volá se při přechodu objekt je zničen.

```
virtual ~CBaseTransition();
```

##  <a name="addtostoryboard"></a>  CBaseTransition::AddToStoryboard

Přidá přechod do scénáře.

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénáře, které budou související proměnné animace.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud přechodu se úspěšně přidal do scénáře.

### <a name="remarks"></a>Poznámky

Přechod platí pro proměnnou související ve scénáři. Pokud je toto první přechod u této proměnné v tomto scénáři, přechod začne na začátku scénáři. V opačném případě přechodu se připojí k přechodu naposledy přidána do proměnné.

##  <a name="addtostoryboardatkeyframes"></a>  CBaseTransition::AddToStoryboardAtKeyframes

Přidá přechod do scénáře.

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénáře, které budou související proměnné animace.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud přechodu se úspěšně přidal do scénáře.

### <a name="remarks"></a>Poznámky

Přechod platí pro proměnnou související ve scénáři. Pokud nebyla zadána start klíčový snímek, přechod začíná u tohoto klíčového snímku. Pokud nebyla zadána end klíčový snímek, přechod začíná na klíčový snímek počáteční a end klíčového snímku se zastaví. Pokud přechod byl vytvořen s doba trvání parametr zadán, je tento čas přepsána doba mezi klíčovými snímky počáteční a koncové. Pokud nebyla zadána žádná klíčový snímek, přechodu se připojí k přechodu naposledy přidána do proměnné.

##  <a name="cbasetransition"></a>  CBaseTransition::CBaseTransition

Vytvoří základní transtion objekt.

```
CBaseTransition();
```

##  <a name="clear"></a>  CBaseTransition::Clear

Verze zapouzdřený objekt modelu COM IUIAnimationTransition.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

Tuto metodu lze volat z odvozenou třídu vytvořit metody aby se zabránilo nevrácení IUITransition rozhraní.

##  <a name="create"></a>  CBaseTransition::Create

Vytvoří COM přechod.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Ukazatel na přechod knihovny, která vytvoří standardní přechodů. To může mít hodnotu NULL pro vlastní přechody.

*pFactory*<br/>
Ukazatel na přechod factory, který vytvoří vlastní přechodů. To může mít hodnotu NULL pro standardní přechody.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě přechodu objekt COM byl úspěšně vytvořen; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

To se čistě virtuální funkci, která se musí přepsat v odvozené třídě. Volá se rozhraním, k vytvoření instance základní přechod objekt modelu COM.

##  <a name="getendkeyframe"></a>  CBaseTransition::GetEndKeyframe

Vrátí start klíčový snímek.

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel klíčový snímek, nebo hodnota NULL, pokud by neměla být vložen přechod mezi klíčovými snímky.

### <a name="remarks"></a>Poznámky

Tuto metodu lze použít pro přístup k objektu klíčový snímek, který byl dříve nastavil SetKeyframes. Je volána službou nejvyšší úrovně kódu při přechody se přidávají do scénáře.

##  <a name="getrelatedvariable"></a>  CBaseTransition::GetRelatedVariable

Vrací ukazatel na související proměnné.

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na proměnnou animace, nebo hodnota NULL, pokud nebyla nastavena podle SetRelatedVariable proměnnou animace.

### <a name="remarks"></a>Poznámky

Toto je přístupový objekt proměnné související animace.

##  <a name="getstartkeyframe"></a>  CBaseTransition::GetStartKeyframe

Vrátí start klíčový snímek.

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel klíčový snímek, nebo hodnota NULL, pokud přechod nesmí začínat po klíčového snímku.

### <a name="remarks"></a>Poznámky

Tuto metodu lze použít pro přístup k objektu klíčový snímek, který byl dříve nastavil SetKeyframes. Je volána službou nejvyšší úrovně kódu při přechody se přidávají do scénáře.

##  <a name="gettransition"></a>  CBaseTransition::GetTransition

Vrací ukazatel na základní objekt modelu COM přechodu.

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Ukazatel na přechod knihovny, která vytvoří standardní přechodů. To může mít hodnotu NULL pro vlastní přechody.

*pFactory*<br/>
Ukazatel na přechod factory, který vytvoří vlastní přechodů. To může mít hodnotu NULL pro standardní přechody.

### <a name="return-value"></a>Návratová hodnota

Nejde vytvořit platný ukazatel na IUIAnimationTransition nebo hodnota NULL, pokud základní přechod.

### <a name="remarks"></a>Poznámky

Tato metoda vrací ukazatel na základní objekt modelu COM přechodu a v případě potřeby ji vytvoří.

##  <a name="gettype"></a>  CBaseTransition::GetType

Vrátí typ přechodu.

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>Návratová hodnota

Jeden z TRANSITION_TYPE hodnot výčtu.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k identifikaci přechodu objektu podle jeho typu. Je typ nastaven v konstruktoru odvozené třídy.

##  <a name="isadded"></a>  CBaseTransition::IsAdded

Informuje, zda přechodu je přidaný do scénáře.

```
BOOL IsAdded();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud byl přidán přechod do scénáře, jinak hodnota FALSE.

### <a name="remarks"></a>Poznámky

Nejvyšší úrovně kódu přidá přechody do scénáře je interně nastavený tento příznak.

##  <a name="m_badded"></a>  CBaseTransition::m_bAdded

Určuje, zda přechodu je přidaný do scénáře.

```
BOOL m_bAdded;
```

##  <a name="m_pendkeyframe"></a>  CBaseTransition::m_pEndKeyframe

Uchovává ukazatel na klíčový snímek, který určuje konci přechodu.

```
CBaseKeyFrame* m_pEndKeyframe;
```

##  <a name="m_prelatedvariable"></a>  CBaseTransition::m_pRelatedVariable

Ukazatel na proměnnou animace, který je animovaný přechodu uložené v m_transition.

```
CAnimationVariable* m_pRelatedVariable;
```

##  <a name="m_pstartkeyframe"></a>  CBaseTransition::m_pStartKeyframe

Uchovává ukazatel na klíčový snímek, který určuje začátek přechodu.

```
CBaseKeyFrame* m_pStartKeyframe;
```

##  <a name="m_transition"></a>  CBaseTransition::m_transition

Uchovává ukazatel na IUIAnimationTransition. Hodnota NULL, pokud nebyl vytvořen objekt modelu COM přechodu.

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

##  <a name="m_type"></a>  CBaseTransition::m_type

Ukládá typ přechodu.

```
TRANSITION_TYPE m_type;
```

##  <a name="setkeyframes"></a>  CBaseTransition::SetKeyframes

Nastaví klíčové snímky pro přechod.

```
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>Parametry

*pStart*<br/>
Klíčový snímek, který určuje začátek přechodu.

*Čekání*<br/>
Klíčový snímek, který určuje konci přechodu.

### <a name="remarks"></a>Poznámky

Tato metoda říká přechodem na spustit po zadanou klíčový snímek a volitelně, pokud čekání nemá hodnotu NULL, ukončit před zadaným klíčový snímek. Pokud přechod byl vytvořen s doba trvání parametr zadán, je tento čas přepsána doba mezi klíčovými snímky počáteční a koncové.

##  <a name="setrelatedvariable"></a>  CBaseTransition::SetRelatedVariable

Vytvoří vztah mezi proměnné animace a přechod.

```
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pVariable*<br/>
Ukazatel na proměnnou související animace.

### <a name="remarks"></a>Poznámky

Vytvoří vztah mezi proměnné animace a přechod. Přechod lze použít pouze pro jednu proměnnou.

##  <a name="transition_type_enumeration"></a>  Výčet CBaseTransition::TRANSITION_TYPE

Definuje typy přechod aktuálně podporováno implementací MFC rozhraní Windows API animace.

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>Poznámky

Typ přechodu je nastavena v konstruktoru konkrétní přechod. Csinusoidaltransitionfromrange – například nastaví jeho typ SINUSOIDAL_FROM_RANGE.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
