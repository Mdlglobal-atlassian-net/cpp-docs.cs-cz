---
title: Formátování dat CString a zobrazení oken zpráv
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: ad880c5302fd2274c5d46719e912461fd7497f10
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854052"
---
# <a name="cstring-formatting-and-message-box-display"></a>Formátování dat CString a zobrazení oken zpráv

K dispozici je řada funkcí pro formátování a analýzu `CString` objektů. Tyto funkce lze použít vždy, když je nutné manipulovat s `CString` objekty, ale jsou zvláště užitečné pro formátování řetězců, které se zobrazí v textu zpráv.

Tato skupina funkcí obsahuje také globální rutinu pro zobrazení okna se zprávou.

### <a name="cstring-functions"></a>CString – funkce

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|Extrahuje podřetězce oddělené jedním znakem z daného zdrojového řetězce.|
|[AfxFormatString1](#afxformatstring1)|Nahradí daný řetězec pro formátovací znaky "%1" v řetězci obsaženém v tabulce řetězců.|
|[AfxFormatString2](#afxformatstring2)|Nahradí dva řetězce pro formátovací znaky "%1" a "%2" v řetězci obsaženém v tabulce řetězců.|
|[AfxMessageBox](#afxmessagebox)|Zobrazí okno se zprávou.|

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxextractsubstring"></a>AfxExtractSubString

Tato globální funkce může být použita k extrakci podřetězce z daného zdrojového řetězce.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na objekt [CString](../../atl-mfc-shared/using-cstring.md) , který obdrží jednotlivý dílčí řetězec.

*lpszFullString*<br/>
Řetězec obsahující úplný text řetězce, ze kterého se má extrahovat.

*iSubString*<br/>
Nulový index dílčího řetězce, který se má extrahovat z *lpszFullString*.

*chSep*<br/>
Znak oddělovače použitý k oddělení podřetězců

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud funkce úspěšně extrahuje podřetězec v zadaném indexu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná pro extrakci více podřetězců ze zdrojového řetězce, když známý samostatný znak odděluje každý podřetězec. Tato funkce vyhledává na začátku parametru *lpszFullString* pokaždé, když je volána.

Tato funkce vrátí hodnotu FALSE, pokud je buď vlastnost *lpszFullString* nastavena na hodnotu null nebo funkce dosáhne konce *lpszFullString* , aniž by bylo nutné najít *iSubString*+ 1 výskytu zadaného znaku oddělovače. Parametr *rString* nebude změněn z původní hodnoty, pokud byla *lpszFullString* nastavena na hodnotu null. v opačném případě je parametr *rString* nastaven na prázdný řetězec, pokud nelze podřetězec extrahovat pro zadaný index.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxformatstring1"></a>AfxFormatString1

Nahradí řetězec, na který odkazuje *lpsz1* , pro všechny výskyty znaků "%1" v prostředku řetězce šablony identifikovaného pomocí *nIDS*.

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na objekt `CString`, který bude obsahovat výsledný řetězec po provedení substituce.

*nIDS*<br/>
ID prostředku řetězce šablony, na kterém bude provedena náhrada

*lpsz1*<br/>
Řetězec, ve kterém budou nahrazeny znaky formátu "%1" v řetězci šablony.

### <a name="remarks"></a>Poznámky

Nově vytvořený řetězec je uložený v *rString*. Například pokud řetězec v tabulce řetězců je "soubor %1 nebyl nalezen" a *lpsz1* se rovná "C:\MYFILE. TXT ", *rString* bude obsahovat řetězec" File C:\MYFILE. TXT nebyl nalezen. Tato funkce je užitečná pro formátování řetězců odesílaných do oken zpráv a dalších oken.

Pokud se formátovací znaky "%1" objeví v řetězci více než jednou, budou provedeny vícenásobné náhrady.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxformatstring2"></a>AfxFormatString2

Nahradí řetězec, na který odkazuje *lpsz1* pro všechny výskyty znaků "%1", a řetězec, na který odkazuje *lpsz2* pro všechny instance znaků "%2" v prostředku řetězce šablony identifikovaného *nIDS*.

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na `CString`, který bude obsahovat výsledný řetězec po provedení nahrazení.

*nIDS*<br/>
ID řetězcové tabulky řetězce šablony, na které bude provedena náhrada.

*lpsz1*<br/>
Řetězec, ve kterém budou nahrazeny znaky formátu "%1" v řetězci šablony.

*lpsz2*<br/>
Řetězec, ve kterém budou nahrazeny znaky formátu "%2" v řetězci šablony.

### <a name="remarks"></a>Poznámky

Nově vytvořený řetězec je uložený v *rString*. Pokud je řetězec v tabulce řetězců například "soubor %1 nebyl nalezen v adresáři %2", *lpsz1* odkazuje na "MYFILE. TXT ", a *lpsz2* odkazuje na" C:\MYDIR ", pak *rString* bude obsahovat řetězec" File MYFILE. V adresáři C:\MYDIR se nenašel znak TXT.

Pokud se formátovací znaky "%1" nebo "%2" objeví v řetězci více než jednou, budou provedeny vícenásobné náhrady. Nemusí být v číselném pořadí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxwin. h

##  <a name="afxmessagebox"></a>AfxMessageBox

Zobrazí okno se zprávou na obrazovce.

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
Odkazuje na objekt `CString` nebo řetězec zakončený hodnotou null obsahující zprávu, která se má zobrazit v okně se zprávou.

*Noznámení*<br/>
Styl okna se zprávou Použijte libovolné [Styly okna zpráv](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) pro pole.

*nIDHelp*<br/>
ID kontextu nápovědu pro zprávu; 0 znamená, že se použije výchozí kontext Help aplikace.

*nIDPrompt*<br/>
Jedinečné ID, které se používá k odkazování na řetězec v tabulce řetězců.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud není k dispozici dostatek paměti k zobrazení okna se zprávou; v opačném případě se vrátí jedna z následujících hodnot:

- Bylo vybráno tlačítko Abort (IDABORT).

- IDCANCEL bylo vybráno tlačítko Storno.

- IDIGNORE tlačítko Ignorovat bylo vybráno.

- IDNOo, že není vybrané žádné tlačítko.

- Bylo vybráno tlačítko OK IDOK.

- IDRETRY bylo vybráno tlačítko Opakovat.

- Bylo vybráno tlačítko Ano (IDYES).

Pokud je v okně se zprávou tlačítko zrušit, bude vrácena hodnota IDCANCEL při stisknutí klávesy ESC nebo při výběru tlačítka zrušit. Pokud okno se zprávou nemá žádné tlačítko Storno, nemá stisknutí klávesy ESC žádný efekt.

Funkce [AfxFormatString1](#afxformatstring1) a [AfxFormatString2](#afxformatstring2) mohou být užitečné při formátování textu, který se zobrazí v okně se zprávou.

### <a name="remarks"></a>Poznámky

První forma této přetížené funkce zobrazuje textový řetězec, na který odkazuje *lpszText* v okně se zprávou, a používá *nIDHelp* k popisu kontextu kontextové aplikace. Kontext nápovědy se používá k přechodu na související téma nápovědy, když uživatel stiskne klávesu nápovědy (obvykle F1).

Druhá forma funkce používá prostředek řetězce s ID *nIDPrompt* k zobrazení zprávy v okně se zprávou. Přidružená Stránka s nápovědě se nachází prostřednictvím hodnoty *nIDHelp*. Pokud je použita výchozí hodnota *nIDHelp* (-1), pro kontext nápovědu se použije ID prostředku řetězce *nIDPrompt*. Další informace o definování kontextů nápovědu najdete v části [technická Poznámka 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT – třída](../../atl-mfc-shared/reference/cstringt-class.md)
