---
title: Třída CDockState
ms.date: 11/04/2016
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
ms.openlocfilehash: 1c76bcda6465ca86b8da4778d3653cb23001b78b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375552"
---
# <a name="cdockstate-class"></a>Třída CDockState

Serializovaná `CObject` třída, která načte, uvolní nebo vymaže stav jednoho nebo více řídicích panelů ukotvení v trvalé paměti (souboru).

## <a name="syntax"></a>Syntaxe

```
class CDockState : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDockState::Vymazat](#clear)|Vymaže informace o stavu doku.|
|[CDockState::GetVersion](#getversion)|Načte číslo verze uloženého stavu pruhu.|
|[CDockState::LoadState](#loadstate)|Načte informace o stavu z registru nebo . INI.|
|[CDockState::Uložitstav](#savestate)|Uloží informace o stavu do registru nebo souboru INI.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Pole ukazatelů na uložené informace o stavu doku s jednou položkou pro každý ovládací panel.|

## <a name="remarks"></a>Poznámky

Stav ukotvení zahrnuje velikost a umístění panelu a zda je ukotven. Při načítání uloženého stavu `CDockState` ukotvení zkontroluje pozici panelu a pokud pruh není `CDockState` viditelný s aktuálním nastavením obrazovky, změní velikost polohy panelu tak, aby byl viditelný. Hlavním účelem `CDockState` je držet celý stav počtu ovládacích panelů a umožnit, aby tento stav byl uložen a načten buď do registru, aplikace . INI nebo v binární podobě jako `CArchive` součást obsahu objektu.

Panel může být libovolný ovládací panel, včetně panelu nástrojů, stavového řádku nebo dialogového panelu. `CDockState`objekty jsou zapsány a čteny `CArchive` do nebo ze souboru prostřednictvím objektu.

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) načte informace o stavu všech `CControlBar` objektů okna rámce `CDockState` a vloží je do objektu. Obsah `CDockState` objektu pak můžete zapsat do úložiště pomocí [Serialize](../../mfc/reference/cobject-class.md#serialize) nebo [CDockState::SaveState](#savestate). Pokud později chcete obnovit stav ovládacích panelů v okně rámce, `Serialize` můžete načíst stav s nebo [CDockState::LoadState](#loadstate), pak použijte [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) použít uložený stav na ovládací panely okna rámce.

Další informace o ovládacích panelech ukotvení naleznete v článcích [Ovládací panely ovládacích panelů](../../mfc/control-bars.md), [Panely nástrojů: Ukotvení a plovoucí](../../mfc/docking-and-floating-toolbars.md)a Okna [rámů](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxadv.h

## <a name="cdockstateclear"></a><a name="clear"></a>CDockState::Vymazat

Voláním této funkce vymažte `CDockState` všechny informace o ukotvení uložené v objektu.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

To zahrnuje nejen to, zda je lišta ukotvena nebo ne, ale velikost a umístění lišty a zda je či není viditelná.

## <a name="cdockstategetversion"></a><a name="getversion"></a>CDockState::GetVersion

Volání této funkce načíst číslo verze uloženého stavu panelu.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Návratová hodnota

1 pokud jsou uložené informace o pruhu starší než aktuální stav pruhu; 2 pokud jsou uložené informace o pruhu stejné jako aktuální stav pruhu.

### <a name="remarks"></a>Poznámky

Podpora verzí umožňuje revidovaným pruhům přidat nové trvalé vlastnosti a stále schopen rozpoznat a načíst trvalý stav vytvořený starší verzí panelu.

## <a name="cdockstateloadstate"></a><a name="loadstate"></a>CDockState::LoadState

Volání této funkce k načtení informací o stavu z registru nebo . INI.

```
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Odkazuje na řetězec s nulovým teminovaným teminovaným kódem, který určuje název oddílu v inicializačním souboru nebo klíče v registru systému Windows, kde jsou uloženy informace o stavu.

### <a name="remarks"></a>Poznámky

Název profilu je část aplikace . INI nebo registru, který obsahuje informace o stavu pruhů. Informace o stavu řídicího panelu můžete uložit do registru nebo . INI soubor `SaveState`s .

## <a name="cdockstatem_arrbarinfo"></a><a name="m_arrbarinfo"></a>CDockState::m_arrBarInfo

Objekt, `CPtrArray` který je pole ukazatele na uložené informace ovládacího panelu pro každý `CDockState` ovládací panel, který má uloženy informace o stavu v objektu.

```
CPtrArray m_arrBarInfo;
```

## <a name="cdockstatesavestate"></a><a name="savestate"></a>CDockState::Uložitstav

Voláním této funkce uložíte informace o stavu do registru nebo . INI.

```
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Odkazuje na řetězec s nulovým teminovaným teminovaným kódem, který určuje název oddílu v inicializačním souboru nebo klíče v registru systému Windows, kde jsou uloženy informace o stavu.

### <a name="remarks"></a>Poznámky

Název profilu je část aplikace . INI nebo registru, který obsahuje informace o stavu ovládacího panelu. `SaveState`také uloží aktuální velikost obrazovky. Informace o ovládacím panelu můžete načíst z registru nebo . INI soubor `LoadState`s .

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
