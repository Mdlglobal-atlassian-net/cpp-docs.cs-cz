---
title: Cbasekeyframe – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::GetAnimationKeyframe
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bIsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_keyframe
dev_langs:
- C++
helpviewer_keywords:
- CBaseKeyFrame [MFC], CBaseKeyFrame
- CBaseKeyFrame [MFC], AddToStoryboard
- CBaseKeyFrame [MFC], GetAnimationKeyframe
- CBaseKeyFrame [MFC], IsAdded
- CBaseKeyFrame [MFC], IsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_bAdded
- CBaseKeyFrame [MFC], m_bIsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_keyframe
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ad9ff4d61647ce84e9aefef99391be51bca467b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435152"
---
# <a name="cbasekeyframe-class"></a>Cbasekeyframe – třída

Implementuje základní funkce keyframe.

## <a name="syntax"></a>Syntaxe

```
class CBaseKeyFrame : public CObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|Vytvoří objekt klíčový snímek.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|Přidá klíčového snímku do scénáře.|
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|Vrátí zdrojovou hodnotu klíčového snímku.|
|[CBaseKeyFrame::IsAdded](#isadded)|Určuje, zda klíčového snímku je přidaný do scénáře.|
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|Určuje, zda klíčový snímek, který má být přidána do scénáře na posunu nebo po přechodu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CBaseKeyFrame::m_bAdded](#m_badded)|Určuje, zda tento klíčový snímek byl přidán do scénáře.|
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Určuje, zda tento klíčový snímek měla být přidána do scénáře na posunu od jiného existujícího klíčového snímku nebo na konci některých přechodu.|
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|Představuje klíčový snímek API animace Windows. Při klíčového snímku není inicializován nastavena na hodnotu předdefinované UI_ANIMATION_KEYFRAME_STORYBOARD_START.|

## <a name="remarks"></a>Poznámky

Zapouzdřuje UI_ANIMATION_KEYFRAME proměnné. Slouží jako základní třída pro žádnou implementaci klíčový snímek. Klíčový snímek představuje okamžik v čase v rámci scénáře a je možné zadat počáteční a koncový čas přechodů. Existují dva typy klíčových snímků – klíčové snímky přidány do scénáře v zadaném posunu (v čase) nebo snímky přidány po zadanou přechodu. Vzhledem k tomu, že před spuštěním animace nemůže být známé dob trvání některé přechodů, skutečné hodnoty některých klíčových snímků jsou určeny pouze za běhu. Klíčové snímky může záviset na přechody, které mohou záviset na klíčové snímky, proto je důležité, aby se zabránilo nekonečná rekurze při vytváření řetězů klíčový snímek.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="addtostoryboard"></a>  CBaseKeyFrame::AddToStoryboard

Přidá klíčového snímku do scénáře.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénáře.

*bDeepAdd*<br/>
Pokud tento parametr je PRAVDA a klíčový snímek přidávaný závisí na některých klíčového snímku nebo přechodu, tato metoda se pokusí přidat tento klíčový snímek nebo přechod na první scénáře.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud klíčový snímek byl přidán do scénáře úspěšně; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda je volána k přidání klíčového snímku do scénáře.

##  <a name="cbasekeyframe"></a>  CBaseKeyFrame::CBaseKeyFrame

Vytvoří objekt klíčový snímek.

```
CBaseKeyFrame();
```

##  <a name="getanimationkeyframe"></a>  CBaseKeyFrame::GetAnimationKeyframe

Vrátí zdrojovou hodnotu klíčového snímku.

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>Návratová hodnota

Klíčový snímek aktuální. Výchozí hodnota je UI_ANIMATION_KEYFRAME_STORYBOARD_START.

### <a name="remarks"></a>Poznámky

Toto je přístupový objekt základní hodnota klíčového snímku.

##  <a name="isadded"></a>  CBaseKeyFrame::IsAdded

Určuje, zda klíčového snímku je přidaný do scénáře.

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud klíčový snímek je přidán do scénáře; otehrwise hodnotu FALSE.

### <a name="remarks"></a>Poznámky

V základní třídě IsAdded vždy vrátí hodnotu TRUE, ale je v odvozených třídách přepsána.

##  <a name="iskeyframeatoffset"></a>  CBaseKeyFrame::IsKeyframeAtOffset

Určuje, zda klíčový snímek, který má být přidána do scénáře na posunu nebo po přechodu.

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud klíčový snímek, který má být přidán do scénáře na některé zadaného posunu. FALSE, pokud klíčový snímek, který má být přidán do scénáře po přechodu některé.

### <a name="remarks"></a>Poznámky

Určuje, zda klíčový snímek, který má být přidána do scénáře na posunu. Posun nebo přechodu potřeba uvést v odvozené třídě.

##  <a name="m_badded"></a>  CBaseKeyFrame::m_bAdded

Určuje, zda tento klíčový snímek byl přidán do scénáře.

```
BOOL m_bAdded;
```

##  <a name="m_biskeyframeatoffset"></a>  CBaseKeyFrame::m_bIsKeyframeAtOffset

Určuje, zda tento klíčový snímek měla být přidána do scénáře na posunu od jiného existujícího klíčového snímku nebo na konci některých přechodu.

```
BOOL m_bIsKeyframeAtOffset;
```

##  <a name="m_keyframe"></a>  CBaseKeyFrame::m_keyframe

Představuje klíčový snímek API animace Windows. Při klíčového snímku není inicializován nastavena na hodnotu předdefinované UI_ANIMATION_KEYFRAME_STORYBOARD_START.

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
