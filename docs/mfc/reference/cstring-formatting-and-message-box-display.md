---
title: Formátování dat CString a zobrazení oken zpráv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.strings
dev_langs:
- C++
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 125d0d3ec1549b9eba46cbfebfb7ecfe2c2186d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387175"
---
# <a name="cstring-formatting-and-message-box-display"></a>Formátování dat CString a zobrazení oken zpráv

Počet funkcí, které jsou k dispozici pro formátování a analýzu `CString` objekty. Tyto funkce můžete použít, kdykoli budete chtít pracovat s `CString` objekty, ale jsou užitečné hlavně při formátovacích řetězců, které se zobrazí okno se zprávou text.

Tato skupina funkce také globální rutina pro zobrazení okna se zprávou.

### <a name="cstring-functions"></a>CString – funkce

|||
|-|-|
|[Afxextractsubstring –](#afxextractsubstring)|Extrahuje dílčích řetězců oddělených jeden znak z daného zdroje řetězce.|
|[AfxFormatString1](#afxformatstring1)|Nahradí zadaného řetězce pro formátování znaků "%1" v řetězci obsažené v tabulce řetězců.|
|[AfxFormatString2](#afxformatstring2)|Nahradí dva řetězce formátu znaky "%1" a "%2" v řetězci obsažené v tabulce řetězců.|
|[AfxMessageBox](#afxmessagebox)|Zobrazí okno se zprávou.|

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxextractsubstring"></a>  Afxextractsubstring –

Tato globální funkce je možné extrahovat dílčí řetězec z daného zdroje řetězce.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz [CString](../../atl-mfc-shared/using-cstring.md) objekt, který se zobrazí jednotlivé dílčí řetězec.

*lpszFullString*<br/>
Řetězec obsahující textu v plném znění extrahovat z řetězce.

*iSubString*<br/>
Index založený na nule podřetězec extrahovat z *lpszFullString*.

*chSep*<br/>
Oddělovač znak použitý k oddělení podřetězců.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud funkci bylo úspěšně extrahováno dílčí řetězec na zadaný index; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná pro extrahování řetězu více podřetězců z řetězce zdroje při známé jeden znak odděluje každý dílčí řetězec. Tato funkce hledá od začátku *lpszFullString* parametr pokaždé, když je volána.

Tato funkce vrátí hodnotu FALSE, pokud buď *lpszFullString* nastaven na hodnotu NULL nebo funkci dosáhne konce *lpszFullString* bez hledání *iSubString*+ 1 výskyty znaků zadaného oddělovače. *RString* parametr se nezmění původní hodnotu Pokud *lpszFullString* byla nastavena na hodnotu NULL; v opačném případě *rString* parametr je nastaven na prázdný řetězec, pokud pro zadaný index nelze extrahovat podřetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxformatstring1"></a>  AfxFormatString1

Nahradí řetězec, který ukazuje *lpsz1* pro všechny instance znaky "%1" v šabloně řetězec prostředku označeném identifikátorem *nIDS*.

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na `CString` objekt, který bude obsahovat výsledný řetězec po provedení nahrazení.

*nIDS*<br/>
ID prostředku šablony řetězce, na kterém se provede nahrazení.

*lpsz1*<br/>
Řetězec, který nahradí formát znaky "%1" v řetězci šablony.

### <a name="remarks"></a>Poznámky

Nově vytvořenou řetězec je uložen v *rString*. Například, pokud je řetězec do tabulky řetězců "Soubor %1 nebyl nalezen" a *lpsz1* je rovno "C:\MYFILE. TXT", pak *rString* bude obsahovat řetězcem"File C:\MYFILE. TXT nebyl nalezen". Tato funkce je užitečná pro formátování řetězce odeslány do okna se zprávou a dalších oknech.

Pokud formát znaky "%1" objevit více než jednou v řetězci, bude proveden více nahrazení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxformatstring2"></a>  AfxFormatString2

Nahradí řetězec, který ukazuje *lpsz1* pro všechny výskyty znaků "%1" a řetězce, na které odkazuje *lpsz2* pro všechny instance znaky "%2" v prostředku šablony řetězců identifikovaný *nIDS*.

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na `CString` po provedení nahrazení, který bude obsahovat výsledný řetězec.

*nIDS*<br/>
ID tabulky řetězec šablony řetězce, na kterém se provede nahrazení.

*lpsz1*<br/>
Řetězec, který nahradí formát znaky "%1" v řetězci šablony.

*lpsz2*<br/>
Řetězec, který nahradí formát znaky "%2" v řetězci šablony.

### <a name="remarks"></a>Poznámky

Nově vytvořenou řetězec je uložen v *rString*. Pokud je řetězec do tabulky řetězců "Soubor %1 nebyl nalezen v adresáři %2", například *lpsz1* odkazuje na "MYFILE. TXT", a *lpsz2* odkazuje na"C:\MYDIR", pak *rString* bude obsahovat řetězcem"File MYFILE. Nebyl nalezen v adresáři C:\MYDIR TXT"

Pokud formát znaky "%1" nebo "%2" se objevit více než jednou v řetězci, bude proveden více nahrazení. Nemají v jejich číselného pořadí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxwin.h

##  <a name="afxmessagebox"></a>  AfxMessageBox

Na obrazovce zobrazí okno se zprávou.

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
Odkazuje `CString` objektu nebo řetězec zakončený hodnotou null obsahující zprávu, která se zobrazí v okně se zprávou.

*nTyp*<br/>
Styl okna se zprávou. Některý [styly oken zpráv](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) do pole.

*nIDHelp*<br/>
ID kontextové nápovědy pro zprávy. Hodnota 0 znamená, že bude použita výchozí Kontextová nápověda aplikace.

*nIDPrompt*<br/>
Jedinečný Identifikátor, který slouží jako odkaz na řetězec do tabulky řetězců.

### <a name="return-value"></a>Návratová hodnota

Nula v případě, že není dostatek paměti k zobrazení okna se zprávou; v opačném případě se vrátí jednu z následujících hodnot:

- Bylo zvoleno tlačítko Přerušit IDABORT.

- Bylo zvoleno tlačítko Zrušit IDCANCEL.

- Bylo zvoleno tlačítko Ignorovat IDIGNORE.

- IDNO The bylo zvoleno tlačítko.

- Bylo zvoleno tlačítko IDOK OK.

- Bylo zvoleno tlačítko Opakovat IDRETRY.

- IDYES The bylo zvoleno tlačítko Ano.

Pokud okno se zprávou má tlačítko Storno, bude vrácena hodnota IDCANCEL, a pokud po stisknutí klávesy ESC nebo je zvoleno tlačítko Storno. Pokud okno se zprávou nemá žádné tlačítko Storno, stisknutí klávesy ESC nemá žádný vliv.

Funkce [AfxFormatString1](#afxformatstring1) a [AfxFormatString2](#afxformatstring2) může být užitečné při formátování textu, který se zobrazí v okně se zprávou.

### <a name="remarks"></a>Poznámky

První formulář této přetížené funkce zobrazí textový řetězec s odkazem *lpszText* v okně se zprávou a využívá *nIDHelp* k popisu kontextové nápovědy. Kontextovou nápovědu lze použít pro přechod na související téma nápovědy, když uživatel stiskne klávesu pro nápovědu (obvykle F1).

Druhý tvar funkce používá řetězec prostředku s ID *nIDPrompt* pro zobrazení zprávy v okně se zprávou. Přidružená stránka nápovědy se vyhledá prostřednictvím hodnoty *nIDHelp*. Pokud výchozí hodnotu *nIDHelp* se používá (-1), ID zdroje řetězce *nIDPrompt*, se používá pro kontextové nápovědy. Další informace o definování kontextů nápovědy naleznete v tématu [Technická poznámka 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT – třída](../../atl-mfc-shared/reference/cstringt-class.md)
