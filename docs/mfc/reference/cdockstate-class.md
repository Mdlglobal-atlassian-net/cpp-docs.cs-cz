---
title: "Třída CDockState | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6669f5a2b54c376e545b1ba6b9227d6137726256
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdockstate-class"></a>CDockState – třída
Serializovaný seznam `CObject` třídu, která načte, zrušeno jeho zavedení nebo vymaže stavu jednoho nebo více ukotvení ovládacího prvku panely v trvalé paměti (soubor).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDockState : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDockState::Clear](#clear)|Vymaže informace o stavu ukotvení.|  
|[CDockState::GetVersion](#getversion)|Načte číslo verze uložené panel stavu.|  
|[CDockState::LoadState](#loadstate)|Načte stav informace z registru nebo. Soubor INI.|  
|[CDockState::SaveState](#savestate)|Uloží informace o stavu do registru nebo soubor INI.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Ukotvení – pole ukazatele na uložené informace o stavu s jeden záznam pro každý ovládací prvek panelu.|  
  
## <a name="remarks"></a>Poznámky  
 Stav ukotvení zahrnuje velikost a umístění panelu a zda je ukotvena. Při načítání uložené ukotvení stavu, `CDockState` kontroluje pruhu pozice a pokud není viditelná s aktuálním nastavením obrazovky panelu `CDockState` škáluje pruhu umístěte tak, aby byl viditelný. Hlavním účelem `CDockState` je pro uložení celé stav počet ovládací pruhy a povolit tento stav uložit a načíst buď registru aplikace společnosti. Soubor INI, nebo v binárním formátu jako součást `CArchive` obsah objektu.  
  
 Na panelu může být libovolný lze ukotvit ovládací prvek panelu, včetně nástrojů, stavový řádek nebo panel dialogového okna. `CDockState`objekty jsou zapsány a číst do nebo ze souboru prostřednictvím `CArchive` objektu.  
  
 [CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) načte informace o stavu všech rámce okna na `CControlBar` objekty a vloží ho do `CDockState` objektu. Poté můžete napsat obsah `CDockState` objektu k úložišti s [serializace](../../mfc/reference/cobject-class.md#serialize) nebo [CDockState::SaveState](#savestate). Pokud chcete později obnovit stav ovládací pruhy v rámci okna, je možné načíst stav s `Serialize` nebo [CDockState::LoadState](#loadstate), pak použít [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) použít uložené Stav má ovládací pruhy rámce okna.  
  
 Další informace o ukotvení ovládací pruhy, najdete v článcích [ovládací pruhy](../../mfc/control-bars.md), [panely nástrojů: Ukotvitelné a plovoucí](../../mfc/docking-and-floating-toolbars.md), a [okna s rámečkem](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDockState`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxadv.h  
  
##  <a name="clear"></a>CDockState::Clear  
 Volání této funkce, které chcete vymazat všechny ukotvení informace uložené v `CDockState` objektu.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Poznámky  
 To zahrnuje nejen zda panelu ukotven nebo Ne, ale na panelu velikost a umístění, a zda je viditelná.  
  
##  <a name="getversion"></a>CDockState::GetVersion  
 Volání této funkce načíst číslo verze uložené panel stavu.  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 v případě 1 panelu uložené informace je starší než aktuální panelu stavu; v případě 2 panelu uložené informace je stejný jako aktuální panel stavu.  
  
### <a name="remarks"></a>Poznámky  
 Podpora verzí umožňuje revidovaný panelu a přidat nové vlastnosti trvalé i dál možné zjistit a načíst trvalý stav vytvořena ve starší verzi panelu.  
  
##  <a name="loadstate"></a>CDockState::LoadState  
 Volání této funkce se načíst informace o stavu z registru nebo. Soubor INI.  
  
```  
void LoadState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszProfileName`  
 Bodů na hodnotu null teminated řetězec, který určuje název oddílu v inicializační soubor nebo klíč v registru systému Windows se uloží informace o stavu.  
  
### <a name="remarks"></a>Poznámky  
 Název profilu je v části aplikace. Soubor INI nebo registru, který obsahuje informace o stavu řádky. Ovládací prvek panelu Informace o stavu můžete uložit do registru nebo. Soubor INI s `SaveState`.  
  
##  <a name="m_arrbarinfo"></a>CDockState::m_arrBarInfo  
 A `CPtrArray` objekt, který je pole odkazy na informace o uložené ovládacího prvku panel pro každý ovládací prvek panel, který má uložené informace o stavu v `CDockState` objektu.  
  
```  
CPtrArray m_arrBarInfo;  
```  
  
##  <a name="savestate"></a>CDockState::SaveState  
 Volání této funkce se uložit informace o stavu do registru nebo. Soubor INI.  
  
```  
void SaveState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszProfileName`  
 Bodů na hodnotu null teminated řetězec, který určuje název oddílu v inicializační soubor nebo klíč v registru systému Windows se uloží informace o stavu.  
  
### <a name="remarks"></a>Poznámky  
 Název profilu je v části aplikace. Soubor INI nebo registru, který obsahuje informace o stavu ovládacích pruhů. `SaveState`Navíc šetří pro aktuální obrazovku. Informace o řízení panelu můžete načíst z registru nebo. Soubor INI s `LoadState`.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)

