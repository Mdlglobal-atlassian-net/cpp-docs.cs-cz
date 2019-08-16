---
title: CUserTool – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: b73cb3d3c6e244a9aa41a91a3ee9ff1efa98d496
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502247"
---
# <a name="cusertool-class"></a>CUserTool – třída

Uživatelský nástroj je položka nabídky, která spustí externí aplikaci. Karta **nástroje** dialogového okna **přizpůsobit** ( [Třída CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) umožňuje uživateli přidat uživatelské nástroje a zadat název, příkaz, argumenty a počáteční adresář pro každý uživatelský nástroj.

## <a name="syntax"></a>Syntaxe

```
class CUserTool : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::DrawToolIcon](#drawtoolicon)|Nakreslí ikonu uživatelského nástroje v zadaném obdélníku.|
|[CUserTool:: Get– příkaz](#getcommand)|Vrátí řetězec, který obsahuje text příkazu přidružený k uživatelskému nástroji.|
|[CUserTool::GetCommandId](#getcommandid)|Vrátí ID příkazu pro položku nabídky nástroje User Tool.|
|[CUserTool::Invoke](#invoke)|Spustí příkaz přidružený k uživatelskému nástroji.|
|[CUserTool:: serializovat](#serialize)|Přečte nebo zapisuje tento objekt z nebo do archivu. (Overrides [CObject:: serializovat](../../mfc/reference/cobject-class.md#serialize).)|
|[CUserTool::SetCommand](#setcommand)|Nastaví příkaz přidružený k uživatelskému nástroji.|
|[CUserTool::SetToolIcon](#settoolicon)|Načte ikonu pro uživatelský nástroj z aplikace přidružené k tomuto nástroji.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Načte výchozí ikonu pro uživatelský nástroj.|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|Argumenty příkazového řádku pro uživatelský nástroj.|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Počáteční adresář pro uživatelský nástroj.|
|[CUserTool::m_strLabel](#m_strlabel)|Název nástroje, který se zobrazí v položce nabídky pro nástroj.|

## <a name="remarks"></a>Poznámky

Další informace o povolení uživatelských nástrojů v aplikaci naleznete v tématu [Třída CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit nástroj z `CUserToolsManager` objektu, `m_strLabel` nastavit členskou proměnnou a nastavit aplikaci, kterou uživatelský nástroj spouští. Tento fragment kódu je součástí ukázkového [vzorku sady Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxusertool. h

##  <a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard

Další podrobnosti najdete ve zdrojovém kódu ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="drawtoolicon"></a>  CUserTool::DrawToolIcon

Nakreslí ikonu uživatelského nástroje na střed zadaného obdélníku.

```
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení.

*rectImage*<br/>
pro Určuje souřadnice oblasti, pro kterou se má zobrazit ikona.

##  <a name="getcommand"></a>CUserTool:: Get– příkaz

Vrátí řetězec, který obsahuje text příkazu přidružený k uživatelskému nástroji.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CString` objekt, který obsahuje text příkazu přidružený k uživatelskému nástroji.

##  <a name="getcommandid"></a>CUserTool::GetCommandId

Vrátí ID příkazu pro uživatelský nástroj.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>Návratová hodnota

ID příkazu tohoto uživatelského nástroje.

##  <a name="invoke"></a>CUserTool:: Invoke

Spustí příkaz přidružený k uživatelskému nástroji.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl příkaz úspěšně proveden; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Volá [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) ke spuštění příkazu přidruženého k uživatelskému nástroji. Funkce se nezdařila, pokud je příkaz prázdný nebo pokud [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) dojde k chybě.

##  <a name="loaddefaulticon"></a>CUserTool::LoadDefaultIcon

Načte výchozí ikonu pro uživatelský nástroj.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro vloženou ikonu (HICON) nebo hodnotu NULL, pokud nelze načíst výchozí ikonu.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když není schopen načíst ikonu pro uživatelsky definovaný nástroj ze spustitelného souboru nástroje.

Potlačí tuto metodu, aby poskytovala vlastní výchozí ikonu nástroje.

##  <a name="m_strarguments"></a>  CUserTool::m_strArguments

Argumenty příkazového řádku pro uživatelský nástroj.

```
CString m_strArguments;
```

### <a name="remarks"></a>Poznámky

Tento řetězec je předán nástroji při volání [CUserTool:: Invoke](#invoke) nebo když uživatel klikne na příkaz přidružený k tomuto nástroji.

##  <a name="m_strinitialdirectory"></a>  CUserTool::m_strInitialDirectory

Určuje počáteční adresář pro uživatelský nástroj.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Poznámky

Tato proměnná Určuje počáteční adresář, ve kterém se nástroj spustí, když zavoláte [CUserTool:: Invoke](#invoke) nebo když uživatel klikne na příkaz přidružený k tomuto nástroji.

##  <a name="m_strlabel"></a>  CUserTool::m_strLabel

Popisek, který se zobrazí v položce nabídky nástroje.

```
CString m_strLabel;
```

##  <a name="serialize"></a>CUserTool:: serializovat

Další podrobnosti najdete ve zdrojovém kódu ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

pro *ar*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setcommand"></a>CUserTool::SetCommand

Nastaví aplikaci, kterou uživatelský nástroj spouští.

```
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>Parametry

*lpszCmd*<br/>
pro Určuje novou aplikaci, která se má přidružit k nástroji pro uživatele.

### <a name="remarks"></a>Poznámky

Voláním této metody nastavíte novou aplikaci, kterou spouští uživatelský nástroj. Metoda zničí starou ikonu a načte novou ikonu z dané aplikace. Pokud nemůže načíst ikonu z aplikace, načte výchozí ikonu pro uživatelský nástroj voláním [CUserTool:: LoadDefaultIcon](#loaddefaulticon).

##  <a name="settoolicon"></a>CUserTool::SetToolIcon

Načte ikonu pro uživatelský nástroj z aplikace, kterou nástroj používá.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač načtené ikony.

### <a name="remarks"></a>Poznámky

Voláním této metody načtete ikonu, která se zobrazí v položce nabídky. Tato metoda vyhledá ikonu ve spustitelném souboru, který nástroj používá. Pokud nemá výchozí ikonu, místo toho se použije ikona zadaná v [CUserTool:: LoadDefaultIcon](#loaddefaulticon) .

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)<br/>
[CUserToolsManager – třída](../../mfc/reference/cusertoolsmanager-class.md)
