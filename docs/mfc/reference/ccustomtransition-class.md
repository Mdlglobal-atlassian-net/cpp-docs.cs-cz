---
title: CCustomTransition – třída
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
ms.openlocfilehash: 76e0d12308ad579e4bdf9866dfcf1cde231a2d0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749149"
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
|[CCustomTransition::CCustomTransition](#ccustomtransition)|Vytvoří vlastní objekt přechodu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CCustomTransition::Vytvořit](#create)|Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM. (Přepíše [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Nastaví počáteční hodnotu, která bude použita na proměnnou animace přidruženou k tomuto přechodu.|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Nastaví počáteční rychlost, která bude použita na proměnnou animace přidruženou k tomuto přechodu.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Určuje, zda byla počáteční hodnota zadána pomocí parametru SetInitialValue.|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Určuje, zda byla počáteční rychlost zadána pomocí parametru SetInitialVelocity.|
|[CCustomTransition::m_initialValue](#m_initialvalue)|Ukládá počáteční hodnotu.|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Ukládá počáteční rychlost.|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Uloží ukazatel na vlastní interpolátor.|

## <a name="remarks"></a>Poznámky

Třída CCustomTransitions umožňuje vývojářům implementovat vlastní přechody. Je vytvořen a používán jako standardní přechod, ale jeho konstruktor přijímá jako parametr ukazatel na vlastní interpolátor. Chcete-li použít vlastní přechody, proveďte následující kroky: 1. Odvodit třídu z CCustomInterpolator a implementovat alespoň InterpolateValue metoda. 2. Ujistěte se, že životnost vlastního interpolátoru objektu musí být delší než doba trvání animace, kde se používá. 3. Konstanci (pomocí operátoru new) CCustomTransition objekt a předat ukazatel na vlastní interpolátor v konstruktoru. 4. Volání CCustomTransition::SetInitialValue a CCustomTransition::SetInitialVelocity, pokud jsou tyto parametry vyžadovány pro vlastní interpolaci. 5. Předajte ukazatel na vlastní přechod na metodu AddTransition objektu animace, jehož hodnota by měla být animována pomocí vlastního algoritmu. 6. Když hodnota objektu animace by měla změnit rozhraní API animace systému Windows bude volat InterpolateValue (a další relevantní metody) v CCustomInterpolator.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="ccustomtransitionccustomtransition"></a><a name="ccustomtransition"></a>CCustomTransition::CCustomTransition

Vytvoří vlastní objekt přechodu.

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parametry

*pInterpolátor*<br/>
Ukazatel na vlastní interpolátor.

## <a name="ccustomtransitioncreate"></a><a name="create"></a>CCustomTransition::Vytvořit

Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>Parametry

*pFactory*<br/>
Ukazatel na továrnu přechodu, která je zodpovědná za vytváření vlastních přechodů.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Tato metoda také můžete nastavit počáteční hodnotu a počáteční rychlost, která má být použita na proměnnou animace, která je spojena s tímto přechodem. Pro tento účel budete muset volat SetInitialValue a SetInitialVelocity před rámec vytvoří zapouzdřený přechod COM objekt (stane se při volání CAnimationController::AnimateGroup).

## <a name="ccustomtransitionm_binitialvaluespecified"></a><a name="m_binitialvaluespecified"></a>CCustomTransition::m_bInitialValueSpecified

Určuje, zda byla počáteční hodnota zadána pomocí parametru SetInitialValue.

```
BOOL m_bInitialValueSpecified;
```

## <a name="ccustomtransitionm_binitialvelocityspecified"></a><a name="m_binitialvelocityspecified"></a>CCustomTransition::m_bInitialVelocitySpecified

Určuje, zda byla počáteční rychlost zadána pomocí parametru SetInitialVelocity.

```
BOOL m_bInitialVelocitySpecified;
```

## <a name="ccustomtransitionm_initialvalue"></a><a name="m_initialvalue"></a>CCustomTransition::m_initialValue

Ukládá počáteční hodnotu.

```
DOUBLE m_initialValue;
```

## <a name="ccustomtransitionm_initialvelocity"></a><a name="m_initialvelocity"></a>CCustomTransition::m_initialVelocity

Ukládá počáteční rychlost.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustomtransitionm_pinterpolator"></a><a name="m_pinterpolator"></a>CCustomTransition::m_pInterpolator

Uloží ukazatel na vlastní interpolátor.

```
CCustomInterpolator* m_pInterpolator;
```

## <a name="ccustomtransitionsetinitialvalue"></a><a name="setinitialvalue"></a>CCustomTransition::SetInitialValue

Nastaví počáteční hodnotu, která bude použita na proměnnou animace přidruženou k tomuto přechodu.

```cpp
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>Parametry

*Initialvalue*

## <a name="ccustomtransitionsetinitialvelocity"></a><a name="setinitialvelocity"></a>CCustomTransition::SetInitialVelocity

Nastaví počáteční rychlost, která bude použita na proměnnou animace přidruženou k tomuto přechodu.

```cpp
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*počáteční rychlost*

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
