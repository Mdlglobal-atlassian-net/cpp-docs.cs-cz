---
title: Cmfccmdusagecount – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44172ffdf7985b7ab304e232eb03b859313df6bc
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853761"
---
# <a name="cmfccmdusagecount-class"></a>Cmfccmdusagecount – třída
Sleduje počet použití zpráv Windows, například když uživatel vybere položku z nabídky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCCmdUsageCount : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Výchozí konstruktor.|  
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Zvýší o jedna čítač, který je přidružen daný příkaz.|  
|[CMFCCmdUsageCount::GetCount](#getcount)|Získá počet použití, který je přidružen ID daného příkazu.|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Určuje, zda tento objekt se budou shromažďovat data o sledování minimální velikost.|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Určuje, zda se často používá daný příkaz.|  
|[CMFCCmdUsageCount::Reset](#reset)|Vymaže počet použití všech příkazů.|  
|[CMFCCmdUsageCount::Serialize](#serialize)|Čte tento objekt z archivu nebo zapíše do archivu. (Přepíše [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Nastaví hodnoty sdílené `CMFCCmdUsageCount` datové členy třídy.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|Název|Popis|  
|`m_CmdUsage`|A `CMap` objekt, který mapuje příkazy k jejich počty využití.|  
|`m_nMinUsagePercentage`|Minimální využití je procento pro příkaz, který se často používá.|  
|`m_nStartCount`|Start čítač, který se používá k určení, zda tento objekt se budou shromažďovat data o sledování minimální velikost.|  
|`m_nTotalUsage`|Počet všech sledovaných příkazy.|  
  
### <a name="remarks"></a>Poznámky  
 `CMFCCmdUsageCount` Třídy mapuje každý číselný identifikátor zprávy Windows čítač 32bitové celé číslo bez znaménka. `CMFCToolBar` Tato třída se používá k zobrazení položky panelu nástrojů často používané. Další informace o `CMFCToolBar`, naleznete v tématu [cmfctoolbar – třída](../../mfc/reference/cmfctoolbar-class.md).  
  
 Je možné zachovat `CMFCCmdUsageCount` třídy dat jednotlivá spuštění tohoto programu. Použití [CMFCCmdUsageCount::Serialize](#serialize) metoda k serializaci dat člena třídy a [CMFCCmdUsageCount::SetOptions](#setoptions) metody nastavte sdílené členská data.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfccmdusagecount –](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmdusagecount.h  
  
##  <a name="addcmd"></a>  CMFCCmdUsageCount::AddCmd  
 Zvýší o jedna čítač, který je přidružen daný příkaz.  
  
```  
void AddCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[in] *uiCmd*|Určuje příkaz čítače se zvýší.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá novou položku do mapy struktury příkaz počty `m_CmdUsage`, pokud položka už neexistuje.  
  
 Tato metoda neprovede v následujících případech:  
  
-   Rozhraní nástrojů je v režimu úprav ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) metoda vrátí nenulovou hodnotu).  
  
-   Příkaz odkazuje na oddělovač podnabídky nebo nabídku ( *uiCmd* rovná 0 nebo -1).  
  
- *uiCmd* odkazuje na standardních příkazů (globální `IsStandardCommand` funkce vrátí nenulovou hodnotu).  
  
##  <a name="getcount"></a>  CMFCCmdUsageCount::GetCount  
 Získá počet použití, který je přidružen ID daného příkazu.  
  
```  
UINT GetCount(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[in] *uiCmd*|ID čítač příkaz pro načtení.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet použití, který je přidružen ID daného příkazu.  
  
##  <a name="hasenoughinformation"></a>  CMFCCmdUsageCount::HasEnoughInformation  
 Určuje, zda tento objekt byl přijat minimální množství data sledování.  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud tento objekt byl přijat minimální množství dat pro sledování jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrací nenulovou hodnotu, pokud celkový počet `m_nTotalUsage`, všechny sledované příkazů je roven nebo větší než počáteční počet `m_nStartCount`. Rozhraní framework ve výchozím nastavení, nastaví počáteční počet 0. Tuto hodnotu lze přepsat pomocí [CMFCCmdUsageCount::SetOptions](#setoptions) metody.  
  
 Tato metoda používá [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) k určení, jestli se má zobrazit všechny dostupné příkazy nabídek.  
  
##  <a name="isfreqeuntlyusedcmd"></a>  CMFCCmdUsageCount::IsFreqeuntlyUsedCmd  
 Určuje, zda se často používá daný příkaz.  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[in] *uiCmd*|Určuje příkaz a zkontrolujte.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud příkaz se často používá; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu 0, pokud využití celkový příkaz `m_nTotalUsage`, je 0. Jinak tato metoda vrátí nenulovou hodnotu, pokud je větší než minimální procento, procento z nich se používá zadaný příkaz `m_nMinUsagePercentage`. Rozhraní framework ve výchozím nastavení, nastaví minimální procento na 5. Tuto hodnotu lze přepsat pomocí [CMFCCmdUsageCount::SetOptions](#setoptions) metody. Pokud je minimální procento 0, tato metoda vrátí nenulovou hodnotu, pokud zadaný příkaz počet je větší než 0.  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) používá tuto metodu pro určení, jestli se příkaz používá zřídka.  
  
##  <a name="reset"></a>  CMFCCmdUsageCount::Reset  
 Vymaže počet použití všech příkazů.  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze vymazat všechny položky ze struktury map příkaz počty `m_CmdUsage`a resetovat použití celkový příkazu `m_nTotalUsage`, čítač na hodnotu 0.  
  
##  <a name="serialize"></a>  CMFCCmdUsageCount::Serialize  
 Čte tento objekt z archivu nebo zapíše do archivu.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[in] *ar*|A `CArchive` objektu určeného k serializaci z nebo do.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda serializuje strukturu mapy příkaz počty `m_CmdUsage`a použití celkový příkazu `m_nTotalUsage`, čítač z nebo do zadaného archivu.  
  
 Příklady serializace naleznete v tématu [serializace: serializace objektu](../../mfc/serialization-serializing-an-object.md).  
  
##  <a name="setoptions"></a>  CMFCCmdUsageCount::SetOptions  
 Nastaví hodnoty sdílené `CMFCCmdUsageCount` datové členy třídy.  
  
```  
static BOOL __stdcall SetOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[in] *nStartCount*|Nový počáteční počet všechny sledované příkazy.|  
|[in] *nMinUsagePercentage*|Nový minimální využití je procento.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda uspěje, FALSE-li *nMinUsagePercentage* parametr je větší než nebo rovna 100.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví sdílený `CMFCCmdUsageCount` datové členy třídy `m_nStartCount` a `m_nMinUsagePercentage` k *nStartCount* a *nMinUsagePercentage*v uvedeném pořadí. `m_nStartCount` používá [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) metodou ke zjištění, zda tento objekt se budou shromažďovat data o sledování minimální velikost. `m_nMinUsagePercentage` používá [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) metodou ke zjištění, zda se často používá daný příkaz.  
  
 V sestavení ladění, tato metoda generuje selhání kontrolního výrazu, pokud *nMinUsagePercentage* parametr je větší než nebo rovna 100.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
