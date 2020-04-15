---
title: CBaseKeyFrame – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 3fcd55f6a157f4b837090a3608fb509b870aae5d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352993"
---
# <a name="cbasekeyframe-class"></a>CBaseKeyFrame – třída

Implementuje základní funkce klíčového snímku.

## <a name="syntax"></a>Syntaxe

```
class CBaseKeyFrame : public CObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|Vytvoří objekt klíčového snímku.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|Přidá klíčový snímek do scénáře.|
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|Vrátí hodnotu základního klíčového snímku.|
|[CbaseKeyFrame::Jepřidán](#isadded)|Určuje, zda byl klíčový snímek přidán do scénáře.|
|[CbaseKeyFrame::IskeyframeatOffset](#iskeyframeatoffset)|Určuje, zda má být klíčový snímek přidán do scénáře při posunu nebo po přechodu.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CBaseKeyFrame::m_bAdded](#m_badded)|Určuje, zda byl tento klíčový snímek přidán do scénáře.|
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Určuje, zda má být tento klíčový snímek přidán do scénáře při posunu od jiného existujícího klíčového snímku nebo na konci nějakého přechodu.|
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|Představuje klíčový snímek rozhraní API pro animaci systému Windows. Pokud klíčový snímek není inicializován, je nastaven na předdefinovanou hodnotu UI_ANIMATION_KEYFRAME_STORYBOARD_START.|

## <a name="remarks"></a>Poznámky

Zapouzdřuje proměnnou UI_ANIMATION_KEYFRAME. Slouží jako základní třída pro všechny klíčové snímkové implementace. Klíčový snímek představuje okamžik v čase ve scénáři a lze jej použít k určení počátečního a koncového času přechodů. Existují dva typy klíčových snímků - klíčové snímky přidané do scénáře na zadaný posun (v čase) nebo klíčové snímky přidané po zadaném přechodu. Vzhledem k tomu, že dobu trvání některých přechodů nelze zjistit před zahájením animace, skutečné hodnoty některých klíčových snímků jsou určeny pouze za běhu. Vzhledem k tomu, že klíčové snímky mohou záviset na přechodech, které zase závisí na klíčových snímcích, je důležité zabránit nekonečným rekurzím při vytváření řetězců klíčových snímků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="cbasekeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseKeyFrame::AddToStoryboard

Přidá klíčový snímek do scénáře.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénář.

*bDeepAdd*<br/>
Pokud je tento parametr TRUE a přidávaný klíčový snímek závisí na některém jiném klíčovém snímku nebo přechodu, tato metoda se nejprve pokusí přidat tento klíčový snímek nebo přechod do scénáře.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud klíčový snímek byl úspěšně přidán do scénáře; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda se nazývá přidat klíčový snímek do scénáře.

## <a name="cbasekeyframecbasekeyframe"></a><a name="cbasekeyframe"></a>CBaseKeyFrame::CBaseKeyFrame

Vytvoří objekt klíčového snímku.

```
CBaseKeyFrame();
```

## <a name="cbasekeyframegetanimationkeyframe"></a><a name="getanimationkeyframe"></a>CBaseKeyFrame::GetAnimationKeyframe

Vrátí hodnotu základního klíčového snímku.

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální klíčový snímek. Výchozí hodnota je UI_ANIMATION_KEYFRAME_STORYBOARD_START.

### <a name="remarks"></a>Poznámky

Toto je přistupující objekt k základní hodnotě klíčového snímku.

## <a name="cbasekeyframeisadded"></a><a name="isadded"></a>CbaseKeyFrame::Jepřidán

Určuje, zda byl klíčový snímek přidán do scénáře.

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je klíčový snímek přidán do scénáře; otehrwise FALSE.

### <a name="remarks"></a>Poznámky

V základní třídě IsAdded vždy vrátí HODNOTU PRAVDA, ale je přepsána v odvozených třídách.

## <a name="cbasekeyframeiskeyframeatoffset"></a><a name="iskeyframeatoffset"></a>CbaseKeyFrame::IskeyframeatOffset

Určuje, zda má být klíčový snímek přidán do scénáře při posunu nebo po přechodu.

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud klíčový snímek by měl být přidán do scénáře na některé zadané posun. FALSE, pokud klíčový snímek by měl být přidán do scénáře po nějaké přechodu.

### <a name="remarks"></a>Poznámky

Určuje, zda má být klíčový snímek přidán do scénáře při posunu. Posun nebo přechod musí být zadán v odvozené třídě.

## <a name="cbasekeyframem_badded"></a><a name="m_badded"></a>CBaseKeyFrame::m_bAdded

Určuje, zda byl tento klíčový snímek přidán do scénáře.

```
BOOL m_bAdded;
```

## <a name="cbasekeyframem_biskeyframeatoffset"></a><a name="m_biskeyframeatoffset"></a>CBaseKeyFrame::m_bIsKeyframeAtOffset

Určuje, zda má být tento klíčový snímek přidán do scénáře při posunu od jiného existujícího klíčového snímku nebo na konci nějakého přechodu.

```
BOOL m_bIsKeyframeAtOffset;
```

## <a name="cbasekeyframem_keyframe"></a><a name="m_keyframe"></a>CBaseKeyFrame::m_keyframe

Představuje klíčový snímek rozhraní API pro animaci systému Windows. Pokud klíčový snímek není inicializován, je nastaven na předdefinovanou hodnotu UI_ANIMATION_KEYFRAME_STORYBOARD_START.

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
