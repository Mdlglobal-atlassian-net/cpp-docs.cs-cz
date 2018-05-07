---
title: Třída CCustomTransition | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
dev_langs:
- C++
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89c3ec260fad8b0e2f8224c639aa745a9101e8b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ccustomtransition-class"></a>CCustomTransition – třída
Implementuje vlastní přechod.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCustomTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CCustomTransition::CCustomTransition](#ccustomtransition)|Vytvoří objekt vlastní přechod.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CCustomTransition::Create](#create)|Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM. (Přepisuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Nastaví počáteční hodnotu, která se použijí pro proměnnou animace přidružený tento přechod.|  
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Nastaví počáteční rychlosti postupu, které se použijí k proměnné animace přidružený tento přechod.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Určuje, zda je zadaná počáteční hodnota s SetInitialValue.|  
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Určuje, zda je zadaná počáteční rychlosti s SetInitialVelocity.|  
|[CCustomTransition::m_initialValue](#m_initialvalue)|Ukládá počáteční hodnota.|  
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Ukládá počáteční rychlosti.|  
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Ukládá ukazatel na vlastní interpolator.|  
  
## <a name="remarks"></a>Poznámky  
 Třída CCustomTransitions umožňuje vývojářům implementovat vlastní přechody. Má vytvořit a použít jako standardní přechodu, ale jeho konstruktor přijímá jako parametr ukazatel na vlastní interpolator. Proveďte následující kroky a použít vlastní přechody: 1. Odvození třídy z CCustomInterpolator a implementovat alespoň InterpolateValue metoda. 2. Ujistěte se, že životnosti objektu vlastní interpolator musí být delší než doba trvání animace kde se používá. 3. Vytvořte instanci (pomocí operátoru nové) CCustomTransition objektu a předejte ukazatel na vlastní interpolator v konstruktoru. 4. Volejte CCustomTransition::SetInitialValue a CCustomTransition::SetInitialVelocity, pokud jsou vyžadovány pro vlastní interpolace tyto parametry. 5. Ukazatele předejte vlastní přechod metodě AddTransition animace objekt, jehož hodnota by měla být animovaný s vlastní algoritmus. 6. Pokud by se měl změnit hodnotu objektu animace bude rozhraní API systému Windows animace v CCustomInterpolator volat InterpolateValue (a další relevantní metody).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CCustomTransition`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="ccustomtransition"></a>  CCustomTransition::CCustomTransition  
 Vytvoří objekt vlastní přechod.  
  
```  
CCustomTransition(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>Parametry  
 `pInterpolator`  
 Ukazatel na vlastní interpolator.  
  
##  <a name="create"></a>  CCustomTransition::Create  
 Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,  
    IUIAnimationTransitionFactory* pFactory);
```  
  
### <a name="parameters"></a>Parametry  
 `pFactory`  
 Ukazatel na přechod factory, který zodpovídá za vytvoření vlastní přechodů.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu můžete také nastavit, výchozí hodnoty a rychlosti počáteční má být použita animace proměnné, která je přidružená tento přechod. K tomuto účelu, budete muset volat SetInitialValue a SetInitialVelocity předtím, než rozhraní framework vytvoří objekt COM zapouzdřené přechodu (Odehrává se při volání CAnimationController::AnimateGroup).  
  
##  <a name="m_binitialvaluespecified"></a>  CCustomTransition::m_bInitialValueSpecified  
 Určuje, zda je zadaná počáteční hodnota s SetInitialValue.  
  
```  
BOOL m_bInitialValueSpecified;  
```  
  
##  <a name="m_binitialvelocityspecified"></a>  CCustomTransition::m_bInitialVelocitySpecified  
 Určuje, zda je zadaná počáteční rychlosti s SetInitialVelocity.  
  
```  
BOOL m_bInitialVelocitySpecified;  
```  
  
##  <a name="m_initialvalue"></a>  CCustomTransition::m_initialValue  
 Ukládá počáteční hodnota.  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>  CCustomTransition::m_initialVelocity  
 Ukládá počáteční rychlosti.  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="m_pinterpolator"></a>  CCustomTransition::m_pInterpolator  
 Ukládá ukazatel na vlastní interpolator.  
  
```  
CCustomInterpolator* m_pInterpolator;  
```  
  
##  <a name="setinitialvalue"></a>  CCustomTransition::SetInitialValue  
 Nastaví počáteční hodnotu, která se použijí pro proměnnou animace přidružený tento přechod.  
  
```  
void SetInitialValue(DOUBLE initialValue);
```  
  
### <a name="parameters"></a>Parametry  
 `initialValue`  
  
##  <a name="setinitialvelocity"></a>  CCustomTransition::SetInitialVelocity  
 Nastaví počáteční rychlosti postupu, které se použijí k proměnné animace přidružený tento přechod.  
  
```  
void SetInitialVelocity(DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Parametry  
 `initialVelocity`  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
