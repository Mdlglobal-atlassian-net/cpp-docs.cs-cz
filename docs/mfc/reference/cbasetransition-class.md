---
title: "Třída CBaseTransition | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a925de05d301d213d67bb699af47d0453478ffc2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cbasetransition-class"></a>CBaseTransition – třída
Představuje základní přechod.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CBaseTransition : public CObject;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-enumerations"></a>Veřejné výčty  
  
|Název|Popis|  
|----------|-----------------|  
|[CBaseTransition::TRANSITION_TYPE – výčet](#transition_type_enumeration)|Definuje typy přechod implementace MFC rozhraní API systému Windows animace v současné době podporuje.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CBaseTransition::CBaseTransition](#cbasetransition)|Vytvoří objekt základní transtion.|  
|[CBaseTransition:: ~ CBaseTransition](#cbasetransition__~cbasetransition)|Destruktor. Voláno, když je objekt přechodu zničen.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|Přidá přechodu do scénáře.|  
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Přidá přechodu do scénáře.|  
|[CBaseTransition::Clear](#clear)|Verze zapouzdřené objektu IUIAnimationTransition COM.|  
|[CBaseTransition::Create](#create)|Vytvoří přechod COM.|  
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|Vrátí spustit klíčový snímek.|  
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|Vrací ukazatel na související proměnné.|  
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|Vrátí spustit klíčový snímek.|  
|[CBaseTransition::GetTransition](#gettransition)|Přetíženo. Vrací ukazatel na základní objekt COM přechodu.|  
|[CBaseTransition::GetType](#gettype)|Vrátí typ přechodu.|  
|[CBaseTransition::IsAdded](#isadded)|Oznamuje, zda přidala přechod scénáře.|  
|[CBaseTransition::SetKeyframes](#setkeyframes)|Nastaví klíčových snímků pro přechod.|  
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|Vytvoří vztah mezi proměnnou animace a přechodu.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CBaseTransition::m_bAdded](#m_badded)|Určuje, zda přidala přechod scénáře.|  
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|Ukládá ukazatel klíčový snímek, který určuje konec přechodu.|  
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|Ukazatel na animace proměnnou, která je animovaný s uložené v m_transition přechodu.|  
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|Ukládá ukazatel klíčový snímek, který určuje začátek přechodu.|  
|[CBaseTransition::m_transition](#m_transition)|Ukládá ukazatel na IUIAnimationTransition. Hodnota NULL, pokud COM přechod objektu nebyl vytvořen.|  
|[CBaseTransition::m_type](#m_type)|Ukládá typ přechodu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída zapouzdří IUIAnimationTransition rozhraní a slouží jako základní třída pro všechny přechody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CBaseTransition`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="_dtorcbasetransition"></a>CBaseTransition:: ~ CBaseTransition  
 Destruktor. Voláno, když je objekt přechodu zničen.  
  
```  
virtual ~CBaseTransition();
```  
  
##  <a name="addtostoryboard"></a>CBaseTransition::AddToStoryboard  
 Přidá přechodu do scénáře.  
  
```  
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Ukazatel na scénáře, který se použije animaci související proměnné.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud přechod byla úspěšně přidána do scénáře.  
  
### <a name="remarks"></a>Poznámky  
 Platí pro proměnnou související ve scénáři, přechodu. Pokud je to první přechodu u této proměnné v tohoto scénáře, začne přechodu na začátku scénáři. Přechodu, jinak se připojuje k přechodu naposledy přidat proměnnou.  
  
##  <a name="addtostoryboardatkeyframes"></a>CBaseTransition::AddToStoryboardAtKeyframes  
 Přidá přechodu do scénáře.  
  
```  
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Ukazatel na scénáře, který se použije animaci související proměnné.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud přechod byla úspěšně přidána do scénáře.  
  
### <a name="remarks"></a>Poznámky  
 Platí pro proměnnou související ve scénáři, přechodu. Klíčový počáteční snímek, který byl zadán, přechod začíná u této klíčový snímek. Zadané koncové klíčový snímek, přechod začíná u klíčový počáteční snímek a a zastaví na koncové klíčového snímku. Pokud přechodu byl vytvořen s trvání parametr zadaný, že doba trvání přepsána doba mezi počáteční a koncové klíčové snímky. Pokud není zadané žádné klíčový snímek, připojí se k přechodu naposledy přidat proměnnou přechodu.  
  
##  <a name="cbasetransition"></a>CBaseTransition::CBaseTransition  
 Vytvoří objekt základní transtion.  
  
```  
CBaseTransition();
```  
  
##  <a name="clear"></a>CBaseTransition::Clear  
 Verze zapouzdřené objektu IUIAnimationTransition COM.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda by měla být volána z metodu Create odvozené třídy, aby se zabránilo úniku IUITransition rozhraní.  
  
##  <a name="create"></a>CBaseTransition::Create  
 Vytvoří přechod COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pLibrary`  
 Ukazatel na přechod knihovny, která vytvoří standardní přechody. Pro vlastní přechody, může být NULL.  
  
 `pFactory`  
 Ukazatel na přechod factory, který vytvoří vlastní přechody. Pro standardní přechody, může být NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud přechod objektu COM byla úspěšně vytvořena; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Toto je čistě virtuální funkci, která musí být přepsána nastaveními v odvozené třídě. Je volána metodou rozhraní framework vytvořit základní objekt COM přechodu.  
  
##  <a name="getendkeyframe"></a>CBaseTransition::GetEndKeyframe  
 Vrátí spustit klíčový snímek.  
  
```  
CBaseKeyFrame* GetEndKeyframe();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Neplatný ukazatel klíčový nebo hodnota NULL, pokud přechod by neměl být vložen mezi klíčových snímků.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda slouží pro přístup k objektu @keyframe, které určuje, který dříve nastavil SetKeyframes. Je volána službou nejvyšší úrovně kódu při přechody se přidávají do scénáře.  
  
##  <a name="getrelatedvariable"></a>CBaseTransition::GetRelatedVariable  
 Vrací ukazatel na související proměnné.  
  
```  
CAnimationVariable* GetRelatedVariable();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Neplatný ukazatel na proměnnou animace nebo hodnota NULL, pokud nebyla nastavena proměnná animace pomocí SetRelatedVariable.  
  
### <a name="remarks"></a>Poznámky  
 Toto je přistupující objekt k proměnné související animace.  
  
##  <a name="getstartkeyframe"></a>CBaseTransition::GetStartKeyframe  
 Vrátí spustit klíčový snímek.  
  
```  
CBaseKeyFrame* GetStartKeyframe();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Neplatný ukazatel klíčový nebo hodnota NULL, pokud by neměl přechod spustit po klíčový.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda slouží pro přístup k objektu @keyframe, které určuje, který dříve nastavil SetKeyframes. Je volána službou nejvyšší úrovně kódu při přechody se přidávají do scénáře.  
  
##  <a name="gettransition"></a>CBaseTransition::GetTransition  
 Vrací ukazatel na základní objekt COM přechodu.  
  
```  
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory);  
  
IUIAnimationTransition* GetTransition();
```  
  
### <a name="parameters"></a>Parametry  
 `pLibrary`  
 Ukazatel na přechod knihovny, která vytvoří standardní přechody. Pro vlastní přechody, může být NULL.  
  
 `pFactory`  
 Ukazatel na přechod factory, který vytvoří vlastní přechody. Pro standardní přechody, může být NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nelze vytvořit platný ukazatel IUIAnimationTransition nebo hodnota NULL, pokud základní přechodu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrací ukazatel na základní objekt přechod COM a v případě potřeby ji vytvoří.  
  
##  <a name="gettype"></a>CBaseTransition::GetType  
 Vrátí typ přechodu.  
  
```  
TRANSITION_TYPE GetType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden z TRANSITION_TYPE uvedené hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda slouží k identifikaci objekt přechod podle jeho typu. Je nastaven typ v konstruktoru odvozené třídy.  
  
##  <a name="isadded"></a>CBaseTransition::IsAdded  
 Oznamuje, zda přidala přechod scénáře.  
  
```  
BOOL IsAdded();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud byla přidána přechod do scénáře, jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tento příznak nastaven interně, pokud kód nejvyšší úrovně přidá přechody do scénáře.  
  
##  <a name="m_badded"></a>CBaseTransition::m_bAdded  
 Určuje, zda přidala přechod scénáře.  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_pendkeyframe"></a>CBaseTransition::m_pEndKeyframe  
 Ukládá ukazatel klíčový snímek, který určuje konec přechodu.  
  
```  
CBaseKeyFrame* m_pEndKeyframe;  
```  
  
##  <a name="m_prelatedvariable"></a>CBaseTransition::m_pRelatedVariable  
 Ukazatel na animace proměnnou, která je animovaný s uložené v m_transition přechodu.  
  
```  
CAnimationVariable* m_pRelatedVariable;  
```  
  
##  <a name="m_pstartkeyframe"></a>CBaseTransition::m_pStartKeyframe  
 Ukládá ukazatel klíčový snímek, který určuje začátek přechodu.  
  
```  
CBaseKeyFrame* m_pStartKeyframe;  
```  
  
##  <a name="m_transition"></a>CBaseTransition::m_transition  
 Ukládá ukazatel na IUIAnimationTransition. Hodnota NULL, pokud COM přechod objektu nebyl vytvořen.  
  
```  
ATL::CComPtr<IUIAnimationTransition> m_transition;  
```  
  
##  <a name="m_type"></a>CBaseTransition::m_type  
 Ukládá typ přechodu.  
  
```  
TRANSITION_TYPE m_type;  
```  
  
##  <a name="setkeyframes"></a>CBaseTransition::SetKeyframes  
 Nastaví klíčových snímků pro přechod.  
  
```  
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,  
    CBaseKeyFrame* pEnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pStart`  
 Klíčový snímek, který určuje začátek přechodu.  
  
 `pEnd`  
 Klíčový snímek, který určuje konec přechodu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda informuje přechod spustit po zadaný klíčový snímek a volitelně čekání má hodnotu NULL, není-li ukončit před zadaný klíčový snímek. Pokud přechodu byl vytvořen s trvání parametr zadaný, že doba trvání přepsána doba mezi počáteční a koncové klíčové snímky.  
  
##  <a name="setrelatedvariable"></a>CBaseTransition::SetRelatedVariable  
 Vytvoří vztah mezi proměnnou animace a přechodu.  
  
```  
void SetRelatedVariable(CAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>Parametry  
 `pVariable`  
 Ukazatel na proměnnou související animace.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří vztah mezi proměnnou animace a přechodu. Přechod lze použít pouze pro jednu proměnnou.  
  
##  <a name="transition_type_enumeration"></a>CBaseTransition::TRANSITION_TYPE – výčet  
 Definuje typy přechod implementace MFC rozhraní API systému Windows animace v současné době podporuje.  
  
```  
enum TRANSITION_TYPE;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ přechodu se nastavuje v konstruktoru konkrétní přechodu. Například CSinusoidalTransitionFromRange nastaví její typ SINUSOIDAL_FROM_RANGE.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
