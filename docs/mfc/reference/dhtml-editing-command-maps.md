---
title: Úpravy mapy příkazů DHTML | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d040f3cb4c9bf8e1f3afc0e8213cd4513fc8571
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123367"
---
# <a name="dhtml-editing-command-maps"></a>Mapy příkazů DHTML pro úpravy
Následující makra můžete použít k mapování DHTML pro úpravy příkazy v [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-odvozených třídách. Příklad jejich použití naleznete v části [HTMLEdit ukázka](../../visual-cpp-samples.md).  
  
### <a name="dhtml-editing-command-map-macros"></a>Makra mapy úpravy příkazů DHTML  
  
|||  
|-|-|  
|[DECLARE_DHTMLEDITING_CMDMAP –](#declare_dhtmlediting_cmdmap)|Deklaruje DHTML pro úpravy příkaz mapu v třídě.|  
|[BEGIN_DHTMLEDITING_CMDMAP –](#begin_dhtmlediting_cmdmap)|Spustí definici DHTML pro úpravy příkaz mapu v rámci třídy.|  
|[END_DHTMLEDITING_CMDMAP –](#end_dhtmlediting_cmdmap)|Označuje konec DHTML pro úpravy mapování příkazu.|  
|[DHTMLEDITING_CMD_ENTRY –](#dhtmlediting_cmd_entry)|Mapuje ID příkazu pro příkaz pro úpravy HTML.|  
|[DHTMLEDITING_CMD_ENTRY_FUNC –](#dhtmlediting_cmd_entry_func)|Mapuje ID příkazu úpravě příkaz HTML a obslužné rutiny zpráv.|  
|[DHTMLEDITING_CMD_ENTRY_TYPE –](#dhtmlediting_cmd_entry_type)|ID příkazu mapuje na element uživatelského rozhraní a úpravy příkaz HTML.|  
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE –](#dhtmlediting_cmd_entry_func_type)|Mapuje ID příkazu pro příkaz, obslužné rutiny zpráv a element uživatelského rozhraní pro úpravy HTML.|  
  
##  <a name="declare_dhtmlediting_cmdmap"></a>  DECLARE_DHTMLEDITING_CMDMAP –  
 Deklaruje DHTML pro úpravy příkaz mapu v třídě.  
  
```  
DECLARE_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 Název třídy.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se má použít v definici [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-odvozených třídách.  
  
 Použití [begin_dhtmlediting_cmdmap –](#begin_dhtmlediting_cmdmap) implementovat mapy.  
  
### <a name="example"></a>Příklad  
 V tématu [HTMLEdit ukázka](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxhtml.h  
  
##  <a name="begin_dhtmlediting_cmdmap"></a>  BEGIN_DHTMLEDITING_CMDMAP –  
 Spustí definici DHTML pro úpravy příkaz mapu v rámci třídy.  
  
```  
BEGIN_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 Název třídy obsahující DHTML pro úpravy příkaz mapy. Tato třída by měl být odvozen přímo nebo nepřímo z [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) a zahrnout [declare_dhtmlediting_cmdmap –](#declare_dhtmlediting_cmdmap) makro v rámci dané definice třídy.  
  
### <a name="remarks"></a>Poznámky  
 Přidáte mapu DHTML pro úpravy příkaz na třídu pro mapování příkazů uživatelského rozhraní na příkazy pro úpravy HTML.  
  
 Umístěte begin_dhtmlediting_cmdmap – makro v souboru implementace (sada) třídy následuje [dhtmlediting_cmd_entry –](#dhtmlediting_cmd_entry) makra pro příkazy třída je mapovat (například z id_edit_cut – k IDM_CUT). Použití [end_dhtmlediting_cmdmap –](#end_dhtmlediting_cmdmap) makro konec mapa událostí.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxhtml.h  
  
##  <a name="end_dhtmlediting_cmdmap"></a>  END_DHTMLEDITING_CMDMAP –  
 Označuje konec DHTML pro úpravy mapování příkazu.  
  
```  
END_DHTMLEDITING_CMDMAP()   
```  
  
### <a name="remarks"></a>Poznámky  
 Použití ve spojení s [begin_dhtmlediting_cmdmap –](#begin_dhtmlediting_cmdmap).  
  
### <a name="example"></a>Příklad  
 V tématu [HTMLEdit ukázka](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry"></a>  DHTMLEDITING_CMD_ENTRY –  
 Mapuje ID příkazu pro příkaz pro úpravy HTML.  
  
```  
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)   
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 ID příkazu (například id_edit_copy –).  
  
 *dhtmlcmdID*  
 HTML úpravy příkaz, ke kterému *cmdID* mapy (například IDM_COPY).  
  
### <a name="example"></a>Příklad  
 V tématu [HTMLEdit ukázka](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func"></a>  DHTMLEDITING_CMD_ENTRY_FUNC –  
 Mapuje ID příkazu úpravě příkaz HTML a obslužné rutiny zpráv.  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 ID příkazu (například id_edit_copy –).  
  
 *dhtmlcmdID*  
 HTML úpravy příkaz, ke kterému *cmdID* mapy (například IDM_COPY).  
  
 *member_func_name*  
 Název funkce popisovač zpráv, na kterou je namapovaná příkaz.  
  
### <a name="example"></a>Příklad  
 V tématu [HTMLEdit ukázka](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_type"></a>  DHTMLEDITING_CMD_ENTRY_TYPE –  
 ID příkazu mapuje na element uživatelského rozhraní a úpravy příkaz HTML.  
  
```  
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)  
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 ID příkazu (například id_edit_copy –).  
  
 *dhtmlcmdID*  
 HTML úpravy příkaz, ke kterému *cmdID* mapy (například IDM_COPY).  
  
 *elemType*  
 Typ elementu uživatelské rozhraní; jeden z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX nebo AFX_UI_ELEMTYPE_RADIO.  
  
### <a name="example"></a>Příklad  
 V tématu [HTMLEdit ukázka](../../visual-cpp-samples.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func_type"></a>  DHTMLEDITING_CMD_ENTRY_FUNC_TYPE –  
 Mapuje ID příkazu pro příkaz, obslužné rutiny zpráv a element uživatelského rozhraní pro úpravy HTML.  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)   
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 ID příkazu (například id_edit_copy –).  
  
 *dhtmlcmdID*  
 HTML úpravy příkaz, ke kterému *cmdID* mapy (například IDM_COPY).  
  
 *member_func_name*  
 Název funkce popisovač zpráv, na kterou je namapovaná příkaz.  
  
 *elemType*  
 Typ elementu uživatelské rozhraní; jeden z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX nebo AFX_UI_ELEMTYPE_RADIO.  
  
### <a name="example"></a>Příklad  
 V tématu [HTMLEdit ukázka](../../visual-cpp-samples.md).  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxhtml.h  
    
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
