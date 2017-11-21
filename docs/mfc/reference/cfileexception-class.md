---
title: "Třída CFileException | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
dev_langs: C++
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e63ba0bf91e57880321371a03eea77195bbe87a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cfileexception-class"></a>CFileException – třída
Představuje podmínku výjimky související s souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFileException : public CException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileException::CFileException](#cfileexception)|Vytvoří `CFileException` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileException::ErrnoToException](#errnotoexception)|Vrátí způsobit odpovídající číslo běhová chyba – kód.|  
|[CFileException::GetErrorMessage](#geterrormessage)|Načte zprávu s popisem výjimku.|  
|[CFileException::OsErrorToException](#oserrortoexception)|Vrátí kód příčina odpovídající kód chyby operačního systému.|  
|[CFileException::ThrowErrno](#throwerrno)|Vyvolá výjimku souborů na základě různých chyby za běhu.|  
|[CFileException::ThrowOsError](#throwoserror)|Vyvolá výjimku souborů podle operačního systému číslo chyby.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileException::m_cause](#m_cause)|Obsahuje odpovídající výjimky příčina přenosné kód.|  
|[CFileException::m_lOsError](#m_loserror)|Obsahuje číslo související chyby operačního systému.|  
|[CFileException::m_strFileName](#m_strfilename)|Obsahuje název souboru pro tuto výjimku.|  
  
## <a name="remarks"></a>Poznámky  
 `CFileException` Třída obsahuje členy veřejná data, které mají kód přenosné příčina a číslo operačního systému – konkrétní chyby. Třída také poskytuje statické členské funkce pro vyvolání souboru výjimek a vrácení kódů příčina chyby operačního systému a běhové chyby C.  
  
 `CFileException`objekty jsou vytvořená a vyvolána `CFile` členské funkce a v členské funkce odvozených tříd. Dostanete tyto objekty v rámci oboru **CATCH** výraz. Pro přenositelnost použijte pouze kód, příčina k získání důvod k výjimce. Další informace o výjimkách, najdete v článku [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CFileException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="cfileexception"></a>CFileException::CFileException  
 Vytvoří `CFileException` objekt, který ukládá příčina kód a kód operačního systému v objektu.  
  
```  
CFileException(
    int cause = CFileException::none,  
    LONG lOsError = -1,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cause`  
 Proměnná výčtového typu, která označuje důvod výjimky. V tématu [CFileException::m_cause](#m_cause) seznam možných hodnot.  
  
 `lOsError`  
 Z důvodu operačního systému specifické pro výjimku, pokud je k dispozici. `lOsError` Parametr poskytuje další informace než `cause` nepodporuje.  
  
 `lpszArchiveName`  
 Odkazuje na řetězec obsahující název `CFile` objekt, který způsobil výjimku.  
  
### <a name="remarks"></a>Poznámky  
 Nepoužívejte tento konstruktor přímo, ale spíš volání globální funkce [afxthrowfileexception –](exception-processing.md#afxthrowfileexception).  
  
> [!NOTE]
>  Proměnná `lOsError` se vztahují pouze na `CFile` a `CStdioFile` objekty. `CMemFile` Třída nezpracovává tomto kódu chyby.  
  
##  <a name="errnotoexception"></a>CFileException::ErrnoToException  
 Převede hodnotu daného běhové knihovny chyba na `CFileException` chybovou hodnotu ve výčtu.  
  
```  
static int PASCAL ErrnoToException(int nErrno);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrno`  
 Celé číslo chybový kód definovaným v souboru zahrnout běhu kód chyby. H.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výčtová hodnota, která odpovídá chybovou hodnotu daného běhové knihovny.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [CFileException::m_cause](#m_cause) seznam možné provést výčet hodnot.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]  
  
##  <a name="geterrormessage"></a>CFileException::GetErrorMessage  
 Načte text, který popisuje výjimku.  
  
```  
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,  
    UINT nMaxError,  
    PUINT pnHelpContext = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [ve out]`lpszError`  
 Ukazatel na vyrovnávací paměť, která obdrží chybovou zprávu.  
  
 [v]`nMaxError`  
 Maximální počet znaků, které mohou být uloženy zadané vyrovnávací paměti. To zahrnuje ukončující znak hodnoty null.  
  
 [ve out]`pnHelpContext`  
 Ukazatel na celé číslo bez znaménka, která přijímá ID kontextové nápovědy Pokud `NULL`, je vrácen žádné ID.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud zadané vyrovnávací paměť je příliš malá, chybová zpráva se zkrátí.  
  
### <a name="example"></a>Příklad  
 Následující příklad používá `CFileException::GetErrorMessage`.  
  
 [!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]  
  
##  <a name="m_cause"></a>CFileException::m_cause  
 Obsahuje hodnoty, které jsou definované `CFileException` výčtového typu.  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen dat je veřejné proměnné typu `int`. Výčty a jejich významy jsou následující:  
  
- `CFileException::none`0: žádné došlo k chybě.  
  
- `CFileException::genericException`1: došlo k neurčené chybě.  
  
- `CFileException::fileNotFound`2: soubor nebyl nalezen.  
  
- `CFileException::badPath`3: nebo její část cesty je neplatná.  
  
- `CFileException::tooManyOpenFiles`4: byl překročen povolený počet otevřených souborů.  
  
- `CFileException::accessDenied`5: soubor není přístupná.  
  
- `CFileException::invalidFile`6: došlo pokusu o použití neplatný popisovač souboru.  
  
- `CFileException::removeCurrentDir`7: aktuální pracovní adresář nelze odebrat.  
  
- `CFileException::directoryFull`8: nejsou žádné další položky adresáře.  
  
- `CFileException::badSeek`9: došlo k chybě při pokusu o nastavení ukazatele souboru.  
  
- `CFileException::hardIO`10: došlo k chybě hardwaru.  
  
- `CFileException::sharingViolation`11: SDÍLENÉ SLOŽKY. EXE nebyl načten nebo byla sdílená oblast uzamčena.  
  
- `CFileException::lockViolation`12: došlo pokusu o uzamčení oblasti, která již byla uzamčena.  
  
- `CFileException::diskFull`14: disk je plný.  
  
- `CFileException::endOfFile`15: byl dosažen konec souboru.  
  
    > [!NOTE]
    >  Tyto `CFileException` výčty příčina se liší od `CArchiveException` způsobit výčty.  
  
    > [!NOTE]
    > `CArchiveException::generic`je zastaralý. Místo nich se používá `genericException`. Pokud `generic` používá v aplikaci a vytvořené s nástroji/CLR, výslednou syntaxi chyby nejsou snadno dekódovat.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]  
  
##  <a name="m_loserror"></a>CFileException::m_lOsError  
 Obsahuje kód chyby operačního systému pro tuto výjimku.  
  
```  
LONG m_lOsError;  
```  
  
### <a name="remarks"></a>Poznámky  
 V příručce k operačního systému technical seznam kódy chyb. Tento člen dat je veřejné proměnné typu **DLOUHO**.  
  
##  <a name="m_strfilename"></a>CFileException::m_strFileName  
 Obsahuje název souboru pro tuto podmínku výjimky.  
  
```  
CString m_strFileName;  
```  
  
##  <a name="oserrortoexception"></a>CFileException::OsErrorToException  
 Vrátí enumerátor, který odpovídá danou `lOsError` hodnotu. Pokud kód chyby neznámá, pak funkce vrátí hodnotu **CFileException::generic**.  
  
```  
static int PASCAL OsErrorToException(LONG lOsError);
```  
  
### <a name="parameters"></a>Parametry  
 `lOsError`  
 Kód chyby operačního systému – konkrétní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výčtová hodnota, která odpovídá hodnotě dané Chyba operačního systému.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]  
  
##  <a name="throwerrno"></a>CFileException::ThrowErrno  
 Vytvoří `CFileException` odpovídající objekt daného `nErrno` hodnotu a pak vyvolá výjimku.  
  
```  
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrno`  
 Celé číslo chybový kód definovaným v souboru zahrnout běhu kód chyby. H.  
  
 `lpszFileName`  
 Ukazatel na řetězec, který obsahuje název souboru, pokud je k dispozici způsobil výjimku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]  
  
##  <a name="throwoserror"></a>CFileException::ThrowOsError  
 Vyvolá `CFileException` odpovídající danou `lOsError` hodnotu. Pokud kód chyby neznámá, pak funkce vyvolá výjimku programového jako **CFileException::generic**.  
  
```  
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lOsError`  
 Kód chyby operačního systému – konkrétní.  
  
 `lpszFileName`  
 Ukazatel na řetězec, který obsahuje název souboru, pokud je k dispozici způsobil výjimku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CException – třída](../../mfc/reference/cexception-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Zpracování výjimek](../../mfc/reference/exception-processing.md)



