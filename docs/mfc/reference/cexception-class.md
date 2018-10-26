---
title: Cexception – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
dev_langs:
- C++
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3de077e636f0dfdd1ab046a57a81808b3f80357e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052834"
---
# <a name="cexception-class"></a>Cexception – třída

Základní třída pro všechny výjimky knihovny Microsoft Foundation Class.

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
|[CException::ReportError](#reporterror)|Sestavy chybová zpráva v okně se zprávou pro uživatele.|

## <a name="remarks"></a>Poznámky

Protože `CException` je abstraktní základní třídu nelze vytvořit `CException` objekty přímo; je nutné vytvořit objekty odvozené třídy. Pokud je potřeba vytvořit vlastní `CException`– styl třídy, použijte jednu z odvozených tříd uvedených jako model. Ujistěte se, že odvozené třídy také používá `IMPLEMENT_DYNAMIC`.

Odvozené třídy a jejich popisy jsou uvedeny níže:

|||
|-|-|
|[Csimpleexception –](../../mfc/reference/csimpleexception-class.md)|Základní třída pro výjimky kritických zdrojů MFC|
|[Cinvalidargexception –](../../mfc/reference/cinvalidargexception-class.md)|Podmínku výjimky neplatného argumentu|
|[Cmemoryexception –](../../mfc/reference/cmemoryexception-class.md)|Výjimka mimo z důvodu nedostatku paměti|
|[Cnotsupportedexception –](../../mfc/reference/cnotsupportedexception-class.md)|Žádost o nepodporovanou operaci|
|[Carchiveexception –](../../mfc/reference/carchiveexception-class.md)|Archiv specifické výjimky|
|[Cfileexception –](../../mfc/reference/cfileexception-class.md)|Výjimka konkrétního souboru|
|[Cresourceexception –](../../mfc/reference/cresourceexception-class.md)|Windows prostředek nebyl nalezen nebo není možné vytvořit|
|[Coleexception –](../../mfc/reference/coleexception-class.md)|OLE – výjimka|
|[CDBException](../../mfc/reference/cdbexception-class.md)|Výjimky databáze (to znamená, že výjimka okolnosti, které pro databázových tříd MFC založených na Open Database Connectivity)|
|[Coledispatchexception –](../../mfc/reference/coledispatchexception-class.md)|Výjimka odeslání (Automatizace) OLE|
|[Cuserexception –](../../mfc/reference/cuserexception-class.md)|Výjimka, která označuje, že prostředek nebyl nalezen.|
|[Cdaoexception –](../../mfc/reference/cdaoexception-class.md)|Objekt výjimky (to znamená, že výjimka okolnosti, které pro třídy DAO) pro přístup k datům|
|[Cinternetexception –](../../mfc/reference/cinternetexception-class.md)|Výjimka Internetu (to znamená, že výjimka okolnosti, které třídy internetových).|

Tyto výjimky jsou určeny pro použití s [THROW](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [zkuste](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch](exception-processing.md#and_catch), a [end_catch](exception-processing.md#end_catch) makra. Další informace o výjimkách, naleznete v tématu [zpracování výjimek](exception-processing.md), nebo se podívejte článek [zpracování výjimek (MFC)](../exception-handling-in-mfc.md).

Chcete-li zachytit specifické výjimky, použijte příslušná odvozená třída. Chcete-li catch, všechny typy výjimek, použijte `CException`a pak použijte [CObject::IsKindOf](cobject-class.md#iskindof) k rozlišení mezi `CException`-odvozené třídy. Všimněte si, že `CObject::IsKindOf` platí jenom pro třídy deklarované s [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) – makro, aby bylo možné využít výhod dynamického typu kontroly. Žádné `CException`-odvozené třídy, které vytvoříte, používejte `IMPLEMENT_DYNAMIC` – makro, příliš.

Podrobnosti o výjimkách uživateli můžete sestavy voláním [GetErrorMessage](cfileexception-class.md#geterrormessage) nebo [ReportError](#reporterror), dva členské funkce, které pracují s žádným z `CException`v odvozených třídách.

Pokud výjimku zachycuje se prostřednictvím jednoho z maker, `CException` objekt automaticky odstraněn, neodstraňujte ho sami. Pokud je výjimka zachycena pomocí **catch** – klíčové slovo, není automaticky odstraněn. Přečtěte si článek [zpracování výjimek (MFC)](../exception-handling-in-mfc.md) Další informace o tom, kdy se odstranit objekt geosyncservice.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="cexception"></a>  CException::CException

Tato členská funkce vytvoří `CException` objektu.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*b_AutoDelete*<br/>
Zadejte hodnotu PRAVDA, pokud paměť pro `CException` objekt byl přidělen na haldě. To způsobí, že `CException` objektu, který chcete odstranit, když `Delete` členská funkce je volána k odstranění výjimku. Zadejte hodnotu FALSE, pokud `CException` objekt v zásobníku nebo je globální objekt. V tomto případě `CException` objektů nebudou odstraněny při `Delete` členská funkce je volána.

### <a name="remarks"></a>Poznámky

Je třeba obvykle nikdy přímo volání tohoto konstruktoru. Funkce, která vyvolá výjimku, by měl vytvořit instanci `CException`-odvozené třídy a volání konstruktoru, nebo použijte jedno z knihovny MFC vyvoláním funkce, jako například [afxthrowfileexception –](exception-processing.md#afxthrowfileexception), vyvolání předdefinovaný typ. Tato dokumentace je k dispozici pouze pro úplnost.

##  <a name="delete"></a>  CException::Delete

Tato funkce zkontroluje, zda `CException` objekt byl vytvořen na haldě, a pokud ano, zavolá **odstranit** operátor v objektu.

```
void Delete();
```

### <a name="remarks"></a>Poznámky

Při odstraňování `CException` objektu, použijte `Delete` členská funkce se odstranit výjimky. Nepoužívejte **odstranit** operátor přímo, protože `CException` objekt může být globální objekt nebo byly vytvořeny v zásobníku.

Můžete určit, zda by měl objekt odstranit při vytvoření objektu. Další informace najdete v tématu [CException::CException](#cexception).

Je třeba volat `Delete` Pokud používáte C++ **zkuste**- **catch** mechanismus. Pokud používáte makra MFC **zkuste** a **CATCH**, pak tato makra bude automaticky voláním této funkce.

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

##  <a name="reporterror"></a>  CException::ReportError

Voláním této členské funkce text chybové zprávy v okně se zprávou pro uživatele.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>Parametry

*nTyp*<br/>
Určuje styl okna se zprávou. Použít libovolnou kombinaci [styly oken zpráv](styles-used-by-mfc.md#message-box-styles) do pole. Pokud tento parametr nezadáte, použije se MB_OK.

*nMessageID*<br/>
Určuje ID prostředku (položky tabulky řetězců) zpráva se zobrazí, pokud objekt výjimky nemá chybovou zprávu. Zobrazí se v případě 0, zpráva "není žádná chybová zpráva k dispozici".

### <a name="return-value"></a>Návratová hodnota

`AfxMessageBox` Hodnotu; jinak 0, pokud není k dispozici dostatek paměti k zobrazení okna se zprávou. Zobrazit [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) pro možných vrácených hodnot.

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

[CObject – třída](cobject-class.md)<br/>
[Graf hierarchie](../hierarchy-chart.md)<br/>
[Zpracování výjimek](exception-processing.md)<br/>
[Jak mohu: vytvořit vlastní třídy vlastní výjimky](http://go.microsoft.com/fwlink/p/?linkid=128045)

