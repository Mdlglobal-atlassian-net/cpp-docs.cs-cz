---
title: Cdockstate – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
dev_langs:
- C++
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e8cde676795067005406f3eba86bdda7082f272
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435594"
---
# <a name="cdockstate-class"></a>Cdockstate – třída

Serializovaný seznam `CObject` panely třídu, která načte, uvolní nebo vymaže stav jednoho nebo více prvků ukotvení v trvalé paměti (soubor).

## <a name="syntax"></a>Syntaxe

```
class CDockState : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDockState::Clear](#clear)|Vymaže informace o stavu ukotvení.|
|[CDockState::GetVersion](#getversion)|Získá číslo verze uložené panelu stavu.|
|[CDockState::LoadState](#loadstate)|Načte informace z registru stavu nebo. Soubor INI.|
|[CDockState::SaveState](#savestate)|Uloží informace o stavu do registru nebo soubor INI.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Pole ukazatelů na uloženou ukotvit informace o stavu s jednou položkou pro každý ovládací prvek panel.|

## <a name="remarks"></a>Poznámky

Ukotvit stavu zahrnuje velikost a umístění panelu a určuje, jestli je ukotven. Při načítání uložený stav, ukotvit `CDockState` kontroluje na panelu umístění a pokud není viditelná s aktuálním nastavením obrazovky, na panelu `CDockState` škáluje na panelu umístění tak, aby byl viditelný. Hlavním účelem `CDockState` je k uložení stavu celou řadu ovládacích pruhů a umožňují tento stav se má uložit a načíst do registru, aplikaci prvku. Soubor INI, nebo v binárním formátu jako součást `CArchive` obsah objektu.

Na panelu může být libovolný ukotvitelné ovládací prvek řádku, včetně nástrojů, stavovém řádku nebo panel dialogového okna. `CDockState` Zapisovat a číst do nebo ze souboru prostřednictvím objektů `CArchive` objektu.

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) načte informace o stavu ze všech rámce okna `CControlBar` objekty a umístí jej do `CDockState` objektu. Pak můžou zapisovat obsah `CDockState` objektu k úložišti s [serializace](../../mfc/reference/cobject-class.md#serialize) nebo [CDockState::SaveState](#savestate). Pokud chcete později obnovit stav ovládací pruhy v okně rámce, můžete načíst stav s `Serialize` nebo [CDockState::LoadState](#loadstate), pak použijte [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) použít uložené Stav má okno rámce ovládací panely.

Další informace o ukotvení ovládacích panelů, najdete v článcích [ovládací pruhy](../../mfc/control-bars.md), [panelů nástrojů: Ukotvitelné a plovoucí](../../mfc/docking-and-floating-toolbars.md), a [rámce Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxadv.h

##  <a name="clear"></a>  CDockState::Clear

Voláním této funkce, které chcete vymazat všechny dokovací informace uložené v `CDockState` objektu.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

To zahrnuje nejen, zda je panel ukotven nebo Ne, ale velikost a umístění na panelu, a jestli je viditelný.

##  <a name="getversion"></a>  CDockState::GetVersion

Voláním této funkce načtete číslo verze uložené panelu stavu.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Návratová hodnota

1, pokud panel uložené informace je starší než aktuální panelu stavu; 2 if panelu uložené informace je stejný jako aktuální stav panelu.

### <a name="remarks"></a>Poznámky

Podpora verzí umožňuje revidované řádku a přidat nové vlastnosti trvalé stále moct zjišťovat a načíst trvalý stav vytvořena pomocí starší verze panelu.

##  <a name="loadstate"></a>  CDockState::LoadState

Volání této funkce načtete informace o stavu z registru nebo. Soubor INI.

```
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Odkazuje na hodnotu null teminated řetězec určující název oddílu v souboru inicializace nebo klíče v registru Windows ukládat informace o stavu.

### <a name="remarks"></a>Poznámky

Název profilu je část vaší aplikace. Soubor INI nebo registru, který obsahuje informace o stavu na pruhy. Ovládací prvek panelu informací o stavu můžete uložit do registru nebo. Soubor INI s `SaveState`.

##  <a name="m_arrbarinfo"></a>  CDockState::m_arrBarInfo

A `CPtrArray` objekt, který je pole ukazatelů na uložené řídicí panel informace pro každý ovládací panel, který se má uložit informace o stavu v `CDockState` objektu.

```
CPtrArray m_arrBarInfo;
```

##  <a name="savestate"></a>  CDockState::SaveState

Voláním této funkce se uložit informace o stavu do registru nebo. Soubor INI.

```
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Odkazuje na hodnotu null teminated řetězec určující název oddílu v souboru inicializace nebo klíče v registru Windows ukládat informace o stavu.

### <a name="remarks"></a>Poznámky

Název profilu je část vaší aplikace. Soubor INI nebo registru, který obsahuje informace o stavu ovládacím panelu. `SaveState` také ukládá aktuální velikost obrazovky. Řídicí panel Informace můžete načíst z registru nebo. Soubor INI s `LoadState`.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

