---
title: Třída CStdioFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
dev_langs:
- C++
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95e05c071057025bda8e841be2cd5c6b17971626
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122565"
---
# <a name="cstdiofile-class"></a>CStdioFile – třída
Představuje soubor datového proudu běhu C, jak otevřít funkce běhové [fopen –](../../c-runtime-library/reference/fopen-wfopen.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CStdioFile : public CFile  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CStdioFile::CStdioFile](#cstdiofile)|Vytvoří `CStdioFile` objektu ze souboru nebo cesta ukazatel.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CStdioFile::Open](#open)|Přetíženo. Otevřete je určen k použití s výchozím `CStdioFile` – konstruktor (přepíše [CFile::Open](../../mfc/reference/cfile-class.md#open)).|  
|[CStdioFile::ReadString](#readstring)|Přečte jeden řádek textu.|  
|[CStdioFile::Seek](#seek)|Umisťuje aktuální ukazatele souboru.|  
|[CStdioFile::WriteString](#writestring)|Zapíše na jednom řádku textu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CStdioFile::m_pStream](#m_pstream)|Obsahuje ukazatel na otevření souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Soubory datového proudu jsou do vyrovnávací paměti a lze otevřít v textovém režimu (výchozí) nebo binárního režimu.  
  
 Režim textové poskytuje speciální zpracování pro dvojice znaků CR vrátit-konce řádku. Při psaní nový řádek znak (0x0A) do režimu text `CStdioFile` objektu, pair bajtů (0x0D, 0x0A) je odeslána do souboru. Když si přečíst, pair bajtů (0x0D, 0x0A) převádějí do jednoho bajtu 0x0A.  
  
 [Cfile –](../../mfc/reference/cfile-class.md) funkce [duplicitní](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), a [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nejsou podporovány pro `CStdioFile`.  
  
 Když zavoláte na tyto funkce `CStdioFile`, zobrazí se [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Další informace o používání `CStdioFile`, najdete v článcích [soubory v prostředí MFC](../../mfc/files-in-mfc.md) a [zpracování souborů](../../c-runtime-library/file-handling.md) v *referenční dokumentace běhové knihovny*.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 `CStdioFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="cstdiofile"></a>  CStdioFile::CStdioFile  
 Vytvoří a inicializuje `CStdioFile` objektu.  
  
```  
CStdioFile();  
CStdioFile(CAtlTransactionManager* pTM);  
  CStdioFile(FILE* pOpenStream);

 
CStdioFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags);

 
CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```  
  
### <a name="parameters"></a>Parametry  
 *pOpenStream*  
 Určuje ukazatele souboru vrácené voláním funkce C Runtime [fopen –](../../c-runtime-library/reference/fopen-wfopen.md).  
  
 *lpszFileName*  
 Určuje řetězec, který představuje cestu k souboru požadovaného. Cesta může být relativní nebo absolutní.  
  
 *nOpenFlags*  
 Určuje možnosti pro vytvoření souboru, sdílení souborů a režimy přístupu k souboru. Je-li zadat více možností pomocí bitová hodnota OR ( **|** ) operátor.  
  
 Jedna možnost režimu přístup k souboru je povinná; Další režimy jsou volitelné. V tématu [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) seznam možností režimu a další příznaky. V prostředí MFC verze 3.0 a novější jsou povoleny příznaky sdílené složky.  
  
 *Druh*  
 Ukazatel na CAtlTransactionManager objektu.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí konstruktor nepřipojí soubor, který chcete `CStdioFile` objektu. Při používání tohoto konstruktoru, je nutné použít `CStdioFile::Open` metodu pro otevření souboru a připojte ji k `CStdioFile` objektu.  
  
 Jeden parametr konstruktoru připojí otevření souboru datového proudu k `CStdioFile` objektu. Povolené hodnoty ukazatele zahrnují ukazatele předdefinované vstupní a výstupní soubor *stdin –*, *stdout*, nebo *stderr*.  
  
 Vytvoří dvě parametr konstruktoru `CStdioFile` objektu a odpovídající soubor se otevře v zadané cestě.  
  
 Pokud předáte hodnotu NULL pro buď *pOpenStream* nebo *lpszFileName*, vyvolá konstruktoru `CInvalidArgException*`.  
  
 Pokud je soubor nelze otevřít nebo vytvořit, vyvolá konstruktoru `CFileException*`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]  
  
##  <a name="m_pstream"></a>  CStdioFile::m_pStream  
 `m_pStream` – Datový člen je má ukazatel na otevření souboru, jak ho vrátila funkce běhu C `fopen`.  
  
```  
FILE* m_pStream;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je soubor, který otevírá nebo bylo ukončeno je NULL.  
  
##  <a name="open"></a>  CStdioFile::Open  
 Přetíženo. Otevřete je určen k použití s výchozím `CStdioFile` konstruktor.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CAtlTransactionManager* pTM,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszFileName*  
 Řetězec, který je cesta k souboru požadovaného. Cesta může být relativní nebo absolutní.  
  
 *nOpenFlags*  
 Režim sdílení a přístup. Určuje akci, která se má provést při otevření souboru. Možnosti můžete kombinovat pomocí bitové operace OR (&#124;) operátor. Jeden přístupová oprávnění a možnost jednu sdílenou složku jsou povinné; režimy modeCreate a modeNoInherit jsou volitelné.  
  
 *pError*  
 Ukazatel na existující objekt výjimky souborů, který se zobrazí stav neúspěšnou operaci.  
  
 *Druh*  
 Ukazatel na `CAtlTransactionManager` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je úspěšné; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="readstring"></a>  CStdioFile::ReadString  
 Načte text dat do vyrovnávací paměti, až limitu *nMax*-1 znaků ze souboru přidružené `CStdioFile` objektu.  
  
```  
virtual LPTSTR ReadString(
    LPTSTR lpsz,  
    UINT nMax);  
  
virtual BOOL ReadString(CString& rString);
```  
  
### <a name="parameters"></a>Parametry  
 *lpsz*  
 Určuje ukazatel uživatelem zadané vyrovnávací paměť, která bude přijímat ukončené hodnotou null textový řetězec.  
  
 *nMax*  
 Určuje maximální počet znaků ke čtení, není počítání ukončující znak hodnoty null.  
  
 *rString*  
 Odkaz na `CString` objekt, který bude obsahovat řetězec, když funkce vrátí hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na obsahující textové datové vyrovnávací paměti. Hodnota NULL, pokud koncový souboru bylo dosaženo bez přečtení všech dat; nebo pokud logická hodnota, FALSE, pokud koncový souboru bylo dosaženo bez přečtení žádná data.  
  
### <a name="remarks"></a>Poznámky  
 Čtení je zastavena první znak nového řádku. Pokud v takovém případě méně než *nMax*přečetli znaků-1, znak nového řádku je uložený ve vyrovnávací paměti. V obou případech se připojí znak hodnoty null ('\0').  
  
 [CFile::Read](../../mfc/reference/cfile-class.md#read) je k dispozici také pro režim textové vstupu, ale nezavře na pár znaků CR vrátit-konce řádku.  
  
> [!NOTE]
>  `CString` Odebere verze této funkce `'\n'` pokud existuje; LPTSTR verze nepracuje.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]  
  
##  <a name="seek"></a>  CStdioFile::Seek  
 Přemístí ukazatele v dříve otevřený soubor.  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOff,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>Parametry  
 *lOff*  
 Počet bajtů přesunout ukazatel.  
  
 *nFrom*  
 Režim pohyb ukazatele. Musí být jedna z následujících hodnot:  
  
- `CFile::begin`: Přesunutí ukazatele souboru *lOff* bajtů předávání od začátku souboru.  
  
- `CFile::current`: Přesunutí ukazatele souboru *lOff* bajtů z aktuální pozice v souboru.  
  
- `CFile::end`: Přesunutí ukazatele souboru *lOff* bajtů od konce souboru. Všimněte si, že *lOff* musí být záporné k vyhledání do existujících souborů; kladné hodnoty bude hledat za koncem souboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je požadovaný pozice právní, `Seek` vrátí novou posun bajtů od začátku souboru. Jinak, není definován návratovou hodnotu a `CFileException` objektu je vyvolána výjimka.  
  
### <a name="remarks"></a>Poznámky  
 `Seek` Funkce umožňuje náhodný přístup k obsahu souboru přesunutím ukazatele po zadanou dobu absolutně nebo relativně. Během hledání ve skutečnosti nenačtou žádná data. Pokud je požadovaný pozice větší než velikost souboru, délku souboru bude rozšířeno na této poloze a žádné dojde k výjimce.  
  
 Po otevření souboru ukazatele souboru je nastavený na posunu 0, na začátek souboru.  
  
 Tato implementace `Seek` vychází z funkce běhové knihovny (CRT) `fseek`. Existuje několik omezení na použití `Seek` na Otevřít v režimu textových datových proudů. Další informace najdete v tématu [fseek, _fseeki64 –](../../c-runtime-library/reference/fseek-fseeki64.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `Seek` ukazatel myši přesunete 1000 bajtů od začátku `cfile` souboru. Všimněte si, že `Seek` číst data, takže následně musí volat [CStdioFile::ReadString](#readstring) číst data.  
  
 [!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]  
  
##  <a name="writestring"></a>  CStdioFile::WriteString  
 Zapisuje data z vyrovnávací paměti do souboru přidružené `CStdioFile` objektu.  
  
```  
virtual void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>Parametry  
 *lpsz*  
 Určuje ukazatel na vyrovnávací paměť, která obsahuje řetězce ukončené hodnotou null.  
  
### <a name="remarks"></a>Poznámky  
 Ukončovací znak hodnoty null ( `\0`) není zapsán do souboru. Tato metoda se zapisují znaky nového řádku *lpsz* k souboru jako pár znaků CR vrátit/konce řádku.  
  
 Pokud chcete zapisovat data, která není null ukončena do souboru, použijte `CStdioFile::Write` nebo [CFile::Write](../../mfc/reference/cfile-class.md#write).  
  
 Tato metoda vyvolá `CInvalidArgException*` Pokud zadáte hodnotu NULL pro *lpsz* parametr.  
  
 Tato metoda vyvolá `CFileException*` v reakci na chyby.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Cfile – třída](../../mfc/reference/cfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cfile – třída](../../mfc/reference/cfile-class.md)   
 [CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)   
 [CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)   
 [CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)   
 [CNotSupportedException – třída](../../mfc/reference/cnotsupportedexception-class.md)
