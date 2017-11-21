---
title: "CCmdUI – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCmdUI
- AFXWIN/CCmdUI
- AFXWIN/CCmdUI::ContinueRouting
- AFXWIN/CCmdUI::Enable
- AFXWIN/CCmdUI::SetCheck
- AFXWIN/CCmdUI::SetRadio
- AFXWIN/CCmdUI::SetText
- AFXWIN/CCmdUI::m_nID
- AFXWIN/CCmdUI::m_nIndex
- AFXWIN/CCmdUI::m_pMenu
- AFXWIN/CCmdUI::m_pOther
- AFXWIN/CCmdUI::m_pSubMenu
dev_langs: C++
helpviewer_keywords:
- CCmdUI [MFC], ContinueRouting
- CCmdUI [MFC], Enable
- CCmdUI [MFC], SetCheck
- CCmdUI [MFC], SetRadio
- CCmdUI [MFC], SetText
- CCmdUI [MFC], m_nID
- CCmdUI [MFC], m_nIndex
- CCmdUI [MFC], m_pMenu
- CCmdUI [MFC], m_pOther
- CCmdUI [MFC], m_pSubMenu
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 657483c85c8b2f03d4a78e76cdc28a5dfff496e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccmdui-class"></a>CCmdUI – třída
Se používá jenom v `ON_UPDATE_COMMAND_UI` obslužné rutiny v `CCmdTarget`-odvozené třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCmdUI  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CCmdUI::ContinueRouting](#continuerouting)|Informuje mechanismus směrování příkazů pokračujte směrování aktuální zprávu v řetězu obslužné rutiny.|  
|[CCmdUI::Enable](#enable)|Povolí nebo zakáže uživatelské rozhraní položky pro tento příkaz.|  
|[CCmdUI::SetCheck](#setcheck)|Zkontrolujte stav položky uživatelského rozhraní pro tento příkaz nastaví.|  
|[CCmdUI::SetRadio](#setradio)|Podobně jako `SetCheck` – členská funkce, ale funguje na přepínač skupiny.|  
|[CCmdUI::SetText](#settext)|Nastaví text pro položku uživatelského rozhraní pro tento příkaz.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CCmdUI::m_nID](#m_nid)|ID objektu uživatelské rozhraní.|  
|[CCmdUI::m_nIndex](#m_nindex)|Index objektu uživatelského rozhraní.|  
|[CCmdUI::m_pMenu](#m_pmenu)|Odkazuje na v nabídce reprezentována `CCmdUI` objektu.|  
|[CCmdUI::m_pOther](#m_pother)|Body k objektu okna, který odesílá oznámení.|  
|[CCmdUI::m_pSubMenu](#m_psubmenu)|Bodů do uzavřeného dílčí nabídky reprezentována `CCmdUI` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CCmdUI`nemá základní třídu.  
  
 Když uživatel aplikace vrátí dolů nabídky, každý nabídky položky musí vědět, jestli by se měla zobrazit jako povolené nebo zakázané. Cíl příkazu nabídky implementací poskytuje tyto informace `ON_UPDATE_COMMAND_UI` obslužné rutiny. Okno Vlastnosti pro každý příkaz objektů uživatelského rozhraní v aplikaci lze použijte k vytvoření mapy zpráv položku a funkce prototypu pro každou obslužnou rutinu.  
  
 Když v nabídce načítána, rozhraní vyhledá a volá všechny `ON_UPDATE_COMMAND_UI` volá obslužnou rutinu, každou obslužnou rutinu `CCmdUI` členské funkce, jako **povolit** a **zkontrolujte**a potom rozhraní správně zobrazí každou položku nabídky.  
  
 Položky nabídky lze nahradit s tlačítkem na ovládací prvek panelu nebo jiného objektu příkaz uživatelského rozhraní beze změny kódu v rámci `ON_UPDATE_COMMAND_UI` obslužné rutiny.  
  
 Následující tabulka shrnuje účinek `CCmdUI`na různé položky příkaz uživatelského rozhraní mají členské funkce.  
  
|Položka uživatelského rozhraní|Povolit|Setcheck –|Setradio –|SetText –|  
|--------------------------|------------|--------------|--------------|-------------|  
|Položky nabídky|Povolí nebo zakáže|Kontroluje nebo zruší tohoto systému zaškrtnutí|Kontroly pomocí tečku|Nastaví položku textu|  
|Tlačítka panelu nástrojů|Povolí nebo zakáže|Vybere, zruší výběr nakresleného, nebo neurčitém|Stejné jako`SetCheck`|(Není k dispozici)|  
|Panelu stavového řádku|Umožňuje text viditelný nebo neviditelná|Nastaví rozbalení nebo normální ohraničení|Stejné jako`SetCheck`|Nastaví podokně text|  
|V okně normální tlačítko`CDialogBar`|Povolí nebo zakáže|Kontroluje nebo zruší tohoto systému zaškrtnutí zaškrtávacího políčka|Stejné jako`SetCheck`|Nastaví tlačítko textu|  
|Normální ovládacího prvku`CDialogBar`|Povolí nebo zakáže|(Není k dispozici)|(Není k dispozici)|Nastaví název okna|  
  
 Další informace o používání této třídy najdete v tématu [postup aktualizace objektů uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CCmdUI`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="continuerouting"></a>CCmdUI::ContinueRouting  
 Volání této funkce člen říct mechanismus směrování příkazů pokračujte směrování aktuální zprávu v řetězu obslužné rutiny.  
  
```  
void ContinueRouting();
```  
  
### <a name="remarks"></a>Poznámky  
 Jedná se rozšířené – členská funkce, která se používá ve spojení s `ON_COMMAND_EX` obslužná rutina, která vrátí **FALSE**. Další informace najdete v tématu [Technická poznámka 6](../../mfc/tn006-message-maps.md).  
  
##  <a name="enable"></a>CCmdUI::Enable  
 Volání této funkce člen k povolení nebo zakázání položku uživatelského rozhraní pro tento příkaz.  
  
```  
virtual void Enable(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bOn`  
 **Hodnota TRUE,** povolit položky **FALSE** ji zakázat.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]  
  
##  <a name="m_nid"></a>CCmdUI::m_nID  
 Identifikátor položky nabídky, tlačítka panelu nástrojů nebo jiného uživatelského rozhraní objektu reprezentována `CCmdUI` objektu.  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_nindex"></a>CCmdUI::m_nIndex  
 Index položky nabídky, tlačítka panelu nástrojů nebo jiného uživatelského rozhraní objektu reprezentována `CCmdUI` objektu.  
  
```  
UINT m_nIndex;  
```  
  
##  <a name="m_pmenu"></a>CCmdUI::m_pMenu  
 Ukazatele (z `CMenu` typu) do nabídky reprezentována `CCmdUI` objektu.  
  
```  
CMenu* m_pMenu;  
```  
  
### <a name="remarks"></a>Poznámky  
 **NULL** Pokud položka není nabídky.  
  
##  <a name="m_psubmenu"></a>CCmdUI::m_pSubMenu  
 Ukazatele (z `CMenu` typu) obsahují dílčí nabídky reprezentována `CCmdUI` objektu.  
  
```  
CMenu* m_pSubMenu;  
```  
  
### <a name="remarks"></a>Poznámky  
 **NULL** Pokud položka není nabídky. Pokud je automaticky otevírané okno, v nabídce dílčí `m_nID` obsahuje ID první položka v místní nabídce. Další informace najdete v tématu [Technická poznámka 21](../../mfc/tn021-command-and-message-routing.md).  
  
##  <a name="m_pother"></a>CCmdUI::m_pOther  
 Ukazatele (typu `CWnd`) do okna objekt, jako je například nástroj nebo stavový řádek, který odeslána oznámení.  
  
```  
CWnd* m_pOther;  
```  
  
### <a name="remarks"></a>Poznámky  
 **NULL** Pokud je položka nabídky nebo jinou hodnotu než `CWnd` objektu.  
  
##  <a name="setcheck"></a>CCmdUI::SetCheck  
 Volání této funkce člen nastavit položku uživatelského rozhraní pro tento příkaz na příslušné kontroly stavu.  
  
```  
virtual void SetCheck(int nCheck = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `nCheck`  
 Určuje stav zkontrolujte nastavení. Pokud 0, zruší tohoto systému zaškrtnutí; Pokud 1, zkontroluje; a pokud 2, nastaví neurčitou.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce funguje u položek nabídky a tlačítka panelu nástrojů. Neurčitého stavu platí pouze pro tlačítka panelu nástrojů.  
  
##  <a name="setradio"></a>CCmdUI::SetRadio  
 Volání této funkce člen nastavit položku uživatelského rozhraní pro tento příkaz na příslušné kontroly stavu.  
  
```  
virtual void SetRadio(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bOn`  
 **Hodnota TRUE,** povolit položce; v opačném případě **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen pracuje jako `SetCheck`kromě toho, že funguje na uživatelské rozhraní položky funguje jako součást skupiny přepínačů. Zrušte zaškrtnutí položky ve skupině není automatické, pokud položky sami udržovat skupina rádiových chování.  
  
##  <a name="settext"></a>CCmdUI::SetText  
 Volání této funkce člen nastavit text položky uživatelského rozhraní pro tento příkaz.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Ukazatel na textový řetězec.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MDI](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
