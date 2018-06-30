---
title: Formátování dat CString a zobrazení oken zpráv | Microsoft Docs
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
ms.openlocfilehash: d0367caf33eea9832d33e4e4ec96144d51b1c5c3
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122261"
---
# <a name="cstring-formatting-and-message-box-display"></a>Formátování dat CString a zobrazení oken zpráv
Počet funkcí jsou k dispozici můžete naformátovat a analyzovat `CString` objekty. Tyto funkce lze použít, když máte k manipulaci s `CString` objekty, ale jsou užitečné zejména pro formátování řetězce, které se zobrazí v textu okno se zprávou.  
  
 Tato skupina funkcí také zahrnuje globální rutiny pro zobrazení okno se zprávou.  
  
### <a name="cstring-functions"></a>CString funkce  
  
|||  
|-|-|  
|[Afxextractsubstring –](#afxextractsubstring)|Extrahuje dílčích řetězců oddělených jednoho znaku v řetězci daný zdroj.|  
|[Afxformatstring1 –](#afxformatstring1)|Nahradí daný řetězec formátu znaky "%1" v řetězci obsažené v tabulce řetězců.|  
|[Afxformatstring2 –](#afxformatstring2)|Nahradí dva řetězce pro formát znaky "%1" a "%2" v řetězci obsažené v tabulce řetězců.|  
|[AfxMessageBox –](#afxmessagebox)|Zobrazí okno se zprávou.|  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxextractsubstring"></a>  Afxextractsubstring –  
 Tato globální funkce slouží k extrakci dílčí řetězec z daného zdrojový řetězec.  
  
```   
BOOL AFXAPI AfxExtractSubString (
    CString& rString,  
    LPCTSTR lpszFullString,  
    int iSubString,  
    TCHAR chSep  = '\n'); 
```  
  
### <a name="parameters"></a>Parametry  
 *rString*  
 -   Odkaz na [CString](../../atl-mfc-shared/using-cstring.md) objekt, který se zobrazí jednotlivé dílčí řetězec.  
  
 *lpszFullString*  
 -   Řetězec obsahující textu v plném znění extrahovat z řetězce.  
  
 *iSubString*  
 -   Index nule dílčí řetězec extrahovat z *lpszFullString*.  
  
 *chSep*  
 -   Oddělovací znak použít k oddělení dílčích řetězců.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud funkci úspěšně extrahovány dílčí řetězec na zadaný index; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je užitečná pro extrahování více dílčích řetězců z zdrojový řetězec při známé jednoho znaku dělí každý dílčí řetězec. Tato funkce vyhledá od začátku *lpszFullString* parametr pokaždé, když je volána.  
  
 Tato funkce vrátí hodnotu FALSE, pokud je buď *lpszFullString* je nastaven na hodnotu NULL nebo funkce dosáhne konce *lpszFullString* bez hledání *iSubString*+ 1 výskyty zadaný oddělovací znak. *RString* parametr se nezmění z původní hodnotu Pokud *lpszFullString* byl nastaven na hodnotu NULL; jinak hodnota, *rString* parametr je nastaven na prázdný řetězec, pokud pro zadaný index nelze extrahovat dílčí řetězec.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxformatstring1"></a>  Afxformatstring1 –  
 Nahradí text, na kterou odkazuje *lpsz1* pro všechny instance znaky "%1" v prostředku řetězec šablony, který se identifikovanou pomocí *nIDS*.  
  
```  
void  AfxFormatString1(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1); 
```  
  
### <a name="parameters"></a>Parametry  
 *rString*  
 Odkaz na `CString` objekt, který bude obsahovat výsledný řetězec po provedení nahrazování.  
  
 *nIDS*  
 ID prostředku řetězec šablony, na kterém bude provedena náhrada.  
  
 *lpsz1*  
 Řetězec, který nahradí formát znaky "%1" v řetězci šablony.  
  
### <a name="remarks"></a>Poznámky  
 Nově vytvořený řetězec je uložen v *rString*. Například, zda je řetězec v tabulce řetězec "Soubor %1 nebyl nalezen" a *lpsz1* je rovno "C:\MYFILE. Soubory TXT", pak *rString* bude obsahovat řetězec"soubor C:\MYFILE. TXT nebyl nalezen". Tato funkce je užitečná pro formátování řetězců odeslána do okna zpráv a windows.  
  
 Pokud formát znaky "%1" se zobrazí v řetězci více než jednou, budou provedeny více nahrazení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxformatstring2"></a>  Afxformatstring2 –  
 Nahradí text, na kterou odkazuje *lpsz1* pro všechny instance znaky "%1" a řetězec, na kterou odkazuje *lpsz2* pro všechny instance znaky "%2" v řetězci prostředku šablony identifikovaný *nIDS*.  
  
```   
void AfxFormatString2(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1,  
    LPCTSTR lpsz2); 
```  
  
### <a name="parameters"></a>Parametry  
 *rString*  
 Odkaz na `CString` po provedení nahrazování, která bude obsahovat výsledný řetězec.  
  
 *nIDS*  
 ID tabulky řetězec řetězec šablony, na kterém bude provedena náhrada.  
  
 *lpsz1*  
 Řetězec, který nahradí formát znaky "%1" v řetězci šablony.  
  
 *lpsz2*  
 Řetězec, který nahradí formát znaky "%2" v řetězci šablony.  
  
### <a name="remarks"></a>Poznámky  
 Nově vytvořený řetězec je uložen v *rString*. Pokud je řetězec v tabulce řetězec "Soubor %1 nebyl nalezen v adresáři %2", například *lpsz1* odkazuje na "MYFILE. Soubory TXT", a *lpsz2* odkazuje na"C:\MYDIR", pak *rString* bude obsahovat řetězec"soubor MYFILE. Nebyl nalezen v adresáři C:\MYDIR TXT"  
  
 Pokud formát znaky "%1" nebo "%2" se zobrazují v řetězci více než jednou, budou provedeny více nahrazení. Nemají být v jejich číselného pořadí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxmessagebox"></a>  AfxMessageBox –  
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
 *lpszText*  
 Odkazuje na `CString` objekt nebo ukončené hodnotou null řetězec obsahující zprávu, která se zobrazí v okně zprávy.  
  
 *Noznámení*  
 Styl do pole zpráva. Použít libovolný z [styly oken zpráv](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) do pole.  
  
 *nIDHelp*  
 ID kontextu nápovědy pro zprávy. Hodnota 0 znamená, že se použije aplikace výchozího nápovědy kontextu.  
  
 *nIDPrompt*  
 Jedinečné ID slouží k odkazování na řetězec v tabulce řetězců.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula. Pokud není k dispozici dostatek paměti pro zobrazení zprávou; jinak se vrátí jednu z následujících hodnot:  
  
- Bylo vybráno IDABORT The Abort tlačítko.  
  
- Tlačítko Zrušit IDCANCEL nebyla vybrána.  
  
- Bylo vybráno tlačítko IDIGNORE The ignorovat.  
  
- Bylo vybráno IDNO žádné tlačítko.  
  
- Tlačítko OK IDOK nebyla vybrána.  
  
- Bylo vybráno tlačítko IDRETRY The opakujte.  
  
- Nebyla vybrána IDYES The tlačítko Ano.  
  
 Pokud okno se zprávou tlačítko Zrušit, bude-li po stisknutí klávesy ESC nebo výběru tlačítka Storno vrácena hodnota IDCANCEL. Pokud do pole zpráva nemá žádné tlačítko Storno, stisknutím klávesy ESC nemá žádný vliv.  
  
 Funkce [afxformatstring1 –](#afxformatstring1) a [afxformatstring2 –](#afxformatstring2) mohou být užitečné při formátování textu, který se zobrazí v okně se zprávou.  
  
### <a name="remarks"></a>Poznámky  
 První formulář tohoto přetížený funkce zobrazí textového řetězce na kterou odkazuje *lpszText* v okně se zprávou a použije *nIDHelp* k popisu kontextové nápovědy. Kontext nápovědy používá přejít k přidružené téma nápovědy, když uživatel stiskne klávesu nápovědy (obvykle F1).  
  
 Druhý formulář funkce používá řetězec prostředku s ID *nIDPrompt* k zobrazení zprávy v okně zprávy. Přidružené stránky nápovědy nenajde prostřednictvím hodnotu *nIDHelp*. Pokud výchozí hodnotu *nIDHelp* je použité (-1), ID prostředku řetězec, *nIDPrompt*, se používá pro daný kontext nápovědy. Další informace o definování kontexty nápovědy, najdete v části [Technická poznámka 28](../../mfc/tn028-context-sensitive-help-support.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)   
 [CStringT – třída](../../atl-mfc-shared/reference/cstringt-class.md)
