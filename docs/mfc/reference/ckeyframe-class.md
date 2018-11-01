---
title: Ckeyframe – třída
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
ms.openlocfilehash: b6ebe5ba78a259014f62bdf04f30e856a57f1aba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451074"
---
# <a name="ckeyframe-class"></a>Ckeyframe – třída

Představuje klíčový snímek animace.

## <a name="syntax"></a>Syntaxe

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CKeyFrame::CKeyFrame](#ckeyframe)|Přetíženo. Sestaví klíčový snímek, který závisí na jiné klíčový snímek.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|Přidá klíčového snímku do scénáře. (Přepíše [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Přidá klíčového snímku do scénáře po přechodu.|
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Přidá klíčového snímku do scénáře na posunu.|
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Vrací ukazatel na klíčový snímek tohoto klíčového snímku, na kterém závisí.|
|[CKeyFrame::GetOffset](#getoffset)|Vrátí posun z jiných klíčový snímek.|
|[CKeyFrame::GetTransition](#gettransition)|Vrací ukazatel na přechod tento klíčový snímek, na kterém závisí.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CKeyFrame::m_offset](#m_offset)|Určuje posun tento klíčový snímek z klíčového snímku uloženy v m_pExistingKeyFrame.|
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Uchovává ukazatel na existující keframe. Tento klíčový snímek se přidá do scénáře s m_offset existující klíčový snímek.|
|[CKeyFrame::m_pTransition](#m_ptransition)|Uchovává ukazatel na transtion, který začíná na tento klíčový snímek.|

## <a name="remarks"></a>Poznámky

Tato třída implementuje klíčový snímek animace. Klíčový snímek představuje okamžik v čase v rámci scénáře a je možné zadat počáteční a koncový čas přechodů. Klíčový snímek mohou být založeny na jiné klíčový snímek a mají posun (v sekundách), nebo mohou být založeny na přechod a představují okamžiku v čase po ukončení tohoto přechodu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cbasekeyframe –](../../mfc/reference/cbasekeyframe-class.md)

[Ckeyframe –](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="addtostoryboard"></a>  CKeyFrame::AddToStoryboard

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
Určuje, jestli se má přidat klíčový snímek nebo přechod rekurzivně.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud klíčový snímek byl úspěšně přidán.

### <a name="remarks"></a>Poznámky

Tato metoda přidá klíčového snímku do scénáře. Pokud závisí na jiné klíčového snímku nebo přechodu a bDeepAdd má hodnotu TRUE, tato metoda se pokusí přidat rekurzivně.

##  <a name="addtostoryboardaftertransition"></a>  CKeyFrame::AddToStoryboardAfterTransition

Přidá klíčového snímku do scénáře po přechodu.

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénáře.

*bDeepAdd*<br/>
Určuje, jestli se má přidat rekurzivně přechodu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud klíčový snímek byl úspěšně přidán.

### <a name="remarks"></a>Poznámky

Tato funkce je volána rozhraním, chcete-li přidat klíčový snímek do scénáře po přechodu.

##  <a name="addtostoryboardatoffset"></a>  CKeyFrame::AddToStoryboardAtOffset

Přidá klíčového snímku do scénáře na posunu.

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Ukazatel na scénáře.

*bDeepAdd*<br/>
Určuje, zda chcete-li přidat klíčový snímek tohoto klíčového snímku závisí na rekurzivně.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud klíčový snímek byl úspěšně přidán.

### <a name="remarks"></a>Poznámky

Tato funkce je volána rozhraním, chcete-li přidat klíčový snímek do scénáře na posunu.

##  <a name="ckeyframe"></a>  CKeyFrame::CKeyFrame

Sestaví klíčový snímek, který závisí na přechod.

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parametry

*pTransition*<br/>
Ukazatel na přechod.

*pKeyframe*<br/>
Ukazatel na klíčový snímek.

*Posun*<br/>
Posun v sekundách, z určeného pKeyframe klíčový snímek.

### <a name="remarks"></a>Poznámky

Konstruovaný klíčový snímek bude reprezentovat okamžik v čase v rámci scénáře při ukončení zadaného přechodu.

##  <a name="getexistingkeyframe"></a>  CKeyFrame::GetExistingKeyframe

Vrací ukazatel na klíčový snímek tohoto klíčového snímku, na kterém závisí.

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel klíčový snímek, nebo hodnota NULL, pokud tento klíčový snímek není závislý na jiných klíčový snímek.

### <a name="remarks"></a>Poznámky

Toto je přístupový objekt pro tento klíčový snímek, na kterém závisí klíčového snímku.

##  <a name="getoffset"></a>  CKeyFrame::GetOffset

Vrátí posun z jiných klíčový snímek.

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>Návratová hodnota

Posun v řádu sekund z jiných klíčový snímek.

### <a name="remarks"></a>Poznámky

Tuto metodu lze volat pro určení posunu v řádu sekund z jiných klíčový snímek.

##  <a name="gettransition"></a>  CKeyFrame::GetTransition

Vrací ukazatel na přechod tento klíčový snímek, na kterém závisí.

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>Návratová hodnota

Platný ukazatel do přechodu nebo hodnota NULL, pokud tento klíčový snímek není závislý na přechod.

### <a name="remarks"></a>Poznámky

Toto je přístupový objekt pro tento klíčový snímek, na kterém závisí přechod.

##  <a name="m_offset"></a>  CKeyFrame::m_offset

Určuje posun tento klíčový snímek z klíčového snímku uloženy v m_pExistingKeyFrame.

```
UI_ANIMATION_SECONDS m_offset;
```

##  <a name="m_pexistingkeyframe"></a>  CKeyFrame::m_pExistingKeyFrame

Uchovává ukazatel na existující keframe. Tento klíčový snímek se přidá do scénáře s m_offset existující klíčový snímek.

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

##  <a name="m_ptransition"></a>  CKeyFrame::m_pTransition

Uchovává ukazatel na transtion, který začíná na tento klíčový snímek.

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
