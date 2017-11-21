---
title: "Třída CUserTool | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
dev_langs: C++
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dbccf88ee493b0d9343660bbbcd447049ca8c19c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cusertool-class"></a>CUserTool – třída
Nástroj pro uživatele je položku nabídky, který spouští externí aplikací. **Nástroje** kartě **přizpůsobit** dialogové okno ( [CMFCToolBarsCustomizeDialog třída](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) umožňuje uživateli přidat uživatele nástroje a zadejte název, argumenty, a Počáteční adresář pro každého uživatele nástroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CUserTool : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||  
|[CUserTool::DrawToolIcon](#drawtoolicon)|V zadané obdélníku nevykresluje ikonu nástroj uživatele.|  
|[CUserTool::GetCommand](#getcommand)|Vrátí řetězec, který obsahuje text příkazu přidružené nástroj pro uživatele.|  
|[CUserTool::GetCommandId](#getcommandid)|Vrátí ID příkazu, který položky nabídky Nástroje pro uživatele.|  
|[CUserTool::Invoke](#invoke)|Spustí příkaz přidružený nástroj pro uživatele.|  
|[CUserTool::Serialize](#serialize)|Čtení nebo zápisu tento objekt z nebo do archivu. (Přepisuje [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CUserTool::SetCommand](#setcommand)|Nastaví příkaz přidružený nástroj pro uživatele.|  
|[CUserTool::SetToolIcon](#settoolicon)|Načte ikonu pro nástroj pro uživatele z aplikace spojené s nástrojem.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Načte výchozí ikonu pro nástroj pro uživatele.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CUserTool::m_strArguments](#m_strarguments)|Argumenty příkazového řádku pro nástroj pro uživatele.|  
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Počáteční adresář pro nástroj pro uživatele.|  
|[CUserTool::m_strLabel](#m_strlabel)|Název nástroj, který se zobrazí v položce nabídky Nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o tom, jak povolit nástroje pro uživatele ve vaší aplikaci najdete v tématu [CUserToolsManager třída](../../mfc/reference/cusertoolsmanager-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit nástroj z `CUserToolsManager` objektu, nastavte `m_strLabel` členské proměnné a nastavte aplikaci, která spouští nástroj pro uživatele. Tento fragment kódu je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserTool](../../mfc/reference/cusertool-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxusertool.h  
  
##  <a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CopyIconToClipboard();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="drawtoolicon"></a>CUserTool::DrawToolIcon  
 Nevykresluje ikonu nástroj uživatele do středu obdélníku zadaný.  
  
```  
void DrawToolIcon(
    CDC* pDC,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rectImage`  
 Určuje souřadnice oblasti zobrazíte ikonu.  
  
##  <a name="getcommand"></a>CUserTool::GetCommand  
 Vrátí řetězec, který obsahuje text příkazu přidružené nástroj pro uživatele.  
  
```  
const CString& GetCommand() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `CString` objekt, který obsahuje text příkazu přidružené nástroj pro uživatele.  
  
##  <a name="getcommandid"></a>CUserTool::GetCommandId  
 Vrátí ID příkazu, který nástroje pro uživatele.  
  
```  
UINT GetCommandId() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 ID příkazu tohoto uživatele nástroje.  
  
##  <a name="invoke"></a>CUserTool::Invoke  
 Spustí příkaz přidružený nástroj pro uživatele.  
  
```  
virtual BOOL Invoke();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl úspěšně; provedení příkazu. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) ke spuštění příkazu přidružené nástroj pro uživatele. Funkce selže, pokud příkaz je prázdný nebo pokud [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) selže.  
  
##  <a name="loaddefaulticon"></a>CUserTool::LoadDefaultIcon  
 Načte výchozí ikonu pro nástroj pro uživatele.  
  
```  
virtual HICON LoadDefaultIcon();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro ikonu načíst ( `HICON`), nebo `NULL` Pokud výchozí ikonu nelze načíst.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu, když se nepodařilo načíst ikonu pro nástroj uživatelem definované ze spustitelného souboru nástroje.  
  
 Potlačí tuto metodu za účelem zadejte vlastní výchozí ikonu nástroj.  
  
##  <a name="m_strarguments"></a>CUserTool::m_strArguments  
 Argumenty příkazového řádku pro nástroj pro uživatele.  
  
```  
CString m_strArguments;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento řetězec je předán do nástroje při volání [CUserTool::Invoke](#invoke) nebo když uživatel klikne příkaz přidružený tento nástroj.  
  
##  <a name="m_strinitialdirectory"></a>CUserTool::m_strInitialDirectory  
 Určuje počáteční adresář pro nástroj pro uživatele.  
  
```  
CString m_strInitialDirectory;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato proměnná Určuje počáteční adresář, který nástroj spouští v při volání [CUserTool::Invoke](#invoke) nebo když uživatel klikne příkaz přidružený tento nástroj.  
  
##  <a name="m_strlabel"></a>CUserTool::m_strLabel  
 Popisek, který se zobrazí v položce nabídky pro nástroj.  
  
```  
CString m_strLabel;  
```  
  
##  <a name="serialize"></a>CUserTool::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`ar`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setcommand"></a>CUserTool::SetCommand  
 Nastaví aplikaci, která spouští nástroj pro uživatele.  
  
```  
void SetCommand(LPCTSTR lpszCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszCmd`  
 Určuje novou aplikaci, která bude přidružen nástroj pro uživatele.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu a nastavit novou aplikaci, která spouští nástroj pro uživatele. Metoda zničí ikonu starý a načte nová ikona z dané aplikaci. Pokud ikonu ho nelze načíst z aplikace, načte výchozí ikonu pro nástroj uživatele voláním [CUserTool::LoadDefaultIcon](#loaddefaulticon).  
  
##  <a name="settoolicon"></a>CUserTool::SetToolIcon  
 Načte ikonu pro nástroj pro uživatele z aplikace, která používá nástroj.  
  
```  
virtual HICON SetToolIcon();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro ikonu načíst.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem načtení ikonu zobrazený na položku nabídky. Tato metoda vyhledá na ikonu v spustitelný soubor, který používá nástroj. Pokud nemá výchozí ikonu, ikonu poskytované [CUserTool::LoadDefaultIcon](#loaddefaulticon) bude místo něj použita.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)   
 [CUserToolsManager – třída](../../mfc/reference/cusertoolsmanager-class.md)
