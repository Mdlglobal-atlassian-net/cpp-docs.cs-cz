---
title: "Třída CMFCCmdUsageCount | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 718f373d51c9b8dfd12e1d3559c3a9078600a54a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|Název|Popis|  
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Výchozí konstruktor.|  
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Zvýší jedním čítač, který je přidružen daný příkaz.|  
|[CMFCCmdUsageCount::GetCount](#getcount)|Načte počet použití, který je přidružen ID daného příkazu.|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Určuje, zda má tento objekt shromažďovány minimální množství data sledování.|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Určuje, zda daný příkaz se často používá.|  
|[CMFCCmdUsageCount::Reset](#reset)|Vymaže počet použití všech příkazů.|  
|[CMFCCmdUsageCount::Serialize](#serialize)|Čte tento objekt z archivu nebo zapíše ho do archivu. (Přepisuje [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Nastaví hodnoty sdílené `CMFCCmdUsageCount` třídy datových členů.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|Název|Popis|  
|`m_CmdUsage`|A `CMap` objekt, který se mapuje na jejich počet použití příkazů.|  
|`m_nMinUsagePercentage`|Procento využití minimální pro příkaz, který má být často používané.|  
|`m_nStartCount`|Spuštění čítač, který se používá k určení, zda tento objekt se budou shromažďovat data sledování minimální velikost.|  
|`m_nTotalUsage`|Počet všechny sledované příkazy.|  
  
### <a name="remarks"></a>Poznámky  
 `CMFCCmdUsageCount` Třída mapuje každý číselný identifikátor zprávy Windows čítač 32bitové celé číslo bez znaménka. `CMFCToolBar`Tato třída se používá pro zobrazení položek používaných nástrojů. Další informace o `CMFCToolBar`, najdete v části [CMFCToolBar třída](../../mfc/reference/cmfctoolbar-class.md).  
  
 Můžete zachovat `CMFCCmdUsageCount` třídy dat mezi spustí vašeho programu. Použití [CMFCCmdUsageCount::Serialize](#serialize) metoda k serializaci dat člena třídy a [CMFCCmdUsageCount::SetOptions](#setoptions) metodu a nastavit dat sdíleného člena.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmdusagecount.h  
  
##  <a name="addcmd"></a>CMFCCmdUsageCount::AddCmd  
 Zvýší jedním čítač, který je přidružen daný příkaz.  
  
```  
void AddCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`uiCmd`|Určuje příkaz čítače se zvýší.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá novou položku mapy struktura příkaz počty `m_CmdUsage`, pokud položka již neexistuje.  
  
 Tato metoda neprovede žádnou akci v následujících případech:  
  
-   Rozhraní framework nástrojů je v režimu přizpůsobení ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) metoda vrátí nenulovou hodnotu).  
  
-   Příkaz odkazuje na dílčí nebo nabídky oddělovače ( `uiCmd` rovná 0 nebo -1).  
  
- `uiCmd`odkazuje na standardních příkazů (na globální `IsStandardCommand` funkce vrátí nenulovou hodnotu).  
  
##  <a name="getcount"></a>CMFCCmdUsageCount::GetCount  
 Načte počet použití, který je přidružen ID daného příkazu.  
  
```  
UINT GetCount(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`uiCmd`|ID čítač příkaz pro načtení.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet použití, který je přidružen ID daného příkazu.  
  
##  <a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation  
 Určuje, zda tento objekt byl přijat minimální množství data sledování.  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud tento objekt byl přijat minimální množství sledování dat; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí nenulovou hodnotu, pokud celkový počet `m_nTotalUsage`, všechny sledované příkazů je rovna nebo větší než počáteční počet `m_nStartCount`. Ve výchozím nastavení rozhraní nastaví počáteční počet 0. Tuto hodnotu lze přepsat pomocí [CMFCCmdUsageCount::SetOptions](#setoptions) metoda.  
  
 Tato metoda se používá ve [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) k určení, zda se zobrazí všechny dostupné příkazy nabídek.  
  
##  <a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd  
 Určuje, zda daný příkaz se často používá.  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`uiCmd`|Určuje příkaz, který chcete zkontrolovat.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se často používá příkaz; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu 0, pokud celkový počet příkaz využití, `m_nTotalUsage`, je 0. Tato metoda vrátí, jinak hodnota nenulové hodnoty, pokud je větší než minimální procento procento, které se používá zadaný příkaz `m_nMinUsagePercentage`. Ve výchozím nastavení rozhraní Nastaví minimální procento 5. Tuto hodnotu lze přepsat pomocí [CMFCCmdUsageCount::SetOptions](#setoptions) metoda. Pokud je minimální procento 0, vrátí tato metoda nenulové hodnoty, pokud je zadaný příkaz počet je větší než 0.  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) tato metoda používá k určení, jestli příkaz zřídka se používá.  
  
##  <a name="reset"></a>CMFCCmdUsageCount::Reset  
 Vymaže počet použití všech příkazů.  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze vymazat všechny položky ze struktury mapy příkaz počty `m_CmdUsage`a resetovat využití celkový příkaz `m_nTotalUsage`, čítač na hodnotu 0.  
  
##  <a name="serialize"></a>CMFCCmdUsageCount::Serialize  
 Čte tento objekt z archivu nebo zapíše ho do archivu.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`ar`|A `CArchive` objektu k serializaci z nebo na.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda serializuje strukturu mapy příkaz počty `m_CmdUsage`a celkový počet příkaz využití `m_nTotalUsage`, čítač z nebo na zadané archivu.  
  
 Serializace příklady najdete v tématu [serializace: serializace objektu](../../mfc/serialization-serializing-an-object.md).  
  
##  <a name="setoptions"></a>CMFCCmdUsageCount::SetOptions  
 Nastaví hodnoty sdílené `CMFCCmdUsageCount` třídy datových členů.  
  
```  
static BOOL __stdcall SetOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`nStartCount`|Nové počáteční počet všechny sledované příkazy.|  
|[v]`nMinUsagePercentage`|Nové procento minimální využití.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda bude úspěšná, `FALSE` Pokud `nMinUsagePercentage` parametr je větší než nebo roven 100.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví sdílený `CMFCCmdUsageCount` třídy datových členů `m_nStartCount` a `m_nMinUsagePercentage` k `nStartCount` a `nMinUsagePercentage`, v uvedeném pořadí. `m_nStartCount`je používán [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) metoda k určení, zda tento objekt se budou shromažďovat data sledování minimální velikost. `m_nMinUsagePercentage`je používán [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) metoda k určení, zda daný příkaz se často používá.  
  
 V sestavení pro ladění tato metoda generuje chybu assertion, pokud `nMinUsagePercentage` parametr je větší než nebo roven 100.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
