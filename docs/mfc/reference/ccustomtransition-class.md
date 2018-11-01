---
title: Ccustomtransition – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: af600704f82a0cad402948286fa0d4b11dca0c71
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578370"
---
# <a name="ccustomtransition-class"></a>Ccustomtransition – třída

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
|[CCustomTransition::Create](#create)|Knihovna přechod k vytvoření objektu přechod zapouzdřený objekt modelu COM zavolá. (Přepíše [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Nastaví počáteční hodnotu, která se použijí pro proměnnou animace přidružené k tento přechod.|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Nastaví počáteční rychlosti, která se použijí pro proměnnou animace přidružené k tento přechod.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Určuje, zda byl zadán SetInitialValue počáteční hodnota.|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Určuje, zda byl zadaný počáteční SetInitialVelocity.|
|[CCustomTransition::m_initialValue](#m_initialvalue)|Uloží počáteční hodnotu.|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Ukládá počáteční.|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Uchovává ukazatel na vlastní interpolator.|

## <a name="remarks"></a>Poznámky

Třída CCustomTransitions umožňuje vývojářům implementovat vlastní přechodů. Má vytvořit a použít jako standardní přechod, ale jeho konstruktor přijímá jako parametr ukazatel na vlastní interpolator. Proveďte následující kroky a použít vlastní přechodů: 1. Odvodit třídu z ccustominterpolator – a implementovat alespoň InterpolateValue metody. 2. Ujistěte se, že doba života objektu vlastní interpolator musí být delší než doba trvání animace ve kterém se používá. 3. Vytvoření (pomocí operátoru new) instance objektu ccustomtransition – a předat ukazatel vlastní interpolator v konstruktoru. 4. Pokud tyto parametry jsou požadovány pro vlastní interpolace volání CCustomTransition::SetInitialValue a CCustomTransition::SetInitialVelocity. 5. Přesune ukazatel na vlastní přechod AddTransition metody objektu animace, jehož hodnota by měla být animován pomocí vlastního algoritmu. 6. Pokud by měl změnit hodnotu objektu animace Windows API animace v ccustominterpolator – volání InterpolateValue (a další relevantní metody).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cbasetransition –](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="ccustomtransition"></a>  CCustomTransition::CCustomTransition

Vytvoří objekt vlastní přechod.

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Ukazatel na vlastní interpolator.

##  <a name="create"></a>  CCustomTransition::Create

Knihovna přechod k vytvoření objektu přechod zapouzdřený objekt modelu COM zavolá.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>Parametry

*pFactory*<br/>
Ukazatel na přechod factory, který je zodpovědný za vytváření vlastních přechodů.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Tato metoda také nastavit výchozí hodnoty a rychlosti počáteční použít proměnnou animace, který je přidružen tohoto přechodu. Pro tento účel je nutné volat SetInitialValue a SetInitialVelocity rozhraní vytvoří objekt modelu COM zapouzdřený přechodu (to se stane, když voláte CAnimationController::AnimateGroup).

##  <a name="m_binitialvaluespecified"></a>  CCustomTransition::m_bInitialValueSpecified

Určuje, zda byl zadán SetInitialValue počáteční hodnota.

```
BOOL m_bInitialValueSpecified;
```

##  <a name="m_binitialvelocityspecified"></a>  CCustomTransition::m_bInitialVelocitySpecified

Určuje, zda byl zadaný počáteční SetInitialVelocity.

```
BOOL m_bInitialVelocitySpecified;
```

##  <a name="m_initialvalue"></a>  CCustomTransition::m_initialValue

Uloží počáteční hodnotu.

```
DOUBLE m_initialValue;
```

##  <a name="m_initialvelocity"></a>  CCustomTransition::m_initialVelocity

Ukládá počáteční.

```
DOUBLE m_initialVelocity;
```

##  <a name="m_pinterpolator"></a>  CCustomTransition::m_pInterpolator

Uchovává ukazatel na vlastní interpolator.

```
CCustomInterpolator* m_pInterpolator;
```

##  <a name="setinitialvalue"></a>  CCustomTransition::SetInitialValue

Nastaví počáteční hodnotu, která se použijí pro proměnnou animace přidružené k tento přechod.

```
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>Parametry

*Počáteční hodnota*

##  <a name="setinitialvelocity"></a>  CCustomTransition::SetInitialVelocity

Nastaví počáteční rychlosti, která se použijí pro proměnnou animace přidružené k tento přechod.

```
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*initialVelocity*

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
