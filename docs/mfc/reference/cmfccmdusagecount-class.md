---
title: CMFCCmdUsageCount – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::AddCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::GetCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::HasEnoughInformation
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Reset
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Serialize
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::SetOptions
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
ms.openlocfilehash: 1c03f0c62e508f9d00a352b71c8f3a18604e36c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367742"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount – třída

Sleduje počet použití zpráv systému Windows, například když uživatel vybere položku z nabídky.

## <a name="syntax"></a>Syntaxe

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name (Název)|Popis|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Výchozí konstruktor.|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name (Název)|Popis|
|[CMFCCmdUsageCountCount::AddCmd](#addcmd)|Přírůstky o jeden čítač, který je přidružen k danému příkazu.|
|[CMFCCmdUsageCountCount::GetCount](#getcount)|Načte počet využití, který je přidružen k dané ID příkazu.|
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Určuje, zda tento objekt shromáždil minimální množství dat sledování.|
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Určuje, zda je daný příkaz často používán.|
|[CMFCCmdUsageCountCount::Obnovit](#reset)|Vymaže počet využití všech příkazů.|
|[CMFCCmdUsageCount::Serializovat](#serialize)|Přečte tento objekt z archivu nebo jej zapíše do archivu. (Přepíše [CObject::Serializovat](../../mfc/reference/cobject-class.md#serialize).)|
|[CMFCCmdUsageCountCount::SetOptions](#setoptions)|Nastaví hodnoty `CMFCCmdUsageCount` sdílených datových členů třídy.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|Name (Název)|Popis|
|`m_CmdUsage`|Objekt, `CMap` který mapuje příkazy na jejich použití se počítá.|
|`m_nMinUsagePercentage`|Minimální procento využití pro příkaz, který má být často používán.|
|`m_nStartCount`|Počáteční čítač, který se používá k určení, zda tento objekt shromáždil minimální množství dat sledování.|
|`m_nTotalUsage`|Počet všech sledovaných příkazů.|

### <a name="remarks"></a>Poznámky

Třída `CMFCCmdUsageCount` mapuje každý číselný identifikátor zprávy systému Windows na 32bitový nepodepsaný celočíselný čítač. `CMFCToolBar`tato třída slouží k zobrazení často používaných položek panelu nástrojů. Další informace `CMFCToolBar`o , naleznete v tématu [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md).

Mezi spuštěními programu můžete zachovat `CMFCCmdUsageCount` data třídy. Pomocí metody [CMFCCmdUsageCountCount::Serialize](#serialize) serialize serialize data členů třídy a [cmcmdusagecount::SetOptions](#setoptions) metoda nastavit sdílená data členů.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmdusagecount.h

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a>CMFCCmdUsageCountCount::AddCmd

Přírůstky o jeden čítač, který je přidružen k danému příkazu.

```
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*uiCmd*|[v] Určuje čítač příkazů na přírůstek.|

### <a name="remarks"></a>Poznámky

Tato metoda přidá novou položku do struktury `m_CmdUsage`mapy počtu příkazů , , pokud položka ještě neexistuje.

Tato metoda neprovede žádnou akci v následujících případech:

- Rozhraní panelu nástrojů je v režimu přizpůsobení (metoda [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) vrátí nenulovou hodnotu).

- Příkaz odkazuje na podnabídku nebo oddělovač nabídky ( *uiCmd* se rovná 0 nebo -1).

- *uiCmd* odkazuje na standardní příkaz `IsStandardCommand` (globální funkce vrátí nenulovou hodnotu).

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a>CMFCCmdUsageCountCount::GetCount

Načte počet využití, který je přidružen k dané ID příkazu.

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*uiCmd*|[v] ID čítače příkazů načíst.|

### <a name="return-value"></a>Návratová hodnota

Počet využití, který je přidružen k dané ID příkazu.

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation

Určuje, zda tento objekt obdržel minimální množství dat sledování.

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud tento objekt obdržel minimální množství dat sledování; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí nenulovou hodnotu, `m_nTotalUsage`pokud je celkový počet všech sledovaných příkazů `m_nStartCount`roven nebo větší než počáteční počet . Ve výchozím nastavení rozhraní framework nastaví počáteční počet 0. Tuto hodnotu můžete přepsat pomocí metody [CMFCCmdUsageCount::SetOptions.](#setoptions)

Tato metoda je použita [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) k určení, zda chcete zobrazit všechny dostupné příkazy nabídky.

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd

Určuje, zda je daný příkaz často používán.

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*uiCmd*|[v] Určuje příkaz, který chcete zkontrolovat.|

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je příkaz často používán; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí 0, pokud `m_nTotalUsage`celkové využití příkazu, , je 0. V opačném případě tato metoda vrátí nenulovou, pokud je procento, `m_nMinUsagePercentage`jehož je použit zadaný příkaz, větší než minimální procento . Ve výchozím nastavení framework nastaví minimální procento na 5. Tuto hodnotu můžete přepsat pomocí metody [CMFCCmdUsageCount::SetOptions.](#setoptions) Pokud je minimální procento 0, vrátí tato metoda nenulovou hodnotu, pokud je zadaný počet příkazů větší než 0.

[CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) používá tuto metodu k určení, zda je příkaz zřídka používán.

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a>CMFCCmdUsageCountCount::Obnovit

Vymaže počet využití všech příkazů.

```
void Reset();
```

### <a name="remarks"></a>Poznámky

Voláním této metody zrušte všechny položky `m_CmdUsage`ze struktury mapy počtu příkazů `m_nTotalUsage`a obnovení celkového využití příkazu , čítače 0.

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a>CMFCCmdUsageCount::Serializovat

Přečte tento objekt z archivu nebo jej zapíše do archivu.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*ar*|[v] Objekt `CArchive` serializovat z nebo do.|

### <a name="remarks"></a>Poznámky

Tato metoda serializuje strukturu mapy počtu `m_CmdUsage`příkazů a celkové využití `m_nTotalUsage`příkazu , čítače od nebo do zadaného archivu.

Příklady serializace naleznete v tématu [Serializace: Serializace objektu](../../mfc/serialization-serializing-an-object.md).

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a>CMFCCmdUsageCountCount::SetOptions

Nastaví hodnoty `CMFCCmdUsageCount` sdílených datových členů třídy.

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*nStartCount*|[v] Nový počáteční počet všech sledovaných příkazů.|
|*nMinUsagePercentage*|[v] Nové minimální procento využití.|

### <a name="return-value"></a>Návratová hodnota

TRUE Pokud je metoda úspěšná, NEPRAVDA, pokud je parametr *nMinUsagePercentage* větší nebo roven 100.

### <a name="remarks"></a>Poznámky

Tato `CMFCCmdUsageCount` metoda nastaví členy `m_nStartCount` `m_nMinUsagePercentage` dat sdílené třídy a *nStartCount* a *nMinUsagePercentage*, v uvedeném pořadí. `m_nStartCount`používá [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) metoda k určení, zda tento objekt shromáždil minimální množství data sledování. `m_nMinUsagePercentage`používá [cmcmdusagecount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) metoda k určení, zda daný příkaz je často používán.

V sestavení ladění tato metoda generuje selhání kontrolního výrazu, pokud je parametr *nMinUsagePercentage* větší nebo roven 100.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
