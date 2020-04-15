---
title: Třída CKeyFrame
ms.date: 11/04/2016
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
helpviewer_keywords:
- CKeyFrame [MFC], CKeyFrame
- CKeyFrame [MFC], AddToStoryboard
- CKeyFrame [MFC], AddToStoryboardAfterTransition
- CKeyFrame [MFC], AddToStoryboardAtOffset
- CKeyFrame [MFC], GetExistingKeyframe
- CKeyFrame [MFC], GetOffset
- CKeyFrame [MFC], GetTransition
- CKeyFrame [MFC], m_offset
- CKeyFrame [MFC], m_pExistingKeyFrame
- CKeyFrame [MFC], m_pTransition
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
ms.openlocfilehash: f535503338a82c7cc70455ae6a08cdab0f13c624
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372297"
---
# <a name="ckeyframe-class"></a>Třída CKeyFrame

Představuje klíčový snímek animace.

## <a name="syntax"></a>Syntaxe

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CKeyFrame::CKeyFrame](#ckeyframe)|Přetíženo. Vytvoří klíčový snímek, který závisí na jiném klíčovém snímku.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|Přidá klíčový snímek do scénáře. (Přepíše [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Přidá klíčový snímek do scénáře po přechodu.|
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Přidá klíčový snímek do scénáře na posun.|
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Vrátí ukazatel na klíčový snímek, na kterém tento klíčový snímek závisí.|
|[CKeyFrame::GetOffset](#getoffset)|Vrátí posun od jiného klíčového snímku.|
|[CKeyFrame::GetTransition](#gettransition)|Vrátí ukazatel na přechod, na kterém tento klíčový snímek závisí.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CKeyFrame::m_offset](#m_offset)|Určuje posun tohoto klíčového snímku od klíčového snímku uloženého v m_pExistingKeyFrame.|
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Uloží ukazatel na existující keframe. Tento klíčový snímek je přidán do scénáře s m_offset existující klíčový snímek.|
|[CKeyFrame::m_pTransition](#m_ptransition)|Ukládá ukazatel na transtion, který začíná v tomto klíčovém snímku.|

## <a name="remarks"></a>Poznámky

Tato třída implementuje klíčový snímek animace. Klíčový snímek představuje okamžik v čase ve scénáři a lze jej použít k určení počátečního a koncového času přechodů. Klíčový snímek může být založen na jiném klíčovém snímku a může mít posun (v sekundách) od něj nebo může být založen na přechodu a představovat okamžik v čase, kdy tento přechod končí.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="ckeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CKeyFrame::AddToStoryboard

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
Určuje, zda má být klíčový snímek nebo přechod rekurzivně.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl klíčový snímek úspěšně přidán.

### <a name="remarks"></a>Poznámky

Tato metoda přidá klíčový snímek do scénáře. Pokud závisí na jiný klíčový snímek nebo přechod a bDeepAdd je PRAVDA, tato metoda se pokusí přidat rekurzivně.

## <a name="ckeyframeaddtostoryboardaftertransition"></a><a name="addtostoryboardaftertransition"></a>CKeyFrame::AddToStoryboardAfterTransition

Přidá klíčový snímek do scénáře po přechodu.

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénář.

*bDeepAdd*<br/>
Určuje, zda má být přechod rekurzivně přidat.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl klíčový snímek úspěšně přidán.

### <a name="remarks"></a>Poznámky

Tato funkce je volána rámci přidat klíčový snímek do scénáře po přechodu.

## <a name="ckeyframeaddtostoryboardatoffset"></a><a name="addtostoryboardatoffset"></a>CKeyFrame::AddToStoryboardAtOffset

Přidá klíčový snímek do scénáře na posun.

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénář.

*bDeepAdd*<br/>
Určuje, zda má být tento klíčový snímek znovu závislý na tomto klíčovém snímku.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl klíčový snímek úspěšně přidán.

### <a name="remarks"></a>Poznámky

Tato funkce je volána rámci přidat klíčový snímek do scénáře na posun.

## <a name="ckeyframeckeyframe"></a><a name="ckeyframe"></a>CKeyFrame::CKeyFrame

Vytvoří klíčový snímek, který závisí na přechodu.

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parametry

*pPřechod*<br/>
Ukazatel na přechod.

*pKlíč*<br/>
Ukazatel na klíčový snímek.

*Posun*<br/>
Posun v sekundách od klíčového snímku určeného pKeyframe.

### <a name="remarks"></a>Poznámky

Vytvořený klíčový snímek bude představovat okamžik v čase ve scénáři při ukončení zadaného přechodu.

## <a name="ckeyframegetexistingkeyframe"></a><a name="getexistingkeyframe"></a>CKeyFrame::GetExistingKeyframe

Vrátí ukazatel na klíčový snímek, na kterém tento klíčový snímek závisí.

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel na klíčový snímek nebo NULL, pokud tento klíčový snímek nezávisí na jiném klíčovém snímku.

### <a name="remarks"></a>Poznámky

Toto je přistupující objekt ke klíčovému snímku, na kterém tento klíčový snímek závisí.

## <a name="ckeyframegetoffset"></a><a name="getoffset"></a>CKeyFrame::GetOffset

Vrátí posun od jiného klíčového snímku.

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>Návratová hodnota

Posun v sekundách od jiného klíčového snímku.

### <a name="remarks"></a>Poznámky

Tato metoda by měla být volána k určení posun v sekundách od jiného klíčového snímku.

## <a name="ckeyframegettransition"></a><a name="gettransition"></a>CKeyFrame::GetTransition

Vrátí ukazatel na přechod, na kterém tento klíčový snímek závisí.

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel přechodu nebo NULL, pokud tento klíčový snímek nezávisí na přechodu.

### <a name="remarks"></a>Poznámky

Toto je přistupující objekt k přechodu tento klíčový snímek závisí na.

## <a name="ckeyframem_offset"></a><a name="m_offset"></a>CKeyFrame::m_offset

Určuje posun tohoto klíčového snímku od klíčového snímku uloženého v m_pExistingKeyFrame.

```
UI_ANIMATION_SECONDS m_offset;
```

## <a name="ckeyframem_pexistingkeyframe"></a><a name="m_pexistingkeyframe"></a>CKeyFrame::m_pExistingKeyFrame

Uloží ukazatel na existující keframe. Tento klíčový snímek je přidán do scénáře s m_offset existující klíčový snímek.

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

## <a name="ckeyframem_ptransition"></a><a name="m_ptransition"></a>CKeyFrame::m_pTransition

Ukládá ukazatel na transtion, který začíná v tomto klíčovém snímku.

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
