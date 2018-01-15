---
title: "Třída COleCmdUI | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
dev_langs: C++
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c9d26ce9e674168f3d3d1c67dc48bb16b1a87169
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="colecmdui-class"></a>COleCmdUI – třída
Implementuje metodu pro MFC aktualizovat stav objektů uživatelského rozhraní související s `IOleCommandTarget`-řízené funkce vaší aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleCmdUI : public CCmdUI  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleCmdUI::COleCmdUI](#colecmdui)|Vytvoří `COleCmdUI` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleCmdUI::Enable](#enable)|Nastaví nebo vymaže příznak pro povolení příkaz.|  
|[COleCmdUI::SetCheck](#setcheck)|Nastaví stav přepnutí zapnout nebo vypnout příkaz.|  
|[COleCmdUI::SetText](#settext)|Vrátí textový řetězec názvu nebo stavu pro příkaz.|  
  
## <a name="remarks"></a>Poznámky  
 V aplikaci, která není povolena pro DocObjects, když uživatel prohlíží nabídky v aplikaci MFC procesy **UPDATE_COMMAND_UI** generovaná. Každého oznámení je uveden [CCmdUI](../../mfc/reference/ccmdui-class.md) objekt, který smí uživatel manipulovat, aby odpovídal stavu konkrétní příkaz. Ale pokud vaše aplikace je povoleno pro DocObjects, MFC zpracovává **UPDATE_OLE_COMMAND_UI** oznámení a přiřadí `COleCmdUI` objekty.  
  
 `COleCmdUI`Umožňuje DocObject přijímají příkazy, které pocházejí z jeho kontejneru uživatelské rozhraní (například funkci FileNew, otevřete, tisku a tak dále), a umožňuje kontejner přijímat příkazy, které mají původ DocObject uživatelské rozhraní. I když `IDispatch` může použít k odesílání stejné příkazy `IOleCommandTarget` nabízí jednodušší způsob pro dotazování a provést, protože je závislé na standardní sadu příkazů, obvykle bez argumentů, a je zahrnuta žádné informace o typu. `COleCmdUI`slouží k povolení, aktualizovat a nastavit další vlastnosti příkazy DocObject uživatelského rozhraní. Když chcete k vyvolání příkazu, volání [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).  
  
 Další informace o DocObjects najdete v tématu [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) a [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md). Viz také [první kroky Internet: aktivní dokumenty](../../mfc/active-documents-on-the-internet.md) a [aktivní dokumenty](../../mfc/active-documents-on-the-internet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdocobj.h  
  
##  <a name="colecmdui"></a>COleCmdUI::COleCmdUI  
 Vytvoří `COleCmdUI` objekt přidružený k příkazu konkrétní uživatelského rozhraní.  
  
```  
COleCmdUI(
    OLECMD* rgCmds,  
    ULONG cCmds,  
    const GUID* m_pGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `rgCmds`  
 Seznam podporovaných příkazů, které jsou přidružené k zadaným identifikátorem GUID. **OLECMD** struktura přidruží příkazy příznaky příkazu.  
  
 *cCmds*  
 Počet příkazy v `rgCmds`.  
  
 `pGroup`  
 Ukazatel na identifikátor GUID, který identifikuje sadu příkazů.  
  
### <a name="remarks"></a>Poznámky  
 `COleCmdUI` Objekt poskytuje programovací rozhraní pro aktualizace objektů uživatelského rozhraní DocObject jako položky nabídky nebo ovládací prvek panelu tlačítka. Objekty uživatelského rozhraní může být povoleno, zakázána, zaškrtnutí nebo vymazat prostřednictvím `COleCmdUI` objektu.  
  
##  <a name="enable"></a>COleCmdUI::Enable  
 Volání této funkce se nastavit příznak příkaz z `COleCmdUI` do objektu **OLECOMDF_ENABLED**, která sděluje rozhraní příkaz je k dispozici a povolená, nebo zrušte příznak příkaz.  
  
```  
virtual void Enable(BOOL bOn);
```  
  
### <a name="parameters"></a>Parametry  
 `bOn`  
 Určuje, zda příkaz přidružené `COleCmdUI` objektu by měla být povolená nebo zakázaná. NonZero umožňuje příkaz; 0 zakáže příkaz.  
  
##  <a name="setcheck"></a>COleCmdUI::SetCheck  
 Volání této funkce pro nastavení stavu zapnout nebo vypnout přepínání příkazu.  
  
```  
virtual void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 `nCheck`  
 Zjištění stavu přepnutí zapnout nebo vypnout nastavit hodnotu příkazu. Hodnoty jsou:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|**1**|Příkaz nastaví na hodnotu on.|  
|**2**|Nastaví příkaz na neurčitou; Stav nelze určit, protože je atribut tohoto příkazu v jak zapnout a vypnout stavů v příslušné výběr.|  
|Jakákoli jiná hodnota|Nastaví vypnuto příkazu.|  
  
##  <a name="settext"></a>COleCmdUI::SetText  
 Volání této funkce vrátit textový řetězec názvu nebo stavu pro příkaz.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Ukazatel na text, který se použije příkaz.  
  
## <a name="see-also"></a>Viz také  
 [CCmdUI – třída](../../mfc/reference/ccmdui-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



