---
title: Cusertool – třída
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
ms.openlocfilehash: 5bb0ae073b722c97e8e30158f8f7832fd88b2fbc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779037"
---
# <a name="cusertool-class"></a>Cusertool – třída

Uživatelský nástroj je položka nabídky, která spustí externí aplikaci. **Nástroje** karty **vlastní** dialogové okno ( [cmfctoolbarscustomizedialog – třída](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) umožňuje uživateli přidat uživatelské nástroje a zadejte název, příkaz, argumenty, a Počáteční adresář pro každý nástroj uživatele.

## <a name="syntax"></a>Syntaxe

```
class CUserTool : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::DrawToolIcon](#drawtoolicon)|Kreslení v obdélníku zadaného ikonu uživatele nástroje.|
|[CUserTool::GetCommand](#getcommand)|Vrátí řetězec, který obsahuje text příkazu přidružený uživatelský nástroj.|
|[CUserTool::GetCommandId](#getcommandid)|Vrátí Identifikátor příkazu položky nabídky uživatelský nástroj.|
|[CUserTool::Invoke](#invoke)|Provede příkaz přidružený uživatelský nástroj.|
|[CUserTool::Serialize](#serialize)|Čtení nebo zápis tento objekt z nebo do archivu. (Přepíše [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CUserTool::SetCommand](#setcommand)|Nastaví příkaz přidružený uživatelský nástroj.|
|[CUserTool::SetToolIcon](#settoolicon)|Načte ikonu pro nástroj pro uživatele z aplikace spojené s nástrojem.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Načte výchozí ikonu pro uživatelský nástroj.|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|Argumenty příkazového řádku pro nástroj pro uživatele.|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Počáteční adresář pro nástroj pro uživatele.|
|[CUserTool::m_strLabel](#m_strlabel)|Název nástroje, který se zobrazí v položce nabídky Nástroje.|

## <a name="remarks"></a>Poznámky

Další informace o tom, jak povolit uživatelské nástroje ve své aplikaci najdete v tématu [cusertoolsmanager – třída](../../mfc/reference/cusertoolsmanager-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit nástroj z `CUserToolsManager` objektu, nastaven `m_strLabel` členské proměnné a sadu aplikací, na kterém běží nástroj uživatele. Tento fragment kódu je součástí [Visual Studio demonstrační ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxusertool.h

##  <a name="copyicontoclipboard"></a>  CUserTool::CopyIconToClipboard

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="drawtoolicon"></a>  CUserTool::DrawToolIcon

Kreslení ikonu uživatele nástroj v centru zadané obdélník.

```
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*rectImage*<br/>
[in] Určuje souřadnice oblasti zobrazit ikonu.

##  <a name="getcommand"></a>  CUserTool::GetCommand

Vrátí řetězec, který obsahuje text příkazu přidružený uživatelský nástroj.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CString` objekt, který obsahuje text příkazu přidružený uživatelský nástroj.

##  <a name="getcommandid"></a>  CUserTool::GetCommandId

Vrátí Identifikátor příkazu uživatelský nástroj.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>Návratová hodnota

ID příkazu tento nástroj uživatele.

##  <a name="invoke"></a>  CUserTool::Invoke

Provede příkaz přidružený uživatelský nástroj.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se příkaz provedl úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Volání [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) ke spuštění příkazu přidružený uživatelský nástroj. Pokud příkaz je prázdný nebo pokud selže funkce [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) selže.

##  <a name="loaddefaulticon"></a>  CUserTool::LoadDefaultIcon

Načte výchozí ikonu pro uživatelský nástroj.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač načíst ikonu (HICON), nebo hodnota NULL, pokud nelze načíst výchozí ikona.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když není schopen načíst ikonu pro uživatelsky definovaného nástroje ze spustitelného souboru nástroje.

Přepsáním této metody můžete zadat vlastní výchozí nástroj ikonu.

##  <a name="m_strarguments"></a>  CUserTool::m_strArguments

Argumenty příkazového řádku pro nástroj pro uživatele.

```
CString m_strArguments;
```

### <a name="remarks"></a>Poznámky

Tento řetězec je předán do nástroje voláte [CUserTool::Invoke](#invoke) nebo když uživatel klepne na příkaz spojený s tímto nástrojem.

##  <a name="m_strinitialdirectory"></a>  CUserTool::m_strInitialDirectory

Určuje počáteční adresář pro nástroj pro uživatele.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Poznámky

Tato proměnná Určuje počáteční adresář, který nástroj spouští v při volání [CUserTool::Invoke](#invoke) nebo když uživatel klepne na příkaz spojený s tímto nástrojem.

##  <a name="m_strlabel"></a>  CUserTool::m_strLabel

Popisek, který se zobrazí v položce nabídky Nástroje.

```
CString m_strLabel;
```

##  <a name="serialize"></a>  CUserTool::Serialize

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

[in] *ar*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setcommand"></a>  CUserTool::SetCommand

Nastaví aplikaci, na kterém běží nástroj uživatele.

```
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>Parametry

*lpszCmd*<br/>
[in] Určuje novou aplikaci, který se má přidružit uživatelský nástroj.

### <a name="remarks"></a>Poznámky

Voláním této metody lze nastavit novou aplikaci, na kterém běží nástroj uživatele. Metoda odstraní staré ikonu a načte nová ikona z dané aplikace. Pokud ho nejde načíst ikonu z aplikace, načte výchozí ikonu pro uživatelský nástroj voláním [CUserTool::LoadDefaultIcon](#loaddefaulticon).

##  <a name="settoolicon"></a>  CUserTool::SetToolIcon

Načte ikonu pro nástroj pro uživatele z aplikace, která používá nástroj.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač načíst ikonu.

### <a name="remarks"></a>Poznámky

Voláním této metody lze načíst ikonu zobrazený na položku nabídky. Tato metoda vyhledává ikona ve spustitelném souboru, který používá nástroj. Pokud nemá žádné výchozí ikona, na ikonu poskytované [CUserTool::LoadDefaultIcon](#loaddefaulticon) místo ní se použije.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)<br/>
[CUserToolsManager – třída](../../mfc/reference/cusertoolsmanager-class.md)
