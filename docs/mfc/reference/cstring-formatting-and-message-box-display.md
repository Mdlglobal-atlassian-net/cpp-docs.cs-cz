---
title: Formátování dat CString a zobrazení oken zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: fa1fe8826543834872de5257a0f5d56b2ad9fc1c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752682"
---
# <a name="cstring-formatting-and-message-box-display"></a>Formátování dat CString a zobrazení oken zpráv

Řada funkcí jsou k dispozici pro `CString` formátování a analýzu objektů. Tyto funkce můžete použít vždy, `CString` když budete muset manipulovat s objekty, ale jsou zvláště užitečné pro formátování řetězců, které se zobrazí v textu okna se zprávou.

Tato skupina funkcí také obsahuje globální rutinu pro zobrazení okna se zprávou.

### <a name="cstring-functions"></a>CString funkce

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|Extrahuje podřetězce oddělené jedním znakem z daného zdrojového řetězce.|
|[AfxFormatString1](#afxformatstring1)|Nahradí daný řetězec formátovanými znaky %1 v řetězci obsaženém v tabulce řetězců.|
|[AfxFormatString2](#afxformatstring2)|Nahradí dva řetězce formátovacích znaků %1 a %2 v řetězci obsaženém v tabulce řetězců.|
|[AfxMessageBox](#afxmessagebox)|Zobrazí okno se zprávou.|

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxextractsubstring"></a><a name="afxextractsubstring"></a>AfxExtractSubString

Tuto globální funkci lze použít k extrahování podřetězce z daného zdrojového řetězce.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na [CString](../../atl-mfc-shared/using-cstring.md) objekt, který obdrží jednotlivé podřetězce.

*lpszFullString*<br/>
Řetězec obsahující úplný text řetězce, ze který má být extrahován.

*iSubString*<br/>
Nulový index podřetězce extrahovat z *lpszFullString*.

*chSep*<br/>
Znak oddělovače používaný k vymezení podřetězců.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud funkce úspěšně extrahuje podřetězec na zadaný index; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná pro extrahování více podřetězců ze zdrojového řetězce, když známý jeden znak odděluje každý podřetězec. Tato funkce hledá od začátku *lpszFullString* parametr pokaždé, když je volána.

Tato funkce vrátí hodnotu FALSE, pokud je parametr *lpszFullString* nastaven na hodnotu NULL nebo pokud funkce dosáhne konce *lpszFullString* bez nalezení výskytů *iSubString*+1 zadaného oddělovacího znaku. Parametr *rString* nebude změněn z původní hodnoty, pokud byl *lpszFullString* nastaven na hodnotu NULL. v opačném případě je parametr *rString* nastaven na prázdný řetězec, pokud podřetězec nelze extrahovat pro zadaný index.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxformatstring1"></a><a name="afxformatstring1"></a>AfxFormatString1

Nahradí řetězec, na který je odkaz *ován lpsz1,* pro všechny výskyty znaků %1 v prostředku řetězce šablony identifikovaném *nIDS*.

```cpp
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na `CString` objekt, který bude obsahovat výsledný řetězec po provedení nahrazení.

*Nids*<br/>
ID prostředku řetězce šablony, na kterém bude provedena náhrada.

*lpsz1*<br/>
Řetězec, který nahradí znaky formátu %1 v řetězci šablony.

### <a name="remarks"></a>Poznámky

Nově vytvořený řetězec je uložen v *rString*. Pokud je například řetězec v tabulce řetězců "Soubor %1 nebyl nalezen" a *lpsz1* se rovná "C:\MYFILE. TXT", pak *rString* bude obsahovat řetězec "Soubor C:\MYFILE. TXT nebyl nalezen". Tato funkce je užitečná pro formátování řetězců odeslaných do oken se zprávami a dalších oken.

Pokud se znaky formátu %1 zobrazí v řetězci více než jednou, bude provedeno více nahrazení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxformatstring2"></a><a name="afxformatstring2"></a>AfxFormatString2

Nahradí řetězec, na který je odkaz *ován lpsz1,* pro všechny výskyty znaků %1 a řetězec odkazovaný *lpsz2* pro všechny výskyty znaků %2 v prostředku řetězce šablony *identifikovaném nIDS*.

```cpp
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na `CString` který bude obsahovat výsledný řetězec po provedení nahrazení.

*Nids*<br/>
ID tabulky řetězců řetězce šablony, na kterém bude provedena náhrada.

*lpsz1*<br/>
Řetězec, který nahradí znaky formátu %1 v řetězci šablony.

*lpsz2*<br/>
Řetězec, který nahradí znaky formátu %2 v řetězci šablony.

### <a name="remarks"></a>Poznámky

Nově vytvořený řetězec je uložen v *rString*. Pokud je například řetězec v tabulce řetězců "Soubor %1 nebyl nalezen v adresáři %2", *bodlpsz1* odkazuje na "MYFILE.For example, if the string in the string table is "File %1 not found in directory %2", lpsz1 points to "MYFILE. TXT", a *lpsz2* odkazuje na "C:\MYDIR", pak *rString* bude obsahovat řetězec "File MYFILE. TXT nebyl nalezen v adresáři C:\MYDIR"

Pokud se znaky formátu %1 nebo %2 zobrazí v řetězci více než jednou, bude provedeno více nahrazení. Nemusí být v číselném pořadí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxwin.h

## <a name="afxmessagebox"></a><a name="afxmessagebox"></a>AfxMessageBox

Zobrazí na obrazovce okno se zprávou.

```
int AfxMessageBox(
    LPCTSTR lpszText,
    UINT nType = MB_OK,
    UINT nIDHelp = 0);

int AFXAPI AfxMessageBox(
    UINT nIDPrompt,
    UINT nType = MB_OK,
    UINT nIDHelp = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Odkazuje na `CString` objekt nebo řetězec s nulovým ukončováním obsahující zprávu, která má být zobrazena v poli se zprávou.

*nTyp*<br/>
Styl okna se zprávou. Použijte některý ze [stylů okna se zprávou](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) do pole.

*nIDNápověda*<br/>
ID kontextu nápovědy pro zprávu; 0 označuje, že bude použit výchozí kontext nápovědy aplikace.

*nIDPrompt*<br/>
Jedinečné ID používané k odkazování na řetězec v tabulce řetězců.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud není dostatek paměti pro zobrazení okna se zprávou; v opačném případě je vrácena jedna z následujících hodnot:

- IDABORT Bylo vybráno tlačítko Přerušit.

- IDCANCEL Bylo vybráno tlačítko Storno.

- IDIGNORE Bylo vybráno tlačítko Ignorovat.

- IDNO Bylo vybráno tlačítko Ne.

- IDOK Bylo vybráno tlačítko OK.

- IDRETRY Bylo vybráno tlačítko Opakovat.

- IDYES Bylo vybráno tlačítko Ano.

Pokud je v poli se zprávou tlačítko Storno, bude vrácena hodnota IDCANCEL, pokud je stisknuto klávesa ESC nebo je vybráno tlačítko Storno. Pokud okno se zprávou nemá tlačítko Storno, stisknutí klávesy ESC nemá žádný vliv.

Funkce [AfxFormatString1](#afxformatstring1) a [AfxFormatString2](#afxformatstring2) mohou být užitečné při formátování textu, který se zobrazí v poli se zprávou.

### <a name="remarks"></a>Poznámky

První forma této přetížené funkce zobrazí textový řetězec, na který poukazuje *lpszText,* v poli se zprávou a používá *nIDHelp* k popisu kontextu nápovědy. Kontext nápovědy se používá ke přechodu na přidružené téma nápovědy, když uživatel stiskne klávesu nápovědy (obvykle F1).

Druhá forma funkce používá prostředek řetězce s ID *nIDPrompt* k zobrazení zprávy v okně zprávy. Přidružená stránka nápovědy je nalezena prostřednictvím hodnoty *nIDHelp*. Pokud je použita výchozí hodnota *nIDHelp* (-1), pro kontext nápovědy se použije ID řetězce *nIDPrompt*. Další informace o definování kontextů nápovědy naleznete [v technické poznámce 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT – třída](../../atl-mfc-shared/reference/cstringt-class.md)
