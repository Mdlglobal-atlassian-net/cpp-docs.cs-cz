---
title: Třída CUserTool
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
ms.openlocfilehash: 203adeac9783da8ea49a8385dad9786865c8a225
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373209"
---
# <a name="cusertool-class"></a>Třída CUserTool

Uživatelský nástroj je položka nabídky, která spouští externí aplikaci. Karta **Nástroje** dialogového okna **Přizpůsobit** [(CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) umožňuje uživateli přidávat uživatelské nástroje a zadávat název, příkaz, argumenty a počáteční adresář pro každý uživatelský nástroj.

## <a name="syntax"></a>Syntaxe

```
class CUserTool : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::DrawToolIkona](#drawtoolicon)|Nakreslí ikonu nástroje uživatele v zadaném obdélníku.|
|[CUserTool::GetCommand](#getcommand)|Vrátí řetězec, který obsahuje text příkazu přidruženého k uživatelskému nástroji.|
|[CUserTool::GetCommandId](#getcommandid)|Vrátí ID příkazu položky nabídky uživatelského nástroje.|
|[CUserTool::Vyvolat](#invoke)|Provede příkaz přidružený k uživatelskému nástroji.|
|[CUserTool::Serializovat](#serialize)|Přečte nebo zapíše tento objekt z nebo do archivu. (Přepíše [CObject::Serializovat](../../mfc/reference/cobject-class.md#serialize).)|
|[CUserTool::SetCommand](#setcommand)|Nastaví příkaz přidružený k uživatelskému nástroji.|
|[CUserTool::Ikona ikony settoolu](#settoolicon)|Načte ikonu uživatelského nástroje z aplikace přidružené k nástroji.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CUserTool::Ikona DefaultIcon](#loaddefaulticon)|Načte výchozí ikonu uživatelského nástroje.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|Argumenty příkazového řádku pro uživatelský nástroj.|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Počáteční adresář pro uživatelský nástroj.|
|[CUserTool::m_strLabel](#m_strlabel)|Název nástroje, který se zobrazí v položce nabídky nástroje.|

## <a name="remarks"></a>Poznámky

Další informace o povolení uživatelských nástrojů v aplikaci naleznete v [tématu CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit nástroj `CUserToolsManager` z objektu, nastavit `m_strLabel` proměnnou člena a nastavit aplikaci, kterou spustí uživatelský nástroj. Tento fragment kódu je součástí [ukázky ukázky aplikace Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Nástroj CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxusertool.h

## <a name="cusertoolcopyicontoclipboard"></a><a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cusertooldrawtoolicon"></a><a name="drawtoolicon"></a>CUserTool::DrawToolIkona

Nakreslí ikonu nástroje uživatele ve středu zadaného obdélníku.

```
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*rectImage*<br/>
[v] Určuje souřadnice oblasti, která má být zobrazena.

## <a name="cusertoolgetcommand"></a><a name="getcommand"></a>CUserTool::GetCommand

Vrátí řetězec, který obsahuje text příkazu přidruženého k uživatelskému nástroji.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CString` objekt, který obsahuje text příkazu přidruženého k uživatelskému nástroji.

## <a name="cusertoolgetcommandid"></a><a name="getcommandid"></a>CUserTool::GetCommandId

Vrátí ID příkazu uživatelského nástroje.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>Návratová hodnota

ID příkazu tohoto uživatelského nástroje.

## <a name="cusertoolinvoke"></a><a name="invoke"></a>CUserTool::Vyvolat

Provede příkaz přidružený k uživatelskému nástroji.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl příkaz úspěšně proveden; jinak 0.

### <a name="remarks"></a>Poznámky

Zavolá [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) provést příkaz přidružený k uživatelskému nástroji. Funkce se nezdaří, pokud je příkaz prázdný nebo pokud se nezdaří [ShellExecute.](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)

## <a name="cusertoolloaddefaulticon"></a><a name="loaddefaulticon"></a>CUserTool::Ikona DefaultIcon

Načte výchozí ikonu uživatelského nástroje.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač načtené ikony ( HICON) nebo NULL, pokud výchozí ikonu nelze načíst.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto metodu, pokud není schopna načíst ikonu uživatelem definovaného nástroje ze spustitelného souboru nástroje.

Přepište tuto metodu a zadejte vlastní ikonu výchozího nástroje.

## <a name="cusertoolm_strarguments"></a><a name="m_strarguments"></a>CUserTool::m_strArguments

Argumenty příkazového řádku pro uživatelský nástroj.

```
CString m_strArguments;
```

### <a name="remarks"></a>Poznámky

Tento řetězec je předán nástroji při volání [CUserTool::Invoke](#invoke) nebo když uživatel klepne na příkaz přidružený k tomuto nástroji.

## <a name="cusertoolm_strinitialdirectory"></a><a name="m_strinitialdirectory"></a>CUserTool::m_strInitialDirectory

Určuje počáteční adresář uživatelského nástroje.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Poznámky

Tato proměnná určuje počáteční adresář, ve kterých se nástroj spustí při volání [CUserTool::Invoke](#invoke) nebo když uživatel klepne na příkaz přidružený k tomuto nástroji.

## <a name="cusertoolm_strlabel"></a><a name="m_strlabel"></a>CUserTool::m_strLabel

Popisek, který se zobrazí v položce nabídky nástroje.

```
CString m_strLabel;
```

## <a name="cusertoolserialize"></a><a name="serialize"></a>CUserTool::Serializovat

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

[v] *ar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cusertoolsetcommand"></a><a name="setcommand"></a>CUserTool::SetCommand

Nastaví aplikaci, kterou spustí uživatelský nástroj.

```
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>Parametry

*lpszCmd*<br/>
[v] Určuje novou aplikaci, která má být přidružena k uživatelskému nástroji.

### <a name="remarks"></a>Poznámky

Volání této metody nastavit novou aplikaci, která spustí uživatelský nástroj. Metoda zničí starou ikonu a načte novou ikonu z dané aplikace. Pokud nemůže načíst ikonu z aplikace, načte výchozí ikonu pro uživatelský nástroj voláním [CUserTool::LoadDefaultIcon](#loaddefaulticon).

## <a name="cusertoolsettoolicon"></a><a name="settoolicon"></a>CUserTool::Ikona ikony settoolu

Načte ikonu uživatelského nástroje z aplikace, kterou nástroj používá.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>Návratová hodnota

Úchyt k načtené ikoně.

### <a name="remarks"></a>Poznámky

Volání této metody načíst ikonu, která má být zobrazena v položce nabídky. Tato metoda vyhledá ikonu ve spustitelném souboru, který nástroj používá. Pokud nemá výchozí ikonu, místo toho se použije ikona poskytnutá [nástrojem CUserTool::LoadDefaultIcon.](#loaddefaulticon)

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[CUserToolsManager – třída](../../mfc/reference/cusertoolsmanager-class.md)
