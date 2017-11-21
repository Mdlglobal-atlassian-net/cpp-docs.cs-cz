---
title: "CException – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
dev_langs: C++
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 15037544b3344f5d43ebaa34fb35b431da581593
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cexception-class"></a>CException – třída
Základní třída pro všechny výjimky v knihovny Microsoft Foundation Class.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AFX_NOVTABLE CException : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CException::CException](#cexception)|Vytvoří `CException` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CException::Delete](#delete)|Odstraní `CException` objektu.|  
|[CException::ReportError](#reporterror)|Chybová zpráva v okně se zprávou sestavy pro uživatele.|  
  
## <a name="remarks"></a>Poznámky  
 Protože `CException` je abstraktní základní třída není možné vytvořit `CException` objekty přímo; je nutné vytvořit objekty odvozených tříd. Pokud je potřeba vytvořit vlastní `CException`– styl třídy, použijte jednu z výše uvedených jako model odvozené třídy. Ujistěte se, že odvozená třída také používá `IMPLEMENT_DYNAMIC`.  
  
 Odvozené třídy a jejich popisy jsou uvedeny níže:  
  
|||  
|-|-|  
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Základní třída pro prostředek kritických výjimek MFC|  
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Neplatný argument podmínku výjimky|  
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Výjimky nedostatku paměti|  
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Žádost o nepodporovanou operaci|  
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Výjimek specifické archivu|  
|[CFileException](../../mfc/reference/cfileexception-class.md)|Výjimek specifické pro soubor|  
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Windows prostředek nebyl nalezen nebo není vytvořitelné|  
|[COleException](../../mfc/reference/coleexception-class.md)|Výjimky OLE|  
|[CDBException](../../mfc/reference/cdbexception-class.md)|Výjimky databáze (to znamená, výjimka okolnosti, které pro databázové třídy MFC podle Open Database Connectivity)|  
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Výjimky OLE odesílání (Automatizace)|  
|[CUserException](../../mfc/reference/cuserexception-class.md)|Výjimka, která určuje, že prostředek nelze nalézt|  
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Objekt výjimky (to znamená, výjimka okolnosti, které pro třídy DAO) přístup k datům|  
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Výjimka Internetu (to znamená, výjimka okolnosti, které pro Internet – třídy).|  
  
 Tyto výjimky jsou určena pro použití s [THROW](exception-processing.md#throw), [throw_last –](exception-processing.md#throw_last), [zkuste](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch –](exception-processing.md#and_catch), a [end_catch –](exception-processing.md#end_catch) makra. Další informace o výjimky najdete v tématu [zpracování výjimky](exception-processing.md), nebo najdete v článku [zpracování výjimek (MFC)](../exception-handling-in-mfc.md).  
  
 K zachycení zvláštních výjimek, použijte odpovídající odvozené třídy. Chcete-li catch všechny typy výjimek, použijte `CException`a potom pomocí [CObject::IsKindOf](cobject-class.md#iskindof) rozlišení mezi `CException`-odvozených třídách. Všimněte si, že `CObject::IsKindOf` platí jenom pro třídy deklarovat s [implement_dynamic –](run-time-object-model-services.md#implement_dynamic) makro, aby bylo možné využít výhod dynamického typu kontroly. Všechny `CException`-měli používat odvozené třídy, které vytvoříte `IMPLEMENT_DYNAMIC` makro, příliš.  
  
 Podrobnosti o výjimkách uživateli můžete sestavu voláním [GetErrorMessage](cfileexception-class.md#geterrormessage) nebo [ReportError](#reporterror), dva členské funkce, které pracují s žádným z `CException`je odvozených třídách.  
  
 Pokud je výjimka zachycena pomocí jedné z makra, `CException` automaticky je odstraněn objekt; neodstraňujte ho sami. Pokud je výjimka zachycena pomocí **catch** – klíčové slovo, není automaticky odstraněn. Najdete v článku [zpracování výjimek (MFC)](../exception-handling-in-mfc.md) Další informace o tom, kdy se odstranit objekt výjimkou.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](cobject-class.md)  
  
 `CException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="cexception"></a>CException::CException  
 Tato funkce člen vytvoří `CException` objektu.  
  
```  
explicit CException(BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parametry  
 *b_AutoDelete*  
 Zadejte **TRUE** Pokud paměti pro `CException` objekt byl přidělen v haldě. To způsobí, že `CException` objekt, který chcete odstranit, když **odstranit** – členská funkce je volána odstranit výjimku. Zadejte **FALSE** Pokud `CException` objekt je v zásobníku nebo je objekt globální. V takovém případě `CException` objekt nebude odstraněn, když **odstranit** členské funkce je volána.  
  
### <a name="remarks"></a>Poznámky  
 Potřebovali byste normálně nikdy přímo volat tento konstruktor. Funkci, která vyvolá výjimku, by měl vytvořit instanci `CException`-odvozené třídy a volat jeho konstruktoru, nebo pomocí některé z knihovny MFC vyvoláním funkce, jako například [afxthrowfileexception –](exception-processing.md#afxthrowfileexception), má být vyvolána předdefinované typu. Tato dokumentace se poskytuje jen pro úplnost.  
  
##  <a name="delete"></a>CException::Delete  
 Tato funkce zkontroluje, zda **CException** objekt byl vytvořen v haldě, a pokud ano, zavolá **odstranit** operátor v objektu.  
  
```  
void Delete();
```  
  
### <a name="remarks"></a>Poznámky  
 Při odstraňování **CException** objektu, použijte **odstranit** – členská funkce odstranit výjimku. Nepoužívejte **odstranit** operátor přímo, protože `CException` objekt může být objekt globální nebo byly vytvořeny v zásobníku.  
  
 Můžete určit, zda objekt měla by být odstraněna, když se objekt. Další informace najdete v tématu [CException::CException](#cexception).  
  
 Je třeba volat **odstranit** Pokud používáte C++ **zkuste**- **catch** mechanismus. Pokud používáte makry MFC **zkuste** a **CATCH**, pak tyto makra bude automaticky volání této funkce.  
  
### <a name="example"></a>Příklad  
 ```cpp  
 CFile* pFile = NULL;
// Constructing a CFile object with this override may throw
// a CFile exception, and won't throw any other exceptions.
// Calling CString::Format() may throw a CMemoryException,
// so we have a catch block for such exceptions, too. Any
// other exception types this function throws will be
// routed to the calling function.
// Note that this example performs the same actions as the 
// example for CATCH, but uses C++ try/catch syntax instead
// of using the MFC TRY/CATCH macros. This sample must use
// CException::Delete() to delete the exception objects
// before closing the catch block, while the CATCH example
// implicitly performs the deletion via the macros.
try
{
   pFile = new CFile(_T("C:\\WINDOWS\\SYSTEM.INI"),
      CFile::modeRead | CFile::shareDenyNone);
   ULONGLONG ullLength = pFile->GetLength();
   CString str;
   str.Format(_T("Your SYSTEM.INI file is %u bytes long."), ullLength);
   AfxMessageBox(str);
}
catch(CFileException* pEx)
{
   // Simply show an error message to the user.
   pEx->ReportError();
   pEx->Delete();
}
catch(CMemoryException* pEx)
{
   // We can't recover from this memory exception, so we'll
   // just terminate the app without any cleanup. Normally, an
   // an application should do everything it possibly can to
   // clean up properly and _not_ call AfxAbort().
   pEx->Delete();
   AfxAbort();
}
// If an exception occurrs in the CFile constructor,
// the language will free the memory allocated by new
// and will not complete the assignment to pFile.
// Thus, our clean-up code needs to test for NULL.
if (pFile != NULL)
{
   pFile->Close();
   delete pFile;
}   
 ```
  
##  <a name="reporterror"></a>CException::ReportError  
 V okně se zprávou uživateli volání této funkce člena na text chyby sestavy.  
  
```  
virtual int ReportError(
    UINT nType = MB_OK,  
    UINT nMessageID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nType`  
 Určuje styl do pole zpráva. Použít libovolnou kombinaci [styly oken zpráv](message-box-styles.md) do pole. Pokud tento parametr nezadáte, výchozí hodnota je **mb_ok –**.  
  
 *nMessageID*  
 Určuje ID prostředku (řetězec položka) zprávy, které chcete zobrazit, pokud objekt výjimky nemá chybovou zprávu. Zobrazí se v případě 0, zpráva "není žádná chybová zpráva k dispozici".  
  
### <a name="return-value"></a>Návratová hodnota  
 `AfxMessageBox` Hodnotu; jinak hodnota 0, pokud není k dispozici dostatek paměti pro zobrazení do pole zpráva. V tématu [AfxMessageBox –](cstring-formatting-and-message-box-display.md#afxmessagebox) pro možné vrácené hodnoty.  
  
### <a name="example"></a>Příklad  
 Tady je příklad použití `CException::ReportError`. Další příklad, podívejte se na příklad pro [CATCH](exception-processing.md#catch).  
  
```cpp  
CFile fileInput;
CFileException ex;

// try to open a file for reading.  
// The file will certainly not
// exist because there are too many explicit
// directories in the name.

// if the call to Open() fails, ex will be
// initialized with exception
// information.  the call to ex.ReportError() will
// display an appropriate
// error message to the user, such as
// "\Too\Many\Bad\Dirs.DAT contains an
// invalid path."  The error message text will be
// appropriate for the
// file name and error condition.

if (!fileInput.Open(_T("\\Too\\Many\\Bad\\Dirs.DAT"), CFile::modeRead, &ex))
{
  ex.ReportError();
}
else
{
  // the file was opened, so do whatever work
  // with fileInput we were planning...

  fileInput.Close();
}
```

## <a name="see-also"></a>Viz také  
 [CObject – třída](cobject-class.md)   
 [Graf hierarchie](../hierarchy-chart.md)   
 [Zpracování výjimek](exception-processing.md)   
 [Jak I: vytvořit vlastní třídy výjimek vlastní](http://go.microsoft.com/fwlink/linkid=128045)


