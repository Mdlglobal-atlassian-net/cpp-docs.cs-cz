---
title: Ccmdui – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a31b522a2d45e4f6c0f09b8d92238d5aedcfbfd
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338318"
---
# <a name="ccmdui-class"></a>Ccmdui – třída
Se používá pouze v rámci `ON_UPDATE_COMMAND_UI` obslužné rutiny v `CCmdTarget`-odvozené třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCmdUI  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CCmdUI::ContinueRouting](#continuerouting)|Určuje mechanismus směrování příkazů pokračujte směrování aktuální zprávu v řetězu obslužné rutiny.|  
|[CCmdUI::Enable](#enable)|Povolí nebo zakáže uživatelské rozhraní položky pro tento příkaz.|  
|[CCmdUI::SetCheck](#setcheck)|Nastaví stav zaškrtnutí položky uživatelského rozhraní pro tento příkaz.|  
|[CCmdUI::SetRadio](#setradio)|Podobně jako `SetCheck` členská funkce, ale funguje v skupiny přepínačů.|  
|[CCmdUI::SetText](#settext)|Nastaví text pro položku uživatelského rozhraní pro tento příkaz.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CCmdUI::m_nID](#m_nid)|ID objektu uživatelské rozhraní.|  
|[CCmdUI::m_nIndex](#m_nindex)|Index objektu uživatelského rozhraní.|  
|[CCmdUI::m_pMenu](#m_pmenu)|Odkazuje na nabídce reprezentována `CCmdUI` objektu.|  
|[CCmdUI::m_pOther](#m_pother)|Odkazuje na objekt okna, které odesláno oznámení.|  
|[CCmdUI::m_pSubMenu](#m_psubmenu)|Odkazuje na omezením dílčí nabídky reprezentována `CCmdUI` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CCmdUI` nemá základní třídu.  
  
 Pokud uživatel aplikaci stáhne nabídky, každou nabídku položky je potřeba vědět, jestli by se měla zobrazit jako povolené nebo zakázané. Cíl příkazu nabídky poskytuje tyto informace pomocí implementace obslužné rutiny ON_UPDATE_COMMAND_UI. Okno Vlastnosti pro každý příkaz objektů uživatelského rozhraní v aplikaci, lze použijte k vytvoření mapy zpráv položky a funkce prototyp pro každou obslužnou rutinu.  
  
 Když v nabídce načítána, Každá obslužná rutina zavolá rozhraní vyhledá a volá Každá obslužná rutina ON_UPDATE_COMMAND_UI, `CCmdUI` členské funkce, jako například `Enable` a `Check`, a následně odpovídajícím způsobem zobrazí rozhraní každou položku nabídky.  
  
 Položka nabídky se dá nahradit výrazem tlačítko ovládacích panelů nebo jiný objekt uživatelského rozhraní příkaz beze změny kódu v rámci `ON_UPDATE_COMMAND_UI` obslužné rutiny.  
  
 Následující tabulka shrnuje vliv `CCmdUI`na různé položky příkazu uživatelského rozhraní mají členské funkce.  
  
|Položka uživatelského rozhraní|Povolit|Setcheck –|Setradio –|SetText –|  
|--------------------------|------------|--------------|--------------|-------------|  
|Položka nabídky|Povolí nebo zakáže|Ověří nebo zruší tohoto systému zaškrtnutí|Kontroly pomocí tečku|Nastaví položku text|  
|Tlačítko panelu nástrojů|Povolí nebo zakáže|Vybere, zruší výběr nakresleného, nebo neurčitý|Stejné jako `SetCheck`|(Není k dispozici)|  
|Panelu stavového řádku|Převede text, viditelné nebo neviditelné|Nastaví rozbalení nebo normální ohraničení|Stejné jako `SetCheck`|Nastaví podokno textu|  
|Normální tlačítko `CDialogBar`|Povolí nebo zakáže|Ověří nebo zruší tohoto systému zaškrtnutí zaškrtávacího políčka|Stejné jako `SetCheck`|Nastaví tlačítko text|  
|Normální ovládací prvek v `CDialogBar`|Povolí nebo zakáže|(Není k dispozici)|(Není k dispozici)|Nastaví text z okna|  
  
 Další informace o použití této třídy najdete v tématu [aktualizace objektů uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CCmdUI`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="continuerouting"></a>  CCmdUI::ContinueRouting  
 Voláním této členské funkce říct směrování příkazů mechanismus pokračujte směrování aktuální zprávu v řetězu obslužné rutiny.  
  
```  
void ContinueRouting();
```  
  
### <a name="remarks"></a>Poznámky  
 To je funkce členů s pokročilým členstvím, které byste měli použít ve spojení s ON_COMMAND_EX obslužná rutina, která vrací hodnotu FALSE. Další informace najdete v tématu [Technická poznámka 6](../../mfc/tn006-message-maps.md).  
  
##  <a name="enable"></a>  CCmdUI::Enable  
 Zavolejte tuto členskou funkci chcete povolit nebo zakázat položku uživatelského rozhraní pro tento příkaz.  
  
```  
virtual void Enable(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *Pozvánka*  
 Hodnota TRUE, FALSE povolíte položku, pro jeho zakázání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]  
  
##  <a name="m_nid"></a>  CCmdUI::m_nID  
 ID položky nabídky, tlačítka panelu nástrojů nebo jiných uživatelského rozhraní objekt reprezentovaný rozhraním `CCmdUI` objektu.  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_nindex"></a>  CCmdUI::m_nIndex  
 Index položky nabídky, tlačítka panelu nástrojů nebo jiný objekt uživatelského rozhraní reprezentována `CCmdUI` objektu.  
  
```  
UINT m_nIndex;  
```  
  
##  <a name="m_pmenu"></a>  CCmdUI::m_pMenu  
 Ukazatel (z `CMenu` typ) do nabídky reprezentována `CCmdUI` objektu.  
  
```  
CMenu* m_pMenu;  
```  
  
### <a name="remarks"></a>Poznámky  
 Hodnota NULL, pokud položka není nabídky.  
  
##  <a name="m_psubmenu"></a>  CCmdUI::m_pSubMenu  
 Ukazatel (z `CMenu` typ) k omezením dílčí nabídky reprezentována `CCmdUI` objektu.  
  
```  
CMenu* m_pSubMenu;  
```  
  
### <a name="remarks"></a>Poznámky  
 Hodnota NULL, pokud položka není nabídky. Pokud dílčí nabídka je automaticky otevírané okno, *m_nID* obsahuje ID první položky v rozbalovací nabídce. Další informace najdete v tématu [Technická poznámka 21](../../mfc/tn021-command-and-message-routing.md).  
  
##  <a name="m_pother"></a>  CCmdUI::m_pOther  
 Ukazatel (typu `CWnd`) na objekt okna, jako je například nástrojů nebo stavového řádku, který odesílat oznámení.  
  
```  
CWnd* m_pOther;  
```  
  
### <a name="remarks"></a>Poznámky  
 Hodnota NULL, pokud je položka nabídky nebo non - `CWnd` objektu.  
  
##  <a name="setcheck"></a>  CCmdUI::SetCheck  
 Voláním této členské funkce, chcete-li nastavit položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.  
  
```  
virtual void SetCheck(int nCheck = 1);
```  
  
### <a name="parameters"></a>Parametry  
 *nZkontrolujte*  
 Určuje stav zkontrolujte nastavení. Pokud se zruší 0, tohoto systému zaškrtnutí; Pokud 1, zkontroluje; a když se 2, nastaví neurčitý.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce funguje pro položky nabídky a tlačítka panelu nástrojů. Neurčitého stavu platí pouze pro tlačítka panelu nástrojů.  
  
##  <a name="setradio"></a>  CCmdUI::SetRadio  
 Voláním této členské funkce, chcete-li nastavit položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.  
  
```  
virtual void SetRadio(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *Pozvánka*  
 TRUE, pokud chcete povolit položky; v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce funguje stejně jako `SetCheck`, s tím rozdílem, že pracuje na položky uživatelského rozhraní, který funguje jako součást skupiny přepínačů. Zrušením zaškrtnutí ostatní položky ve skupině není automatické, pokud samotné položky zachovat shodné chování přepínač group.  
  
##  <a name="settext"></a>  CCmdUI::SetText  
 Voláním této členské funkce, chcete-li nastavit text položky uživatelského rozhraní pro tento příkaz.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszText*  
 Ukazatel na textový řetězec.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC MDI](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
