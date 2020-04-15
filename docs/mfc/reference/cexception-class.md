---
title: CException – třída
ms.date: 11/04/2016
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
ms.openlocfilehash: c3742db7475e626b18e9c073a0b7417a8034863f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373943"
---
# <a name="cexception-class"></a>CException – třída

Základní třída pro všechny výjimky v knihovně tříd Microsoft Foundation.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CException::CException](#cexception)|Vytvoří `CException` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CException::Delete](#delete)|Odstraní `CException` objekt.|
|[CException::Chyba sestavy](#reporterror)|Nahlásí uživateli chybovou zprávu v poli se zprávou.|

## <a name="remarks"></a>Poznámky

Protože `CException` je abstraktní základní třída, nelze vytvářet `CException` objekty přímo; musíte vytvořit objekty odvozených tříd. Pokud potřebujete vytvořit vlastní `CException`třídu stylu, použijte jednu z výše uvedených odvozených tříd jako model. Ujistěte se, že vaše `IMPLEMENT_DYNAMIC`odvozené třídy také používá .

Odvozené třídy a jejich popisy jsou uvedeny níže:

|||
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Základní třída pro výjimky knihovny MFC kritické pro prostředky|
|[Výjimka CInvalidargException](../../mfc/reference/cinvalidargexception-class.md)|Neplatná podmínka výjimky argumentu|
|[Výjimka cmemoryexception](../../mfc/reference/cmemoryexception-class.md)|Výjimka nedostatku paměti|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Požadavek na nepodporovanou operaci|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Výjimka specifická pro archiv|
|[Výjimka souboru C](../../mfc/reference/cfileexception-class.md)|Výjimka specifická pro soubor|
|[CVýjimka prostředků](../../mfc/reference/cresourceexception-class.md)|Prostředek systému Windows nebyl nalezen nebo není kreatable|
|[COleException](../../mfc/reference/coleexception-class.md)|Výjimka OLE|
|[Výjimka CDB](../../mfc/reference/cdbexception-class.md)|Výjimka databáze (to znamená podmínky výjimky vznikající pro třídy databáze knihovny MFC založené na připojení otevřené databáze)|
|[Výjimka COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Výjimka pro odeslání OLE (automatizace)|
|[Výjimka CUserException](../../mfc/reference/cuserexception-class.md)|Výjimka, která označuje, že prostředek nebyl nalezen.|
|[Výjimka CDao](../../mfc/reference/cdaoexception-class.md)|Výjimka objektu přístupu k datům (to znamená podmínky výjimky vznikající pro třídy DAO)|
|[Výjimka CInternet](../../mfc/reference/cinternetexception-class.md)|Internetová výjimka (to znamená podmínky výjimky vznikající pro internetové třídy).|

Tyto výjimky jsou určeny pro použití s [makry THROW](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [try](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch](exception-processing.md#and_catch)a [end_catch.](exception-processing.md#end_catch) Další informace o výjimkách naleznete v [tématu Zpracování výjimek](exception-processing.md)nebo v článku [Zpracování výjimek (MFC).](../exception-handling-in-mfc.md)

Chcete-li zachytit konkrétní výjimku, použijte příslušnou odvozenou třídu. Chcete-li zachytit všechny typy `CException`výjimek, použijte a potom použijte [CObject::IsKindOf](cobject-class.md#iskindof) k rozlišení mezi `CException`odvozenými třídami. Všimněte `CObject::IsKindOf` si, že funguje pouze pro třídy deklarované s [makro IMPLEMENT_DYNAMIC,](run-time-object-model-services.md#implement_dynamic) aby bylo možné využít dynamické kontroly typu. Všechny `CException`-odvozené třídy, které `IMPLEMENT_DYNAMIC` vytvoříte by měl použít makro, taky.

Podrobnosti o výjimkách pro uživatele můžete hlásit voláním [GetErrorMessage](cfileexception-class.md#geterrormessage) nebo [ReportError](#reporterror), dvou členských funkcí, které pracují s některou z `CException`odvozených tříd společnosti .

Pokud je výjimka zachycena jedním z `CException` maker, objekt se odstraní automaticky; neodstraňujte jej sami. Pokud je výjimka zachycena pomocí klíčového slova **catch,** není automaticky odstraněna. Další informace o tom, kdy odstranit objekt exeption, naleznete v článku [Zpracování výjimek (MFC).](../exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](cobject-class.md)

`CException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cexceptioncexception"></a><a name="cexception"></a>CException::CException

Tato členská funkce `CException` vytvoří objekt.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*b_AutoDelete*<br/>
Zadejte hodnotu TRUE, pokud byla na haldě přidělena paměť `CException` pro objekt. To způsobí, `CException` že objekt, `Delete` který má být odstraněn, když je volána členská funkce k odstranění výjimky. Zadejte hodnotu NEPRAVDA, `CException` pokud je objekt v zásobníku nebo je globálním objektem. V takovém případě `CException` nebude objekt odstraněn `Delete` při volání členské funkce.

### <a name="remarks"></a>Poznámky

Za normálních okolností by nikdy nutné volat tento konstruktor přímo. Funkce, která vyvolá výjimku by měla `CException`vytvořit instanci odvozené třídy a volat jeho konstruktor, nebo by měla použít jednu z funkcí mfc throw, jako je například [AfxThrowFileException](exception-processing.md#afxthrowfileexception), k vyvolání předdefinovaného typu. Tato dokumentace je k dispozici pouze pro úplnost.

## <a name="cexceptiondelete"></a><a name="delete"></a>CException::Delete

Tato funkce zkontroluje, `CException` zda byl objekt vytvořen na haldě, a pokud ano, volá operátor **delete** na objektu.

```
void Delete();
```

### <a name="remarks"></a>Poznámky

Při odstraňování objektu `CException` použijte `Delete` členovou funkci k odstranění výjimky. Nepoužívejte operátor **delete** přímo, `CException` protože objekt může být globální objekt nebo byly vytvořeny v zásobníku.

Můžete určit, zda má být objekt odstraněn při vytvoření objektu. Další informace naleznete v [tématu CException::CException](#cexception).

Stačí volat, `Delete` pokud používáte c++ **zkuste**- **catch** mechanismus. Pokud používáte makra knihovny MFC **TRY** a **CATCH**, budou tato makra automaticky volat tuto funkci.

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

## <a name="cexceptionreporterror"></a><a name="reporterror"></a>CException::Chyba sestavy

Volání této členské funkce pro hlášení textu chyby v poli se zprávou uživateli.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>Parametry

*nTyp*<br/>
Určuje styl okna se zprávou. Použijte libovolnou kombinaci [stylů okno se zprávou](styles-used-by-mfc.md#message-box-styles) do pole. Pokud tento parametr nezadáte, výchozí hodnota je MB_OK.

*nID zprávy*<br/>
Určuje ID prostředku (položku tabulky řetězců) zprávy, která se má zobrazit, pokud objekt výjimky nemá chybovou zprávu. Pokud 0, zobrazí se zpráva "Není k dispozici žádná chybová zpráva".

### <a name="return-value"></a>Návratová hodnota

Hodnota; `AfxMessageBox` jinak 0, pokud není dostatek paměti pro zobrazení okna se zprávou. Možné vrácené hodnoty naleznete v poli [AfxMessageBox.](cstring-formatting-and-message-box-display.md#afxmessagebox)

### <a name="example"></a>Příklad

Zde je příklad použití `CException::ReportError`. Další příklad naleznete v příkladu [catch](exception-processing.md#catch).

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

[CObject – třída](cobject-class.md)<br/>
[Graf hierarchie](../hierarchy-chart.md)<br/>
[Zpracování výjimek](exception-processing.md)<br/>
[Jak mohu: Vytvořit vlastní vlastní třídy výjimek](https://go.microsoft.com/fwlink/p/?linkid=128045)
